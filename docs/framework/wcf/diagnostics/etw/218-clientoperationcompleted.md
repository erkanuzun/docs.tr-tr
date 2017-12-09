---
title: 218 - ClientOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d5b6fcc1c7ec4dd2f2c008e9d8bcfb58b2b4991
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="ddc99-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="ddc99-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="ddc99-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ddc99-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddc99-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ddc99-104">ID</span></span>|<span data-ttu-id="ddc99-105">218</span><span class="sxs-lookup"><span data-stu-id="ddc99-105">218</span></span>|  
|<span data-ttu-id="ddc99-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ddc99-106">Keywords</span></span>|<span data-ttu-id="ddc99-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ddc99-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ddc99-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ddc99-108">Level</span></span>|<span data-ttu-id="ddc99-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="ddc99-109">Information</span></span>|  
|<span data-ttu-id="ddc99-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ddc99-110">Channel</span></span>|<span data-ttu-id="ddc99-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ddc99-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ddc99-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddc99-112">Description</span></span>  
 <span data-ttu-id="ddc99-113">Bu olay yalnızca bir işlem tamamlandıktan sonra istemciler tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="ddc99-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="ddc99-114">Yalnızca ileti başarıyla gönderildikten sonra tek yönlü işlemlerinde budur.</span><span class="sxs-lookup"><span data-stu-id="ddc99-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="ddc99-115">Yanıt alındıktan sonra istek-yanıt işlemlerinde budur.</span><span class="sxs-lookup"><span data-stu-id="ddc99-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ddc99-116">İleti</span><span class="sxs-lookup"><span data-stu-id="ddc99-116">Message</span></span>  
 <span data-ttu-id="ddc99-117">İstemci, '%2' sözleşmeyle ilişkilendirilmiş ' %1' eylemi yürütülürken tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ddc99-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="ddc99-118">'%3' ileti gönderildi.</span><span class="sxs-lookup"><span data-stu-id="ddc99-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ddc99-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ddc99-119">Details</span></span>  
  
|<span data-ttu-id="ddc99-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ddc99-120">Data Item Name</span></span>|<span data-ttu-id="ddc99-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ddc99-121">Data Item Type</span></span>|<span data-ttu-id="ddc99-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddc99-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ddc99-123">Eylem</span><span class="sxs-lookup"><span data-stu-id="ddc99-123">Action</span></span>|<span data-ttu-id="ddc99-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="ddc99-124">xs:string</span></span>|<span data-ttu-id="ddc99-125">Giden iletinin SOAP eylemi üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="ddc99-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="ddc99-126">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="ddc99-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="ddc99-127">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="ddc99-127">The name of the contract.</span></span> <span data-ttu-id="ddc99-128">Örnek: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="ddc99-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="ddc99-129">Hedef</span><span class="sxs-lookup"><span data-stu-id="ddc99-129">Destination</span></span>|`xs:string`|<span data-ttu-id="ddc99-130">İletinin gönderildiği hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="ddc99-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="ddc99-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="ddc99-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="ddc99-132">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ddc99-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ddc99-133">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="ddc99-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ddc99-134">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ddc99-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ddc99-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ddc99-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ddc99-136">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ddc99-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|