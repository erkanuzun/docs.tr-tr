---
title: "Windows iş akışı mimarisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1b58456fe99331a47871fbf4b1ad86cd43c53c2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="windows-workflow-architecture"></a><span data-ttu-id="898ea-102">Windows iş akışı mimarisi</span><span class="sxs-lookup"><span data-stu-id="898ea-102">Windows Workflow Architecture</span></span>
[!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="898ea-103">Etkileşimli uzun süre çalışan uygulamalar geliştirmek için özet düzeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="898ea-103"> raises the abstraction level for developing interactive long-running applications.</span></span> <span data-ttu-id="898ea-104">İş birimleri etkinlikler olarak kapsüllenir.</span><span class="sxs-lookup"><span data-stu-id="898ea-104">Units of work are encapsulated as activities.</span></span> <span data-ttu-id="898ea-105">Olanakları sağlar akış denetimi, özel durum işleme, arıza yayma, yüklenmesi ve devam eden iş akışlarının bellek, izleme ve işlem akışı kaldırılması durumu verilerinin kalıcılığı için bir ortamda etkinlikleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="898ea-105">Activities run in an environment that provides facilities for flow control, exception handling, fault propagation, persistence of state data, loading and unloading of in-progress workflows from memory, tracking, and transaction flow.</span></span>  
  
## <a name="activity-architecture"></a><span data-ttu-id="898ea-106">Etkinlik mimarisi</span><span class="sxs-lookup"><span data-stu-id="898ea-106">Activity Architecture</span></span>  
 <span data-ttu-id="898ea-107">Etkinliklerin herhangi birinden türetilen CLR türleri olarak geliştirilen <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, veya <xref:System.Activities.NativeActivity>, veya bir değer döndürmesi bunların türevleri <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, veya <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="898ea-107">Activities are developed as CLR types that derive from either <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>, or their variants that return a value, <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601>, or <xref:System.Activities.NativeActivity%601>.</span></span> <span data-ttu-id="898ea-108">Öğesinden türetilen etkinliklerini geliştirme <xref:System.Activities.Activity> hızlı bir şekilde iş akışı ortamında yürütme iş birimleri oluşturmak için önceden var olan etkinlikleri derleyecek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="898ea-108">Developing activities that derive from <xref:System.Activities.Activity> allows the user to assemble pre-existing activities to quickly create units of work that execute in the workflow environment.</span></span> <span data-ttu-id="898ea-109"><xref:System.Activities.CodeActivity>, diğer yandan, yönetilen kod kullanarak yazılmasını yürütme mantığını etkinleştirir <xref:System.Activities.CodeActivityContext> etkinlik bağımsız değişken erişimi için öncelikle.</span><span class="sxs-lookup"><span data-stu-id="898ea-109"><xref:System.Activities.CodeActivity>, on the other hand, enables execution logic to be authored in managed code using <xref:System.Activities.CodeActivityContext> primarily for access to activity arguments.</span></span> <span data-ttu-id="898ea-110"><xref:System.Activities.AsyncCodeActivity>benzer <xref:System.Activities.CodeActivity> dışında zaman uyumsuz görevleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="898ea-110"><xref:System.Activities.AsyncCodeActivity> is similar to <xref:System.Activities.CodeActivity> except that it can be used to implement asynchronous tasks.</span></span> <span data-ttu-id="898ea-111">Öğesinden türetilen etkinliklerini geliştirme <xref:System.Activities.NativeActivity> çalışma zamanı üzerinden erişmesine olanak tanır <xref:System.Activities.NativeActivityContext> alt yer işaretleri, oluşturma, zamanlama gibi işlevler için zaman uyumsuz iş kayıt işlemleri ve çok çağırma.</span><span class="sxs-lookup"><span data-stu-id="898ea-111">Developing activities that derive from <xref:System.Activities.NativeActivity> allows users to access the runtime through the <xref:System.Activities.NativeActivityContext> for functionality like scheduling children, creating bookmarks, invoking asynchronous work, registering transactions, and more.</span></span>  
  
 <span data-ttu-id="898ea-112">Öğesinden türetilen etkinlikleri yazma <xref:System.Activities.Activity> tanımlayıcıdır ve bu etkinlikler XAML'de yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="898ea-112">Authoring activities that derive from <xref:System.Activities.Activity> is declarative and these activities can be authored in XAML.</span></span> <span data-ttu-id="898ea-113">Aşağıdaki örnekte, bir etkinlik olarak adlandırılan `Prompt` yürütme gövdesi için diğer etkinlikleri kullanarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="898ea-113">In the following example, an activity called `Prompt` is created using other activities for the execution body.</span></span>  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a><span data-ttu-id="898ea-114">Etkinlik bağlamı</span><span class="sxs-lookup"><span data-stu-id="898ea-114">Activity Context</span></span>  
 <span data-ttu-id="898ea-115"><xref:System.Activities.ActivityContext> İş akışı çalışma zamanı için etkinlik yazarın arabirimi ve özellikleri zamanının bol erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="898ea-115">The <xref:System.Activities.ActivityContext> is the activity author's interface to the workflow runtime and provides access to the runtime's wealth of features.</span></span> <span data-ttu-id="898ea-116">Aşağıdaki örnekte, bir etkinlik yürütme bağlamı yer işareti (bir devamlılık noktası verileri activity içine geçirmeden bir ana bilgisayar tarafından sürdürülebilecek yürütülmesinin kaydetmek için bir etkinlik sağlar mekanizması) oluşturmak için kullandığı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="898ea-116">In the following example, an activity is defined that uses the execution context to create a bookmark (the mechanism that allows an activity to register a continuation point in its execution that can be resumed by a host passing data into the activity).</span></span>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a><span data-ttu-id="898ea-117">Etkinlik yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="898ea-117">Activity Life Cycle</span></span>  
 <span data-ttu-id="898ea-118">Bir etkinliği örneği başlatır <xref:System.Activities.ActivityInstanceState.Executing> durumu.</span><span class="sxs-lookup"><span data-stu-id="898ea-118">An instance of an activity starts out in the <xref:System.Activities.ActivityInstanceState.Executing> state.</span></span> <span data-ttu-id="898ea-119">Özel durumlar karşılaşılan sürece tüm alt etkinlikleri çalıştırma ve diğer iş bekleyen tamamlanana kadar bu durumda kalır (<xref:System.Activities.Bookmark> nesneleri, örneğin) tamamlandığında, anda bunu geçişleri <xref:System.Activities.ActivityInstanceState.Closed> durumu.</span><span class="sxs-lookup"><span data-stu-id="898ea-119">Unless exceptions are encountered, it remains in this state until all child activities are finished executing and any other pending work (<xref:System.Activities.Bookmark> objects, for instance) is completed, at which point it transitions to the <xref:System.Activities.ActivityInstanceState.Closed> state.</span></span> <span data-ttu-id="898ea-120">Bir etkinlik örneğinin üst iptal etmek için bir alt isteyebilir; alt iptal ederse tamamlanır <xref:System.Activities.ActivityInstanceState.Canceled> durumu.</span><span class="sxs-lookup"><span data-stu-id="898ea-120">The parent of an activity instance can request a child to cancel; if the child is able to be canceled it completes in the <xref:System.Activities.ActivityInstanceState.Canceled> state.</span></span> <span data-ttu-id="898ea-121">Yürütme sırasında bir özel durum, çalışma zamanı etkinliğe koyar <xref:System.Activities.ActivityInstanceState.Faulted> belirtin ve özel etkinlikleri üst zincirine yukarı yayar.</span><span class="sxs-lookup"><span data-stu-id="898ea-121">If an exception is thrown during execution, the runtime puts the activity into the <xref:System.Activities.ActivityInstanceState.Faulted> state and propagates the exception up the parent chain of activities.</span></span> <span data-ttu-id="898ea-122">Bir etkinlik üç tamamlanma durumunu şunlardır:</span><span class="sxs-lookup"><span data-stu-id="898ea-122">Following are the three completion states of an activity:</span></span>  
  
-   <span data-ttu-id="898ea-123">**Kapalı:** etkinlik kendi iş tamamlandı ve çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="898ea-123">**Closed:** The activity has completed its work and exited.</span></span>  
  
-   <span data-ttu-id="898ea-124">**İptal edilen:** etkinliği düzgün bir şekilde çalışmasını terk ve çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="898ea-124">**Canceled:** The activity has gracefully abandoned its work and exited.</span></span> <span data-ttu-id="898ea-125">Bu durum geri girildiğinde, iş açıkça döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="898ea-125">Work is not explicitly rolled back when this state is entered.</span></span>  
  
-   <span data-ttu-id="898ea-126">**Hatalı:** etkinliği bir hatayla karşılaştı ve çalışmasını tamamlamadan çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="898ea-126">**Faulted:** The activity has encountered an error and has exited without completing its work.</span></span>  
  
 <span data-ttu-id="898ea-127">Etkinlikler kalır <xref:System.Activities.ActivityInstanceState.Executing> kalıcı veya kaldırıldı durumu.</span><span class="sxs-lookup"><span data-stu-id="898ea-127">Activities remain in the <xref:System.Activities.ActivityInstanceState.Executing> state when they are persisted or unloaded.</span></span>