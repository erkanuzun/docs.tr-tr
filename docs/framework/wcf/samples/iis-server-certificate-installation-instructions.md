---
title: "Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0d035e703b79eb184bf06e3e75255e2f987c170
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="08688-102">Internet Information Services (IIS) Sunucu Sertifikası Yükleme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="08688-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="08688-103">Internet Information Services (IIS) güvenli iletişim örnekleri çalıştırmak için oluşturma ve sunucu sertifikasını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="08688-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="08688-104">Adım 1.</span><span class="sxs-lookup"><span data-stu-id="08688-104">Step 1.</span></span> <span data-ttu-id="08688-105">Sertifikaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="08688-105">Creating Certificates</span></span>  
 <span data-ttu-id="08688-106">Bilgisayarınız için bir sertifika oluşturmak için yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve her IIS ile güvenli iletişim kullanmak örnekleri dahil Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="08688-106">To create a certificate for your computer, open a Visual Studio command prompt with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="08688-107">Bu toplu iş dosyasını çalıştırmadan önce Makecert.exe içeren klasörün yolunu içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="08688-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="08688-108">Aşağıdaki komutu Setup.bat sertifikayı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08688-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="08688-109">Adım 2.</span><span class="sxs-lookup"><span data-stu-id="08688-109">Step 2.</span></span> <span data-ttu-id="08688-110">Sertifikaları yükleme</span><span class="sxs-lookup"><span data-stu-id="08688-110">Installing Certificates</span></span>  
 <span data-ttu-id="08688-111">Yeni oluşturduğunuz sertifikaları yüklemek için gerekli olan adımları IIS sürümünü kullanmakta olduğunuz üzerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="08688-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="08688-112">IIS 5.1 (Windows XP) ve IIS 6. 0'ı (Windows Server 2003) IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="08688-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1.  <span data-ttu-id="08688-113">Internet Bilgi Hizmetleri Yöneticisi'ni MMC ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="08688-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2.  <span data-ttu-id="08688-114">Varsayılan Web sitesini sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="08688-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="08688-115">Seçin **dizin güvenliği** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="08688-115">Select the **Directory Security** tab.</span></span>  
  
4.  <span data-ttu-id="08688-116">Tıklatın **sunucu sertifikası** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="08688-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="08688-117">Web Sunucusu Sertifika Sihirbazı'nı başlatır.</span><span class="sxs-lookup"><span data-stu-id="08688-117">The Web Server Certificate Wizard starts.</span></span>  
  
5.  <span data-ttu-id="08688-118">Sihirbazı tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="08688-118">Complete the wizard.</span></span> <span data-ttu-id="08688-119">Bir sertifika atama seçeneğini seçin.</span><span class="sxs-lookup"><span data-stu-id="08688-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="08688-120">ServiceModelSamples HTTPS sunucusu sertifikasını görüntülenen sertifika listesinden seçin.</span><span class="sxs-lookup"><span data-stu-id="08688-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="08688-121">![IIS Sertifika Sihirbazı](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="08688-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6.  <span data-ttu-id="08688-122">Hizmete erişim HTTPS adresi https://localhost/servicemodelsamples/service.svc kullanarak bir tarayıcıda sınayın.</span><span class="sxs-lookup"><span data-stu-id="08688-122">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="08688-123">SSL, daha önce Httpcfg.exe kullanılarak yapılandırıldıysa</span><span class="sxs-lookup"><span data-stu-id="08688-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1.  <span data-ttu-id="08688-124">MakeCert.exe (veya çalışma Setup.bat) sunucu sertifikası oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="08688-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2.  <span data-ttu-id="08688-125">IIS Yöneticisi'ni çalıştırın ve önceki adımları göre sertifika yükleyin.</span><span class="sxs-lookup"><span data-stu-id="08688-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3.  <span data-ttu-id="08688-126">Aşağıdaki kod satırını istemci programına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="08688-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08688-127">Bu kod yalnızca gerekli olan test Makecert.exe tarafından oluşturulanlar gibi sertifikaları.</span><span class="sxs-lookup"><span data-stu-id="08688-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="08688-128">Üretim kodu için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="08688-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="08688-129">IIS 7.0 (Windows Vista ve Windows Server 2008) IIS yüklemek için</span><span class="sxs-lookup"><span data-stu-id="08688-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1.  <span data-ttu-id="08688-130">Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın **inetmgr** Internet Information Services (IIS) MMC ek bileşenini açmak için.</span><span class="sxs-lookup"><span data-stu-id="08688-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="08688-131">Sağ **varsayılan Web sitesi** seçip **bağlamaları Düzenle...**</span><span class="sxs-lookup"><span data-stu-id="08688-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3.  <span data-ttu-id="08688-132">Tıklatın **Ekle** düğmesine **Site bağlamaları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="08688-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4.  <span data-ttu-id="08688-133">Seçin **HTTPS** gelen **türü** aşağı açılan liste.</span><span class="sxs-lookup"><span data-stu-id="08688-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5.  <span data-ttu-id="08688-134">Seçin **ServiceModelSamples HTTPS sunucusu** gelen **SSL sertifikası** aşağı açılan liste ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="08688-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6.  <span data-ttu-id="08688-135">Hizmete erişim HTTPS adresi https://localhost/servicemodelsamples/service.svc kullanarak bir tarayıcıda sınayın.</span><span class="sxs-lookup"><span data-stu-id="08688-135">Test access to the service in a browser by using the HTTPS address https://localhost/servicemodelsamples/service.svc.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08688-136">Yeni yüklediğiniz test sertifikası güvenilen bir sertifika olduğundan, bu sertifikası ile güvenli yerel Web adresler gözatarken ek Internet Explorer güvenlik uyarılarını karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08688-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="08688-137">Sertifikaları kaldırma</span><span class="sxs-lookup"><span data-stu-id="08688-137">Removing Certificates</span></span>  
  
-   <span data-ttu-id="08688-138">Internet Information Services Yöneticisi, daha önce yönlendirilmiş ancak sertifika veya onu eklemek yerine bağlama Kaldır olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="08688-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
-   <span data-ttu-id="08688-139">Aşağıdaki komutu kullanarak bilgisayar sertifikası kaldırın.</span><span class="sxs-lookup"><span data-stu-id="08688-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```