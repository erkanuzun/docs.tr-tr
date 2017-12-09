---
title: "Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fed03374a21406866b19d0028ee24edfc7edb707
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a><span data-ttu-id="ff016-102">Nasıl yapılır: Bir İş Akışı Uygulamasından Bir Hizmete Erişme</span><span class="sxs-lookup"><span data-stu-id="ff016-102">How To: Access a Service From a Workflow Application</span></span>
<span data-ttu-id="ff016-103">Bu konuda, bir iş akışı konsol uygulamasından bir iş akışı hizmeti çağırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="ff016-103">This topic describes how to call a workflow service from a workflow console application.</span></span> <span data-ttu-id="ff016-104">Tamamlanma bağlı olduğu [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ff016-104">It depends on completion of the [How to: Create a Workflow Service with Messaging Activities](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span> <span data-ttu-id="ff016-105">Herhangi bir çağrıda için bu konu bir iş akışı uygulamasından bir iş akışı hizmeti nasıl açıklansa da, aynı yöntemleri kullanılabilir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir iş akışı uygulamasından service.</span><span class="sxs-lookup"><span data-stu-id="ff016-105">Although this topic describes how to call a workflow service from a workflow application, the same methods can be used to call any [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service from a workflow application.</span></span>  
  
### <a name="create-a-workflow-console-application-project"></a><span data-ttu-id="ff016-106">Bir iş akışı konsol uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff016-106">Create a Workflow Console Application Project</span></span>  
  
1.  <span data-ttu-id="ff016-107">Başlat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff016-107">Start [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="ff016-108">Oluşturduğunuz MyWFService proje yük [nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) konu.</span><span class="sxs-lookup"><span data-stu-id="ff016-108">Load the MyWFService project you created in the [How to: Create a Workflow Service with Messaging Activities](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md) topic.</span></span>  
  
3.  <span data-ttu-id="ff016-109">Sağ tıklayın **MyWFService** çözümde **Çözüm Gezgini** seçip **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="ff016-109">Right click the **MyWFService** solution in the **Solution Explorer** and select **Add**, **New Project**.</span></span> <span data-ttu-id="ff016-110">Seçin **iş akışı** içinde **yüklü şablonlar** ve **iş akışı konsol uygulaması** proje türleri listesinden.</span><span class="sxs-lookup"><span data-stu-id="ff016-110">Select **Workflow** in the **Installed Templates** and **Workflow Console Application** from the list of project types.</span></span> <span data-ttu-id="ff016-111">Projeyi MyWFClient adlandırın ve varsayılan konumu aşağıdaki çizimde gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff016-111">Name the project MyWFClient and use the default location as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="ff016-112">![Yeni Proje iletişim kutusu ekleme](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")</span><span class="sxs-lookup"><span data-stu-id="ff016-112">![Add New Project Dialog](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")</span></span>  
  
     <span data-ttu-id="ff016-113">Tıklatın **Tamam** kapatmak için düğmesini **yeni proje iletişim kutusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="ff016-113">Click the **OK** button to dismiss the **Add New Project Dialog**.</span></span>  
  
4.  <span data-ttu-id="ff016-114">Proje oluşturulduktan sonra Workflow1.xaml dosyası tasarımcıda açılır.</span><span class="sxs-lookup"><span data-stu-id="ff016-114">After the project is created, the Workflow1.xaml file is opened in the designer.</span></span> <span data-ttu-id="ff016-115">Tıklatın **araç** sekmesini zaten açın ve araç penceresi açık tutmak için Raptiye tıklatın değilse araç kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="ff016-115">Click the **Toolbox** tab to open the toolbox if it is not already open and click the pushpin to keep the toolbox window open.</span></span>  
  
5.  <span data-ttu-id="ff016-116">Derleme ve hizmeti başlatmak için Ctrl + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ff016-116">Press Ctrl + F5 to build and launch the service.</span></span> <span data-ttu-id="ff016-117">Önceki gibi ASP.NET Geliştirme Sunucusu başlatılır ve Internet Explorer WCF Yardım sayfasını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ff016-117">As before, the ASP.NET Development Server is launched and Internet Explorer displays the WCF Help Page.</span></span> <span data-ttu-id="ff016-118">Sonraki adımda kullanmanız gerektiği gibi bu sayfa için URI dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ff016-118">Notice the URI for this page as you must use it in the next step.</span></span>  
  
     <span data-ttu-id="ff016-119">![WCF Yardım sayfası ve URI IE görüntüleme](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")</span><span class="sxs-lookup"><span data-stu-id="ff016-119">![IE displaying WCF Help Page and URI](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")</span></span>  
  
6.  <span data-ttu-id="ff016-120">Sağ tıklayın **MyWFClient** proje **Çözüm Gezgini** seçip **hizmet Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="ff016-120">Right click the **MyWFClient** project in the **Solution Explorer** and select **Add Service Reference**.</span></span> <span data-ttu-id="ff016-121">Tıklatın **bulma** diğer hizmetler için geçerli çözümü aramak için düğmesini.</span><span class="sxs-lookup"><span data-stu-id="ff016-121">Click the **Discover** button to search the current solution for any services.</span></span> <span data-ttu-id="ff016-122">Hizmetler listesinde Service1.xamlx yanındaki üçgen'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ff016-122">Click the triangle next to Service1.xamlx in the Services list.</span></span> <span data-ttu-id="ff016-123">Service1 hizmeti tarafından uygulanan sözleşmeleri listelemek için Service1 yanındaki üçgen'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="ff016-123">Click the triangle next to Service1 to list the contracts implemented by the Service1 service.</span></span> <span data-ttu-id="ff016-124">Genişletme **Service1** düğümünde **Hizmetleri** listesi.</span><span class="sxs-lookup"><span data-stu-id="ff016-124">Expand the **Service1** node in the **Services** list.</span></span> <span data-ttu-id="ff016-125">Echo işlemi görüntülenen **Operations** listesinde aşağıdaki çizimde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ff016-125">The Echo operation is displayed in the **Operations** list as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="ff016-126">![Hizmet Başvurusu Ekle iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "Addservıcereference")</span><span class="sxs-lookup"><span data-stu-id="ff016-126">![Add Service Reference Dialog](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")</span></span>  
  
     <span data-ttu-id="ff016-127">Varsayılan ad alanını tutun ve tıklatın **Tamam** kapatmak için **hizmet Başvurusu Ekle** iletişim.</span><span class="sxs-lookup"><span data-stu-id="ff016-127">Keep the default namespace and click **OK** to dismiss the **Add Service Reference** dialog.</span></span> <span data-ttu-id="ff016-128">Aşağıdaki iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ff016-128">The following dialog is displayed.</span></span>  
  
     <span data-ttu-id="ff016-129">![Ekle hizmet başvurusu bildirim iletişim kutusu](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")</span><span class="sxs-lookup"><span data-stu-id="ff016-129">![The add service reference notification dialog](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")</span></span>  
  
     <span data-ttu-id="ff016-130">Tıklatın **Tamam** iletişim kutusunu kapatmak üzere.</span><span class="sxs-lookup"><span data-stu-id="ff016-130">Click **OK** to dismiss the dialog.</span></span> <span data-ttu-id="ff016-131">Ardından, çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ff016-131">Next, press CTRL+SHIFT+B to build the solution.</span></span> <span data-ttu-id="ff016-132">Araç kutusu yeni bir bölüm eklenmiştir bildiriminde adlı **MyWFClient.ServiceReference1.Activities**.</span><span class="sxs-lookup"><span data-stu-id="ff016-132">Notice in the toolbox a new section has been added called **MyWFClient.ServiceReference1.Activities**.</span></span> <span data-ttu-id="ff016-133">Bu bölümü genişletin ve aşağıdaki çizimde gösterildiği gibi eklenen Yankı etkinlik dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ff016-133">Expand this section and notice the Echo activity that has been added as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="ff016-134">![Araç kutusu etkinliğinde echo](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")</span><span class="sxs-lookup"><span data-stu-id="ff016-134">![Echo activity in toolbox](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")</span></span>  
  
