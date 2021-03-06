---
title: Geliştirme ve WCF Veri Hizmetleri dağıtma
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- deploying [WCF Data Services
- developing applications [WCF Data Services]
ms.assetid: 6557c0e3-5aea-4f6e-bc14-77ad317a168b
ms.openlocfilehash: ca0f78239e6e259ec5bd75e9f93af5c3a4b7adf1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805453"
---
# <a name="developing-and-deploying-wcf-data-services"></a>Geliştirme ve WCF Veri Hizmetleri dağıtma
Bu konuda geliştirme ve dağıtma hakkında bilgi verilmektedir [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Hakkında daha fazla temel bilgiler için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], bkz: [Başlarken](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md) ve [genel bakış](../../../../docs/framework/data/wcf/wcf-data-services-overview.md).  
  
## <a name="developing-wcf-data-services"></a>WCF Veri Hizmetleri Geliştirme  
 Kullandığınızda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] destekleyen bir veri hizmeti oluşturmak için [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], geliştirme sırasında aşağıdaki temel görevleri gerçekleştirmeniz gerekir:  
  
1.  **Veri modelini tanımlar**  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] geç bağlama veri türleri için ilişkisel veritabanlarından veri kaynakları çeşitli dayalı bir veri modeli tanımlamanıza olanak sağlayan veri hizmeti sağlayıcıları, çeşitli destekler. Daha fazla bilgi için bkz: [Veri Hizmetleri sağlayıcıları](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
2.  **Veri hizmeti oluşturma**  
  
     Öğesinden devralınan bir sınıf en temel veri hizmeti sunan <xref:System.Data.Services.DataService%601> sınıfının bir türü `T` olan ad alanı tam varlık kapsayıcısının adı. Daha fazla bilgi için bkz: [tanımlayan WCF Veri Hizmetleri](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Veri Hizmeti yapılandırma**  
  
     Varsayılan olarak, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bir varlık kapsayıcısı tarafından sunulan kaynaklara erişimi devre dışı bırakır. <xref:System.Data.Services.DataServiceConfiguration> Arabirimi kaynaklarına erişimi yapılandırmak ve işlemleri hizmet, desteklenen bir sürümü olanak tanır [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]ve davranışları veya yapabilirsiniz varlıkların sayısı toplu işleme gibi diğer hizmet geneli davranışları tanımlamak için Akış tek bir yanıtta döndürülen. Daha fazla bilgi için bkz: [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Bu konu, Visual Studio kullanarak birincil olarak geliştirme ve Veri Hizmetleri dağıtımını kapsar. Tarafından sağlanan esneklik hakkında bilgi için [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] verilerinizi olarak gösterme için [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] akışlarını bkz [tanımlayan WCF Veri Hizmetleri](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
### <a name="choosing-a-development-web-server"></a>Geliştirme Web Sunucusu Seçme  
 WCF veri hizmeti olarak geliştirirken bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Visual Studio'yu kullanarak Web sitesi geliştirme sırasında veri hizmeti çalıştırmak için Web sunucularında seçimine sahip. Aşağıdaki Web sunucuları, test ve hata ayıklama veri hizmetlerinizi yerel bilgisayarda daha kolay hale getirmek için Visual Studio ile tümleştirin.  
  
1.  **Yerel IIS sunucusu**  
  
     Veri Hizmeti oluşturduğunuzda olan bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Internet Information Services (IIS) çalıştıran Web sitesini öneririz geliştirmek ve veri hizmeti yerel bilgisayarda IIS kullanarak test. IIS üzerinde veri hizmetinin çalıştırılması, hata ayıklama sırasında HTTP isteklerinin izlenmesini kolaylaştırır. Bu, IIS tarafından dosyalara, veritabanlarına ve veri hizmeti tarafından gerekli kılınan diğer kaynaklara erişmek için gereken hakları önceden belirlemenizi de sağlar. Veri Hizmeti IIS üzerinde çalıştırmak için gereken yapar IIS ve Windows Communication Foundation (WCF) yüklü ve doğru şekilde yapılandırıldığından emin ve dosya sistemi ve veritabanlarında IIS hesaplarına erişim vermek. Daha fazla bilgi için bkz: [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirmek](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
    > [!NOTE]
    >  Visual Studio yerel IIS sunucusunu yapılandırmak geliştirme ortamı sağlamak için yönetici haklarıyla çalıştırmanız gerekir.  
  
2.  **Visual Studio geliştirme sunucusu**  
  
     Visual Studio içeren yerleşik bir Web sunucusu, Visual Studio geliştirme sunucusu varsayılan Web sunucu için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeleri. Bu Web sunucusu çalışmak üzere tasarlanmıştır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeleri geliştirme sırasında yerel bilgisayarda. [WCF Veri Hizmetleri quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) Visual Studio geliştirme sunucusunda çalışan bir veri hizmetin nasıl oluşturulacağını gösterir.  
  
     Veri hizmeti geliştirmek için Visual Studio geliştirme sunucusu kullanırken aşağıdaki sınırlamaları bilmeniz gerekir:  
  
    -   Bu sunucuya yalnızca yerel bilgisayar üzerinde erişilebilir.  
  
    -   Bu sunucunun dinlediği `localhost` ve belirli bir bağlantı noktası, HTTP iletileri için varsayılan bağlantı noktası olan olmayan bağlantı noktası 80. Daha fazla bilgi için bkz: [ASP.NET Web projeleri için Visual Studio'da Web sunucuları](http://msdn.microsoft.com/library/31d4f588-df59-4b7e-b9ea-e1f2dd204328).  
  
    -   Bu sunucu, geçerli kullanıcı hesabınızın bağlamında veri hizmetini çalıştırır. Örneğin, bir yönetici düzeyi kullanıcı olarak çalıştırıyorsanız, Visual Studio geliştirme sunucusunda çalışan bir veri hizmeti yönetici ayrıcalıklarına sahip olacaktır. Bu, veri hizmetinin IIS sunucusuna dağıtıldığında erişim hakkı olmayan kaynaklara erişebilmesini sağlar.  
  
    -   Bu sunucu, IIS'nin kimlik doğrulama gibi ek özelliklerini içermez.  
  
    -   Bu sunucu öbekli HTTP işleyemiyor gönderilen akışları olması varsayılan olarak [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] büyük ikili veri veri hizmetinden erişirken istemci. Daha fazla bilgi için bkz: [Akış sağlayıcısı](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
    -   Bu sunucu işleme süresi ile sorunları vardır (`.`) rağmen bu karakteri tarafından desteklenen bir URL'de karakter [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] anahtar değerleri.  
  
    > [!TIP]
    >  Veri Hizmetleri geliştirme sırasında test etmek için Visual Studio geliştirme sunucusu kullanabileceğiniz olsa bile, IIS çalıştıran bir Web sunucusu dağıttıktan sonra sınamalısınız.  
  
3.  **Windows Azure geliştirme ortamı**  
  
     Windows Azure Araçları Visual Studio için Visual Studio'da Windows Azure hizmetlerini geliştirmek için Araçlar tümleşik bir dizi içerir. Bu araçlarla, Microsoft Azure'a dağıtılabilen bir veri hizmeti geliştirebilir ve veri hizmetini dağıtımdan önce yerel bilgisayarda test edebilirsiniz. Windows Azure platformu üzerinde çalışan veri hizmeti geliştirmek için Visual Studio kullanarak bu araçları kullanın. Visual Studio'dan için Windows Azure Araçları'nı yükleyebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). Post Windows Azure üzerinde çalışan veri hizmeti geliştirme hakkında daha fazla bilgi için bkz: [Windows Azure bir OData hizmetini dağıtma](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="development-tips"></a>Geliştirme İpuçları  
 Bir veri hizmeti geliştirirken, aşağıdakileri dikkate almanız gerekir:  
  
-   Kullanıcıların kimliğini doğrulamayı veya belirli kullanıcılar için erişimi kısıtlamayı planlıyorsanız, veri hizmetinizin güvenlik gereksinimlerini belirleyin. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri güvenli hale getirme](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
-   HTTP inceleme programı, istek ve yanıt iletilerinin içeriğini denetlemenizi sağlayarak veri hizmetinde hata ayıklarken size epey yardımcı olabilir. Veri hizmetine yapılan HTTP isteklerini ve veri hizmetinden alınan yanıtları denetlemek için ham paketleri görüntüleyebilen herhangi bir ağ paketi çözümleyicisi kullanılabilir.  
  
-   Veri hizmetinde hata ayıklarken, veri hizmetinden bir hatayla ilgili olarak normal çalışmaya göre daha fazla bilgi almak isteyebilirsiniz. Ek hata bilgileri ayarlayarak veri hizmetinden veri alma <xref:System.Data.Services.DataServiceConfiguration.UseVerboseErrors%2A> özelliğinde <xref:System.Data.Services.DataServiceConfiguration> için `true` ayarlayarak <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A> özelliği <xref:System.ServiceModel.Description.ServiceDebugBehavior> verihizmetisınıfınaöznitelikte`true`. Post daha fazla bilgi için bkz: [hata ayıklama WCF Veri Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=201868). WCF HTTP Mesajlaşma katmanda yükseltilmiş özel durumlarını görüntülemek için izleme de etkinleştirebilirsiniz. Daha fazla bilgi için bkz: [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Veri Hizmeti genellikle olarak geliştirilen bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama projesi, ancak da oluşturabilir, veri hizmeti olarak bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Visual Studio'da Web sitesi projesi. İki proje türleri arasındaki farklar hakkında daha fazla bilgi için bkz: [NIB: Visual Studio'da Web sitesi projeleri ile Web uygulaması projelerine](http://msdn.microsoft.com/library/2861815e-f5a2-4378-a2f8-b8a86dc012f5).  
  
-   Kullanarak bir veri hizmeti oluşturduğunuzda **Yeni Öğe Ekle** Visual Studio'da veri hizmeti iletişim kutusu tarafından barındırılan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] IIS'de. Sırada [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve IIS varsayılan ana bilgisayar veri hizmeti için farklı barındırma seçenekleri desteklenir. Daha fazla bilgi için bkz: [veri hizmetini barındıran](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md).  
  
## <a name="deploying-wcf-data-services"></a>WCF Veri Hizmetlerini Dağıtma  
 WCF Veri Hizmeti, veri hizmetini barındıran işlemi seçmede esneklik sağlar. Veri hizmeti aşağıdaki platformlara dağıtmak için Visual Studio'yu kullanabilirsiniz:  
  
-   **IIS tarafından barındırılan Web sunucusu**  
  
     Bir veri hizmeti zaman geliştirilmiş olarak bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projesi için IIS Web sunucusunu, dağıtılabilir standart kullanarak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dağıtım işlemleri.  Visual Studio için aşağıdaki dağıtım teknolojileri sağlar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]türü bağlı olarak, [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dağıtmakta olduğunuz veri hizmeti barındıran proje.  
  
    -   **ASP.NET Web uygulamaları için dağıtım teknolojileri**  
  
        -   [Web dağıtım paketi](http://msdn.microsoft.com/library/1f9713c8-9540-494c-b80d-9893b970ad6f)  
  
        -   [Tek tıklamayla yayımlama](http://msdn.microsoft.com/library/59226246-99ad-4aec-975d-7c61e8a8911c)  
  
    -   **ASP.NET Web siteleri için dağıtım teknolojileri**  
  
        -   [Web sitesi aracı kopyalayın](http://msdn.microsoft.com/library/b819aed4-014b-427e-be80-02317b1bb003)  
  
        -   [Web sitesi aracı yayımlama](http://msdn.microsoft.com/library/d0a1a20f-15be-4940-9485-cb8e4aa8181b)  
  
        -   [XCopy](http://msdn.microsoft.com/library/4312c651-2119-49be-bbeb-ee28bdbfe71e)  
  
     Dağıtım seçenekleri hakkında daha fazla bilgi için bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama, bkz: [Visual Studio ve ASP.NET Web dağıtımına genel bakış](http://msdn.microsoft.com/library/99bd1927-b59f-4e02-87b4-55c6ba2adbc3).  
  
    > [!TIP]
    >  Veri hizmetini IIS'ye dağıtmayı denemeden önce, IIS çalıştıran Web sunucusuna dağıtımı test ettiğinizden emin olun. Daha fazla bilgi için bkz: [nasıl yapılır: bir WCF veri hizmeti üzerinde çalışan IIS geliştirmek](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).  
  
-   **Microsoft Azure**  
  
     Visual Studio için Windows Azure araçları kullanarak, bir veri hizmeti Windows Azure'a dağıtabilirsiniz. Visual Studio'dan için Windows Azure Araçları'nı yükleyebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=201848). Post için Windows Azure veri hizmeti dağıtma hakkında daha fazla bilgi için bkz: [Windows Azure bir OData hizmetini dağıtma](http://go.microsoft.com/fwlink/?LinkId=201847).  
  
### <a name="deployment-considerations"></a>Dağıtım Hakkında Önemli Noktalar  
 Bir veri hizmetini dağıtırken, aşağıdakileri dikkate almanız gerekir:  
  
-   Kullanan bir veri hizmeti dağıttığınızda [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] bir SQL Server veritabanına erişmek için sağlayıcı veri yapılarını, verileri yaymak gerekebilir veya ikisi verilerinizi ile dağıtım hizmet. Visual Studio hedef veritabanında bunun için komut dosyalarını (.sql dosyaları) otomatik olarak oluşturabilir ve bu komut dosyaları Web dağıtımı paketi dahil edilebilir bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: bir veritabanı ile bir Web uygulaması projesi dağıtma](http://msdn.microsoft.com/library/683b33f1-8a3d-45cf-af6e-61ab50fc518b). İçin bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web sitesi, bunu yapabilirsiniz kullanarak **veritabanı Yayımlama Sihirbazı'nı** Visual Studio. Daha fazla bilgi için bkz: [veritabanı Yayımlama Sihirbazı'nı kullanarak bir veritabanı dağıtma](http://msdn.microsoft.com/library/1e3682e7-8b57-4da6-a393-af9640ccf8b7).  
  
-   Çünkü [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] temel bir WCF uygulaması içeren Windows Server AppFabric, IIS Windows Server'da çalışan dağıtılmış bir veri hizmeti izlemek için kullanabilirsiniz. Post veri hizmeti izlemek için Windows Server AppFabric kullanma hakkında daha fazla bilgi için bkz: [izleme WCF Veri Hizmetleri ile Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=202005).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Hizmeti Barındırma](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 [WCF Veri Hizmetlerinin Güvenliğini Sağlama](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
