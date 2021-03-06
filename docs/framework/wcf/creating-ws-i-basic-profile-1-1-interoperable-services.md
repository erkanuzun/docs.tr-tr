---
title: WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: aa76a6633ef86a908e00bb9dcb1b16eefe35c12d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804956"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>WS-I Temel Profil 1.1 Birlikte Çalışabilir Hizmetler Oluşturma
Birlikte çalışabilir olması için bir WCF Hizmeti uç noktası yapılandırmak için [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmeti istemcileri:  
  
-   Kullanım <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> türü olarak hizmet uç noktası için bağlama türü.  
  
-   Geri çağırma ve oturum sözleşme özellikleri veya işlem davranışları Hizmeti uç noktanızı kullanmayın  
  
 İsteğe bağlı olarak, HTTPS ve bağlama üzerinde aktarım düzeyinde istemci kimlik doğrulaması için destek de etkinleştirebilirsiniz.  
  
 Aşağıdaki özellikleri <xref:System.ServiceModel.BasicHttpBinding> sınıfı WS ötesinde işlevselliği gerektiren-ı temel Profil 1.1:  
  
-   İleti iletim en iyi duruma getirme mekanizmasını (MTOM) ileti kodlama denetlenen <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> özelliği. Bu özellik olan kendi varsayılan değerinde bırakın <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> MTOM kullanmayacak şekilde.  
  
-   İleti tarafından denetlenen güvenlik <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> değeri, WS-güvenlik desteği WS ile uyumlu sağlar-ı temel güvenlik profili 1.0. Bu özellik olan kendi varsayılan değerinde bırakın <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> WS-güvenlik kullanmayacak şekilde.  
  
 Bir WCF hizmeti için meta veriler kullanılabilir hale getirmek için [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Web hizmeti istemcisi oluşturma araçlarını kullanma: [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Hizmetleri bulma Aracı (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)ve `Add Web Reference` özellik Visual Studio'da; meta veri yayımlama etkinleştirmeniz gerekir. Daha fazla bilgi için bkz: [yayımlama meta veri uç noktalarını](../../../docs/framework/wcf/publishing-metadata-endpoints.md).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği ile uyumlu bir WCF uç noktası eklemek gösterilmiştir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web hizmeti istemcileri kodda ve alternatif olarak, bir yapılandırma dosyası.  
  
### <a name="code"></a>Kod  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET Web Hizmetleri ile Birlikte Çalışabilirlik](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
