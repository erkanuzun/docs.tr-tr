---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f17b31e1dfe9ba60b2042a85a6d673d986fe0a33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="01147-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="01147-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="01147-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="01147-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01147-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01147-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="01147-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="01147-105">Methods</span></span>  
 <span data-ttu-id="01147-106">ServiceMetadataBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="01147-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="01147-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="01147-107">Properties</span></span>  
 <span data-ttu-id="01147-108">ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="01147-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="01147-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="01147-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="01147-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="01147-110">Data type: string</span></span>  
  
 <span data-ttu-id="01147-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01147-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01147-112">Hizmet meta veri isteklerini yeniden yönlendirdiği konumu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="01147-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="01147-113">De</span><span class="sxs-lookup"><span data-stu-id="01147-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="01147-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="01147-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="01147-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01147-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01147-116">Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="01147-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="01147-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="01147-117">HttpGetUrl</span></span>  
 <span data-ttu-id="01147-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="01147-118">Data type: string</span></span>  
  
 <span data-ttu-id="01147-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01147-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01147-120">WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="01147-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="01147-121">De</span><span class="sxs-lookup"><span data-stu-id="01147-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="01147-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="01147-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="01147-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01147-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01147-124">Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="01147-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="01147-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="01147-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="01147-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="01147-126">Data type: string</span></span>  
  
 <span data-ttu-id="01147-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="01147-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="01147-128">WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="01147-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01147-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01147-129">Requirements</span></span>  
  
|<span data-ttu-id="01147-130">MOF</span><span class="sxs-lookup"><span data-stu-id="01147-130">MOF</span></span>|<span data-ttu-id="01147-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="01147-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="01147-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="01147-132">Namespace</span></span>|<span data-ttu-id="01147-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="01147-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01147-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01147-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>