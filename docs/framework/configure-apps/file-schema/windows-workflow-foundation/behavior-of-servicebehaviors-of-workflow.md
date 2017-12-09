---
title: "&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3a25e0cf9f5390fcc05cf9db0b6071ea94b9a4c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="39dfc-102">&lt;davranış&gt; , &lt;serviceBehaviors&gt; iş akışı</span><span class="sxs-lookup"><span data-stu-id="39dfc-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="39dfc-103">**Davranışı** öğesi içeren bir hizmet davranışını için ayarlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="39dfc-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="39dfc-104">Her davranış tarafından dizine kendi **adı**.</span><span class="sxs-lookup"><span data-stu-id="39dfc-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="39dfc-105">Hizmetleri kullanarak bu ad aracılığıyla her davranış bağlanması **behaviorConfiguration**özniteliği [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="39dfc-105">Services can link to each behavior through this name using the **behaviorConfiguration**attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="39dfc-106">Bu ayarları yeniden tanımlama olmadan davranışı yapılandırmaların paylaşmak uç noktaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="39dfc-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="39dfc-107">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="39dfc-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="39dfc-108">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="39dfc-108">\<behaviors></span></span>  
<span data-ttu-id="39dfc-109">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="39dfc-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="39dfc-110">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="39dfc-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39dfc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39dfc-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39dfc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="39dfc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="39dfc-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="39dfc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39dfc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="39dfc-114">Attributes</span></span>  
  
|<span data-ttu-id="39dfc-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="39dfc-115">Attribute</span></span>|<span data-ttu-id="39dfc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39dfc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39dfc-117">name</span><span class="sxs-lookup"><span data-stu-id="39dfc-117">name</span></span>|<span data-ttu-id="39dfc-118">Davranış yapılandırma adını içeren benzersiz bir dize.</span><span class="sxs-lookup"><span data-stu-id="39dfc-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="39dfc-119">Öğesinin kimlik dizesi olarak davranan bu yana, benzersiz olmalıdır ve kullanıcı tanımlı bir dize değeridir.</span><span class="sxs-lookup"><span data-stu-id="39dfc-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39dfc-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="39dfc-120">Child Elements</span></span>  
  
|<span data-ttu-id="39dfc-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="39dfc-121">Element</span></span>|<span data-ttu-id="39dfc-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39dfc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39dfc-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="39dfc-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="39dfc-124">Bir hizmet davranışını etkinleştirir hizmeti kullanmak için arabelleğe alınan sırası iletileri işlemek bir iş akışı hizmeti sağlayan işleme alırsınız.</span><span class="sxs-lookup"><span data-stu-id="39dfc-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="39dfc-125">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="39dfc-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="39dfc-126">ETW İzleme kullanılarak kullanmak bir hizmet sağlayan bir hizmet davranışı bir <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="39dfc-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="39dfc-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="39dfc-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="39dfc-128">Paylaşım düzeyleri, kanal fabrikası önbellek ayarlarını ve ileti gönderme Mesajlaşma etkinlikleri kullanarak hizmet uç noktalarına gönderme iş akışları için kanal önbellek ayarlarını önbellek özelleştirmesini sağlar hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="39dfc-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="39dfc-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="39dfc-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="39dfc-130">Yapılandırmanıza olanak sağlayan bir hizmet davranışı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> iş akışı hizmeti örneklerinin bir SQL Server 2005 veya SQL Server 2008 veritabanına kalıcı durum bilgilerini destekleyen özelliği.</span><span class="sxs-lookup"><span data-stu-id="39dfc-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="39dfc-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="39dfc-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="39dfc-132">Boşta iş akışı örnekleri zaman kaldırıldı ve kalıcı denetimleri hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="39dfc-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="39dfc-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="39dfc-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="39dfc-134">Nasıl iş akışı örnekleri, Kalıcılık, işlenmemiş özel durum davranışını ve boşta davranışı dahil olmak üzere çalıştığını denetleyen ayarları belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="39dfc-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="39dfc-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="39dfc-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="39dfc-136">Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluştuğunda yapılacak eylem belirtmenize olanak tanıyan bir hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="39dfc-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39dfc-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="39dfc-137">Parent Elements</span></span>  
  
|<span data-ttu-id="39dfc-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="39dfc-138">Element</span></span>|<span data-ttu-id="39dfc-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39dfc-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39dfc-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="39dfc-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="39dfc-141">Hizmet davranışı öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="39dfc-141">A collection of service behavior elements.</span></span>|