7.  <span data-ttu-id="ff016-135">Sürükleme ve bırakma bir <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` Tasarımcı yüzeyine etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ff016-135">Drag and drop a <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activity onto the designer surface.</span></span> <span data-ttu-id="ff016-136">Altında olan **akış denetimi** araç bölümü.</span><span class="sxs-lookup"><span data-stu-id="ff016-136">It is under the **Control Flow** section of the toolbox.</span></span>  
  
8.  <span data-ttu-id="ff016-137">İle <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` , odakta etkinliği tıklatın **değişkenleri** adlı bir dize değişkeni ekleyin ve bağlama `inString`.</span><span class="sxs-lookup"><span data-stu-id="ff016-137">With the <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activity in focus, click the **Variables** link and add a string variable named `inString`.</span></span> <span data-ttu-id="ff016-138">Varsayılan değer olan değişkeni verin `"Hello, world"` adlı bir dize değişkeni yanı sıra `outString` aşağıdaki çizimde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ff016-138">Give the variable a default value of `"Hello, world"` as well as a string variable named `outString` as shown in the following diagram.</span></span>  
  
     <span data-ttu-id="ff016-139">![Bir değişken ekleme](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")</span><span class="sxs-lookup"><span data-stu-id="ff016-139">![Adding a variable](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")</span></span>  
  
