---
title: 104 - ActivityScheduledRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae202178-8fb1-4646-a3aa-18beeda8ff93
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36196f6814081a059e4a04de0ee9f0dd42d79bbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="104---activityscheduledrecord"></a><span data-ttu-id="2fdce-102">104 - ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="2fdce-102">104 - ActivityScheduledRecord</span></span>
## <a name="properties"></a><span data-ttu-id="2fdce-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2fdce-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2fdce-104">Kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-104">Id</span></span>|<span data-ttu-id="2fdce-105">104</span><span class="sxs-lookup"><span data-stu-id="2fdce-105">104</span></span>|  
|<span data-ttu-id="2fdce-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2fdce-106">Keywords</span></span>|<span data-ttu-id="2fdce-107">Sorun giderme, ögesi, WFTracking EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="2fdce-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="2fdce-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2fdce-108">Level</span></span>|<span data-ttu-id="2fdce-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="2fdce-109">Information</span></span>|  
|<span data-ttu-id="2fdce-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2fdce-110">Channel</span></span>|<span data-ttu-id="2fdce-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="2fdce-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2fdce-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fdce-112">Description</span></span>  
 <span data-ttu-id="2fdce-113">Bir iş akışı örneği içinde bir etkinlik ActivityScheduledRecord yayar, bu olay ETW İzleme katılımcı tarafından gösterilen</span><span class="sxs-lookup"><span data-stu-id="2fdce-113">This event is emitted by the ETW tracking participant when an activity within a workflow instance emits ActivityScheduledRecord</span></span>  
  
## <a name="message"></a><span data-ttu-id="2fdce-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2fdce-114">Message</span></span>  
 <span data-ttu-id="2fdce-115">TrackRecord ActivityScheduledRecord, örnek kimliği = %1, kayıt numarası = = %2, EventTime = %3, ad = %4, etkinlik kimliği = %5, ActivityInstanceId = %6, ActivityTypeName = % 7 ' ye ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = % 10 ChildActivityTypeName % 11, ek açıklamaları = % 12, ProfileName = % 13 =</span><span class="sxs-lookup"><span data-stu-id="2fdce-115">TrackRecord = ActivityScheduledRecord, InstanceID = %1,  RecordNumber = %2, EventTime = %3, Name = %4, ActivityId = %5, ActivityInstanceId = %6, ActivityTypeName = %7, ChildActivityName = %8, ChildActivityId = %9, ChildActivityInstanceId = %10, ChildActivityTypeName =%11, Annotations=%12, ProfileName = %13</span></span>  
  
## <a name="details"></a><span data-ttu-id="2fdce-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2fdce-116">Details</span></span>  
  
