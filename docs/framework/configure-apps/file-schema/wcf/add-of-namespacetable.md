---
title: '&lt;namespaceTable&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f159e3d92fdc7443cd20cf88300f331b78273ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="3353e-102">&lt;namespaceTable&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="3353e-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="3353e-103">Ardından yönlendirme XPath filtreleri kullanılabilir eşleme öneki için bir ad alanı içeren bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3353e-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="3353e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3353e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3353e-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="3353e-105">\<routing></span></span>  
<span data-ttu-id="3353e-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="3353e-106">\<namespaceTable></span></span>  
<span data-ttu-id="3353e-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="3353e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3353e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3353e-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3353e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3353e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3353e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3353e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3353e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3353e-111">Attributes</span></span>  
  
|<span data-ttu-id="3353e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3353e-112">Attribute</span></span>|<span data-ttu-id="3353e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3353e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3353e-114">ad alanı</span><span class="sxs-lookup"><span data-stu-id="3353e-114">namespace</span></span>|<span data-ttu-id="3353e-115">Ad alanı içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3353e-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="3353e-116">önek</span><span class="sxs-lookup"><span data-stu-id="3353e-116">prefix</span></span>|<span data-ttu-id="3353e-117">Bu ad alanı öneki içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3353e-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3353e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3353e-118">Child Elements</span></span>  
 <span data-ttu-id="3353e-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="3353e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3353e-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3353e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3353e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="3353e-121">Element</span></span>|<span data-ttu-id="3353e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3353e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3353e-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="3353e-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="3353e-124">Ardından yönlendirme XPath filtreleri kullanılabilir önek eşlemeleri için ad alanı içeren öğeleri kümesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3353e-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3353e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3353e-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    