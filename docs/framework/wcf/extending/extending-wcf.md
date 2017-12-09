---
title: "WCF'yi Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3d436690108158cfd7675cf00788a564b8a1dc6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="extending-wcf"></a><span data-ttu-id="bb2d8-102">WCF'yi Genişletme</span><span class="sxs-lookup"><span data-stu-id="bb2d8-102">Extending WCF</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="bb2d8-103">değiştirmek ve tam olarak denetlemek için çalışma zamanı bileşenleri genişletmek ve hizmet tabanlı uygulamalar genişletmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-103"> allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="bb2d8-104">Bu bölümdeki konular, genişletilebilirlik mimarisi hakkında ayrıntılı gidin.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="bb2d8-105">Temel programlama hakkında daha fazla bilgi için bkz: [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="bb2d8-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb2d8-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bb2d8-106">In This Section</span></span>  
 [<span data-ttu-id="bb2d8-107">Genişletme ServiceHost ve hizmet modeli katmanını</span><span class="sxs-lookup"><span data-stu-id="bb2d8-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="bb2d8-108">Temel alınan kanalları dışında gelen iletileri çekme, bunları yöntem çağrılarına uygulama kodundaki içine çevirme ve sonuçları çağırana geri göndermek için hizmet modeli katmanını sorumludur.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="bb2d8-109">Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve dağıtıcı işlevselliği, özel davranışları, ileti ve parametre kişiler tarafından ele ve diğer genişletilebilirlik işlevleri içeren özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="bb2d8-110">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="bb2d8-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="bb2d8-111">Bağlamaları bir bitiş noktasına bağlanmak için gereken iletişim ayrıntılarını açıklayan nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="bb2d8-112">Özel bağlamalar veya bağlama uzantıları uygulama özellikleri desteklemek için gereken özel iletişim işlevselliği uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="bb2d8-113">Kanal katmanını genişletme</span><span class="sxs-lookup"><span data-stu-id="bb2d8-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="bb2d8-114">Kanal katmanını hizmet modeli katmanını altında bulunur ve exchange istemcileri ve Hizmetleri arasındaki iletilerinin sorumludur.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="bb2d8-115">Kanal uzantıları güvenlik gibi yeni protokol işlevselliği uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="bb2d8-116">Kanal uzantıları SOAP iletilerine taşımak için yeni bir ağ aktarımı uygulama gibi işlevlerini de taşıma.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="bb2d8-117">Güvenliği genişletme</span><span class="sxs-lookup"><span data-stu-id="bb2d8-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="bb2d8-118">Güvenlik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktarımı güvenliğini (bütünlüğü, gizlilik ve kimlik doğrulaması) erişim denetimi (yetkilendirme) oluşur ve denetim.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-118">Security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="bb2d8-119">Bulunan sınıflar `IdentityModel` ad alanı tarafından kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] erişim denetimi için.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-119">The classes found in the `IdentityModel` namespace are used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] for access control.</span></span> <span data-ttu-id="bb2d8-120">Güvenlik mimarisini anlama, özel erişim denetimi sistemlerine uyum sağlamak için özel talep türleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="bb2d8-121">Meta veri sistemini genişletme</span><span class="sxs-lookup"><span data-stu-id="bb2d8-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="bb2d8-122">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Meta veri sistemi grubudur sınıflar ve arabirimler hizmet tabanlı uygulamalar uygulamak için gereken meta verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-122">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="bb2d8-123">Değiştirin veya sınıflarını genişletmek veya uygulama ve Web Hizmetleri Açıklama Dili (WSDL) uzantıları veya özel WS-PolicyAttachments onaylar gibi özel meta verileri içeri ve dışarı aktarmak arabirimleri yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="bb2d8-124">Kodlayıcılar ve seri hale getiricileri genişletme</span><span class="sxs-lookup"><span data-stu-id="bb2d8-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="bb2d8-125">Kodlayıcılar ve serileştiricileri verileri bir biçimden diğerine çevir.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="bb2d8-126">Bu bölümdeki konular, özel gereksinimleri karşılamak için sağlanan sınıflarını genişletmek nasıl ele almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb2d8-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bb2d8-127">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bb2d8-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="bb2d8-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bb2d8-128">Related Sections</span></span>  
 [<span data-ttu-id="bb2d8-129">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="bb2d8-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="bb2d8-130">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="bb2d8-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="bb2d8-131">Kılavuzları ve en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bb2d8-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)