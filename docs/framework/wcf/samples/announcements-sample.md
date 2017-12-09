---
title: "Duyuru Örnekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 045807df433d519b00969812afb0ae2feac94b75
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="announcements-sample"></a><span data-ttu-id="9904d-102">Duyuru Örnekleri</span><span class="sxs-lookup"><span data-stu-id="9904d-102">Announcements Sample</span></span>
<span data-ttu-id="9904d-103">Bu örnek duyuru işlevselliğinin bulma özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9904d-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="9904d-104">Duyurular, hizmet hakkındaki meta verileri içeren duyuru iletilerini göndermek hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9904d-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="9904d-105">Varsayılan olarak, hizmet başlatıldığında ve hizmet kapatıldığında bye duyuru gönderilen hello duyuru gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9904d-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="9904d-106">Noktadan noktaya gönderilen veya bu Duyurular çok noktaya yayın olabilir.</span><span class="sxs-lookup"><span data-stu-id="9904d-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="9904d-107">Bu örnek iki proje hizmet ve istemci oluşur.</span><span class="sxs-lookup"><span data-stu-id="9904d-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="9904d-108">Hizmet</span><span class="sxs-lookup"><span data-stu-id="9904d-108">Service</span></span>  
 <span data-ttu-id="9904d-109">Bu proje bir kendi kendini barındıran hesaplayıcı hizmeti içerir.</span><span class="sxs-lookup"><span data-stu-id="9904d-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="9904d-110">İçinde `Main` yöntemi, bir hizmet ana bilgisayarı oluşturulur ve hizmet uç noktası için eklenir.</span><span class="sxs-lookup"><span data-stu-id="9904d-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="9904d-111">Ardından, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9904d-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="9904d-112">Duyurular etkinleştirmek için bir duyuru uç noktası eklenmelidir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="9904d-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="9904d-113">Bu durumda çok noktaya yayın UDP kullanan standart bir uç nokta duyuru uç noktası olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="9904d-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="9904d-114">Bu, iyi bilinen bir UDP adresi duyuruları yayınlar.</span><span class="sxs-lookup"><span data-stu-id="9904d-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="9904d-115">İstemci</span><span class="sxs-lookup"><span data-stu-id="9904d-115">Client</span></span>  
 <span data-ttu-id="9904d-116">Bu projede unutmayın istemci konakları bir <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="9904d-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="9904d-117">Ayrıca, iki temsilciler olayı kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="9904d-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="9904d-118">Bu olaylar, çevrimiçi ve çevrimdışı duyuruları alındığında istemcinin ne yaptığını dikte.</span><span class="sxs-lookup"><span data-stu-id="9904d-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="9904d-119">`OnOnlineEvent` Ve `OnOfflineEvent` yöntemlerini işlemek hello ve bye duyuru iletileri sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="9904d-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9904d-120">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9904d-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="9904d-121">Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="9904d-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="9904d-122">Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9904d-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="9904d-123">Komut olduğu gibi çalışmazsa, etki alanı ve kullanıcı adı şu bağımsız değişkenleri yerine isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9904d-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="9904d-124">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9904d-124">Build the solution.</span></span>  
  
3.  <span data-ttu-id="9904d-125">Client.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9904d-125">Run the client.exe application.</span></span>  
  
4.  <span data-ttu-id="9904d-126">Service.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9904d-126">Run the service.exe application.</span></span> <span data-ttu-id="9904d-127">İstemci çevrimiçi duyuru alır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9904d-127">Note the client receives an online announcement.</span></span>  
  
5.  <span data-ttu-id="9904d-128">Service.exe uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="9904d-128">Close the service.exe application.</span></span> <span data-ttu-id="9904d-129">Not istemci çevrimdışı duyuru alır.</span><span class="sxs-lookup"><span data-stu-id="9904d-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9904d-130">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9904d-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9904d-131">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9904d-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9904d-132">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9904d-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9904d-133">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9904d-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a><span data-ttu-id="9904d-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9904d-134">See Also</span></span>