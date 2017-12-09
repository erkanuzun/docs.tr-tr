---
title: "Bağıntı Sorunlarını Giderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea348811a1b2dbd19254f6979a5165c821aa31e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="95863-102">Bağıntı Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="95863-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="95863-103">Bağıntı iş akışı hizmeti iletileri birbirine ve doğru iş akışı örneği ilişkilendirmek için kullanılır, ancak doğru yapılandırılmamışsa, ileti alınmadı ve uygulamaların düzgün çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="95863-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="95863-104">Bu konuda bağıntı sorunlarını gidermek için çeşitli yöntemler genel bir bakış sağlar ve ayrıca bağıntı kullandığınızda oluşabilecek bazı ortak sorunlar listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="95863-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>  
  
## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="95863-105">UnknownMessageReceived olayını işle</span><span class="sxs-lookup"><span data-stu-id="95863-105">Handle the UnknownMessageReceived Event</span></span>  
 <span data-ttu-id="95863-106"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Olayı var olan bir örneğini bağıntılı iletileri dahil olmak üzere bir hizmet tarafından bilinmeyen bir ileti alındığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="95863-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="95863-107">Kendini barındıran hizmetler için bu olay konak uygulamada işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="95863-107">For self-hosted services, this event can be handled in the host application.</span></span>  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 <span data-ttu-id="95863-108">Web barındırılan hizmetler için bu olay bir sınıftan türetilen tarafından işlenip <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> ve geçersiz kılma <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="95863-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>  
  
```csharp  
class CustomFactory : WorkflowServiceHostFactory  
{  
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)  
    {  
        // Create the WorkflowServiceHost.  
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);  
  
        // Handle the UnknownMessageReceived event.  
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
        {  
            Console.WriteLine("Unknown Message Received:");  
            Console.WriteLine(e.Message);  
        };  
  
        return host;  
    }  
}  
```  
  
 <span data-ttu-id="95863-109">Bu özel <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> sonra belirtilebilir `svc` hizmet için dosya.</span><span class="sxs-lookup"><span data-stu-id="95863-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 <span data-ttu-id="95863-110">Bu işleyici çağrıldığında, ileti kullanılarak alınabilir <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> özelliği <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>ve aşağıdaki iletiyi benzeyecektir.</span><span class="sxs-lookup"><span data-stu-id="95863-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>  
  
