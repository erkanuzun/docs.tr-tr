---
title: "Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
caps.latest.revision: "64"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd2740cfef2a618e4ab220f7db84fc78a10e0980
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a><span data-ttu-id="69a4c-102">Nasıl yapılır: Bir Windows Communication Foundation İstemcisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="69a4c-102">How to: Create a Windows Communication Foundation Client</span></span>
<span data-ttu-id="69a4c-103">Bu dördüncü altı görev oluşturmak için gerekli olan bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="69a4c-103">This is the fourth of six tasks required to create a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="69a4c-104">Tüm altı görevlerinin genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="69a4c-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="69a4c-105">Bu konu, meta verilerini almak açıklar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oluşturmak için kullanın ve hizmeti bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmete erişim proxy.</span><span class="sxs-lookup"><span data-stu-id="69a4c-105">This topic describes how to retrieve metadata from a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service and use it to create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy that can access the service.</span></span> <span data-ttu-id="69a4c-106">Bu görev, Visual Studio tarafından sağlanan hizmet Başvurusu Ekle işlevini kullanarak tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="69a4c-106">This task is completed by using the Add Service Reference functionality provided by Visual Studio .</span></span> <span data-ttu-id="69a4c-107">Bu araç hizmetin MEX uç noktasından meta verileri alır ve yönetilen kaynak kodu dosyasının oluşturur istemci proxy dilinde (C# varsayılan olarak) seçtiniz.</span><span class="sxs-lookup"><span data-stu-id="69a4c-107">This tool obtains the metadata from the service’s MEX endpoint and generates a managed source code file for a client proxy in the language you have chosen (C# by default).</span></span> <span data-ttu-id="69a4c-108">İstemci proxy oluşturma, yanı sıra aracı ayrıca oluşturur veya kendi uç noktaları birinde hizmetine bağlanmak için istemci uygulaması sağlayan istemci yapılandırma dosyası güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="69a4c-108">In addition to creating the client proxy, the tool also creates or updates the client configuration file which enables the client application to connect to the service at one of its endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69a4c-109">Aynı zamanda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy sınıfı ve Visual Studio içinde hizmet Başvurusu Ekle kullanmak yerine yapılandırması oluşturmak için aracı.</span><span class="sxs-lookup"><span data-stu-id="69a4c-109">You can also use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to generate the proxy class and configuration instead of using Add Service Reference inside of Visual Studio.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="69a4c-110">Çağrılırken bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] öğesinden bir sınıf kitaplığı projesinde hizmet [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] otomatik olarak bir proxy ve ilişkili yapılandırma dosyası oluşturmak için hizmet Başvurusu Ekle özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69a4c-110">When calling a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service from a class library project in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] you can use the Add Service Reference feature to automatically generate a proxy and associated configuration file.</span></span>  <span data-ttu-id="69a4c-111">Yapılandırma dosyası sınıf kitaplığı proje tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="69a4c-111">The configuration file will not be used by the class library project.</span></span> <span data-ttu-id="69a4c-112">Sınıf kitaplığı çağıracak yürütülebilir dosyası için app.config dosyasına oluşturulan yapılandırma dosyasında ayarları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="69a4c-112">You will need to add the settings in the generated configuration file to the app.config file for the executable that will call the class library.</span></span>  
  
 <span data-ttu-id="69a4c-113">İstemci uygulaması hizmetiyle iletişim kurmak için oluşturulan proxy sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="69a4c-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="69a4c-114">Bu yordamda açıklanan [nasıl yapılır: bir istemci kullanın](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="69a4c-114">This procedure is described in [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
