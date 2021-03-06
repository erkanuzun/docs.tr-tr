---
title: .NET Framework'te Ağ Programlaması
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efecd4f2858843a2401e3d69538d87f92475b816
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397903"
---
# <a name="network-programming-in-the-net-framework"></a>.NET Framework'te Ağ Programlaması
Microsoft .NET Framework, uygulamalarınızla hızlı ve kolay bir şekilde tümleştirilebilen katmanlı, genişletilebilir ve yönetilen Internet hizmetleri sağlar. Ağ uygulamalarınız, yeni Internet protokollerinden otomatik olarak yararlanabilmek için takılabilir protokolleri temel alabilir veya ağ ile yuva düzeyinde çalışmak için Windows yuva arabiriminin yönetilen uygulamasını kullanabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Takılabilir Protokollere Giriş](../../../docs/framework/network-programming/introducing-pluggable-protocols.md)  
 Bir Internet kaynağına, ihtiyaç duyduğu erişim protokolüne bakılmaksızın nasıl erişileceğini açıklar.  
  
 [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)  
 Internet kaynaklarında veri yüklemek ve indirmek için takılabilir protokollerin nasıl kullanılacağını açıklar.  
  
 [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 Takılabilir protokoller uygulamak için protokole özgü sınıfların nasıl türetileceğini açıklar.  
  
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)  
 TCP, UDP ve HTTP gibi ağ protokollerinden yararlanan programlama uygulamalarını açıklar.  
  
 [İnternet Protokolü Sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 Internet Protokolü sürüm 6'nın (IPv6) Internet Protokolü paketinin geçerli sürümüne (IPv4) göre avantajlarını, IPv6 adresini, yönlendirmeyi, otomatik yapılandırmayı ve IPv6'nın nasıl etkinleştirileceğini ve devre dışı bırakılacağını açıklar.  
  
 [İnternet Uygulamalarını Yapılandırma](../../../docs/framework/network-programming/configuring-internet-applications.md)  
 .NET Framework yapılandırma dosyalarının Internet uygulamalarını yapılandırmak için nasıl kullanılacağını açıklar.  
  
 [.NET Framework'te Ağ İzleme](../../../docs/framework/network-programming/network-tracing.md)  
 Ağ izlemenin yönetilen uygulama tarafından oluşturulan yöntem çağrıları ve ağ trafiğiyle ilgili bilgiler almak için nasıl kullanılacağını açıklar.  
  
 [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 Kullanan uygulamalar için önbelleğe almayı kullanmak üzere açıklar <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, ve <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> sınıfları.  
  
 [Ağ Programlama Güvenliği](../../../docs/framework/network-programming/security-in-network-programming.md)  
 Standart Internet güvenliği ve kimlik doğrulama tekniklerinin nasıl kullanılacağını açıklar.  
  
 [System.Net Sınıfları için En İyi Yöntemler](../../../docs/framework/network-programming/best-practices-for-system-net-classes.md)  
 Internet uygulamalarınızdan en iyi şekilde yararlanmanız için ipuçları ve püf noktaları sağlar.  
  
 [Ara Sunucu Üzerinden İnternet Erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 Proxy'lerin nasıl yapılandırılacağını açıklar.  
  
 [NetworkInformation](../../../docs/framework/network-programming/networkinformation.md)  
 Ağ olayları, değişiklikleri, istatistikleri ve özellikler hakkında bilgi toplamak açıklar ve ayrıca kullanarak uzak ana bilgisayar erişilebilir olup olmadığını belirlemek nasıl açıklar <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> sınıfı.  
  
 [System.Uri ad alanında sürüm 2.0’da yapılan değişiklikler](../../../docs/framework/network-programming/changes-to-the-system-uri-namespace-in-version-2-0.md)  
 Yapılan bazı değişiklikler açıklanmaktadır <xref:System.Uri?displayProperty=nameWithType> sınıf sabit yanlış davranışa sürüm 2.0, kullanılabilirliğini geliştiren ve güvenliğini.  
  
 [System.Uri’de Uluslararası Kaynak Tanımlayıcı Desteği](../../../docs/framework/network-programming/international-resource-identifier-support-in-system-uri.md)  
 Geliştirmeler açıklanmaktadır <xref:System.Uri?displayProperty=nameWithType> sürüm 3.5, 3.0 SP1 ve uluslararası kaynak tanımlayıcısı (IRI) ve Uluslararası yapılan etki alanı adı (IDN) 2.0 SP1 sınıfında destekler.  
  
 [Sürüm 3.5’teki Yuva Performansı Geliştirmeleri](../../../docs/framework/network-programming/socket-performance-enhancements-in-version-3-5.md)  
 Geliştirmeler kümesini <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sürüm 3.5, 3.0 SP1 ve özelleştirilmiş yüksek performanslı yuva uygulamaları tarafından kullanılan bir alternatif zaman uyumsuz desen sağlayan 2.0 SP1 sınıfta.  
  
 [Eş Adı Çözümleme Protokolü](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)  
 Sunucusuz ve dinamik ad kayıt ve ad çözümleme protokolü olan Eş Adı Çözümleme Protokolü'nü (PNRP) desteklemek için Sürüm 3.5'e eklenen desteği açıklar. Bu yeni özellikleri tarafından desteklenen <xref:System.Net.PeerToPeer?displayProperty=nameWithType> ad alanı.  
  
 [Eşler Arası İş Birliği](../../../docs/framework/network-programming/peer-to-peer-collaboration.md)  
 PNRP'yi temel alan Eşler Arası İşbirliği'ni desteklemek için Sürüm 3.5'e eklenen desteği açıklar. Bu yeni özellikleri tarafından desteklenen <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> ad alanı.  
  
 [Sürüm 3.5 SP1’de HttpWebRequest için NTLM kimlik doğrulamasındaki değişiklikler](../../../docs/framework/network-programming/changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 Sürüm 3.5 SP1 yapılan nasıl tümleşik Windows kimlik doğrulaması tarafından işlenir etkileyen güvenlik değişiklikleri açıklar <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, ve ilgili System.Net ad alanındaki sınıflar.  
  
 [Genişletilmiş Koruma ile Tümleşik Windows Kimlik Doğrulaması](../../../docs/framework/network-programming/integrated-windows-authentication-with-extended-protection.md)  
 Nasıl tümleşik Windows kimlik doğrulaması etkileyen genişletilmiş koruma tarafından işlenir için geliştirmeler açıklanmaktadır <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, ilgili sınıflar ve <xref:System.Net?displayProperty=nameWithType> ve ilgili ad alanları.  
  
 [IPv6 ve Teredo kullanarak NAT Geçişi](../../../docs/framework/network-programming/nat-traversal-using-ipv6-and-teredo.md)  
 Eklenen geliştirmeler açıklanmaktadır <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, ve <xref:System.Net.Sockets?displayProperty=nameWithType> IPv6 ve Teredo kullanarak NAT geçişi desteklemek için ad alanları.  
  
 [Windows Mağazası Uygulamaları için Ağ Yalıtımı](../../../docs/framework/network-programming/network-isolation-for-windows-store-apps.md)  
 Ağ yalıtımı etkisini açıklar olduğunda sınıfları <xref:System.Net>, <xref:System.Net.Http>, ve <xref:System.Net.Http.Headers> ad alanları kullanıldığı [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar.  
  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 Ağ bağlantıları indirilebilir için sınıfları kullanma programlama örnekleri <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> ad alanları.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Net?displayProperty=nameWithType>  
 Günümüzde ağlarda kullanılan birçok protokol için basit bir programlama arabirimi sağlar. <xref:System.Net.WebRequest?displayProperty=nameWithType> Ve <xref:System.Net.WebResponse?displayProperty=nameWithType> bu ad alanındaki sınıflar olan takılabilir protokol için temel.  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 Türleri ve kullanarak elde kaynaklar için önbellek ilkelerini tanımlamak için kullanılan numaralandırmaları tanımlar <xref:System.Net.WebRequest?displayProperty=nameWithType> ve <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> sınıfları.  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 Uygulamaların System.Net ad alanlarının yapılandırma ayarlarına programlı bir şekilde erişmek ve bunları güncelleştirmek için kullandığı sınıflar.  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 Modern HTTP uygulamaları için programlama arabirimi sağlayan sınıflar.  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 Tarafından kullanılan HTTP üstbilgilerinin koleksiyonlar için destek sağlayan <xref:System.Net.Http?displayProperty=nameWithType> ad alanı  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 SMTP protokolünü kullanarak e-posta oluşturan ve gönderen sınıflar.  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 Çok Amaçlı Internet posta Exchange (MIME) üstbilgileri sınıfları tarafından kullanılan temsil etmek için kullanılan türlerini tanımlar <xref:System.Net.Mail?displayProperty=nameWithType> ad alanı.  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 Ağ olayları, değişiklikler, istatistikler ve özellikler hakkında programlı bir şekilde bilgi toplayan sınıflar.  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 Geliştiriciler için Eş Adı Çözümleme Protokolü'nün (PNRP) yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 Geliştiriciler için Eşler Arası İşbirliği'nin yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 Ana bilgisayarlar arasında güvenli iletişim için ağ akışlarını sağlayan sınıflar.  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 Ağa erişimin denetlenmesine yardımcı olmak isteyen geliştiriciler için Windows Sockets'in (Winsock) yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 Geliştiriciler için WebSocket'in yönetilen bir uygulamasını sağlar.  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 Tekdüzen kaynak tanımlayıcısının (URI) nesne temsilini ve URI'nin bölümlerine kolay erişim sağlar.  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 Uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulama desteği sağlar.  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 Uygulamalar için genişletilmiş koruma kullanarak kimlik doğrulama yapılandırmasına yönelik destek sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  

 [.NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar](../../../docs/framework/network-programming/tls.md)  
 [Görsel Katman Programlama ile İlgili Nasıl Yapılır Konuları](../../../docs/framework/network-programming/network-programming-how-to-topics.md)  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [MSDN kod Galerisi'nden .NET ağ örnekleri](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)  
 [HttpClient örnek](http://go.microsoft.com/fwlink/?LinkId=242550)
