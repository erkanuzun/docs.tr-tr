---
title: 'İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: 5ba6d2016a36809910561543a531dd4d44aac9b9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808490"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma
Bu konu, nasıl özel istemci ve hizmet kimlik bilgilerini uygulanacağını ve uygulama kodu özel kimlik bilgilerini kullanmayı gösterir.  
  
## <a name="credentials-extensibility-classes"></a>Kimlik bilgileri genişletilebilirlik sınıfları  
 <xref:System.ServiceModel.Description.ClientCredentials> Ve <xref:System.ServiceModel.Description.ServiceCredentials> Windows Communication Foundation (WCF) güvenlik genişletilebilirliği için ana giriş noktaları sınıflarıdır. Bu kimlik bilgileri sınıflar uygulama kodu kimlik bilgilerini ayarlamak için ve kimlik bilgisi türlerinin güvenlik belirteçleri şeklinde dönüştürmek için etkinleştirme API'ler sağlar. (*Güvenlik belirteçleri* kimlik bilgileri SOAP iletilerine içine aktarmak için kullanılan şeklindedir.) Bu kimlik bilgileri sınıfları sorumluluklarını iki alana ayrılabilir:  
  
-   Kimlik bilgilerini ayarlamak üzere uygulamalar için API sağlar.  
  
