---
title: "Bilgileri Açıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bf20f11e7077c981e73aa087c654b9cf0c87bcb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="information-disclosure"></a><span data-ttu-id="c759d-102">Bilgileri Açıklama</span><span class="sxs-lookup"><span data-stu-id="c759d-102">Information Disclosure</span></span>
<span data-ttu-id="c759d-103">Bilgilerin açığa çıkmasına bir sistemi hakkında değerli bilgiler sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c759d-103">Information disclosure enables an attacker to gain valuable information about a system.</span></span> <span data-ttu-id="c759d-104">Bu nedenle, her zaman ve ortaya bilgiler, kötü niyetli bir kullanıcı tarafından kullanılıp kullanılamayacağını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c759d-104">Therefore, always consider what information you are revealing and whether it can be used by a malicious user.</span></span> <span data-ttu-id="c759d-105">Aşağıdaki olası bilgileri açığa saldırıları listeler ve bunları azaltmanın yollarını her sağlar.</span><span class="sxs-lookup"><span data-stu-id="c759d-105">The following lists possible information disclosure attacks and provides mitigations for each.</span></span>  
  
## <a name="message-security-and-http"></a><span data-ttu-id="c759d-106">İleti güvenliği ve HTTP</span><span class="sxs-lookup"><span data-stu-id="c759d-106">Message Security and HTTP</span></span>  
 <span data-ttu-id="c759d-107">Bir HTTP Aktarım katmanı üzerinden ileti düzeyi güvenlik kullanıyorsanız, ileti düzeyi güvenlik HTTP üstbilgileri korumaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c759d-107">If you are using message-level security over an HTTP transport layer, be aware that message-level security does not protect HTTP headers.</span></span> <span data-ttu-id="c759d-108">HTTP üst bilgilerini korumak için tek yolu, HTTP yerine HTTPS aktarımı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c759d-108">The only way to protect HTTP headers is to use HTTPS transport instead of HTTP.</span></span> <span data-ttu-id="c759d-109">HTTPS aktarımı Güvenli Yuva Katmanı (SSL) protokolü kullanılarak şifrelenmesi için HTTP üstbilgileri dahil olmak üzere tüm iletinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="c759d-109">HTTPS transport causes the entire message, including the HTTP headers, to be encrypted using the Secure Sockets Layer (SSL) protocol.</span></span>  
  