### <a name="to-create-a-windows-communication-foundation-client"></a><span data-ttu-id="69a4c-115">Bir Windows Communication Foundation istemcisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="69a4c-115">To create a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="69a4c-116">Başlarken çözüm seçerek, üzerinde sağ tıklayarak yeni bir konsol uygulama projesi oluşturma **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="69a4c-116">Create a new console application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="69a4c-117">İçinde **Yeni Proje Ekle** iletişim seçin sol tarafındaki iletişim **Windows** altında **C#** veya **VB**.</span><span class="sxs-lookup"><span data-stu-id="69a4c-117">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="69a4c-118">İletişim kutusunun Orta kısım seçin **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="69a4c-118">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="69a4c-119">Proje adı `GettingStartedClient`.</span><span class="sxs-lookup"><span data-stu-id="69a4c-119">Name the project `GettingStartedClient`.</span></span>  
  
2.  <span data-ttu-id="69a4c-120">Sağ tıklayarak GettingStartedClient projenin hedef çerçevesini .NET Framework 4.5 ayarlamak **GettingStartedClient** Çözüm Gezgini'nde seçerek **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="69a4c-120">Set the target framework of the GettingStartedClient project to .NET Framework 4.5 by right clicking on **GettingStartedClient** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="69a4c-121">Aşağı açılan kutusunda etiketli **hedef Framework** seçin **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="69a4c-121">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="69a4c-122">Hedef Framework'ü GettingStartedClient Proje Özellikleri iletişim kutusunda, biraz farklı VB projedir ayarı, tıklatın **derleme** sekmesinde ekranın sol tarafında ve ardından **Gelişmiş Derleme Seçenekleri** iletişim kutusunun sol alt köşesindeki düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69a4c-122">Setting the target framework for a VB project is a little different, in the GettingStartedClient project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="69a4c-123">Ardından **.NET Framework 4.5** açılır kutusunda etiketli **hedef Framework**.</span><span class="sxs-lookup"><span data-stu-id="69a4c-123">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="69a4c-124">Hedef Framework'ü ayarlanırsa, çözümü yeniden yüklemek Visual Studio 2011'e basın **Tamam** istendiğinde.</span><span class="sxs-lookup"><span data-stu-id="69a4c-124">Setting the target framework will cause Visual Studio 2011 to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="69a4c-125">System.ServiceModel başvuru GettingStartedClient projeye sağ tıklayarak ekleyin **başvuru** klasörü altında Çözüm Gezgini'nde ve select GettingStartedClient proje **Ekle** Başvuru.</span><span class="sxs-lookup"><span data-stu-id="69a4c-125">Add a reference to System.ServiceModel to the GettingStartedClient project by right-clicking the **Reference** folder under the GettingStartedClient project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="69a4c-126">İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki.</span><span class="sxs-lookup"><span data-stu-id="69a4c-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="69a4c-127">Arama derlemeleri metin kutusuna yazın `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="69a4c-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="69a4c-128">İletişim kutusunun Orta kısım seçin **System.ServiceModel**, tıklatın **Ekle** düğmesine tıklayın ve **Kapat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69a4c-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="69a4c-129">Tıklayarak çözümü kaydetmek **Tümünü Kaydet** aşağıda ana menü düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69a4c-129">Save the solution by clicking the **Save All** button below the main menu.</span></span>  
  
4.  <span data-ttu-id="69a4c-130">Sonraki wlll hesaplayıcı hizmetine hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69a4c-130">Next you wlll add a service reference to the Calculator Service.</span></span> <span data-ttu-id="69a4c-131">Bunu yapmadan önce GettingStartedHost konsol uygulamasını başlatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="69a4c-131">Before you can do that, you must start up the GettingStartedHost console application.</span></span> <span data-ttu-id="69a4c-132">Ana bilgisayar çalışmaya başladıktan sonra başvuruları klasörü altında Çözüm Gezgini'nde GettingStartedClient projeye sağ tıklayın ve hizmet Başvurusu Ekle iletişim kutusunun adres kutusuna aşağıdaki URL'de hizmet Başvurusu Ekle ve türünü seçin: HYPERLINK "http:/ / localhost:8000/ServiceModelSamples/hizmet "ServiceModelSamples/8000/hizmet ve tıklatın **Git** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69a4c-132">Once the host is running you can right click the References folder under the GettingStartedClient project in the Solution Explorer and select Add Service Reference and type in the following URL in the address box of the Add Service Reference dialog:  HYPERLINK "http://localhost:8000/ServiceModelSamples/Service" http://localhost:8000/ServiceModelSamples/Service and   click the **Go** button.</span></span> <span data-ttu-id="69a4c-133">CalculatorService sonra hizmetleri liste kutusunda çift tıklatın CalculatorService görüntülenmesi gerekir ve onu genişletin ve hizmeti tarafından uygulanan Hizmet sözleşmeleri göster.</span><span class="sxs-lookup"><span data-stu-id="69a4c-133">The CalculatorService should then be displayed in the Services list box, Double click CalculatorService and it will expand and show the service contracts implemented by the service.</span></span> <span data-ttu-id="69a4c-134">Varsayılan ad olan ve'ı tıklatın bırakın **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="69a4c-134">Leave the default namespace as is and click the **OK** button.</span></span>  
  
     <span data-ttu-id="69a4c-135">Visual Studio yeni bir öğe kullanarak bir hizmet için bir başvuru GettingStartedClient projesinin altındaki hizmeti başvuruları klasörü altında Çözüm Gezgini'nde görünecektir eklediğinizde.</span><span class="sxs-lookup"><span data-stu-id="69a4c-135">When you add a reference to a service using Visual Studio a new item will appear in the Solution Explorer under the Service References folder under the GettingStartedClient project.</span></span>  <span data-ttu-id="69a4c-136">Kullanırsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı bir kaynak kodu dosyasının ve app.config dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="69a4c-136">If you use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool a source code file and app.config file will be generated.</span></span>  
  
     <span data-ttu-id="69a4c-137">Komut satırı aracı kullanabilirsiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci kodu oluşturmak için uygun anahtarlara sahip.</span><span class="sxs-lookup"><span data-stu-id="69a4c-137">You can also use the command-line tool [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the appropriate switches to create the client code.</span></span> <span data-ttu-id="69a4c-138">Aşağıdaki örnek kod dosyası ve hizmet için bir yapılandırma dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="69a4c-138">The following example generates a code file and a configuration file for the service.</span></span> <span data-ttu-id="69a4c-139">İlk örnek içinde VB proxy oluşturmak nasıl gösterir ve ikinci oluşturulan proxy C# ' ta gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="69a4c-139">The first example shows how to generate the proxy in VB and the second shows how to generated the proxy in C#:</span></span>  
  
    ```  
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
    ```csharp  
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/ServiceModelSamples/service  
    ```  
  
 <span data-ttu-id="69a4c-140">İstemci uygulaması hesaplayıcı hizmetini çağırmak için kullanacağı proxy oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="69a4c-140">You have now created the proxy that the client application will use to call the calculator service.</span></span> <span data-ttu-id="69a4c-141">Serideki sonraki bölümüne geçin: [nasıl yapılır: bir istemci yapılandırma](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)</span><span class="sxs-lookup"><span data-stu-id="69a4c-141">Proceed to the next topic in the series: [How to: Configure a Client](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a4c-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69a4c-142">See Also</span></span>  
 [<span data-ttu-id="69a4c-143">ServiceModel meta veri yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="69a4c-143">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="69a4c-144">Başlarken</span><span class="sxs-lookup"><span data-stu-id="69a4c-144">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="69a4c-145">Kendini barındırma</span><span class="sxs-lookup"><span data-stu-id="69a4c-145">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="69a4c-146">Nasıl yapılır: bir yapılandırma dosyası kullanarak bir hizmet için meta verileri yayımlama</span><span class="sxs-lookup"><span data-stu-id="69a4c-146">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="69a4c-147">Nasıl yapılır: meta veri belgelerini indirmek için Svcutil.exe kullanma</span><span class="sxs-lookup"><span data-stu-id="69a4c-147">How to: Use Svcutil.exe to Download Metadata Documents</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)