---
title: "Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 8137e41f92335849916dfc9e9ce72afeb186e73c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="abd52-102">Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="abd52-102">How to: Add Installers to Your Service Application</span></span>
<span data-ttu-id="abd52-103">Visual Studio hizmet uygulamalarınızla ilişkili kaynakları yükleyebilirsiniz Yükleme bileşenleri gelir.</span><span class="sxs-lookup"><span data-stu-id="abd52-103">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="abd52-104">Yükleme bileşenleri bireysel bir hizmet olarak yüklendiği ve Hizmet Denetim Yöneticisi'nin hizmetinin var olduğunu bilmek istiyorum sistemdeki kaydedin.</span><span class="sxs-lookup"><span data-stu-id="abd52-104">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="abd52-105">Bir hizmet uygulaması ile çalışırken, bağlantı otomatik olarak uygun yükleyicileri projenize eklemek için Özellikler penceresini seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abd52-105">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abd52-106">Hizmetiniz için özellik değerleri hizmet sınıfından yükleyici sınıfa kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="abd52-106">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="abd52-107">Hizmet sınıfı özellik değerlerini güncelleştirirseniz, bunlar otomatik olarak yükleyicisinde güncelleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="abd52-107">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="abd52-108">Projenize yeni bir sınıf bir yükleyici eklediğinizde (varsayılan olarak adlandırılan, `ProjectInstaller`) proje ve bileşenleri içinde oluşturulur uygun yükleme örnekleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="abd52-108">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="abd52-109">Bu sınıf davranır tüm yükleme bileşenleri için merkezi bir nokta olarak projenizi gerekir.</span><span class="sxs-lookup"><span data-stu-id="abd52-109">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="abd52-110">Örneğin, ikinci bir hizmeti uygulamanıza ekleyin ve Yükleyici Ekle bağlantısına tıklayın, ikinci bir yükleyici sınıfı oluşturulmaz; Bunun yerine, ikinci hizmeti için gerekli ek yükleme bileşen varolan bir sınıfa eklenir.</span><span class="sxs-lookup"><span data-stu-id="abd52-110">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="abd52-111">Hizmetlerinizin düzgün yüklenmesi yapmak için yükleyiciler içinde özel hiçbir kodlama yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="abd52-111">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="abd52-112">Ancak, bazen yükleme işlemine özel işlevsellik eklemeniz gerekiyorsa yükleyicileri içeriğini değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="abd52-112">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abd52-113">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="abd52-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="abd52-114">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="abd52-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="abd52-115">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="abd52-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="abd52-116">Hizmet uygulamasına yükleyiciler eklemek için</span><span class="sxs-lookup"><span data-stu-id="abd52-116">To add installers to your service application</span></span>  
  
1.  <span data-ttu-id="abd52-117">İçinde **Çözüm Gezgini**, erişim **tasarım** bir yükleme bileşeni eklemek istediğiniz hizmet için görünümü.</span><span class="sxs-lookup"><span data-stu-id="abd52-117">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2.  <span data-ttu-id="abd52-118">Hizmet seçmek için tasarlayıcı arka planını kendisi yerine İçeriklerinden biri'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="abd52-118">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3.  <span data-ttu-id="abd52-119">Odak, sağ tıklatın ve ardından Tasarımcısı ile **Yükleyici Ekle**.</span><span class="sxs-lookup"><span data-stu-id="abd52-119">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="abd52-120">Yeni bir sınıf `ProjectInstaller`ve iki yükleme bileşenleri <xref:System.ServiceProcess.ServiceProcessInstaller> ve <xref:System.ServiceProcess.ServiceInstaller>, hizmet kopyalanır için bileşenlere, proje ve özellik değerleri için eklenir.</span><span class="sxs-lookup"><span data-stu-id="abd52-120">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4.  <span data-ttu-id="abd52-121">' I tıklatın <xref:System.ServiceProcess.ServiceInstaller> bileşen doğrulayın değerini <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> özelliği aynı değere ayarlanmış <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> hizmeti özelliği.</span><span class="sxs-lookup"><span data-stu-id="abd52-121">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5.  <span data-ttu-id="abd52-122">Hizmetinizi çalışmaya nasıl belirlemek için tıklatın <xref:System.ServiceProcess.ServiceInstaller> bileşen ve ayarlanmış <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> uygun değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="abd52-122">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="abd52-123">Değer</span><span class="sxs-lookup"><span data-stu-id="abd52-123">Value</span></span>|<span data-ttu-id="abd52-124">Sonuç</span><span class="sxs-lookup"><span data-stu-id="abd52-124">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="abd52-125">Hizmeti yüklendikten sonra el ile başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="abd52-125">The service must be manually started after installation.</span></span> <span data-ttu-id="abd52-126">Daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri başlatma](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="abd52-126">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="abd52-127">Bilgisayar yeniden başlatıldığında hizmet kendiliğinden başlar.</span><span class="sxs-lookup"><span data-stu-id="abd52-127">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="abd52-128">Hizmet başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="abd52-128">The service cannot be started.</span></span>|  
  
6.  <span data-ttu-id="abd52-129">Hizmetinizin çalışacağı güvenlik bağlamı belirlemek için tıklatın <xref:System.ServiceProcess.ServiceProcessInstaller> bileşeni ve uygun özellik değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="abd52-129">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="abd52-130">Daha fazla bilgi için bkz: [nasıl yapılır: Hizmetleri için güvenlik bağlamı belirtin](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span><span class="sxs-lookup"><span data-stu-id="abd52-130">For more information, see [How to: Specify the Security Context for Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span></span>  
  
7.  <span data-ttu-id="abd52-131">Özel işleme gerçekleştirmek gereken yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="abd52-131">Override any methods for which you need to perform custom processing.</span></span>  
  
8.  <span data-ttu-id="abd52-132">Projenizdeki ek her hizmet için 1 ile 7 arasındaki adımları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="abd52-132">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="abd52-133">Projenizdeki her ek hizmet için ek bir eklemelisiniz <xref:System.ServiceProcess.ServiceInstaller> projenin bileşen `ProjectInstaller` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="abd52-133">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="abd52-134"><xref:System.ServiceProcess.ServiceProcessInstaller> Üç adımda eklenen bileşeni, bireysel hizmet yükleyicileri projedeki tüm çalışır.</span><span class="sxs-lookup"><span data-stu-id="abd52-134">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd52-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abd52-135">See Also</span></span>  
 [<span data-ttu-id="abd52-136">Windows hizmet uygulamalarına giriş</span><span class="sxs-lookup"><span data-stu-id="abd52-136">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="abd52-137">Nasıl yapılır: Hizmetleri Yükleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="abd52-137">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="abd52-138">Nasıl yapılır: Hizmetleri başlatma</span><span class="sxs-lookup"><span data-stu-id="abd52-138">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="abd52-139">Nasıl yapılır: Hizmetleri için güvenlik bağlamı belirtin</span><span class="sxs-lookup"><span data-stu-id="abd52-139">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)