---
title: '&lt;etwTracking&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3a5ac9d63c542b64c9aa5a7eed46dd4df2c49e7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="e73ae-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="e73ae-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="e73ae-103">ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışı bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="e73ae-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="e73ae-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e73ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e73ae-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="e73ae-105">\<behaviors></span></span>  
<span data-ttu-id="e73ae-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e73ae-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e73ae-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="e73ae-107">\<behavior></span></span>  
<span data-ttu-id="e73ae-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="e73ae-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e73ae-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e73ae-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e73ae-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e73ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e73ae-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e73ae-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e73ae-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e73ae-112">Attributes</span></span>  
  
|<span data-ttu-id="e73ae-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e73ae-113">Attribute</span></span>|<span data-ttu-id="e73ae-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e73ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e73ae-115">ProfilAdı</span><span class="sxs-lookup"><span data-stu-id="e73ae-115">profileName</span></span>|<span data-ttu-id="e73ae-116">Bu davranışı ile ilişkili izleme profilin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="e73ae-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e73ae-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e73ae-117">Child Elements</span></span>  
 <span data-ttu-id="e73ae-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e73ae-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e73ae-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e73ae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e73ae-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e73ae-120">Element</span></span>|<span data-ttu-id="e73ae-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e73ae-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e73ae-122">\<davranış >, \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e73ae-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e73ae-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e73ae-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e73ae-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e73ae-124">Remarks</span></span>  
 <span data-ttu-id="e73ae-125">Hizmetin davranışı yapılandırmasına eklendiğinde, bu yapılandırma öğesi üzerinde bir iş akışı hizmeti izleme katılımcı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="e73ae-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="e73ae-126">İzleme katılımcıları iş akışını yayılan izleme verilerini almak için kullanılan ve farklı ortamları depolar.</span><span class="sxs-lookup"><span data-stu-id="e73ae-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="e73ae-127">Benzer şekilde, tüm kayıtları içinde izleme katılımcı de yapılabilir izleme üzerinde işlem sonrası.</span><span class="sxs-lookup"><span data-stu-id="e73ae-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e73ae-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="e73ae-128">Example</span></span>  
 <span data-ttu-id="e73ae-129">Aşağıdaki yapılandırma örnek Web.config dosyasında yapılandırılan standart ETW İzleme katılımcı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e73ae-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="e73ae-130">ETW İzleme katılımcı için ETW İzleme kayıtları yazmak için kullandığı sağlayıcı kimliği tanımlanan  **\<Tanılama >** bölümü.</span><span class="sxs-lookup"><span data-stu-id="e73ae-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="e73ae-131">İzleme katılımcı için abone oldu izleme kayıtları belirtmek için ilişkili bir profil var.</span><span class="sxs-lookup"><span data-stu-id="e73ae-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="e73ae-132">Bu tarafından tanımlanan **profileName** özniteliği  **\<Ekle >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="e73ae-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="e73ae-133">Bunlar tanımlandıktan sonra izleme katılımcı eklenen  **\<etwTracking >** hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="e73ae-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="e73ae-134">Böylece izleme kayıtlarını alır başlamadan bu iş akışı örneğinin uzantıları için seçilen izleme katılımcıları ekler.</span><span class="sxs-lookup"><span data-stu-id="e73ae-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e73ae-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e73ae-135">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="e73ae-136">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="e73ae-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e73ae-137">Katılımcıların izleme</span><span class="sxs-lookup"><span data-stu-id="e73ae-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)