## <a name="policy-information"></a><span data-ttu-id="c759d-110">İlke bilgilerini</span><span class="sxs-lookup"><span data-stu-id="c759d-110">Policy Information</span></span>  
 <span data-ttu-id="c759d-111">İlke güvenliğini sağlamanın özellikle hassas verilen belirteç gereksinimleri veya belirteç verenin bilgileri ilkesinde Burada sunulan Federasyon senaryolarında önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c759d-111">Keeping policy secure is important, especially in federation scenarios where sensitive issued-token requirements or token-issuer information is exposed in policy.</span></span> <span data-ttu-id="c759d-112">Bu durumlarda verilen belirteç koymak için talep türü gibi hizmeti hakkında bilgi almak veya istemciler için kötü amaçlı belirteci verenler yönlendirme saldırganların önlemek için federasyon hizmetinin İlkesi uç nokta güvenliğini sağlamak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="c759d-112">In these cases, the recommendation is to secure the federated service's policy endpoint to prevent attackers from obtaining information about the service, such as the type of claims to put in the issued token, or redirecting clients to malicious token issuers.</span></span> <span data-ttu-id="c759d-113">Örneğin, bir saldırganın man-in--middle saldırı yürütülen bir veren sonlandırmak için federe güven zinciri yapılandırarak kullanıcı adı/parola çiftlerini bulmak.</span><span class="sxs-lookup"><span data-stu-id="c759d-113">For example, an attacker could discover user name/password pairs by reconfiguring the federated trust chain to terminate in an issuer that executed a man-in-the-middle attack.</span></span> <span data-ttu-id="c759d-114">Ayrıca, bağlantıları ilke alma işlemi aracılığıyla elde Federasyon istemcileri edinilen federe güven zincirinde verenler güven doğrulamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="c759d-114">It is also recommended that federated clients who obtain their bindings through policy retrieval verify that they trust the issuers in the obtained federated trust chain.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c759d-115">Federasyon senaryolarında bkz [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="c759d-115"> federation scenarios, see [Federation](../../../../docs/framework/wcf/feature-details/federation.md).</span></span>  
  
## <a name="memory-dumps-can-reveal-claim-information"></a><span data-ttu-id="c759d-116">Bellek dökümlerini talep bilgilerini ortaya çıkarabilir</span><span class="sxs-lookup"><span data-stu-id="c759d-116">Memory Dumps Can Reveal Claim Information</span></span>  
 <span data-ttu-id="c759d-117">Bir uygulama başarısız olduğunda, günlük dosyalarını olanlar Dr tarafından üretilen gibi. Watson, talep bilgilerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c759d-117">When an application fails, log files, such as those produced by Dr. Watson, can contain the claim information.</span></span> <span data-ttu-id="c759d-118">Bu bilgileri destek ekiplerini gibi diğer varlıklar için verilebilir; Aksi takdirde, özel verileri içeren talep bilgileri de aktarılır.</span><span class="sxs-lookup"><span data-stu-id="c759d-118">This information should not be exported to other entities, such as support teams; otherwise, the claim information that contains private data is also exported.</span></span> <span data-ttu-id="c759d-119">Bu günlük dosyaları için bilinmeyen varlıkların göndererek değil azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c759d-119">You can mitigate this by not sending the log files to unknown entities.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="c759d-120">[Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160).</span><span class="sxs-lookup"><span data-stu-id="c759d-120"> [Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160).</span></span>  
  
## <a name="endpoint-addresses"></a><span data-ttu-id="c759d-121">Uç Noktası Adresleri</span><span class="sxs-lookup"><span data-stu-id="c759d-121">Endpoint Addresses</span></span>  
 <span data-ttu-id="c759d-122">Bir uç nokta adresi bir uç nokta ile iletişim kurmak için gereken bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c759d-122">An endpoint address contains the information needed to communicate with an endpoint.</span></span> <span data-ttu-id="c759d-123">SOAP Güvenliği tam olarak bir istemci ve sunucu arasında bir simetrik anahtar anlaşması için alınıp verilen güvenlik anlaşma iletileri adresi içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c759d-123">SOAP security must include the address in full in the security negotiation messages that are exchanged in order to negotiate a symmetric key between a client and a server.</span></span> <span data-ttu-id="c759d-124">Güvenlik görüşmeleri önyükleme bir işlem olduğundan, adres üstbilgileri bu işlem sırasında şifrelenemez.</span><span class="sxs-lookup"><span data-stu-id="c759d-124">Because security negotiation is a bootstrap process, the address headers cannot be encrypted during this process.</span></span> <span data-ttu-id="c759d-125">Bu nedenle, adres gizli herhangi bir veri içermemesi gerekir; Aksi takdirde, bilgi ifşası saldırılara yol açar.</span><span class="sxs-lookup"><span data-stu-id="c759d-125">Therefore, the address should not contain any confidential data; otherwise, it leads to information disclosure attacks.</span></span>  
  
## <a name="certificates-transferred-unencrypted"></a><span data-ttu-id="c759d-126">Sertifikaları şifrelenmemiş aktarılan</span><span class="sxs-lookup"><span data-stu-id="c759d-126">Certificates Transferred Unencrypted</span></span>  
 <span data-ttu-id="c759d-127">Bir istemci kimlik doğrulaması için bir X.509 sertifikası kullandığınızda, sertifika temiz SOAP üstbilgisi içine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="c759d-127">When you use an X.509 certificate to authenticate a client, the certificate is transferred in the clear, inside the SOAP header.</span></span> <span data-ttu-id="c759d-128">Olası bir kişisel bilgileri (PII) açığa çıkması bunun farkında olun.</span><span class="sxs-lookup"><span data-stu-id="c759d-128">Be aware of this as a potential personally identifiable information (PII) disclosure.</span></span> <span data-ttu-id="c759d-129">Bu bir sorun için değil `TransportWithMessageCredential` burada tüm ileti şifrelenir ile aktarım düzeyinde güvenlik modu.</span><span class="sxs-lookup"><span data-stu-id="c759d-129">This is not an issue for `TransportWithMessageCredential` mode, where the entire message is encrypted with transport-level security.</span></span>  
  
## <a name="service-references"></a><span data-ttu-id="c759d-130">Hizmet başvuruları</span><span class="sxs-lookup"><span data-stu-id="c759d-130">Service References</span></span>  
 <span data-ttu-id="c759d-131">Hizmet başvurusu başka bir hizmet başvurudur.</span><span class="sxs-lookup"><span data-stu-id="c759d-131">A service reference is a reference to another service.</span></span> <span data-ttu-id="c759d-132">Örneğin, bir hizmet bir işlem sırasında istemciye hizmet başvurusu iletebilir.</span><span class="sxs-lookup"><span data-stu-id="c759d-132">For example, a service may pass a service reference to a client in the course of an operation.</span></span> <span data-ttu-id="c759d-133">Hizmet başvurusu ayrıca ile kullanılan bir *kimlik doğrulayıcı güven*, uygulama verileri veya hedef için kimlik bilgileri gibi bilgileri açıklamadan önce hedef asıl kimliğini sağlar iç bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="c759d-133">The service reference is also used with a *trust identity verifier*, an internal component that ensures the identity of the target principal before disclosing information such as application data or credentials to the target.</span></span> <span data-ttu-id="c759d-134">Uzak güven kimliği doğrulanamıyor veya yanlış gönderen hiçbir veri kendisi, uygulama veya kullanıcıya tehlikeye atabilecek duyurulmuştur olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c759d-134">If the remote trust identity cannot be verified or is incorrect, the sender should ensure that no data was disclosed that could compromise itself, the application, or the user.</span></span>  
  
 <span data-ttu-id="c759d-135">Azaltıcı Etkenler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c759d-135">Mitigations include the following:</span></span>  
  
-   <span data-ttu-id="c759d-136">Hizmet başvuruları güvenilir olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c759d-136">Service references are assumed to be trustworthy.</span></span> <span data-ttu-id="c759d-137">Bunlar ile oynanmadığını emin olmak için hizmet başvurusu örnekleri aktarma zaman dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="c759d-137">Take care whenever transferring service reference instances to ensure that they have not been tampered with.</span></span>  
  
-   <span data-ttu-id="c759d-138">Bazı uygulamalar, uzak ana bilgisayar tarafından kanıtlanmış hizmet başvurusu ve güven verilerini dayalı güvenin etkileşimli kurma izin veren bir kullanıcı deneyimi sunabilir.</span><span class="sxs-lookup"><span data-stu-id="c759d-138">Some applications can present a user experience that allows interactive establishment of trust based on data in the service reference and trust data proven by the remote host.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="c759d-139">Genişletilebilirlik noktaları gibi bir tesis ancak kullanıcı için gereken bunları uygulanan sağlar.</span><span class="sxs-lookup"><span data-stu-id="c759d-139"> provides extensibility points for such a facility, but the user must implemented them.</span></span>  
  
## <a name="ntlm"></a><span data-ttu-id="c759d-140">NTLM</span><span class="sxs-lookup"><span data-stu-id="c759d-140">NTLM</span></span>  
 <span data-ttu-id="c759d-141">Varsayılan olarak, Windows etki alanı ortamında kimliğini doğrulamak ve kullanıcılara yetki vermek için Kerberos protokolünü Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c759d-141">By default, in the Windows domain environment, Windows authentication uses the Kerberos protocol to authenticate and authorize users.</span></span> <span data-ttu-id="c759d-142">Kerberos protokolü için herhangi bir nedenle kullanılamaz, NT LAN Yöneticisi (NTLM) bir geri dönüş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c759d-142">If the Kerberos protocol cannot be used for some reason, NT LAN Manager (NTLM) is used as a fallback.</span></span> <span data-ttu-id="c759d-143">Ayarlayarak bu davranışı devre dışı bırakabilirsiniz <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="c759d-143">You can disable this behavior by setting the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property to `false`.</span></span> <span data-ttu-id="c759d-144">NTLM izin verirken dikkat edilmesi gereken konular şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c759d-144">Issues to be aware of when allowing NTLM include:</span></span>  
  
-   <span data-ttu-id="c759d-145">NTLM istemci kullanıcı adı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c759d-145">NTLM exposes the client user name.</span></span> <span data-ttu-id="c759d-146">Kullanıcı adı gizli tutulması gerekiyorsa, daha sonra ayarlamak `AllowNTLM` özelliği için bağlama üzerinde `false`.</span><span class="sxs-lookup"><span data-stu-id="c759d-146">If the user name needs to be kept confidential, then set the `AllowNTLM` property on the binding to `false`.</span></span>  
  
-   <span data-ttu-id="c759d-147">NTLM kimlik doğrulaması sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c759d-147">NTLM does not provide server authentication.</span></span> <span data-ttu-id="c759d-148">Bu nedenle, istemci, NTLM kimlik doğrulama protokolü olarak kullandığınızda, doğru hizmete bağlanıyor garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="c759d-148">Therefore, the client cannot ensure that it is communicating with the right service when you use NTLM as an authentication protocol.</span></span>  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a><span data-ttu-id="c759d-149">İstemci kimlik bilgileri veya geçersiz kimlik zorlar NTLM kullanımını belirtme</span><span class="sxs-lookup"><span data-stu-id="c759d-149">Specifying Client Credentials or Invalid Identity Forces NTLM Usage</span></span>  
 <span data-ttu-id="c759d-150">Bir istemci oluştururken, istemci kimlik bilgileri bir etki alanı adı olmadan belirterek veya geçersiz sunucu kimlik belirtmeyi yerine Kerberos protokolünün kullanılması için NTLM neden olur (varsa `AlllowNtlm` özelliği ayarlanmış `true`).</span><span class="sxs-lookup"><span data-stu-id="c759d-150">When creating a client, specifying client credentials without a domain name, or specifying an invalid server identity, causes NTLM to be used instead of the Kerberos protocol (if the `AlllowNtlm` property is set to `true`).</span></span> <span data-ttu-id="c759d-151">NTLM kimlik doğrulaması yapmak için bilgi potansiyel olarak bildirilen.</span><span class="sxs-lookup"><span data-stu-id="c759d-151">Because  NTLM does not do server authentication, information can potentially be disclosed.</span></span>  
  
 <span data-ttu-id="c759d-152">Örneğin, aşağıda gösterildiği gibi bir etki alanı adı olmadan Windows istemci kimlik bilgileri belirtmek mümkündür [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] kodu.</span><span class="sxs-lookup"><span data-stu-id="c759d-152">For example, it is possible to specify Windows client credentials without a domain name, as shown in the following [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] code.</span></span>  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 <span data-ttu-id="c759d-153">Kod bir etki alanı adı belirtmiyor ve bu nedenle NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c759d-153">The code does not specify a domain name, and therefore NTLM will be used.</span></span>  
  
 <span data-ttu-id="c759d-154">Etki alanı belirtildi, ancak geçersiz hizmet asıl adı uç noktası kimlik özelliği kullanılarak belirtilir NTLM kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c759d-154">If the domain is specified, but an invalid service principal name is specified using the endpoint identity feature, then NTLM is used.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c759d-155">uç noktası kimlik belirtilen bkz [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c759d-155"> how endpoint identity is specified, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c759d-156">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c759d-156">See Also</span></span>  
 [<span data-ttu-id="c759d-157">Güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="c759d-157">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [<span data-ttu-id="c759d-158">Ayrıcalık yükseltme</span><span class="sxs-lookup"><span data-stu-id="c759d-158">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [<span data-ttu-id="c759d-159">Hizmet reddi</span><span class="sxs-lookup"><span data-stu-id="c759d-159">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [<span data-ttu-id="c759d-160">Oynama</span><span class="sxs-lookup"><span data-stu-id="c759d-160">Tampering</span></span>](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [<span data-ttu-id="c759d-161">Desteklenmeyen senaryolar</span><span class="sxs-lookup"><span data-stu-id="c759d-161">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [<span data-ttu-id="c759d-162">Yeniden yürütme saldırıları</span><span class="sxs-lookup"><span data-stu-id="c759d-162">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)