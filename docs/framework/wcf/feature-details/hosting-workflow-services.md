---
title: "İş Akışı Hizmetlerini Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bf0b63d3de750b5ec2aea41dcb6bb700385663a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-workflow-services"></a><span data-ttu-id="82874-102">İş Akışı Hizmetlerini Barındırma</span><span class="sxs-lookup"><span data-stu-id="82874-102">Hosting Workflow Services</span></span>
<span data-ttu-id="82874-103">Bir iş akışı hizmeti, gelen iletilere yanıt vermesi için barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82874-103">A workflow service must be hosted for it to respond to incoming messages.</span></span> <span data-ttu-id="82874-104">İş akışı hizmetleri kullanım [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı ve bu nedenle Mesajlaşma barındırılan benzer şekilde.</span><span class="sxs-lookup"><span data-stu-id="82874-104">Workflow services use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messaging infrastructure and are therefore hosted in similar ways.</span></span> <span data-ttu-id="82874-105">Gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, iş akışı hizmetleri yönetilen bir uygulamada, Internet Information Services (IIS) altında ya da Windows İşlem Etkinleştirme Hizmetleri (WAS) altında barındırılması.</span><span class="sxs-lookup"><span data-stu-id="82874-105">Like [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, workflow services can be hosted in any managed application, under Internet Information Services (IIS), or under Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="82874-106">Ayrıca iş akışı Hizmetleri Windows Server App Fabric altında barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="82874-106">In addition workflow services can be hosted under Windows Server App Fabric.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="82874-107">Windows Server App Fabric bakın [Windows Server App Fabric belgelerine](http://go.microsoft.com/fwlink/?LinkId=193037), [AppFabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=196494), ve [AppFabric barındırma kavramları](http://go.microsoft.com/fwlink/?LinkId=196495).</span><span class="sxs-lookup"><span data-stu-id="82874-107"> Windows Server App Fabric see [Windows Server App Fabric documentation](http://go.microsoft.com/fwlink/?LinkId=193037), [AppFabric Hosting Features](http://go.microsoft.com/fwlink/?LinkId=196494), and [AppFabric Hosting Concepts](http://go.microsoft.com/fwlink/?LinkId=196495).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="82874-108">ana bilgisayar için çeşitli şekillerde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri bakın [barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="82874-108"> the various ways to host [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="hosting-in-a-managed-application"></a><span data-ttu-id="82874-109">Yönetilen bir uygulamada barındırma</span><span class="sxs-lookup"><span data-stu-id="82874-109">Hosting in a managed application</span></span>  
 <span data-ttu-id="82874-110">Yönetilen bir uygulamada bir iş akışı hizmeti barındırmak için kullandığınız <xref:System.ServiceModel.Activities.WorkflowServiceHost> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="82874-110">To host a workflow service in a managed application, use the <xref:System.ServiceModel.Activities.WorkflowServiceHost> class.</span></span> <span data-ttu-id="82874-111"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Oluşturucusu bir singleton iş akışı hizmet örneği, bir iş akışı hizmeti tanımı veya Mesajlaşma etkinlikleriyle iş akışının kullandığı bir etkinlik belirtmenize olanak verir.</span><span class="sxs-lookup"><span data-stu-id="82874-111">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> constructor allows you to specify a singleton workflow service instance, a workflow service definition, or an activity that uses the workflow messaging activities.</span></span> <span data-ttu-id="82874-112">Çağırma <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> gelen iletiler için dinleme başlatmak hizmetinin neden olur.</span><span class="sxs-lookup"><span data-stu-id="82874-112">Calling <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> causes the service to start listening for incoming messages.</span></span>  
  
## <a name="hosting-under-iis-or-was"></a><span data-ttu-id="82874-113">IIS ya da WAS altında barındırma</span><span class="sxs-lookup"><span data-stu-id="82874-113">Hosting under IIS or WAS</span></span>  
 <span data-ttu-id="82874-114">IIS ya da WAS altında bir iş akışı hizmeti barındıran bir sanal dizin oluşturma ve hizmet ve davranışını tanımlamak sanal dizinde dosyaları yerleştirme içerir.</span><span class="sxs-lookup"><span data-stu-id="82874-114">Hosting a workflow service under IIS or WAS involves creating a virtual directory and placing files in the virtual directory that define the service and its behavior.</span></span> <span data-ttu-id="82874-115">IIS ya da WAS altında bir iş akışı hizmeti var. barındırma birkaç olasılık olduğunda:</span><span class="sxs-lookup"><span data-stu-id="82874-115">When hosting a workflow service under IIS or WAS there are several possibilities:</span></span>  
  