-   İçin bir üreteci olarak gerçekleştirmek <xref:System.IdentityModel.Selectors.SecurityTokenManager> uygulamaları.  
  
 Hem <xref:System.ServiceModel.Description.ClientCredentials> ve <xref:System.ServiceModel.Description.ServiceCredentials> sınıfları devral Özet <xref:System.ServiceModel.Security.SecurityCredentialsManager> döndürmek için sözleşmesini tanımlayan sınıfı <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
 Kimlik bilgileri sınıfları ve bunlar WCF güvenlik mimariye nasıl uyduğunu hakkında daha fazla bilgi için bkz: [güvenlik mimarisi](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
 WCF'de sağlanan varsayılan uygulamaları sistem tarafından sağlanan kimlik bilgisi türlerini destekler ve bu kimlik bilgileri türlerde işleyebilen belirteci Yöneticisi güvenlik oluşturun.  
  
## <a name="reasons-to-customize"></a>Özelleştirme için nedenleri  
 İstemci veya hizmet kimlik bilgisi sınıfları özelleştirmek için birden çok neden vardır. Öncelikle sistem tarafından sağlanan kimlik bilgisi türlerini, özellikle aşağıdaki nedenlerle işleme açısından varsayılan WCF güvenliği davranışını değiştirmek için gereksinimdir:  
  
-   Diğer genişletilebilirlik noktaları kullanarak mümkün olmayan değişir.  
  
-   Yeni kimlik bilgisi türlerinin ekleniyor.  
  
-   Yeni özel güvenlik belirteci türleri ekleme.  
  
 Bu konu, nasıl uygulanacağı özel istemci ve hizmet kimlik bilgileri ve bunların uygulama kodundan nasıl kullanılacağını açıklar.  
  
## <a name="first-in-a-series"></a>Bir dizinin ilk  
 Kimlik bilgileri özelleştirme nedeni kimlik bilgileri sağlama, güvenlik belirteci seri hale getirme veya kimlik doğrulaması ile ilgili WCF davranışını değiştirmek için bir özel kimlik bilgileri sınıfı oluşturma yalnızca ilk adımı olduğundan. Bu bölümdeki diğer konulara özel serileştiricileri ve Doğrulayıcı nasıl oluşturulacağını açıklar. Bu konuda, özel kimlik bilgileri sınıfı oluşturma ilk serideki konudur. Sonraki Eylemler (özel serileştiricileri ve Doğrulayıcı oluşturma), özel kimlik bilgileri yalnızca oluşturduktan sonra yapılabilir. Bu konu yapı ek konular şunlardır:  
  
-   [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
  
-   [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
  
-   [Nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-implement-custom-client-credentials"></a>Özel istemci kimlik bilgileri uygulamak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Description.ClientCredentials> sınıfı.  
  
2.  İsteğe bağlı. Yeni yöntemleri veya yeni kimlik bilgisi türlerinin özellikleri ekleyin. Yeni kimlik bilgisi türlerinin eklemezseniz, bu adımı atlayın. Aşağıdaki örnek, bir `CreditCardNumber` özelliği.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> yöntemi. Özel istemci kimlik bilgisi kullanıldığında, bu yöntem WCF güvenlik altyapısı tarafından otomatik olarak çağrılır. Bu yöntem oluşturma ve uygulaması örneğini döndüren sorumludur <xref:System.IdentityModel.Selectors.SecurityTokenManager> sınıfı.  
  
    > [!IMPORTANT]
    >  Bu dikkate almak önemlidir <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> özel bir güvenlik belirteci yöneticisi oluşturmak için yöntem geçersiz. Güvenlik belirteci yöneticisi türetilen <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, türetilmiş bir özel güvenlik belirteci sağlayıcısı döndürmelidir <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, gerçek güvenlik belirteci oluşturulamadı. Güvenlik belirteçleri oluşturmak için bu deseni uygulamazsanız uygulamanızı yanlış çalışabilir zaman <xref:System.ServiceModel.ChannelFactory> nesneleri önbelleğe alınır (Bu varsayılan davranışı WCF istemci proxy'leri için), bir ayrıcalık yükseltme saldırısı, büyük olasılıkla sonuç. Özel kimlik bilgisi nesnesinin bir parçası olarak önbelleğe <xref:System.ServiceModel.ChannelFactory>. Ancak, özel <xref:System.IdentityModel.Selectors.SecurityTokenManager> belirteci oluşturma mantığı yerleştirilir sürece, bir güvenlik tehdidi azaltır her çağırma oluşturulan <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
4.  Geçersiz kılma <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> yöntemi.  
  
     [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
     [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]  
  
#### <a name="to-implement-a-custom-client-security-token-manager"></a>Özel istemci güvenlik belirteci yöneticisi uygulamak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
2.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> yöntemi bir özel durumunda <xref:System.IdentityModel.Selectors.SecurityTokenProvider> uygulama oluşturulmalıdır. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel bir güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> yöntemi bir özel durumunda <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> uygulama oluşturulmalıdır. Özel güvenlik belirteci Doğrulayıcı hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md).  
  
4.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A> yöntemi bir özel durumunda <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> oluşturulması gerekir. Özel güvenlik belirteçleri ve özel güvenlik belirteci seri hale getiricileri genişletme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
     [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]  
  
#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>Özel bir istemci kullanılacak uygulama kodundan kimlik bilgileri  
  
1.  Hizmet arabirimi temsil eder oluşturulan istemci örneği oluşturabilir veya bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory> ile iletişim kurmak istediğiniz bir hizmete işaret ediyor.  
  
2.  Sistem tarafından sağlanan istemci kimlik bilgileri davranışından kaldırmak <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> üzerinden erişilen koleksiyonu <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> özelliği.  
  
3.  Özel istemci kimlik bilgileri sınıfının yeni bir örneğini oluşturun ve ona ekleyin <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> üzerinden erişilen koleksiyonu <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> özelliği.  
  
     [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
     [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]  
  
 Önceki yordamda uygulama kodu üzerinden istemci kimlik bilgilerini kullanmayı gösterir. WCF kimlik bilgilerini de uygulama yapılandırma dosyası kullanarak yapılandırılabilir. Uygulama Yapılandırması'nı kullanarak genellikle, kaynak, yeniden derlenmesi ve yeniden dağıtım değiştirmek zorunda kalmadan uygulama parametreleri değiştirilmesini sağladığından kodlamak için tercih edilir.  
  
 Sonraki yordam desteklemek için özel kimlik bilgileri yapılandırmasını açıklar.  
  
#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>Bir yapılandırma işleyicisi özel istemci kimlik bilgileri oluşturma  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Configuration.ClientCredentialsElement>.  
  
2.  İsteğe bağlı. Uygulama yapılandırma aracılığıyla kullanıma sunmak istediğiniz tüm ek yapılandırma parametrelerini özellikleri ekleyin. Aşağıdaki örnek adında bir özellik ekler `CreditCardNumber`.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> özelliğinin dönüş türü özel istemci kimlik bilgileri yapılandırma öğesi ile oluşturulan sınıf.  
  
4.  Geçersiz kılma <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> yöntemi. Yöntemi, oluşturma ve yapılandırma dosyasından yüklenen ayarlara göre özel kimlik bilgileri sınıfının bir örneğini döndüren sorumludur. Temel çağrı <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> sistem tarafından sağlanan kimlik bilgileri ayarlarını almak için bu yöntem yönteminden özel istemci kimlik bilgileri örneğine yüklenir.  
  
5.  İsteğe bağlı. 2. adımda ek özellikler eklediyseniz, geçersiz kılmanız gerekir <xref:System.Configuration.ConfigurationElement.Properties%2A> bunları tanıyabilmesi için yapılandırma framework için ek yapılandırma ayarlarını kaydetmek için özellik. Bu özel istemci kimlik bilgileri yapılandırma öğesi aracılığıyla yapılandırılması için sistem tarafından sağlanan ayarları izin vermek için temel sınıf özellikleriyle özelliklerinizi birleştirin.  
  
     [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
     [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]  
  
 Yapılandırma işleyici sınıf olduktan sonra WCF yapılandırma Framework'e tümleştirilebilir. Sonraki yordamda gösterildiği gibi istemci uç noktası davranışı öğelerinde kullanılacak özel istemci kimlik bilgileri sağlar.  
  
#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>Kimlik bilgilerini yapılandırma işleyicisi uygulama yapılandırmasında kaydolun ve özel bir istemci kullanmak için  
  
1.  Ekleme bir <`extensions`> öğesi ve bir <`behaviorExtensions`> yapılandırma dosyası öğesi.  
  
2.  Ekleme bir <`add`> öğesi <`behaviorExtensions`> öğesi ve kümesi `name` öznitelik için uygun bir değer.  
  
3.  Ayarlama `type` özniteliği için tam olarak nitelenmiş tür adı. Derleme adı ve diğer derleme özniteliklerinin da kapsar.  
  
    ```xml  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
      </extensions>  
    <system.serviceModel>  
    ```  
  
4.  Yapılandırma işleyicinizi kaydolduktan sonra özel kimlik bilgileri öğesi sistem tarafından sağlanan yerine aynı yapılandırma dosyası içinde kullanılabilir <`clientCredentials`> öğesi. Sistem tarafından sağlanan özellikleri ve yapılandırma işleyici uygulamanızı eklediğiniz tüm yeni özellikleri kullanabilirsiniz. Aşağıdaki örneği kullanarak bir özel özellik değerini ayarlar `creditCardNumber` özniteliği.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myClientCredentialsBehavior">  
          <myClientCredentials creditCardNumber="123-123-123"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    ```  
  
#### <a name="to-implement-custom-service-credentials"></a>Özel hizmet kimlik bilgilerini uygulamak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Description.ServiceCredentials>.  
  
2.  İsteğe bağlı. Eklenmekte olan kimlik bilgisi için yeni değerleri API'leri sağlamak için yeni özellikler ekleyin. Yeni kimlik bilgileri değerlerini eklemezseniz, bu adımı atlayın. Aşağıdaki örnek, bir `AdditionalCertificate` özelliği.  
  
3.  Geçersiz kılma <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> yöntemi. Özel istemci kimlik bilgisi kullanıldığında, bu yöntem WCF altyapısı tarafından otomatik olarak çağrılır. Yöntem oluşturma ve uygulaması örneğini döndüren sorumludur <xref:System.IdentityModel.Selectors.SecurityTokenManager> (sonraki yordamda açıklanan) sınıfı.  
  
4.  İsteğe bağlı. Geçersiz kılma <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> yöntemi. Bu, yalnızca özel istemci kimlik bilgileri kullanımla yeni özellikleri veya iç alanlar ekleyerek, gereklidir.  
  
     [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
     [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]  
  
#### <a name="to-implement-a-custom-service-security-token-manager"></a>Bir özel hizmet güvenlik belirteci yöneticisi uygulamak için  
  
1.  Türetilen yeni bir sınıf tanımlama <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfı.  
  
2.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> yöntemi bir özel durumunda <xref:System.IdentityModel.Selectors.SecurityTokenProvider> uygulama oluşturulmalıdır. Özel güvenlik belirteci sağlayıcıları hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel bir güvenlik belirteci sağlayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
3.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> yöntemi bir özel durumunda <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> uygulama oluşturulmalıdır. Özel güvenlik belirteci Doğrulayıcı hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir özel güvenlik belirteci kimlik doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md) konu.  
  
4.  İsteğe bağlı. Geçersiz kılma <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29> yöntemi bir özel durumunda <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> oluşturulması gerekir. Özel güvenlik belirteçleri ve özel güvenlik belirteci seri hale getiricileri genişletme hakkında daha fazla bilgi için bkz: [nasıl yapılır: özel belirteç oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
     [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]  
  
#### <a name="to-use-custom-service-credentials-from-application-code"></a>Uygulama kodu özel hizmet kimlik bilgilerini kullanmak için  
  
1.  Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost>.  
  
2.  Sistem tarafından sağlanan hizmet kimlik bilgilerini davranışından kaldırmak <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonu.  
  
3.  Özel hizmet kimlik bilgilerini sınıfının yeni bir örneğini oluşturun ve ona ekleyin <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonu.  
  
     [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
     [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]  
  
 Daha önce yordamlarda açıklanan adımları kullanarak yapılandırma desteği eklemek "`To create a configuration handler for custom client credentials`"ve"`To register and use a custom client credentials configuration handler in the application configuration`." Tek fark kullanmaktır <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> sınıfının yerine <xref:System.ServiceModel.Configuration.ClientCredentialsElement> sınıfı yapılandırma işleyicisi için temel sınıf olarak. Özel hizmet kimlik bilgisi öğesi sonra olabilir yerde kullanılan sistem tarafından sağlanan `<serviceCredentials>` öğe kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.Security.SecurityCredentialsManager>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 [Nasıl yapılır: Özel Güvenlik Belirteci Sağlayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Nasıl yapılır: Özel Güvenlik Belirteci Kimlik Doğrulayıcı Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Nasıl yapılır: Özel Belirteç Oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