9. <span data-ttu-id="ff016-140">Sürükleme ve bırakma bir **Echo** etkinliğini <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`.</span><span class="sxs-lookup"><span data-stu-id="ff016-140">Drag and drop an **Echo** activity into the <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence`.</span></span> <span data-ttu-id="ff016-141">Özellikler penceresinde bağlamak `inMsg` bağımsız değişkeni `inString` değişken ve `outMsg` bağımsız değişkeni `outString` aşağıdaki çizimde gösterildiği gibi değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ff016-141">In the properties window bind the `inMsg` argument to the `inString` variable and the `outMsg` argument to the `outString` variable as shown in the following illustration.</span></span> <span data-ttu-id="ff016-142">Bu değeri geçirir `inString` değişken işlemi için dönüş değerini alır ve yerleştirir `outString` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="ff016-142">This passes in the value of the `inString` variable to the operation and then takes the return value and places it in the `outString` variable.</span></span>  
  
     <span data-ttu-id="ff016-143">![Bağımsız değişkenler bağlama](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")</span><span class="sxs-lookup"><span data-stu-id="ff016-143">![Binding the arguments to variables](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")</span></span>  
  
10. <span data-ttu-id="ff016-144">Sürükleme ve bırakma bir **WriteLine** etkinlik aşağıdaki **Echo** hizmet çağrı tarafından döndürülen dize görüntülemek için etkinliği.</span><span class="sxs-lookup"><span data-stu-id="ff016-144">Drag and drop a **WriteLine** activity below the **Echo** activity to display the string returned by the service call.</span></span> <span data-ttu-id="ff016-145">**WriteLine** etkinlik bulunduğu **Temelleri** araç düğümünde.</span><span class="sxs-lookup"><span data-stu-id="ff016-145">The **WriteLine** activity is located in the **Primitives** node in the toolbox.</span></span> <span data-ttu-id="ff016-146">Bağlama **metin** bağımsız değişkeni **WriteLine** etkinliğe `outString` yazarak değişken `outString` üzerinde metin kutusuna **WriteLine** etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ff016-146">Bind the **Text** argument of the **WriteLine** activity to the `outString` variable by typing `outString` into the text box on the **WriteLine** activity.</span></span> <span data-ttu-id="ff016-147">İş akışı şimdi aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ff016-147">The workflow should now look like the following illustration.</span></span>  
  
     <span data-ttu-id="ff016-148">![Tam istemci iş akışı](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")</span><span class="sxs-lookup"><span data-stu-id="ff016-148">![The complete client workflow](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")</span></span>  
  
11. <span data-ttu-id="ff016-149">MyWFService çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla...** . Seçin **birden fazla başlangıç projesi** radyo düğmesini seçin ve Seç **Başlat** her proje için **eylem** aşağıdaki çizimde gösterildiği gibi sütun.</span><span class="sxs-lookup"><span data-stu-id="ff016-149">Right-click the MyWFService solution and select **Set Startup Projects ...**. Select the **Multiple startup projects** radio button and select **Start** for each project in the **Action** column as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="ff016-150">![Başlangıç projeleri seçenekleri](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")</span><span class="sxs-lookup"><span data-stu-id="ff016-150">![Startup projects options](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")</span></span>  
  
12. <span data-ttu-id="ff016-151">Hem hizmet hem de istemci başlatmak için Ctrl + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ff016-151">Press Ctrl + F5 to launch both the service and the client.</span></span> <span data-ttu-id="ff016-152">ASP.NET Geliştirme Sunucusu hizmeti barındıran, Internet Explorer WCF Yardım sayfasını görüntüler ve istemci iş akışı uygulama konsol penceresinde başlatılır ve ("Hello, world") hizmetinden döndürülen dize görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ff016-152">The ASP.NET Development Server hosts the service, Internet Explorer displays the WCF help page, and the client workflow application is launched in a console window and displays the string returned from the service ("Hello, world").</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff016-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff016-153">See Also</span></span>  
 [<span data-ttu-id="ff016-154">İş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ff016-154">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="ff016-155">Nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="ff016-155">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="ff016-156">Bir Web projesi bir iş akışında bir WCF hizmetinden kullanma</span><span class="sxs-lookup"><span data-stu-id="ff016-156">Consuming a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)