-   <span data-ttu-id="82874-116">İş akışı hizmeti bir IIS tanımlar / hizmet davranışları, uç noktaları ve diğer yapılandırma öğeleri belirten bir Web.config dosyası ile birlikte sanal dizini olan bir .xamlx dosyası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="82874-116">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory along with a Web.config file that specifies the service behaviors, endpoints, and other configuration elements.</span></span>  
  
-   <span data-ttu-id="82874-117">İş akışı hizmeti bir IIS tanımlar / sanal dizini olan bir .xamlx dosyası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="82874-117">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory.</span></span> <span data-ttu-id="82874-118">.Xamlx dosya kullanıma sunmak için uç nokta belirtir.</span><span class="sxs-lookup"><span data-stu-id="82874-118">The .xamlx file specifies the endpoints to expose.</span></span> <span data-ttu-id="82874-119">Uç noktalar olarak belirtilen bir `WorkflowService.Endpoints` aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="82874-119">Endpoints are specified in a `WorkflowService.Endpoints` element as shown in the following example.</span></span>  
  
    ```xml  
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
      <WorkflowService.Endpoints>  
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">  
          <Endpoint.Binding>  
            <BasicHttpBinding />  
          </Endpoint.Binding>  
        </Endpoint>  
      </WorkflowService.Endpoints>  
    <!-- ... -->  
    </WorkflowService>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="82874-120">Davranış ayarları belirtmeniz gerekiyorsa bir Web.config kullanmalısınız davranışları .xamlx dosyasında belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="82874-120">Behaviors cannot be specified in a .xamlx file, so you must use a Web.config if you need to specify behavior settings.</span></span>  
  
-   <span data-ttu-id="82874-121">İş akışı hizmeti bir IIS tanımlar / sanal dizini olan bir .xamlx dosyası yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="82874-121">Place a .xamlx file that defines the workflow service in an IIS/WAS virtual directory.</span></span> <span data-ttu-id="82874-122">Ayrıca, sanal dizinde .svc dosya yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="82874-122">In addition, place a .svc file in the virtual directory.</span></span> <span data-ttu-id="82874-123">.Svc dosyasındaki özel bir Web hizmeti ana bilgisayar üreteci belirtin, özel davranışı uygulamak veya özel bir konumdan yapılandırma yük sağlar.</span><span class="sxs-lookup"><span data-stu-id="82874-123">The .svc file allows you to specify a custom Web service host factory, apply custom behavior, or load configuration from a custom location.</span></span>  
  
-   <span data-ttu-id="82874-124">IIS'de bir derlemeyi yerleştirin / WCF kullanan bir etkinlik içeren sanal dizin etkinlikleri Mesajlaşma.</span><span class="sxs-lookup"><span data-stu-id="82874-124">Place an assembly in the IIS/WAS virtual directory that contains an activity that uses the WCF messaging activities.</span></span>  
  
 <span data-ttu-id="82874-125">Bir iş akışı hizmeti tanımlayan bir .xamlx dosyanın içermesi gereken bir <`Service`> kök türetilmiş herhangi bir türü içeren bir kök öğesi veya <xref:System.Workflow.ComponentModel.Activity>.</span><span class="sxs-lookup"><span data-stu-id="82874-125">A .xamlx file that defines a workflow service must contain a <`Service`> root element or a root element that contains any type derived from <xref:System.Workflow.ComponentModel.Activity>.</span></span> <span data-ttu-id="82874-126">Kullanırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] etkinlik şablonu .xamlx dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82874-126">When using the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Activity template a .xamlx file is created.</span></span> <span data-ttu-id="82874-127">WCF iş akışı hizmeti şablonu kullanarak bir .xamlx dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82874-127">When using the WCF Workflow Service template a .xamlx file is created.</span></span>  
  
## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a><span data-ttu-id="82874-128">Windows Server App Fabric altında iş akışı hizmetlerini barındırma</span><span class="sxs-lookup"><span data-stu-id="82874-128">Hosting Workflow Services under Windows Server App Fabric</span></span>  
 <span data-ttu-id="82874-129">Windows Server App Fabric altında bir iş akışı hizmeti barındırma IIS altında barındırma olarak aynı şekilde yapılır / OLUŞTU.</span><span class="sxs-lookup"><span data-stu-id="82874-129">Hosting a workflow service under Windows Server App Fabric is done in the same way as hosting under IIS/WAS.</span></span> <span data-ttu-id="82874-130">Tek fark, Windows Server App Fabric yüklendiğini gerçeğidir.</span><span class="sxs-lookup"><span data-stu-id="82874-130">The only difference is the fact that Windows Server App Fabric is installed.</span></span> <span data-ttu-id="82874-131">Windows Server App Fabric Internet Information Services Yöneticisi yanı için powershell cmdlet'leri eklenen araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="82874-131">Windows Server App Fabric provides tools that are added to Internet Information Services Manager, as well as powershell commandlets.</span></span> <span data-ttu-id="82874-132">Bu araçlar, dağıtma, yönetme ve iş akışı hizmetleri ve WCF hizmetlerini izleme basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="82874-132">These tools simplify deploying, managing, and tracking of workflow services and WCF services.</span></span> <span data-ttu-id="82874-133">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="82874-133">.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="82874-134">Windows Server App Fabric bakın [Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037)</span><span class="sxs-lookup"><span data-stu-id="82874-134"> Windows Server App Fabric see [Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037)</span></span>  
  
## <a name="referencing-custom-activities"></a><span data-ttu-id="82874-135">Özel etkinlikler başvurma</span><span class="sxs-lookup"><span data-stu-id="82874-135">Referencing Custom Activities</span></span>  
 <span data-ttu-id="82874-136">Özel etkinlikler başvurular eklenmelidir <`Assemblies`> altında bölümünde <`System.Web.Compilation`> uygulama etki alanına yüklenir ve XAML kaldırıcı türleri bulabilir.</span><span class="sxs-lookup"><span data-stu-id="82874-136">References to custom activities must be added to the <`Assemblies`> section under <`System.Web.Compilation`> so that they are loaded into the Application Domain and the XAML deserializer is able to locate the types.</span></span> <span data-ttu-id="82874-137">Makinedeki tüm uygulamalar için ayarlar uygulanması gerekiyorsa bu ayarları, uygulama düzeyinde veya kök Web.config yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="82874-137">These settings can be made at the application level or in the root Web.config if the settings should be applied to all applications on the machine.</span></span>  
  
## <a name="deployment"></a><span data-ttu-id="82874-138">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="82874-138">Deployment</span></span>  
 <span data-ttu-id="82874-139">Web dağıtım aracı, dağıtım işlemini kolaylaştırmak için oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="82874-139">The Web Deployment tool has been created to make the job of deployment easier.</span></span> <span data-ttu-id="82874-140">Aracı, IIS 6.0 ve IIS 7.0 arasında uygulamaları geçirmek, sunucu grupları, eşitleme ve paketleme, arşivleme ve Web uygulamalarını dağıtmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="82874-140">The tool allows you to migrate applications between IIS 6.0 and IIS 7.0, synchronize server farms, and package, archive and deploy Web applications.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="82874-141">[MS dağıtım aracı](http://go.microsoft.com/fwlink/?LinkId=178690)</span><span class="sxs-lookup"><span data-stu-id="82874-141"> [MS Deployment Tool](http://go.microsoft.com/fwlink/?LinkId=178690)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82874-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82874-142">See Also</span></span>  
 [<span data-ttu-id="82874-143">İş akışı hizmeti konağı dahili bileşenleri</span><span class="sxs-lookup"><span data-stu-id="82874-143">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [<span data-ttu-id="82874-144">WorkflowServiceHost yapılandırma</span><span class="sxs-lookup"><span data-stu-id="82874-144">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)