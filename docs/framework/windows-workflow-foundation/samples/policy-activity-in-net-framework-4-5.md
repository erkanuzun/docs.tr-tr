---
title: .NET Framework 4.5 ilke etkinlik
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e375e0c-d7c1-4d69-88ab-36d52db0aa7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 68c81b81ac8070cff539b52c75e1cd7ffb3e54b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="policy-activity-in-net-framework-45"></a><span data-ttu-id="b012b-102">.NET Framework 4.5 ilke etkinlik</span><span class="sxs-lookup"><span data-stu-id="b012b-102">Policy Activity in .NET Framework 4.5</span></span>
<span data-ttu-id="b012b-103">Policy4 etkinlik verir [!INCLUDE[wf2](../../../../includes/wf2-md.md)] içinde [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> kullanılacak nesneleri [!INCLUDE[wf2](../../../../includes/wf2-md.md)] içinde [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) WF 3. 5 ' sevk kurallar altyapısı kullanarak doğrudan.</span><span class="sxs-lookup"><span data-stu-id="b012b-103">The Policy4 activity allows [!INCLUDE[wf2](../../../../includes/wf2-md.md)] in [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects to be used in [!INCLUDE[wf2](../../../../includes/wf2-md.md)] in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span> <span data-ttu-id="b012b-104">Bu etkinlik kullanarak oluşturma ve WF 3.5 yürütme <xref:System.Workflow.Activities.Rules.RuleSet>.</span><span class="sxs-lookup"><span data-stu-id="b012b-104">By using this activity, you can create and execute a WF 3.5 <xref:System.Workflow.Activities.Rules.RuleSet>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b012b-105">WF 3.5 kural Windows Workflow Foundation, bir parçası olarak dahil edilen altyapısı Lütfen Windows Workflow Foundation kurallar altyapısı giriş okuyun.</span><span class="sxs-lookup"><span data-stu-id="b012b-105"> WF 3.5 Rules Engine included as part of Windows Workflow Foundation, please read Introduction to the Windows Workflow Foundation Rules Engine.</span></span> <span data-ttu-id="b012b-106">Geçiş hakkında daha fazla bilgi için WF kuralları [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], Lütfen okuyun [Geçiş Kılavuzu](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="b012b-106">For more information about migrating rules to WF in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], please read [Migration Guidance](../../../../docs/framework/windows-workflow-foundation/migration-guidance.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b012b-107">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b012b-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b012b-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b012b-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b012b-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b012b-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b012b-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b012b-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Rules-Policy4`  
  
## <a name="projects-in-this-sample"></a><span data-ttu-id="b012b-111">Bu örnek proje</span><span class="sxs-lookup"><span data-stu-id="b012b-111">Projects in this Sample</span></span>  
  
|<span data-ttu-id="b012b-112">Proje adı</span><span class="sxs-lookup"><span data-stu-id="b012b-112">Project Name</span></span>|<span data-ttu-id="b012b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b012b-113">Description</span></span>|<span data-ttu-id="b012b-114">Ana dosyaları</span><span class="sxs-lookup"><span data-stu-id="b012b-114">Main Files</span></span>|  
|------------------|-----------------|----------------|  
|<span data-ttu-id="b012b-115">Policy4</span><span class="sxs-lookup"><span data-stu-id="b012b-115">Policy4</span></span>|<span data-ttu-id="b012b-116">Policy4 etkinlik içerir ve kendi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="b012b-116">Contains the Policy4 activity and its [!INCLUDE[wf1](../../../../includes/wf1-md.md)] designer.</span></span>|<span data-ttu-id="b012b-117">**Policy4.cs**: Policy4 etkinlik tanımı.</span><span class="sxs-lookup"><span data-stu-id="b012b-117">**Policy4.cs**: Policy4 activity definition.</span></span><br /><br /> <span data-ttu-id="b012b-118">**PolicyDesigner.xaml**: özel Tasarımcısı Policy4 etkinliği.</span><span class="sxs-lookup"><span data-stu-id="b012b-118">**PolicyDesigner.xaml**: Custom designer for Policy4 activity.</span></span> <span data-ttu-id="b012b-119">Kuralları Düzenleyicisi'ni kullanır ([RuleSetDialog sınıfı](http://go.microsoft.com/fwlink/?LinkId=150378)) gelen [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kurallar altyapısı.</span><span class="sxs-lookup"><span data-stu-id="b012b-119">It uses the rules editor ([RuleSetDialog Class](http://go.microsoft.com/fwlink/?LinkId=150378)) from [!INCLUDE[wf1](../../../../includes/wf1-md.md)] rules engine.</span></span>|  
|<span data-ttu-id="b012b-120">ImperativeCodeClientSample</span><span class="sxs-lookup"><span data-stu-id="b012b-120">ImperativeCodeClientSample</span></span>|<span data-ttu-id="b012b-121">Örnek yapılandırır ve kesinlik temelli C# kod kullanarak bir Policy4 uygulaması kullanarak bir iş akışı çalıştıran istemci uygulaması (hiçbir [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kullanılan Designer).</span><span class="sxs-lookup"><span data-stu-id="b012b-121">Sample client application that configures and runs a workflow using a Policy4 application using imperative C# code (no [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Designer used).</span></span>|<span data-ttu-id="b012b-122">**ApplyDiscount.rules**: ile dosya [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kural tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b012b-122">**ApplyDiscount.rules**: File with [!INCLUDE[wf1](../../../../includes/wf1-md.md)] rule definitions.</span></span><br /><br /> <span data-ttu-id="b012b-123">**Order.cs**: Müşteri siparişi temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="b012b-123">**Order.cs**: Type that represents a customer order.</span></span> <span data-ttu-id="b012b-124">Kuralları, bu tür nesnelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b012b-124">Rules are applied to objects of this type.</span></span><br /><br /> <span data-ttu-id="b012b-125">**Program.cs**: yapılandırır ve sipariş nesnelerinin örneklerini ApplyDiscount.rules tanımlanmış kuralları uygulamak için Policy4 etkinlik sahip bir iş akışı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b012b-125">**Program.cs**: Configures and runs a workflow that has a Policy4 activity to apply rules defined in ApplyDiscount.rules to instances of Order objects.</span></span><br /><br /> <span data-ttu-id="b012b-126">**App.config**: kuralları dosyasının yolunu yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="b012b-126">**App.config**: Configuration file with the path of the rules file.</span></span>|  
|<span data-ttu-id="b012b-127">DesignerClientSample</span><span class="sxs-lookup"><span data-stu-id="b012b-127">DesignerClientSample</span></span>|<span data-ttu-id="b012b-128">Örnek yapılandırır ve bir Policy4 uygulaması kullanarak bir iş akışı çalıştıran istemci uygulamanın [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="b012b-128">Sample client application that configures and runs a workflow using a Policy4 application in the [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Designer.</span></span>|<span data-ttu-id="b012b-129">**Sequence1.XAML**: Policy4 etkinlik kural değerlendirmesi gerçekleştirmek için kullandığı sıralı iş akışı.</span><span class="sxs-lookup"><span data-stu-id="b012b-129">**Sequence1.xaml**: Sequential workflow that uses a Policy4 activity to perform rule evaluations.</span></span><br /><br /> <span data-ttu-id="b012b-130">`Program.cs`: Sequence1.xaml içinde tanımlanan iş akışı örneğini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b012b-130">`Program.cs`: Runs an instance of the workflow defined in Sequence1.xaml.</span></span>|  
  
## <a name="the-policy4-activity"></a><span data-ttu-id="b012b-131">Policy4 etkinliği</span><span class="sxs-lookup"><span data-stu-id="b012b-131">The Policy4 Activity</span></span>  
 <span data-ttu-id="b012b-132">Öğesinden türeyen bir sınıf Policy4 etkinliktir <xref:System.Activities.NativeActivity%601> yürütmek için iş akışlarını tanır [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets.</span><span class="sxs-lookup"><span data-stu-id="b012b-132">The Policy4 activity is a class that derives from <xref:System.Activities.NativeActivity%601> that allows workflows to execute [!INCLUDE[wf1](../../../../includes/wf1-md.md)] RuleSets.</span></span> <span data-ttu-id="b012b-133">Aşağıdaki kod örneği, etkinlik ortak OM Basitleştirilmiş tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="b012b-133">The following code example is a simplified definition of the public OM of the activity.</span></span>  
  
```csharp  
public class Policy4Activity<TResult>: NativeActivity<TResult>  
{  
    public RuleSet RuleSet  
  
    [IsRequired]  
    public InArgument Input  
  
    public OutArgument<ValidationErrorCollection> ValidationErrors  
}  
```  
  
|<span data-ttu-id="b012b-134">Özellik</span><span class="sxs-lookup"><span data-stu-id="b012b-134">Property</span></span>|<span data-ttu-id="b012b-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b012b-135">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b012b-136">RuleSet</span><span class="sxs-lookup"><span data-stu-id="b012b-136">RuleSet</span></span>|<span data-ttu-id="b012b-137">WF [RuleSet sınıfı](http://go.microsoft.com/fwlink/?LinkId=150379) etkinlik çalıştırıldığında değerlendirilecek .NET Framework 3.5 için.</span><span class="sxs-lookup"><span data-stu-id="b012b-137">The WF [RuleSet Class](http://go.microsoft.com/fwlink/?LinkId=150379) for .NET Framework 3.5 to be evaluated when the activity is executed.</span></span>|  
|<span data-ttu-id="b012b-138">TargetObject</span><span class="sxs-lookup"><span data-stu-id="b012b-138">TargetObject</span></span>|<span data-ttu-id="b012b-139">Nesneyle kurallarında [RuleSet sınıfı](http://go.microsoft.com/fwlink/?LinkId=150379) değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b012b-139">The object against which the Rules in the [RuleSet Class](http://go.microsoft.com/fwlink/?LinkId=150379) are evaluated.</span></span>|  
|<span data-ttu-id="b012b-140">ValidationError</span><span class="sxs-lookup"><span data-stu-id="b012b-140">ValidationError</span></span>|<span data-ttu-id="b012b-141">Tarafından döndürülen doğrulama hataları listesine [!INCLUDE[wf1](../../../../includes/wf1-md.md)] kuralı altyapısı doğrularken .NET Framework 3.5 için [RuleSet sınıfı](http://go.microsoft.com/fwlink/?LinkId=150379) karşı yürütmeden önce hedef nesne.</span><span class="sxs-lookup"><span data-stu-id="b012b-141">The list of validation errors returned by the [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Rule Engine for .NET Framework 3.5 when validating the [RuleSet Class](http://go.microsoft.com/fwlink/?LinkId=150379) against the target object before execution.</span></span>|  
  
## <a name="policy4-activity-designer"></a><span data-ttu-id="b012b-142">Policy4 etkinlik Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="b012b-142">Policy4 Activity Designer</span></span>  
 <span data-ttu-id="b012b-143">Policy4 Tasarımcısı Policy4 etkinlik kod yazmak zorunda kalmadan yapılandırma yeteneği ekler.</span><span class="sxs-lookup"><span data-stu-id="b012b-143">The Policy4 designer adds the capability to configure a Policy4 activity without the need to write code.</span></span> <span data-ttu-id="b012b-144">Çözümü derledikten sonra şu araç kutusunda bölümünde bulunabilir **Microsoft.Samples.Activities.Rules**.</span><span class="sxs-lookup"><span data-stu-id="b012b-144">After building the solution, it can be found in the toolbox in the section **Microsoft.Samples.Activities.Rules**.</span></span>  
  
 <span data-ttu-id="b012b-145">WF Tasarımcısı, hedef nesnesi ve bir RuleSet yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b012b-145">The WF Designer allows you to configure a target object and a RuleSet.</span></span> <span data-ttu-id="b012b-146">Zaman **Düzenle RuleSet** düğmesine tıklandığında, WF [RuleSetDialog sınıfı](http://go.microsoft.com/fwlink/?LinkId=150378) için [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b012b-146">When the **Edit RuleSet** button is clicked, the WF [RuleSetDialog Class](http://go.microsoft.com/fwlink/?LinkId=150378) for [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] is displayed.</span></span> <span data-ttu-id="b012b-147">Bu iletişim kutusunu yeniden barındırılır [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] kurallar düzenleyicisinde.</span><span class="sxs-lookup"><span data-stu-id="b012b-147">This dialog is the re-hosted [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Rules Editor.</span></span> <span data-ttu-id="b012b-148">Düzenleyici oluşturmak ve Policy4 etkinlik yürütür kuralları düzenlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b012b-148">Use the editor to create and edit the rules that the Policy4 activity executes.</span></span>  
  
## <a name="using-this-sample"></a><span data-ttu-id="b012b-149">Bu örnek kullanma</span><span class="sxs-lookup"><span data-stu-id="b012b-149">Using this Sample</span></span>  
 <span data-ttu-id="b012b-150">Hiçbir özel ayarlama, bu örneği çalıştırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b012b-150">No special set up is required to run this sample.</span></span> <span data-ttu-id="b012b-151">Yalnızca Visual Studio'da Çözüm açmak ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b012b-151">Just open the solution in Visual Studio, and press F5 to run the application.</span></span>  
  
 <span data-ttu-id="b012b-152">Bu örnek iki istemci uygulamaları içerir: ImperativeCodeClientSample ve DesignerClientSample.</span><span class="sxs-lookup"><span data-stu-id="b012b-152">This sample contains two client applications: ImperativeCodeClientSample and DesignerClientSample.</span></span> <span data-ttu-id="b012b-153">ImperativeCodeClientSample istemci, yapılandırma ve C# kesinlik temelli kodu kullanarak Policy40 etkinliği çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b012b-153">The ImperativeCodeClientSample client shows how to configure and run the Policy40 activity using C# imperative code.</span></span> <span data-ttu-id="b012b-154">DesignerClientSample, yapılandırma ve çalıştırma Tasarımcısı'nı kullanarak Policy4 etkinliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b012b-154">The DesignerClientSample shows how to configure and run the Policy4 activity using the designer.</span></span>  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a><span data-ttu-id="b012b-155">ImperativeCodeClientSample istemci uygulamasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b012b-155">To run the ImperativeCodeClientSample client application</span></span>  
  
1.  <span data-ttu-id="b012b-156">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4Sample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b012b-156">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Policy4Sample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b012b-157">İçinde **Çözüm Gezgini**, sağ **ImperativeCodeClientSample** proje ve ardından **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="b012b-157">In **Solution Explorer**, right-click the **ImperativeCodeClientSample** project and then select **Set as startup project**.</span></span>  
  
3.  <span data-ttu-id="b012b-158">Projeyi çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b012b-158">To run the project, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-imperativecodeclientsample-client-application"></a><span data-ttu-id="b012b-159">ImperativeCodeClientSample istemci uygulamasını çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b012b-159">To run the ImperativeCodeClientSample client application</span></span>  
  
1.  <span data-ttu-id="b012b-160">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Policy4Sample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b012b-160">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Policy4Sample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b012b-161">İçinde **Çözüm Gezgini**, sağ **DesignerClientSample** projesi.</span><span class="sxs-lookup"><span data-stu-id="b012b-161">In **Solution Explorer**, right-click the **DesignerClientSample** project.</span></span>  
  
    -   <span data-ttu-id="b012b-162">Seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="b012b-162">Select **Set as startup project**.</span></span>  
  
3.  <span data-ttu-id="b012b-163">Projeyi derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b012b-163">To compile the project, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="b012b-164">Projeyi çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b012b-164">To run the project, press CTRL+F5.</span></span>