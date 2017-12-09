---
title: "Windows Communication Foundation Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 38f62a6ccc0c9291f3963173475f99d5800feb39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="bebe8-102">Windows Communication Foundation Güvenliği</span><span class="sxs-lookup"><span data-stu-id="bebe8-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="bebe8-103">Bu bölümdeki konularda açıklanmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik özellikleri ve bunları güvenli iletiler yardımcı olmak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="bebe8-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bebe8-104">Bkz: Windows Server AppFabric ve güvenlik, [Windows Server AppFabric güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="bebe8-104"> Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bebe8-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bebe8-105">In This Section</span></span>  
 [<span data-ttu-id="bebe8-106">Güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="bebe8-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="bebe8-107">Güvenlik özellikleri açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bebe8-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="bebe8-108">Güvenlik kavramları</span><span class="sxs-lookup"><span data-stu-id="bebe8-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="bebe8-109">Temel terimler ve kullanılan kavramlar açıklanmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik.</span><span class="sxs-lookup"><span data-stu-id="bebe8-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="bebe8-110">Ortak Güvenlik senaryoları</span><span class="sxs-lookup"><span data-stu-id="bebe8-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="bebe8-111">Senaryolar ve Topolojileri ile yapılandırabileceğiniz açıklanmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bebe8-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="bebe8-112">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="bebe8-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="bebe8-113">Kimlik bilgilerini ayarlama gibi güvenliğini etkileyen WCF davranışları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="bebe8-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="bebe8-114">Bağlamalar ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="bebe8-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="bebe8-115">Özel güvenlik bağlamaları oluşturmak nasıl ekleyebileceğiniz gösterilmektedir konuları dahil olmak üzere bağlamaları, güvenlik odaklı görünümünü.</span><span class="sxs-lookup"><span data-stu-id="bebe8-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="bebe8-116">Hizmetler ve istemcileri güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="bebe8-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="bebe8-117">Kullanarak iletileri güvenli hale getirmek açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="bebe8-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="bebe8-118">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="bebe8-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="bebe8-119">Genel kimlik doğrulama görevlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bebe8-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="bebe8-120">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="bebe8-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="bebe8-121">Güvenlik uygulamalarıyla birlikte genel yetkilendirme senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bebe8-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="bebe8-122">Federasyon ve verilen belirteçler</span><span class="sxs-lookup"><span data-stu-id="bebe8-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="bebe8-123">Federasyon ve Federasyon sunucusu ile iletişim kuran istemciler oluşturmak nasıl temelleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bebe8-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="bebe8-124">Kısmi güven</span><span class="sxs-lookup"><span data-stu-id="bebe8-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="bebe8-125">Kısmen güvenilen senaryoları çalıştırılacağını açıklar ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmen güvenilen çalıştırırken sınırlamaları.</span><span class="sxs-lookup"><span data-stu-id="bebe8-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="bebe8-126">Denetleme</span><span class="sxs-lookup"><span data-stu-id="bebe8-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="bebe8-127">Güvenlik olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bebe8-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="bebe8-128">Güvenlik Kılavuzu ve en iyi yöntemler</span><span class="sxs-lookup"><span data-stu-id="bebe8-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="bebe8-129">Güvenli oluşturma yönergeleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="bebe8-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bebe8-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bebe8-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="bebe8-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bebe8-131">Related Sections</span></span>  
 [<span data-ttu-id="bebe8-132">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="bebe8-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="bebe8-133">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="bebe8-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="bebe8-134">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="bebe8-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="bebe8-135">Kavramsal genel bakış</span><span class="sxs-lookup"><span data-stu-id="bebe8-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="bebe8-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bebe8-136">See Also</span></span>  
 [<span data-ttu-id="bebe8-137">Uygulamanızı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bebe8-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)