```Output  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
  </s:Header>  
  <s:Body>  
    <AddItem xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItem>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="95863-111">Gönderilen iletileri incelemek için <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> işleyici neden ileti bir iş akışı hizmeti örneğine ilişkilendirmek değil hakkında ipuçları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="95863-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="95863-112">İş akışı ilerlemesini izlemek için izleme kullanma</span><span class="sxs-lookup"><span data-stu-id="95863-112">Use Tracking to Monitor the Progress of the Workflow</span></span>  
 <span data-ttu-id="95863-113">İzleme, bir iş akışı ilerlemesini izlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="95863-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="95863-114">Varsayılan olarak, iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, arıza yayma ve yer işareti sürdürme izleme kayıtları gösterilen.</span><span class="sxs-lookup"><span data-stu-id="95863-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="95863-115">Ayrıca, özel izleme kayıtları özel etkinlikler tarafından gösterilen.</span><span class="sxs-lookup"><span data-stu-id="95863-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="95863-116">Bağıntı sorunlarını giderirken, etkinlik kayıtları, yer işareti sürdürme kaydeder ve hataya yayma kayıtları izlemeyi en kullanışlı olan.</span><span class="sxs-lookup"><span data-stu-id="95863-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="95863-117">Kayıtları İzleme etkinlik iş akışının geçerli ilerlemesini belirlemek için kullanılabilir ve hangi Mesajlaşma etkinlik iletileri için şu anda bekleyen tanımlamaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="95863-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="95863-118">Yer işareti sürdürme kayıtları, iş akışı tarafından bir ileti alındı ve hataya yayma kayıtları, iş akışındaki tüm hataları kaydını sağlar belirttiğinden faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="95863-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="95863-119">İzlemeyi etkinleştirmek için istenen belirtin <xref:System.Activities.Tracking.TrackingParticipant> içinde <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> , <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="95863-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="95863-120">Aşağıdaki örnekte, `ConsoleTrackingParticipant` (gelen [özel izleme](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) örnek) varsayılan profili izleme kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="95863-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="95863-121">İzleme katılımcı ConsoleTrackingParticipant gibi bir konsol penceresi sahip kendini barındıran iş akışı hizmetleri için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="95863-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="95863-122">Web barındırılan bir hizmet için izleme bilgilerini dayanıklı bir depolama alanına oturum izleme katılımcı, yerleşik gibi kullanılmalıdır <xref:System.Activities.Tracking.EtwTrackingParticipant>, veya bilgileri gibi bir dosyaya kaydeder özel izleme katılımcı `TextWriterTrackingParticpant` gelen[ Bir metin dosyası kullanarak izleme](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="95863-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file, such as the `TextWriterTrackingParticpant` from the [Tracking Using a Text File](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95863-123">İzleme ve bir iş akışı Web barındırılan hizmet için izleme yapılandırma Bkz [izleme ve izleme iş akışı](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [yapılandırma izleme iş akışı için](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)ve [izleme &#91; WF örnekleri &#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) örnekleri.</span><span class="sxs-lookup"><span data-stu-id="95863-123"> tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>  
  
## <a name="use-wcf-tracing"></a><span data-ttu-id="95863-124">WCF izleme kullanın</span><span class="sxs-lookup"><span data-stu-id="95863-124">Use WCF Tracing</span></span>  
 <span data-ttu-id="95863-125">WCF izleme ve bir iş akışı hizmetinden ileti akışı izlemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95863-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="95863-126">Bu izleme bilgilerini bağıntı sorunlarını, özellikle içerik tabanlı bağıntı sorunlarını giderirken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="95863-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="95863-127">İzlemeyi etkinleştirmek için istenen izleme dinleyicilerini belirtin `system.diagnostics` bölümünü `web.config` Web barındırılan iş akışı hizmeti ise, dosya veya `app.config` iş akışı hizmeti kendini barındıran ise dosya.</span><span class="sxs-lookup"><span data-stu-id="95863-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="95863-128">İzleme dosyasında iletilerinin içeriğini dahil edileceğini belirtin `true` için `logEntireMessage` içinde `messageLogging` öğesinde `diagnostics` bölümünü `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="95863-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="95863-129">Aşağıdaki örnekte, mesajlarının içeriğini izleme bilgilerini adlı bir dosyaya yazılması için yapılandırılmış `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="95863-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
    </sources>  
  
    <sharedListeners>  
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging logEntireMessage="true" logMalformedMessages="false"  
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">  
      </messageLogging>  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="95863-130">Bulunan izleme bilgilerini görüntülemek için `service.svclog`, [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95863-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="95863-131">İleti içeriğini görüntülemek ve tam olarak ne geçirilen ve eşleşen olup olmadığını görmek için içerik tabanlı bağıntı sorunlarını giderme gönderdiğinde, bu özellikle yararlı olur <xref:System.ServiceModel.CorrelationQuery> içerik tabanlı bağıntı için.</span><span class="sxs-lookup"><span data-stu-id="95863-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95863-132">WCF bkz: izleme, [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), ve [uygulamanız sorun giderme kullanarak izlemeyi](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="95863-132"> WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="95863-133">Ortak bağlam Exchange bağıntı sorunları</span><span class="sxs-lookup"><span data-stu-id="95863-133">Common Context Exchange Correlation Issues</span></span>  
 <span data-ttu-id="95863-134">Belirli türde bir bağıntı düzgün çalışması için belirli bir bağlama türü için bağıntı kullanılır gerektirir.</span><span class="sxs-lookup"><span data-stu-id="95863-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="95863-135">Örnekler arasında iki yönlü bağlama gibi gerektirir istek-yanıt bağıntısı <xref:System.ServiceModel.BasicHttpBinding>ve bir bağlam tabanlı gibi bağlama gerektirir bağlam değişimi bağıntısı <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="95863-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="95863-136">Bu istek-yanıt bağıntısı için yaygın bir sorun değildir ancak dahil olmak üzere içerik tabanlı bağlamalar sayıda vardır çoğu bağlamalar iki yönlü işlemlerini destekleyen <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, ve <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="95863-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="95863-137">Bu bağlamaların bir tanesini kullanılmaz bir iş akışı hizmeti ilk çağrı başarılı olur, ancak sonraki çağrılar başarısız olur şununla <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="95863-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 <span data-ttu-id="95863-138">Bağlam bağıntı için kullanılan bağlam bilgilerini tarafından döndürülen <xref:System.ServiceModel.Activities.SendReply> için <xref:System.ServiceModel.Activities.Receive> iki yönlü bir işlem veya kullanma işlemi ise, çağıran tarafından belirtilebilir yükleyen bağlam bağıntı başlatır etkinliği tek yönlü.</span><span class="sxs-lookup"><span data-stu-id="95863-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="95863-139">Bağlam çağıran tarafından gönderilen değil veya iş akışı hizmeti sonra aynı tarafından döndürülen <xref:System.ServiceModel.FaultException> açıklanan daha önce bir sonraki işlemi çalıştırıldığında döndürülür.</span><span class="sxs-lookup"><span data-stu-id="95863-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="95863-140">[Bağlam değişimi](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="95863-140"> [Context Exchange](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span></span>  
  
## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="95863-141">İstek-yanıt bağıntısı ile ilgili genel sorunları</span><span class="sxs-lookup"><span data-stu-id="95863-141">Common Request-Reply Correlation Issues</span></span>  
 <span data-ttu-id="95863-142">İstek-yanıt bağıntısı ile kullanılan bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti ile bir iş akışı hizmeti de iki yönlü bir işlem uygulamak için bir <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> iki yönlü bir işlem başka bir Web çağırır çifti hizmet.</span><span class="sxs-lookup"><span data-stu-id="95863-142">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="95863-143">Bir WCF hizmetindeki iki yönlü bir işlem çağrılırken, hizmet ya da bir geleneksel kesinliği kod tabanlı olabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti veya bir iş akışı hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="95863-143">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="95863-144">İstek-yanıt bağıntısı iki yönlü bir bağlama kullanılmalıdır, gibi kullanmak için <xref:System.ServiceModel.BasicHttpBinding>, ve işlemler iki yönlü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95863-144">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>  
  
 <span data-ttu-id="95863-145">İş akışı hizmeti paralel veya örtüşen iki yönlü işlemlerinde varsa <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çiftleri sonra örtük bağıntı işlemek tarafındansağlananYönetim<xref:System.ServiceModel.Activities.WorkflowServiceHost>özellikle yüksek stres senaryolarda yeterli olmayabilir ve iletileri doğru biçimde yönlendirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="95863-145">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="95863-146">Bu sorunun oluşmasını önlemek için her zaman açıkça belirttiğiniz öneririz bir <xref:System.ServiceModel.Activities.CorrelationHandle> istek-yanıt bağıntısı kullanırken.</span><span class="sxs-lookup"><span data-stu-id="95863-146">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="95863-147">Kullanırken **SendAndReceiveReply** ve **ReceiveAndSendReply** ileti bölümünden şablonları **araç** iş akışı Tasarımcısı'nda bir <xref:System.ServiceModel.Activities.CorrelationHandle> açıkça varsayılan olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="95863-147">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="95863-148">Bir iş akışı kodu kullanarak oluştururken <xref:System.ServiceModel.Activities.CorrelationHandle> belirtilen <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> çiftindeki ilk etkinliğin.</span><span class="sxs-lookup"><span data-stu-id="95863-148">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="95863-149">Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.Receive> etkinliği açık bir yapılandırılmış <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> belirtilen <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="95863-149">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = ... // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="95863-150">Kalıcılık arasında izin verilmez bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> çifti veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çifti.</span><span class="sxs-lookup"><span data-stu-id="95863-150">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="95863-151">No-persist bölge hem etkinlikleri tamamlanana kadar sürer oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95863-151">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="95863-152">Bir gecikme etkinliği gibi bir etkinlik bu no-persist bölgesinde bulunan ve boşta durumuna iş akışı neden olursa, konak olduklarında iş akışları kalıcı olacak şekilde yapılandırılmış boş olsa bile iş akışı kalıcı olmaz.</span><span class="sxs-lookup"><span data-stu-id="95863-152">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="95863-153">Kalan etkinliği gibi bir etkinlik açıkça Hayır kalan bölgesinde kalıcı hale getirmek çalışırsa, bir önemli özel durum, iş akışı durdurulduğunda oluşur ve bir <xref:System.ServiceModel.FaultException> çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="95863-153">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="95863-154">Önemli özel durum iletisi "System.InvalidOperationException: kalıcı etkinlikleri hiçbir Kalıcılık bloğu içinde bulunan yapılamıyor.".</span><span class="sxs-lookup"><span data-stu-id="95863-154">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="95863-155">Bu özel durumun çağırana döndürülmez ancak izleme etkin olup olmadığını gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="95863-155">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="95863-156">İleti için <xref:System.ServiceModel.FaultException> yapana "işlemi gerçekleştirilemedi iş akışı örneği '5836145b-7da2 - 49 d 0-a052-a49162adeab6' tamamlandığından" değil.</span><span class="sxs-lookup"><span data-stu-id="95863-156">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95863-157">İstek-yanıt bağıntısı bkz [istek-yanıt](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="95863-157"> request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>  
  
## <a name="common-content-correlation-issues"></a><span data-ttu-id="95863-158">İçerik bağıntı ile ilgili genel sorunları</span><span class="sxs-lookup"><span data-stu-id="95863-158">Common Content Correlation Issues</span></span>  
 <span data-ttu-id="95863-159">İçeriğe dayalı bağıntı birden fazla ileti bir iş akışı hizmeti alır ve bir veri alışverişi iletilerindeki parçasını istenen örneğini tanımlar olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95863-159">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="95863-160">İçeriğe dayalı bağıntı iletide, müşteri numarası veya sipariş kimliği iletileri yönlendirmek için doğru iş akışı örneği gibi bu verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="95863-160">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="95863-161">Bu bölümde içerik tabanlı bağıntı kullanırken oluşabilecek çeşitli ortak sorunlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95863-161">This section describes several common issues that may occur when using content-based correlation.</span></span>  
  
### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="95863-162">Benzersiz tanımlayıcı veri sağlayın</span><span class="sxs-lookup"><span data-stu-id="95863-162">Ensure the Identifying Data Is Unique</span></span>  
 <span data-ttu-id="95863-163">Örneği tanımlamak için kullanılan veri bir bağıntı anahtara karma haline getirilir.</span><span class="sxs-lookup"><span data-stu-id="95863-163">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="95863-164">Bağıntı için kullanılan veri benzersizdir Aksi takdirde karma anahtarında çakışması ortaya ve iletileri misrouted neden güvence altına almak için dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="95863-164">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="95863-165">Örneğin, aynı ada sahip birden çok müşteri olabileceğinden yalnızca müşteri adına göre bir bağıntı bir çakışma neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="95863-165">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="95863-166">İki nokta (:) ileti sorgunun anahtar ve değer daha sonra karma dizesi oluşturmak için sınırlandırmak için zaten kullanılmakta olduğundan ileti ilişkilendirmek için kullanılan veri bir parçası olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="95863-166">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="95863-167">Kalıcılık kullanılıyorsa, geçerli tanımlayıcı verileri önceden Sürdürülen bir örneği tarafından kullanılmamış emin olun.</span><span class="sxs-lookup"><span data-stu-id="95863-167">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="95863-168">Geçici olarak Kalıcılık devre dışı bırakma, bu sorunu tanımlamaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="95863-168">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="95863-169">WCF izleme hesaplanan bağıntı anahtarını görüntülemek için kullanılabilir ve bu tür bir sorunu hata ayıklama için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="95863-169">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>  
  
### <a name="race-conditions"></a><span data-ttu-id="95863-170">Yarış durumları</span><span class="sxs-lookup"><span data-stu-id="95863-170">Race Conditions</span></span>  
 <span data-ttu-id="95863-171">Bir ileti ve gerçekte başlatılmakta bağıntı alma hizmeti arasındaki süre izleme iletileri yoksayılacak küçük boşluk yoktur.</span><span class="sxs-lookup"><span data-stu-id="95863-171">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="95863-172">Tek yönlü bir işlem istemciden geçirilen verileri kullanarak bir iş akışı hizmeti içerik tabanlı bağıntı başlatır ve arayan hemen izleme iletileri gönderir, bu zaman aralığı boyunca bu iletiler yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="95863-172">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="95863-173">Bu bağıntı başlatmak için iki yönlü bir işlemi kullanarak veya kullanılarak önlenebilir bir <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="95863-173">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>  
  
### <a name="correlation-query-issues"></a><span data-ttu-id="95863-174">Bağıntı sorgu sorunları</span><span class="sxs-lookup"><span data-stu-id="95863-174">Correlation Query Issues</span></span>  
 <span data-ttu-id="95863-175">Bağıntı sorgular, hangi verilerin iletide ileti ilişkilendirmek için kullanıldığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95863-175">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="95863-176">Bu veriler, bir XPath sorgusu kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="95863-176">This data is specified by using an XPath query.</span></span> <span data-ttu-id="95863-177">Her şeyin doğru görünüyor olsa bile bir hizmete ileti gönderilir değil, bir XPath sorgusu yerine ileti veri değeri ile eşleşen bir hazır değer belirtmek için sorun giderme için bir strateji olur.</span><span class="sxs-lookup"><span data-stu-id="95863-177">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="95863-178">Değişmez değer belirtmek için kullanın `string` işlevi.</span><span class="sxs-lookup"><span data-stu-id="95863-178">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="95863-179">Aşağıdaki örnekte, bir <xref:System.ServiceModel.MessageQuerySet> değişmez değeri kullanmak üzere yapılandırılmış `11445` için `OrderId` ve XPath sorgusu dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="95863-179">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>  
  
```csharp  
MessageQuerySet = new MessageQuerySet  
{  
    {  
        "OrderId",   
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")  
        new XPathMessageQuery("string('11445')")  
    }  
}  
```  
  
 <span data-ttu-id="95863-180">Bir XPath sorgusu bağıntı veri alınır, hatalı yapılandırıldıysa şu iletisiyle bir hata döndürdü: "bağıntı sorgu boş bir sonuç kümesi veriyor.</span><span class="sxs-lookup"><span data-stu-id="95863-180">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="95863-181">Lütfen bağıntı sorguları uç noktası için doğru şekilde yapılandırıldığından emin olun."</span><span class="sxs-lookup"><span data-stu-id="95863-181">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="95863-182">Bu sorunu gidermek için hızlı bir şekilde değişmez değerle açıklandığı önceki bölümdeki XPath sorgusu değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="95863-182">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="95863-183">XPath Sorgu Oluşturucu'da kullanıyorsanız, bu sorun ortaya çıkabilir **eklemek bağıntı başlatıcıları** veya **CorrelatesOn tanımı** iletişim kutuları ve iş akışı hizmeti ileti sözleşmeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="95863-183">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="95863-184">Aşağıdaki örnekte, bir ileti sözleşme sınıfı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="95863-184">In the following example, a message contract class is defined.</span></span>  
  
```csharp  
[MessageContract]  
public class AddItemMessage  
{  
    [MessageHeader]  
    public string CartId;  
  
    [MessageBodyMember]  
    public string Item;  
}  
```  
  
 <span data-ttu-id="95863-185">Bu ileti sözleşmesi tarafından kullanılan bir <xref:System.ServiceModel.Activities.Receive> bir iş akışı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="95863-185">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="95863-186">`CartId` İleti üstbilgisinde doğru örneği iletiye ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95863-186">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="95863-187">XPath sorgusu, alır, `CartId` sorgu oluşturulur aşağıdaki hatalı XPath iş akışı Tasarımcısı'nda bağıntı iletişim kutuları kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95863-187">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 <span data-ttu-id="95863-188">Bu XPath sorgusu doğru olması durumunda <xref:System.ServiceModel.Activities.Receive> etkinlik kullanılan parametreleri için veri, ancak ileti sözleşmesi kullanıldığından geçersiz.</span><span class="sxs-lookup"><span data-stu-id="95863-188">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="95863-189">Aşağıdaki XPath sorgusu almak için doğru XPath sorgusu değil `CartId` başlığından.</span><span class="sxs-lookup"><span data-stu-id="95863-189">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>  
  
```  
sm:header()/tempuri:CartId  
```  
  
 <span data-ttu-id="95863-190">Bu, ileti gövdesi inceleyerek onaylanabilir.</span><span class="sxs-lookup"><span data-stu-id="95863-190">This can be confirmed by examining the body of the message.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>  
  </s:Header>  
  <s:Body>  
    <AddItemMessage xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItemMessage>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="95863-191">Aşağıdaki örnekte gösterildiği bir <xref:System.ServiceModel.Activities.Receive> etkinlik için yapılandırılmış bir `AddItem` önceki ileti sözleşmesi veri almak için kullandığı işlemi.</span><span class="sxs-lookup"><span data-stu-id="95863-191">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="95863-192">XPath sorgusu doğru yapılandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="95863-192">The XPath query is correctly configured.</span></span>  
  
```xaml  
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">  
  <Receive.CorrelatesOn>  
    <XPathMessageQuery x:Key="key1">  
      <XPathMessageQuery.Namespaces>  
        <ssx:XPathMessageContextMarkup>  
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>  
        </ssx:XPathMessageContextMarkup>  
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>  
  </Receive.CorrelatesOn>  
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">  
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>  
  </ReceiveMessageContent>  
</Receive>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="95863-193">içeriğe dayalı bağıntı bkz [içerik tabanlı](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) ve [bağıntılı hesaplayıcı](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="95863-193"> content-based correlation, see [Content Based](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) and the [Correlated Calculator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) sample.</span></span>