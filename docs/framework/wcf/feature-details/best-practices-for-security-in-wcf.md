---
title: WCF'de Güvenlik için En İyi Uygulamalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- best practices [WCF], security
ms.assetid: 3639de41-1fa7-4875-a1d7-f393e4c8bd69
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2c1588fa48631aec4e185fd8362a02505aa15e58
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753467"
---
# <a name="best-practices-for-security-in-wcf"></a>WCF'de Güvenlik için En İyi Uygulamalar
Aşağıdaki bölümlerde Windows Communication Foundation (WCF) kullanarak güvenli uygulamaları oluştururken dikkate alınması gereken en iyi uygulamaları listeleyin. Güvenlik hakkında daha fazla bilgi için bkz: [güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md), [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md), ve [meta veriler hakkında güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md).  
  
## <a name="identify-services-performing-windows-authentication-with-spns"></a>Windows kimlik doğrulaması ile SPN'ler gerçekleştirme Services belirle  
 Hizmetleri, kullanıcı asıl adları (UPN'ler) veya hizmet asıl adları (SPN) ile tanımlanabilir. Ağ hizmeti gibi makine hesabı altında çalışan hizmetleri çalıştırdıkları makineye karşılık gelen bir SPN kimliğe sahip. Kullanıcı hesapları altında çalışan hizmetleri sahip çalışıyor, kullanıcı ancak karşılık gelen bir UPN kimliği `setspn` aracı, kullanıcı hesabı için bir SPN atamak için kullanılabilir. Bir hizmeti SPN tanımlanabilir ve hizmete bağlanmada istemcilerini bu SPN kullanacak şekilde yapılandırma belirli yapabilirsiniz yapılandırma daha zor saldırıları. Bu kılavuz, Kerberos veya SSPI anlaşması kullanarak bağlamaları için geçerlidir.  İstemciler, burada SSPI NTLM'ye geri döner durumda bir SPN hala belirtmeniz gerekir.  
  
## <a name="verify-service-identities-in-wsdl"></a>WSDL hizmet kimliklerini doğrulama  
 WS-SecurityPolicy meta verilerde kendi kimlikleri hakkında bilgi yayımlamak hizmetler sağlar. Aracılığıyla alınırken `svcutil` veya gibi diğer yöntemleri <xref:System.ServiceModel.Description.WsdlImporter>, bu kimlik bilgileri WCF Hizmeti uç nokta adresleri kimlik özelliklerinin çevrilir. Bu hizmet kimlikleri etkili bir şekilde doğru ve geçerli olduğundan emin olun olmayan istemcilerin hizmeti kimlik doğrulama atlama. Kötü amaçlı bir hizmete kimlik bilgisi iletme ve diğer "ortadaki adam" saldırılarına kendi WSDL içinde istenen kimlik değiştirerek yürütmek için bu tür istemciler yararlanabilir.  
  
## <a name="use-x509-certificates-instead-of-ntlm"></a>NTLM yerine sertifikaları X509 kullan  
 WCF eşler arası kimlik doğrulaması için iki mekanizma sunar: X509 (eş kanal tarafından kullanılan) sertifikaları ve burada SSPI anlaşması daha aşağı düşürmeden Kerberos'tan için NTLM Windows kimlik doğrulaması.  Sertifika tabanlı kimlik doğrulaması 1024 bit veya daha fazla anahtar boyutları kullanarak çeşitli nedenlerle NTLM için tercih edilir:  
  
-   Karşılıklı kimlik doğrulaması kullanılabilirliği,  
  
-   daha güçlü şifreleme algoritmaları kullanımını ve  
  
-   X509 kullanan büyük zorluğunu iletilen kimlik bilgileri.  
   
## <a name="always-revert-after-impersonation"></a>Kimliğe bürünme sonra her zaman geri  
 İstemcinin kimliğe bürünme özelliğini etkinleştirme API'leri kullanırken, özgün kimliğine geri dönülemiyor emin olun. Kullanırken, örneğin, <xref:System.Security.Principal.WindowsIdentity> ve <xref:System.Security.Principal.WindowsImpersonationContext>, C# kullanan `using` deyimi veya Visual Basic`Using` aşağıdaki kodda gösterildiği gibi deyimi. <xref:System.Security.Principal.WindowsImpersonationContext> Uygulayan sınıf <xref:System.IDisposable> arabirimi ve bu nedenle ortak dil çalışma zamanı (CLR) otomatik olarak özgün kimliğine geri döner kodu bırakır sonra `using` bloğu.  
  
 [!code-csharp[c_SecurityBestPractices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securitybestpractices/cs/source.cs#1)]
 [!code-vb[c_SecurityBestPractices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securitybestpractices/vb/source.vb#1)]  
  
## <a name="impersonate-only-as-needed"></a>Yalnızca gerektiğinde kimliğine bürün  
 Kullanarak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemi <xref:System.Security.Principal.WindowsIdentity> sınıfı, bu çok denetimli bir kapsamda kimliğe bürünme kullanmak mümkün. Bunun aksine kullanmaktır <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği <xref:System.ServiceModel.OperationBehaviorAttribute>, kapsam için tüm işlem kimliğine bürünme izin verir. Mümkün olduğunda, daha kesin kullanarak kimliğe bürünme kapsamını denetleme <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> yöntemi.  
  
## <a name="obtain-metadata-from-trusted-sources"></a>Meta veri güvenilir kaynaklardan alın  
 Emin olun, meta veri kaynağına güveniyorsanız ve hiç kimse meta verileriyle değiştirilmiş olduğundan emin olun. HTTP protokolü kullanılarak alınan meta veriler düz metin olarak gönderilir ve ile değiştirilmiş. Hizmet kullanıyorsa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özellikleri, hizmet oluşturucusu tarafından sağlanan URL HTTPS protokolünü kullanarak veri yüklemek için kullanın.  
  
## <a name="publish-metadata-using-security"></a>Güvenlik kullanarak meta verileri yayımlama  
 Bir hizmetin yayımlanan meta verileriyle üzerinde oynanmasını önlemek için meta verileri exchange uç nokta taşıma veya ileti düzeyi güvenlik ile güvenli hale getirin. Daha fazla bilgi için bkz: [yayımlama meta veri uç noktalarını](../../../../docs/framework/wcf/publishing-metadata-endpoints.md) ve [nasıl yapılır: meta verileri kullanarak bir hizmet kodu yayımlama](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).  
  
## <a name="ensure-use-of-local-issuer"></a>Yerel yayımlayan kullanımını emin olun  
 Yerel yayımlayan bir veren adresi ve bağlama için belirtilen bir bağlama belirtilirse, bu bağlamayı kullanan uç noktaları için kullanılmaz. Her zaman yerel yayımlayan kullanmayı düşündüğünüz istemcilerinin veren adresi null olacak şekilde, bunlar bağlama değiştirmek veya böyle bir bağlama kullanmayın emin olun.  
  
## <a name="saml-token-size-quotas"></a>SAML belirteci boyutu kotaları  
 Güvenlik onaylar biçimlendirme dili (SAML) belirteçleri iletilerinde, bir güvenlik belirteci hizmeti (STS) tarafından verildiğinde veya istemciler bunları Hizmetleri kimlik doğrulaması bir parçası olarak mevcut olduğunda serileştirildiği zaman maksimum ileti boyutu kotası yeterince olmalıdır SAML belirteci ve diğer ileti bölümleri içerecek kadar büyük. Normal durumlarda, varsayılan ileti boyutu kotalarını yeterlidir. Ancak, talep yüzlerce içerdiğinden bir SAML belirtecine büyük olduğu durumlarda, kotalar serileştirilmiş belirteci uyum sağlayacak şekilde artırılacak. Kotalar hakkında daha fazla bilgi için bkz: [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="set-securitybindingelementincludetimestamp-to-true-on-custom-bindings"></a>SecurityBindingElement.IncludeTimestamp üzerinde özel bağlamalar True olarak ayarlayın  
 Özel bağlama oluşturduğunuzda, ayarlamalısınız <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> için `true`. Aksi halde, eğer <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> ayarlanır `false`, ve istemci bir X509 gibi bir asimetrik anahtar tabanlı belirteci kullanarak sertifika, ileti imzalanmamış.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Veriler için Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
