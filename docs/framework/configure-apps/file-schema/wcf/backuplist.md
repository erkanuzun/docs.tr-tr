---
title: '&lt;backupList&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8cb8f08c1d9c48aee9d3b42aadce0f65c8fe0585
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="96667-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="96667-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="96667-103">Birincil endpoint ulaşılamıyor durumunda kullanmak için yönlendirme hizmeti istediğiniz uç noktalar kümesi numaralandırır yedekleme listesini tanımlamak için yapılandırma bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="96667-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="96667-104">Listedeki ilk uç noktası kapalı ise, yönlendirme hizmeti otomatik olarak yük için listedeki bir sonraki devretme.</span><span class="sxs-lookup"><span data-stu-id="96667-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="96667-105">Bu karmaşık desenleri nasıl ele alınacağını veya hizmetlerinizin tümünün dağıtıldığı istemci uygulamanızı öğretmek gerekmeden güvenilirlik uygulamanıza eklemek için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="96667-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="96667-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="96667-106">\<system.serviceModel></span></span>  
<span data-ttu-id="96667-107">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="96667-107">\<routing></span></span>  
<span data-ttu-id="96667-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="96667-108">\<backupLists></span></span>  
<span data-ttu-id="96667-109">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="96667-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96667-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96667-110">Syntax</span></span>  
  
```xml 
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96667-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="96667-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96667-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96667-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96667-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="96667-113">Attributes</span></span>  
  
|<span data-ttu-id="96667-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="96667-114">Attribute</span></span>|<span data-ttu-id="96667-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96667-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96667-116">name</span><span class="sxs-lookup"><span data-stu-id="96667-116">name</span></span>|<span data-ttu-id="96667-117">Bu uç nokta listesi tanımlamak için kullanılan adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="96667-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96667-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="96667-118">Child Elements</span></span>  
  
|<span data-ttu-id="96667-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="96667-119">Element</span></span>|<span data-ttu-id="96667-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96667-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96667-121">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="96667-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="96667-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="96667-122">Parent Elements</span></span>  
  
|<span data-ttu-id="96667-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="96667-123">Element</span></span>|<span data-ttu-id="96667-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96667-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96667-125">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="96667-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="96667-126">Yedekleme uç noktaları listesi.</span><span class="sxs-lookup"><span data-stu-id="96667-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96667-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96667-127">Remarks</span></span>  
 <span data-ttu-id="96667-128">Bu bölüm bir ileti için bir iletişim özel durumunda birincil uç noktasına gönderirken aktarılmaz uç noktaları sıralı bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="96667-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="96667-129">Birincil uç gönderme listelenen `endpointName` özniteliği [ \<Ekle >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) iletişimleri özel durum ile başarısız oluyor, yönlendirme hizmeti ilk uç noktası bu iletiyi göndermeyi deneyecek yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="96667-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="96667-130">Bu da bir iletişim özel durumuyla başarısız olursa, yönlendirme hizmeti iletişim özel durumu veya tüm uç noktalar olarak başka bir hata döndürür gönderme girişimi başarılı olana kadar bu bölümde yer alan sonraki iletiye iletiyi göndermeyi deneyecek Koleksiyon bir hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="96667-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="96667-131">Bir iletişim özel Gönder "Hedef" adlı birincil uç döndürürse, aşağıdaki örnekte, "alternateServiceQueue" iletisi göndermek hizmeti çalışacak.</span><span class="sxs-lookup"><span data-stu-id="96667-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="96667-132">Bu deneme ayrıca bir iletişim özel döndürürse, yönlendirme hizmeti koleksiyonda sonraki uç nokta ileti göndermeye çalışacak.</span><span class="sxs-lookup"><span data-stu-id="96667-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96667-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96667-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    