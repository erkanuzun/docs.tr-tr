---
title: '&lt;commonParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbb67714a58df0c5ccec86c7eac85a5194d780a5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="5e96d-102">&lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="5e96d-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="5e96d-103">Birden fazla hizmet genel olarak kullanılan parametreleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e96d-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="5e96d-104">Bu koleksiyon genellikle sürekli hizmetler tarafından paylaşılan veritabanı bağlantı dizesi içerir.</span><span class="sxs-lookup"><span data-stu-id="5e96d-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="5e96d-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e96d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e96d-106">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="5e96d-106">\<behaviors></span></span>  
<span data-ttu-id="5e96d-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5e96d-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="5e96d-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5e96d-108">\<behavior></span></span>  
<span data-ttu-id="5e96d-109">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="5e96d-109">\<workflowRuntime></span></span>  
<span data-ttu-id="5e96d-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="5e96d-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e96d-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e96d-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e96d-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e96d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5e96d-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e96d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e96d-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e96d-114">Attributes</span></span>  
 <span data-ttu-id="5e96d-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e96d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5e96d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e96d-116">Child Elements</span></span>  
  
|<span data-ttu-id="5e96d-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e96d-117">Element</span></span>|<span data-ttu-id="5e96d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e96d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e96d-119">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="5e96d-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="5e96d-120">Bir ad-değer çifti koleksiyonuna Hizmetleri tarafından kullanılan ortak parametreler ekler.</span><span class="sxs-lookup"><span data-stu-id="5e96d-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e96d-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e96d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5e96d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e96d-122">Element</span></span>|<span data-ttu-id="5e96d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e96d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e96d-124">\<İş akışı workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="5e96d-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="5e96d-125">Öğesinin bir örneği için ayarları belirtir <xref:System.Workflow.Runtime.WorkflowRuntime> iş akışı tabanlı barındırmak için [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="5e96d-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e96d-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e96d-126">Remarks</span></span>  
 <span data-ttu-id="5e96d-127">`<commonParameters>` Öğesi genel olarak birden fazla hizmet, örneğin kullanılan parametreleri tanımlar `ConnectionString` kullanırken <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="5e96d-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e96d-128">SQL izleme hizmeti sürekli olarak kullanmaz `ConnectionString` içinde belirtilen değeri `<commonParameters>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="5e96d-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="5e96d-129">Bazı alma gibi işlemlerinin `StateMachineWorkflowInstance.StateHistory` özelliği başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e96d-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="5e96d-130">Geçici çözüm için bunu belirtin `ConnectionString` özniteliği izleme sağlayıcısı için yapılandırma bölümünde aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5e96d-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="5e96d-131">İş yürütme Hizmetleri için Kalıcılık depolarına gibi toplu iş <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> ve <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, kendi işlem kullanarak yeniden etkinleştirebilirsiniz `EnableRetries` aşağıdaki örnekte gösterildiği gibi parametre:</span><span class="sxs-lookup"><span data-stu-id="5e96d-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="5e96d-132">Dikkat `EnableRetries` parametresi ya da genel düzeyinde ayarlanabilir (gösterildiği gibi *CommonParameters* bölüm) veya bireysel destekleyen Hizmetler `EnableRetries` (gösterildiği gibi *Hizmetleri*bölümü).</span><span class="sxs-lookup"><span data-stu-id="5e96d-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="5e96d-133">Aşağıdaki örnek kod, ortak parametreler programlı olarak nasıl değiştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e96d-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="5e96d-134">Davranışını denetlemek için bir yapılandırma dosyası kullanma hakkında daha fazla bilgi için bir <xref:System.Workflow.Runtime.WorkflowRuntime> nesnesi bir Windows Workflow Foundation ana bilgisayar uygulamasının bkz [iş akışı yapılandırma dosyalarını](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="5e96d-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e96d-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e96d-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e96d-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e96d-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="5e96d-137">İş akışı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="5e96d-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="5e96d-138">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="5e96d-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)