|<span data-ttu-id="2fdce-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2fdce-117">Data Item Name</span></span>|<span data-ttu-id="2fdce-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2fdce-118">Data Item Type</span></span>|<span data-ttu-id="2fdce-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fdce-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2fdce-120">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-120">InstanceId</span></span>|<span data-ttu-id="2fdce-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="2fdce-121">xs:GUID</span></span>|<span data-ttu-id="2fdce-122">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2fdce-123">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="2fdce-123">RecordNumber</span></span>|<span data-ttu-id="2fdce-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="2fdce-124">xs:long</span></span>|<span data-ttu-id="2fdce-125">Verilmiş kaydı sıra sayısı</span><span class="sxs-lookup"><span data-stu-id="2fdce-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="2fdce-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="2fdce-126">EventTime</span></span>|<span data-ttu-id="2fdce-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="2fdce-127">xs:dateTime</span></span>|<span data-ttu-id="2fdce-128">Olay gösterilen zaman UTC zamanı</span><span class="sxs-lookup"><span data-stu-id="2fdce-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="2fdce-129">Ad</span><span class="sxs-lookup"><span data-stu-id="2fdce-129">Name</span></span>|<span data-ttu-id="2fdce-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-130">xs:string</span></span>|<span data-ttu-id="2fdce-131">Alt aktivitesi etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="2fdce-131">The name of the activity that scheduled the child activity</span></span>|  
|<span data-ttu-id="2fdce-132">Etkinlik Kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-132">ActivityId</span></span>|<span data-ttu-id="2fdce-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-133">xs:string</span></span>|<span data-ttu-id="2fdce-134">Zamanlanmış alt etkinliğin etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-134">The id of the activity that scheduled the child activity</span></span>|  
|<span data-ttu-id="2fdce-135">ActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2fdce-135">ActivityInstanceId</span></span>|<span data-ttu-id="2fdce-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-136">xs:string</span></span>|<span data-ttu-id="2fdce-137">Alt aktivitesi etkinlik örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-137">The instance id of the activity that scheduled the child activity</span></span>|  
|<span data-ttu-id="2fdce-138">ActivityTypeName</span><span class="sxs-lookup"><span data-stu-id="2fdce-138">ActivityTypeName</span></span>|<span data-ttu-id="2fdce-139">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-139">xs:string</span></span>|<span data-ttu-id="2fdce-140">İptal işlemi istenen etkinlik türü</span><span class="sxs-lookup"><span data-stu-id="2fdce-140">The type of the activity that requested the cancel operation</span></span>|  
|<span data-ttu-id="2fdce-141">ChildActivityName</span><span class="sxs-lookup"><span data-stu-id="2fdce-141">ChildActivityName</span></span>|<span data-ttu-id="2fdce-142">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-142">xs:string</span></span>|<span data-ttu-id="2fdce-143">Zamanlanan etkinlik adı</span><span class="sxs-lookup"><span data-stu-id="2fdce-143">The name of the scheduled activity</span></span>|  
|<span data-ttu-id="2fdce-144">ChildActivityId</span><span class="sxs-lookup"><span data-stu-id="2fdce-144">ChildActivityId</span></span>|<span data-ttu-id="2fdce-145">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-145">xs:string</span></span>|<span data-ttu-id="2fdce-146">Zamanlanan etkinlik kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-146">The id of the scheduled activity</span></span>|  
|<span data-ttu-id="2fdce-147">ChildActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2fdce-147">ChildActivityInstanceId</span></span>|<span data-ttu-id="2fdce-148">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-148">xs:string</span></span>|<span data-ttu-id="2fdce-149">Zamanlanan etkinlikten örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="2fdce-149">The instance id of the scheduled activity</span></span>|  
|<span data-ttu-id="2fdce-150">ChildActivityTypeName</span><span class="sxs-lookup"><span data-stu-id="2fdce-150">ChildActivityTypeName</span></span>|<span data-ttu-id="2fdce-151">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-151">xs:string</span></span>|<span data-ttu-id="2fdce-152">Zamanlanan etkinlik türü</span><span class="sxs-lookup"><span data-stu-id="2fdce-152">The type of the scheduled activity</span></span>|  
|<span data-ttu-id="2fdce-153">Ek Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fdce-153">Annotations</span></span>|<span data-ttu-id="2fdce-154">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-154">xs:string</span></span>|<span data-ttu-id="2fdce-155">Bu olay için eklenen ek açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="2fdce-155">The annotations that were added to this event.</span></span>  <span data-ttu-id="2fdce-156">Değerleri bir xml öğesi biçimde depolanır \<öğeleri >\< öğe adı "annotationName" type="System.String =" > annotationValue\</Madde > \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="2fdce-156">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="2fdce-157">Ek açıklama dizesi içeriyorsa belirtilmişse \<öğeleri / >.</span><span class="sxs-lookup"><span data-stu-id="2fdce-157">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="2fdce-158">ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yükü sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="2fdce-158">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="2fdce-159">Olay boyutu ETW sınırlarını aşıyor sonra olay ek açıklamalar bırakarak ve ek açıklama değeri ile değiştirerek kesilir \<öğeleri >...  \< /öğelerini >.</span><span class="sxs-lookup"><span data-stu-id="2fdce-159">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="2fdce-160">ProfileName</span><span class="sxs-lookup"><span data-stu-id="2fdce-160">ProfileName</span></span>|<span data-ttu-id="2fdce-161">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-161">xs:string</span></span>|<span data-ttu-id="2fdce-162">Adı veya gösterilmesini bu olay sonuçlandı izleme profili</span><span class="sxs-lookup"><span data-stu-id="2fdce-162">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="2fdce-163">HostReference</span><span class="sxs-lookup"><span data-stu-id="2fdce-163">HostReference</span></span>|<span data-ttu-id="2fdce-164">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-164">xs:string</span></span>|<span data-ttu-id="2fdce-165">Bu alan, barındırılan web hizmetleri için web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2fdce-165">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="2fdce-166">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName' örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'</span><span class="sxs-lookup"><span data-stu-id="2fdce-166">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="2fdce-167">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2fdce-167">AppDomain</span></span>|<span data-ttu-id="2fdce-168">xs: String</span><span class="sxs-lookup"><span data-stu-id="2fdce-168">xs:string</span></span>|<span data-ttu-id="2fdce-169">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2fdce-169">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|