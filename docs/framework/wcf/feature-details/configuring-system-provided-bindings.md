---
title: "Sistem Tarafından Sağlanan Bağlamaları Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 91994fc31e4b0f30d575cd43ad44e66dcdb0a7f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-system-provided-bindings"></a><span data-ttu-id="ad816-102">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ad816-102">Configuring System-Provided Bindings</span></span>
<span data-ttu-id="ad816-103">Bağlamalar ve bir bitiş noktasına bağlanmak nasıl belirtmek için bir uç nokta konuşurken kullanmak için iletişim mekanizması belirtin.</span><span class="sxs-lookup"><span data-stu-id="ad816-103">Bindings specify the communication mechanism to use when talking to an endpoint and indicate how to connect to an endpoint.</span></span> <span data-ttu-id="ad816-104">Bağlamaları oluşur tanımlayan öğeleri nasıl [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanalları katmanlı yedeklemek için gerekli iletişim özelliklerini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="ad816-104">Bindings consist of elements that define how the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channels are layered up to provide the required communication features.</span></span> <span data-ttu-id="ad816-105">Bağlama öğeleri üç tür içerir:</span><span class="sxs-lookup"><span data-stu-id="ad816-105">A binding contains three types of elements:</span></span>  
  
-   <span data-ttu-id="ad816-106">Güvenlik, güvenilirlik, içeriği akış ayarları veya kullanıcı tanımlı protokolleri uç noktasına gönderilen iletileri ile birlikte kullanmak için belirleyen Protokolü kanal bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ad816-106">Protocol channel binding elements, which determine the security, reliability, context flow settings, or user-defined protocols to use with messages that are sent to the endpoint.</span></span>  
  
-   <span data-ttu-id="ad816-107">Uç nokta için örneğin, TCP veya HTTP iletileri gönderirken kullanmak için temel Aktarım Protokolü belirlemek kanal bağlama öğelerini taşıma.</span><span class="sxs-lookup"><span data-stu-id="ad816-107">Transport channel binding elements, which determine the underlying transport protocol to use when sending messages to the endpoint, for example, TCP or HTTP.</span></span>  
  
-   <span data-ttu-id="ad816-108">Kablo text/XML, ikili, örneğin, uç noktasına gönderilen iletiler için kullanılacak kodlamayı bağlama öğeleri kodlama ileti veya ileti iletim en iyi duruma getirme mekanizmasını (MTOM).</span><span class="sxs-lookup"><span data-stu-id="ad816-108">Message encoding binding elements, which determine the wire encoding to use for messages that are sent to the endpoint, for example, text/XML, binary, or Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="ad816-109">Bu konuda tüm sistem tarafından sağlanan sunulmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bağlar.</span><span class="sxs-lookup"><span data-stu-id="ad816-109">This topic presents all of the system-provided [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bindings.</span></span> <span data-ttu-id="ad816-110">Hiçbiri, uygulamanız için tam gereksinimleri karşılıyorsa, kullanarak bir bağlama oluşturabilirsiniz <xref:System.ServiceModel.Channels.CustomBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ad816-110">If none of these meets the exact requirements for your application, you can create a binding using the <xref:System.ServiceModel.Channels.CustomBinding> class.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ad816-111">özel bağlama oluşturma, bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ad816-111"> creating custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ad816-112">Güvenliği etkinleştirilmiş sahip bir bağlama seçin.</span><span class="sxs-lookup"><span data-stu-id="ad816-112">Select a binding that has security enabled.</span></span> <span data-ttu-id="ad816-113">Varsayılan olarak, tüm bağlamaları dışında <xref:System.ServiceModel.BasicHttpBinding> bağlama, güvenliği etkinleştirilmiş olması.</span><span class="sxs-lookup"><span data-stu-id="ad816-113">By default, all bindings, except the <xref:System.ServiceModel.BasicHttpBinding> binding, have security enabled.</span></span> <span data-ttu-id="ad816-114">Güvenli bağlama seçmezseniz veya güvenlik devre dışı bırakırsanız, ağ iletişimlerini güvenli veri merkezinde veya yalıtılmış bir ağda olması gibi bazı diğer şekilde, korunan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ad816-114">If you do not select a secure binding, or if you disable security, be sure your network exchanges are protected in some other manner, such as being in a secured data center or on an isolated network.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ad816-115">Çift yönlü sözleşmeler güvenlik desteklemez veya başka bir şekilde ağ exchange güvenli sürece devre dışı, güvenlik sahip bağlamalarla kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ad816-115">Do not use duplex contracts with bindings that do not support security, or that have security disabled, unless the network exchange is secured by some other means.</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="ad816-116">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ad816-116">System-Provided Bindings</span></span>  
 <span data-ttu-id="ad816-117">Aşağıdaki bağlamaları ile birlikte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad816-117">The following bindings are shipped with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
|<span data-ttu-id="ad816-118">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ad816-118">Binding</span></span>|<span data-ttu-id="ad816-119">Yapılandırma öğesi</span><span class="sxs-lookup"><span data-stu-id="ad816-119">Configuration Element</span></span>|<span data-ttu-id="ad816-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad816-120">Description</span></span>|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="ad816-121">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-121">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="ad816-122">WS-temel profil uyumluluğunu Web Hizmetleri ile Örneğin, ASP.NET Web Hizmetleri (ASMX) iletişim kurmak için uygun olan bir bağlama-services tabanlı.</span><span class="sxs-lookup"><span data-stu-id="ad816-122">A binding that is suitable for communicating with WS-Basic Profile conformant Web services, for example, ASP.NET Web services (ASMX)-based services.</span></span> <span data-ttu-id="ad816-123">Bu bağlama taşıma ve varsayılan ileti kodlama olarak text/XML olarak HTTP kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad816-123">This binding uses HTTP as the transport and text/XML as the default message encoding.</span></span>|  
|<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="ad816-124">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-124">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="ad816-125">Olmayan yönlü Hizmet sözleşmeleri için uygun bir güvenli ve birlikte çalışabilir bağlama.</span><span class="sxs-lookup"><span data-stu-id="ad816-125">A secure and interoperable binding that is suitable for non-duplex service contracts.</span></span>|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[<span data-ttu-id="ad816-126">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-126">\<ws2007HttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="ad816-127">Doğru sürümleri için destek sağlayan bir güvenli ve birlikte çalışabilir bağlama <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, ve <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ad816-127">A secure and interoperable binding that provides support for the correct versions of the <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, and <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> binding elements.</span></span>|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="ad816-128">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-128">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="ad816-129">Çift yönlü Hizmet sözleşmeleri veya SOAP aracılarla iletişim için uygun bir güvenli ve birlikte çalışabilir bağlama.</span><span class="sxs-lookup"><span data-stu-id="ad816-129">A secure and interoperable binding that is suitable for duplex service contracts or communication through SOAP intermediaries.</span></span>|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="ad816-130">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-130">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="ad816-131">Güvenli ve birlikte çalışabilir, bağlama verimli bir şekilde kimlik doğrulaması ve kullanıcılara yetki vermek için bir Federasyon olan kuruluşların etkinleştirme WS-Federasyon protokolünü destekler.</span><span class="sxs-lookup"><span data-stu-id="ad816-131">A secure and interoperable binding that supports the WS-Federation protocol, enabling organizations that are in a federation to efficiently authenticate and authorize users.</span></span>|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[<span data-ttu-id="ad816-132">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-132">\<ws2007FederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|<span data-ttu-id="ad816-133">Türetilen bir güvenli ve birlikte çalışabilir bağlama <xref:System.ServiceModel.WS2007HttpBinding> ve Federasyon güvenlik destekler.</span><span class="sxs-lookup"><span data-stu-id="ad816-133">A secure and interoperable binding that derives from <xref:System.ServiceModel.WS2007HttpBinding> and supports federated security.</span></span>|  
|<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="ad816-134">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-134">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="ad816-135">Güvenli ve en iyi duruma getirilmiş bağlama arasında makineler arası iletişim için uygun [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="ad816-135">A secure and optimized binding suitable for cross-machine communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[<span data-ttu-id="ad816-136">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-136">\<netNamedPipeBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|<span data-ttu-id="ad816-137">Makine üzerindeki arasındaki iletişim için uygun bir güvenli, güvenilir ve en iyi duruma getirilmiş bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="ad816-137">A secure, reliable, optimized binding that is suitable for on-machine communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>|  
|<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="ad816-138">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-138">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="ad816-139">Arasında makineler arası iletişim için uygun bir sıralı bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="ad816-139">A queued binding that is suitable for cross-machine communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[<span data-ttu-id="ad816-140">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-140">\<netPeerTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|<span data-ttu-id="ad816-141">Güvenli, çok makineli iletişimi sağlayan bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="ad816-141">A binding that enables secure, multi-machine communication.</span></span>|  
|<xref:System.ServiceModel.WebHttpBinding>|[<span data-ttu-id="ad816-142">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-142">\<webHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="ad816-143">Uç noktaları için yapılandırmak için kullanılan bir bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Hizmetleri SOAP iletilerine yerine HTTP istekleri aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="ad816-143">A binding used to configure endpoints for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services that are exposed through HTTP requests instead of SOAP messages.</span></span>|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[<span data-ttu-id="ad816-144">\<MsmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="ad816-144">\<msmqIntegrationBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|<span data-ttu-id="ad816-145">Bir bağlama arasında makineler arası iletişim için uygun olan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama ve uygulamalara Message Queuing (MSMQ olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="ad816-145">A binding that is suitable for cross-machine communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application and existing Message Queuing (also known as MSMQ) applications.</span></span>|  
  
## <a name="binding-features"></a><span data-ttu-id="ad816-146">Bağlama özellikleri</span><span class="sxs-lookup"><span data-stu-id="ad816-146">Binding Features</span></span>  
 <span data-ttu-id="ad816-147">Sonraki tabloda önemli özelliklerinden bazıları her sağlanan sistem tarafından sağlanan bağlamalar gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad816-147">The next table shows some of the key features each of the system-provided bindings provided.</span></span> <span data-ttu-id="ad816-148">Bağlamaları ilk sütununda listelenir ve özellikleri ile ilgili bilgiler tabloda açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ad816-148">The bindings are listed in the first column and information regarding the features is described in the table.</span></span> <span data-ttu-id="ad816-149">Aşağıdaki tabloda kullanılan bağlama kısaltmalar için bir anahtar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad816-149">The following table provides a key for the binding abbreviations used.</span></span> <span data-ttu-id="ad816-150">Bir bağlama seçmek için gereksinim duyduğunuz satır özelliklerin tümü, hangi sütunun karşılayan belirler.</span><span class="sxs-lookup"><span data-stu-id="ad816-150">To select a binding, determine which column satisfies all of the row features you need.</span></span>  
  
|<span data-ttu-id="ad816-151">Bağlama</span><span class="sxs-lookup"><span data-stu-id="ad816-151">Binding</span></span>|<span data-ttu-id="ad816-152">Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="ad816-152">Interoperability</span></span>|<span data-ttu-id="ad816-153">Mod güvenlik (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="ad816-153">Mode of Security (Default)</span></span>|<span data-ttu-id="ad816-154">Oturum</span><span class="sxs-lookup"><span data-stu-id="ad816-154">Session</span></span><br /><br /> <span data-ttu-id="ad816-155">(Varsayılan)</span><span class="sxs-lookup"><span data-stu-id="ad816-155">(Default)</span></span>|<span data-ttu-id="ad816-156">İşlemler</span><span class="sxs-lookup"><span data-stu-id="ad816-156">Transactions</span></span>|<span data-ttu-id="ad816-157">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="ad816-157">Duplex</span></span>|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|<span data-ttu-id="ad816-158">Temel Profil 1.1</span><span class="sxs-lookup"><span data-stu-id="ad816-158">Basic Profile 1.1</span></span>|<span data-ttu-id="ad816-159">(Hiçbiri), Aktarım, ileti, karma</span><span class="sxs-lookup"><span data-stu-id="ad816-159">(None), Transport, Message, Mixed</span></span>|<span data-ttu-id="ad816-160">None, (yok)</span><span class="sxs-lookup"><span data-stu-id="ad816-160">None, (None)</span></span>|<span data-ttu-id="ad816-161">(Hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="ad816-161">(None)</span></span>|<span data-ttu-id="ad816-162">yok</span><span class="sxs-lookup"><span data-stu-id="ad816-162">n/a</span></span>|  
|<xref:System.ServiceModel.WSHttpBinding>|<span data-ttu-id="ad816-163">WS</span><span class="sxs-lookup"><span data-stu-id="ad816-163">WS</span></span>|<span data-ttu-id="ad816-164">None, taşıma (ileti), karma</span><span class="sxs-lookup"><span data-stu-id="ad816-164">None, Transport, (Message), Mixed</span></span>|<span data-ttu-id="ad816-165">(Hiçbiri), Aktarım, güvenilir oturum</span><span class="sxs-lookup"><span data-stu-id="ad816-165">(None), Transport, Reliable Session</span></span>|<span data-ttu-id="ad816-166">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-166">(None), Yes</span></span>|<span data-ttu-id="ad816-167">yok</span><span class="sxs-lookup"><span data-stu-id="ad816-167">n/a</span></span>|  
|<xref:System.ServiceModel.WS2007HttpBinding>|<span data-ttu-id="ad816-168">WS-güvenlik, WS-Trust, WS-SecureConversation, WS-SecurityPolicy</span><span class="sxs-lookup"><span data-stu-id="ad816-168">WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy</span></span>|<span data-ttu-id="ad816-169">None, taşıma (ileti), karma</span><span class="sxs-lookup"><span data-stu-id="ad816-169">None, Transport, (Message), Mixed</span></span>|<span data-ttu-id="ad816-170">(Hiçbiri), Aktarım, güvenilir oturum</span><span class="sxs-lookup"><span data-stu-id="ad816-170">(None), Transport, Reliable Session</span></span>|<span data-ttu-id="ad816-171">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-171">(None), Yes</span></span>|<span data-ttu-id="ad816-172">yok</span><span class="sxs-lookup"><span data-stu-id="ad816-172">n/a</span></span>|  
|<xref:System.ServiceModel.WSDualHttpBinding>|<span data-ttu-id="ad816-173">WS</span><span class="sxs-lookup"><span data-stu-id="ad816-173">WS</span></span>|<span data-ttu-id="ad816-174">Hiçbiri (ileti)</span><span class="sxs-lookup"><span data-stu-id="ad816-174">None, (Message)</span></span>|<span data-ttu-id="ad816-175">(Güvenilir oturum)</span><span class="sxs-lookup"><span data-stu-id="ad816-175">(Reliable Session)</span></span>|<span data-ttu-id="ad816-176">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-176">(None), Yes</span></span>|<span data-ttu-id="ad816-177">Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-177">Yes</span></span>|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|<span data-ttu-id="ad816-178">WS-Federasyon</span><span class="sxs-lookup"><span data-stu-id="ad816-178">WS-Federation</span></span>|<span data-ttu-id="ad816-179">Hiçbiri (ileti), karma</span><span class="sxs-lookup"><span data-stu-id="ad816-179">None, (Message), Mixed</span></span>|<span data-ttu-id="ad816-180">(Hiçbiri), güvenli oturum</span><span class="sxs-lookup"><span data-stu-id="ad816-180">(None), Reliable Session</span></span>|<span data-ttu-id="ad816-181">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-181">(None), Yes</span></span>|<span data-ttu-id="ad816-182">Hayır</span><span class="sxs-lookup"><span data-stu-id="ad816-182">No</span></span>|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|<span data-ttu-id="ad816-183">WS-Federasyon</span><span class="sxs-lookup"><span data-stu-id="ad816-183">WS-Federation</span></span>|<span data-ttu-id="ad816-184">Hiçbiri (ileti), karma</span><span class="sxs-lookup"><span data-stu-id="ad816-184">None, (Message), Mixed</span></span>|<span data-ttu-id="ad816-185">(Hiçbiri), güvenli oturum</span><span class="sxs-lookup"><span data-stu-id="ad816-185">(None), Reliable Session</span></span>|<span data-ttu-id="ad816-186">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-186">(None), Yes</span></span>|<span data-ttu-id="ad816-187">Hayır</span><span class="sxs-lookup"><span data-stu-id="ad816-187">No</span></span>|  
|<xref:System.ServiceModel.NetTcpBinding>|<span data-ttu-id="ad816-188">.NET</span><span class="sxs-lookup"><span data-stu-id="ad816-188">.NET</span></span>|<span data-ttu-id="ad816-189">Hiçbiri (aktarım) ileti,</span><span class="sxs-lookup"><span data-stu-id="ad816-189">None, (Transport), Message,</span></span><br /><br /> <span data-ttu-id="ad816-190">Karma</span><span class="sxs-lookup"><span data-stu-id="ad816-190">Mixed</span></span>|<span data-ttu-id="ad816-191">Güvenilir oturum, (aktarım)</span><span class="sxs-lookup"><span data-stu-id="ad816-191">Reliable Session, (Transport)</span></span>|<span data-ttu-id="ad816-192">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-192">(None), Yes</span></span>|<span data-ttu-id="ad816-193">Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-193">Yes</span></span>|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|<span data-ttu-id="ad816-194">.NET</span><span class="sxs-lookup"><span data-stu-id="ad816-194">.NET</span></span>|<span data-ttu-id="ad816-195">None,</span><span class="sxs-lookup"><span data-stu-id="ad816-195">None,</span></span><br /><br /> <span data-ttu-id="ad816-196">(Aktarım)</span><span class="sxs-lookup"><span data-stu-id="ad816-196">(Transport)</span></span>|<span data-ttu-id="ad816-197">Hiçbiri (aktarım)</span><span class="sxs-lookup"><span data-stu-id="ad816-197">None, (Transport)</span></span>|<span data-ttu-id="ad816-198">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-198">(None), Yes</span></span>|<span data-ttu-id="ad816-199">Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-199">Yes</span></span>|  
|<xref:System.ServiceModel.NetMsmqBinding>|<span data-ttu-id="ad816-200">.NET</span><span class="sxs-lookup"><span data-stu-id="ad816-200">.NET</span></span>|<span data-ttu-id="ad816-201">None, iletiyi (aktarım), her ikisi</span><span class="sxs-lookup"><span data-stu-id="ad816-201">None, Message, (Transport), Both</span></span>|<span data-ttu-id="ad816-202">(Hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="ad816-202">(None)</span></span>|<span data-ttu-id="ad816-203">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-203">(None), Yes</span></span>|<span data-ttu-id="ad816-204">Hayır</span><span class="sxs-lookup"><span data-stu-id="ad816-204">No</span></span>|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|<span data-ttu-id="ad816-205">Eş</span><span class="sxs-lookup"><span data-stu-id="ad816-205">Peer</span></span>|<span data-ttu-id="ad816-206">None, iletiyi (aktarım), karma</span><span class="sxs-lookup"><span data-stu-id="ad816-206">None, Message, (Transport), Mixed</span></span>|<span data-ttu-id="ad816-207">(Hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="ad816-207">(None)</span></span>|<span data-ttu-id="ad816-208">(Hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="ad816-208">(None)</span></span>|<span data-ttu-id="ad816-209">Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-209">Yes</span></span>|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|<span data-ttu-id="ad816-210">MSMQ</span><span class="sxs-lookup"><span data-stu-id="ad816-210">MSMQ</span></span>|<span data-ttu-id="ad816-211">Hiçbiri (aktarım)</span><span class="sxs-lookup"><span data-stu-id="ad816-211">None, (Transport)</span></span>|<span data-ttu-id="ad816-212">(Hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="ad816-212">(None)</span></span>|<span data-ttu-id="ad816-213">(Hiçbiri), Evet</span><span class="sxs-lookup"><span data-stu-id="ad816-213">(None), Yes</span></span>|<span data-ttu-id="ad816-214">yok</span><span class="sxs-lookup"><span data-stu-id="ad816-214">n/a</span></span>|  
  
 <span data-ttu-id="ad816-215">Aşağıdaki tabloda önceki tabloda bulunan özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ad816-215">The following table explains the features found in the previous table.</span></span>  
  
|<span data-ttu-id="ad816-216">Özellik</span><span class="sxs-lookup"><span data-stu-id="ad816-216">Feature</span></span>|<span data-ttu-id="ad816-217">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad816-217">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad816-218">Birlikte çalışabilirlik türü</span><span class="sxs-lookup"><span data-stu-id="ad816-218">Interoperability Type</span></span>|<span data-ttu-id="ad816-219">Adları protokolü veya teknolojisi ile birlikte çalışma bağlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad816-219">Names the protocol or technology with which the binding ensures interoperation.</span></span>|  
|<span data-ttu-id="ad816-220">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ad816-220">Security</span></span>|<span data-ttu-id="ad816-221">Kanal güvenliği nasıl belirtir:</span><span class="sxs-lookup"><span data-stu-id="ad816-221">Specifies how the channel is secured:</span></span><br /><br /> <span data-ttu-id="ad816-222">-Hiçbiri: SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış.</span><span class="sxs-lookup"><span data-stu-id="ad816-222">-   None: The SOAP message is not secured and the client is not authenticated.</span></span><br /><span data-ttu-id="ad816-223">-Taşıma: Güvenlik gereksinimlerini aktarım katmanında karşılanır.</span><span class="sxs-lookup"><span data-stu-id="ad816-223">-   Transport: Security requirements are satisfied at the transport layer.</span></span><br /><span data-ttu-id="ad816-224">-İleti: Güvenlik gereksinimlerini ileti katmanında karşılanır.</span><span class="sxs-lookup"><span data-stu-id="ad816-224">-   Message: Security requirements are satisfied at the message layer.</span></span><br /><span data-ttu-id="ad816-225">-Karma: Bu güvenlik modu olarak bilinir `TransportWithMessageCredentials`.</span><span class="sxs-lookup"><span data-stu-id="ad816-225">-   Mixed: This security mode is known as `TransportWithMessageCredentials`.</span></span> <span data-ttu-id="ad816-226">Kimlik bilgileri ileti düzeyinde işler ve bütünlüğü ve gizliliği gereksinimleri Aktarım katmanı tarafından karşılanır.</span><span class="sxs-lookup"><span data-stu-id="ad816-226">It handles credentials at the message level, and integrity and confidentiality requirements are satisfied by the transport layer.</span></span><br /><span data-ttu-id="ad816-227">-Her ikisi: Her iki ileti düzeyi ve aktarım düzeyi güvenlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ad816-227">-   Both: Both message level and transport level security are used.</span></span> <span data-ttu-id="ad816-228">Bu özellik için benzersiz olan <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="ad816-228">This ability is unique to the <xref:System.ServiceModel.NetMsmqBinding>.</span></span>|  
|<span data-ttu-id="ad816-229">Oturum</span><span class="sxs-lookup"><span data-stu-id="ad816-229">Session</span></span>|<span data-ttu-id="ad816-230">Bu bağlama oturum sözleşmeleri destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad816-230">Specifies whether this binding supports session contracts.</span></span>|  
|<span data-ttu-id="ad816-231">İşlemler</span><span class="sxs-lookup"><span data-stu-id="ad816-231">Transactions</span></span>|<span data-ttu-id="ad816-232">İşlemler etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad816-232">Specifies whether transactions are enabled.</span></span>|  
|<span data-ttu-id="ad816-233">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="ad816-233">Duplex</span></span>|<span data-ttu-id="ad816-234">Çift yönlü sözleşmeler desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad816-234">Specifies whether duplex contracts are supported.</span></span> <span data-ttu-id="ad816-235">Bu özellik destek oturumlarının bağlamasında gerektirir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ad816-235">Note this feature requires support for Sessions in the binding.</span></span>|  
|<span data-ttu-id="ad816-236">Akış</span><span class="sxs-lookup"><span data-stu-id="ad816-236">Streaming</span></span>|<span data-ttu-id="ad816-237">İleti akış desteklenip desteklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ad816-237">Specifies whether the message streaming is supported.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad816-238">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad816-238">See Also</span></span>  
 [<span data-ttu-id="ad816-239">Uç noktası oluşturma genel bakış</span><span class="sxs-lookup"><span data-stu-id="ad816-239">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="ad816-240">Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="ad816-240">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="ad816-241">Temel WCF programlama</span><span class="sxs-lookup"><span data-stu-id="ad816-241">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)