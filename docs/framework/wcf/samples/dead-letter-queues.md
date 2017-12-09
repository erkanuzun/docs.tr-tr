---
title: "Teslim Edilemeyen İletiler Sırası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e2cd61bf9c1e3d7165b76f55f1808b04c979d4d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="dead-letter-queues"></a><span data-ttu-id="f0240-102">Teslim Edilemeyen İletiler Sırası</span><span class="sxs-lookup"><span data-stu-id="f0240-102">Dead Letter Queues</span></span>
<span data-ttu-id="f0240-103">Bu örnek, işler ve işlem teslim başarısız olmuş iletileri gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0240-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="f0240-104">Bağlı olduğu [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="f0240-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="f0240-105">Bu örnekte `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="f0240-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="f0240-106">Hizmeti, sıraya alınan iletileri alma hizmeti izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f0240-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0240-107">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f0240-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0240-108">Bu örnek yalnızca kullanılabilir olan her uygulama sahipsiz sıra gösteren [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0240-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="f0240-109">Örnek üzerinde MSMQ 3.0 için varsayılan sistem genelinde kuyruklarını kullanma değiştirilebilir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0240-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>  
  
 <span data-ttu-id="f0240-110">Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="f0240-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f0240-111">Daha hassas bir şekilde istemci kuyruğa ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="f0240-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f0240-112">Hizmet kuyruktan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="f0240-112">The service receives messages from the queue.</span></span> <span data-ttu-id="f0240-113">Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f0240-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="f0240-114">Kuyruğa alınan iletişim dormancy belirli bir miktar içerebildiğinden, yaşam süresi değeri zamanından daha sonra geçti, ileti uygulamaya teslim değil emin olmak için iletideki ilişkilendirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0240-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="f0240-115">Burada bir uygulama bir ileti teslim başarısız olup olmadığını haberdar olmak gerekir durumlarda da vardır.</span><span class="sxs-lookup"><span data-stu-id="f0240-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="f0240-116">Bu durumların tümünde gibi zaman yaşam ileti üzerinde süresi dolmuş veya ileti teslim başarısız olduğunda, ileti sahipsiz sıraya konur.</span><span class="sxs-lookup"><span data-stu-id="f0240-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="f0240-117">Gönderen uygulama teslim edilemeyen kuyruğundaki iletileri okumak ve herhangi bir eylemi başarısız Teslimat nedenleri düzeltme ve iletiyi yeniden göndermeyi aralığı düzeltme girişimlerinde bulunun.</span><span class="sxs-lookup"><span data-stu-id="f0240-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>  
  
 <span data-ttu-id="f0240-118">Sahipsiz sıra `NetMsmqBinding` bağlama aşağıdaki özelliklerinde ifade:</span><span class="sxs-lookup"><span data-stu-id="f0240-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>  
  
-   <span data-ttu-id="f0240-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>İstemci tarafından gerekli sahipsiz sırayı tür express özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0240-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="f0240-120">Bu numaralandırma aşağıdaki değerlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f0240-120">This enumeration has the following values:</span></span>  
  
-   <span data-ttu-id="f0240-121">`None`: Hiçbir eski ileti sırası istemci tarafından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f0240-121">`None`: No dead-letter queue is required by the client.</span></span>  
  
-   <span data-ttu-id="f0240-122">`System`: Sistem sahipsiz sırayı ölü iletileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0240-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="f0240-123">Sistem sahipsiz sırayı bilgisayar üzerinde çalışan tüm uygulamalar tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="f0240-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>  
  
-   <span data-ttu-id="f0240-124">`Custom`Kullanarak belirtilen özel sahipsiz sırayı <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> özelliği ölü iletileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0240-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="f0240-125">Bu özellik yalnızca üzerinde kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0240-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="f0240-126">Bu uygulama aynı bilgisayarda çalışan diğer uygulamalarla paylaşma yerine kendi sahipsiz sıra kullanmalıdır olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0240-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>  
  
-   <span data-ttu-id="f0240-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>belirli sıranın atılacak kullanmak için express özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0240-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="f0240-128">Bu yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0240-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="f0240-129">Bu örnekte, istemci hizmetinden bir işlem kapsamı içinde toplu iletiler gönderir ve "zaman yaşam" Bu iletiler (yaklaşık 2 saniye) için rasgele düşük bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0240-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="f0240-130">İstemci ayrıca sıraya alma süresi dolan iletileri kullanmak için özel bir sahipsiz sırayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0240-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>  
  
 <span data-ttu-id="f0240-131">İstemci uygulaması, sahipsiz sırayı ve ileti göndermek ya da yeniden deneme iletiler okuma ya da teslim edilemeyen sırasına ve ileti göndermek özgün ileti nedeniyle hatayı düzeltin.</span><span class="sxs-lookup"><span data-stu-id="f0240-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="f0240-132">Örnekte, istemci bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f0240-132">In the sample, the client displays an error message.</span></span>  
  
 <span data-ttu-id="f0240-133">Hizmet sözleşme `IOrderProcessor`, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="f0240-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 <span data-ttu-id="f0240-134">Örnek hizmet kodunda budur [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="f0240-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="f0240-135">Hizmet ile iletişim bir işlem kapsamı içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="f0240-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="f0240-136">Hizmet kuyruktan iletileri okur, işlemi gerçekleştirir ve işlemin sonuçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f0240-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="f0240-137">Uygulama atılacak teslim edilemeyen iletiler için de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0240-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>  
  
```  
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration  
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];  
  
        // Create the transacted MSMQ queue for storing dead message if necessary.  
        if (!MessageQueue.Exists(deadLetterQueueName))  
            MessageQueue.Create(deadLetterQueueName, true);  
  
        // Create a proxy with given client endpoint configuration  
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
        // Create the purchase order  
        PurchaseOrder po = new PurchaseOrder();  
        po.CustomerId = "somecustomer.com";  
        po.PONumber = Guid.NewGuid().ToString();  
  
        PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
        lineItem1.ProductId = "Blue Widget";  
        lineItem1.Quantity = 54;  
        lineItem1.UnitCost = 29.99F;  
  
        PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
        lineItem2.ProductId = "Red Widget";  
        lineItem2.Quantity = 890;  
        lineItem2.UnitCost = 45.89F;  
  
        po.orderLineItems = new PurchaseOrderLineItem[2];  
        po.orderLineItems[0] = lineItem1;  
        po.orderLineItems[1] = lineItem2;  
  
        //Create a transaction scope.  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Make a queued call to submit the purchase order  
            client.SubmitPurchaseOrder(po);  
            // Complete the transaction.  
            scope.Complete();  
        }  
  
        client.Close();  
  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="f0240-138">İstemcinin yapılandırma iletisinin hizmete erişmek kısa bir süre belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0240-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="f0240-139">Belirtilen süre içinde ileti iletilemedi, ileti süresi dolar ve sahipsiz sıraya taşınır.</span><span class="sxs-lookup"><span data-stu-id="f0240-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0240-140">İstemcinin belirtilen süre içinde hizmet kuyruğuna ileti teslim mümkündür.</span><span class="sxs-lookup"><span data-stu-id="f0240-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="f0240-141">Eylem sahipsiz hizmetinde gördüğünüz emin olmak için İstemci Hizmeti başlatmadan önce çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0240-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="f0240-142">İletiyi zaman aşımına uğradı ve teslim edilemeyen hizmete teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="f0240-142">The message times out and is delivered to the dead-letter service.</span></span>  
  
 <span data-ttu-id="f0240-143">Uygulamanın kendi eski ileti sırası olarak kullanmak için hangi kuyruğa tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0240-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="f0240-144">Sıra belirtilmezse, varsayılan sistem genelinde işleme uygun eski ileti sırası eski iletilerin sıraya almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0240-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="f0240-145">Bu örnekte, istemci uygulaması, kendi uygulama sahipsiz sırayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0240-145">In this example, the client application specifies its own application dead-letter queue.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->  
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>  
  </appSettings>  
  
  <system.serviceModel>  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                binding="netMsmqBinding"   
                bindingConfiguration="PerAppDLQBinding"   
                contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PerAppDLQBinding"  
                 deadLetterQueue="Custom"  
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"   
                 timeToLive="00:00:02"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="f0240-146">Teslim edilemeyen ileti hizmeti iletileri teslim edilemeyen kuyruktaki iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="f0240-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="f0240-147">Teslim edilemeyen ileti hizmeti uygulayan `IOrderProcessor` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="f0240-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="f0240-148">Kendi uygulama ancak değil işlem siparişler.</span><span class="sxs-lookup"><span data-stu-id="f0240-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="f0240-149">Teslim edilemeyen ileti hizmeti istemci hizmeti ve siparişleri işlemek için olanaklara sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f0240-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0240-150">Sahipsiz sıra bir istemci sıra ve istemci sıra yerel olan.</span><span class="sxs-lookup"><span data-stu-id="f0240-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>  
  
 <span data-ttu-id="f0240-151">Teslim edilemeyen iletisi hizmet uygulaması bir ileti teslim ve gerçekleştirilen işlemlerin düzeltici önlemleri başarısız nedeni denetler.</span><span class="sxs-lookup"><span data-stu-id="f0240-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="f0240-152">Bir ileti başarısızlık nedeni iki numaralandırmalara yakalanan <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="f0240-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="f0240-153">Alabilirsiniz <xref:System.ServiceModel.Channels.MsmqMessageProperty> gelen <xref:System.ServiceModel.OperationContext> aşağıdaki örnek kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="f0240-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>  
  
```  
public void SubmitPurchaseOrder(PurchaseOrder po)  
{  
    Console.WriteLine("Submitting purchase order did not succed ", po);  
    MsmqMessageProperty mqProp =   
                  OperationContext.Current.IncomingMessageProperties[  
                  MsmqMessageProperty.Name] as MsmqMessageProperty;  
    Console.WriteLine("Message Delivery Status: {0} ",   
                                                mqProp.DeliveryStatus);  
    Console.WriteLine("Message Delivery Failure: {0}",   
                                               mqProp.DeliveryFailure);  
    Console.WriteLine();  
    ….  
}  
```  
  
 <span data-ttu-id="f0240-154">İletileri teslim edilemeyen sırasındaki ileti işlenirken hizmetine gönderilen iletiler ' dir.</span><span class="sxs-lookup"><span data-stu-id="f0240-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="f0240-155">Bu nedenle, ne zaman teslim edilemeyen ileti hizmeti okur iletileri sıradan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanal katmanını uyuşmazlığı uç noktalarını bulur ve ileti göndermez.</span><span class="sxs-lookup"><span data-stu-id="f0240-155">Therefore, when the dead-letter message service reads messages from the queue, the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="f0240-156">Bu durumda, ileti hizmeti işlem sırasını ele ancak teslim edilemeyen ileti hizmeti tarafından alınan.</span><span class="sxs-lookup"><span data-stu-id="f0240-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="f0240-157">Farklı bir uç noktası için gönderilen bir ileti almak için bir adres filtresinin eşleşen herhangi bir adres için belirtilen `ServiceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="f0240-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="f0240-158">Bu, başarılı bir şekilde teslim edilemeyen kuyruktan okunmak iletileri işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f0240-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>  
  
 <span data-ttu-id="f0240-159">Başarısızlık nedeni ise, bu örnekte, teslim edilemeyen ileti hizmeti ileti iletinin zaman aşımına uğradı düzenini yeniden gönderir. Diğer nedenlerle, aşağıdaki örnek kodda gösterildiği gibi teslim hatası gösterir:</span><span class="sxs-lookup"><span data-stu-id="f0240-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]  
public class PurchaseOrderDLQService : IOrderProcessor  
{  
    OrderProcessorClient orderProcessorService;  
    public PurchaseOrderDLQService()  
    {  
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Console.WriteLine("Submitting purchase order did not succeed ", po);  
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;  
  
        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);  
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);  
        Console.WriteLine();  
  
        // resend the message if timed out  
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||  
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)  
        {  
            // re-send  
            Console.WriteLine("Purchase order Time To Live expired");  
            Console.WriteLine("Trying to resend the message");  
  
            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue  
            orderProcessorService.SubmitPurchaseOrder(po);  
            Console.WriteLine("Purchase order resent");  
        }  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the PurchaseOrderDLQService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))  
        {  
            // Open the ServiceHostBase to create listeners and start listening for messages.  
            serviceHost.Open();  
  
            // The service can now be accessed.  
            Console.WriteLine("The dead letter service is ready.");  
            Console.WriteLine("Press <ENTER> to terminate service.");  
            Console.WriteLine();  
            Console.ReadLine();  
        }  
    }  
}   
```  
  
 <span data-ttu-id="f0240-160">Aşağıdaki örnek, bir teslim edilemeyen ileti için yapılandırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="f0240-160">The following sample shows the configuration for a dead-letter message:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">  
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="DefaultBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"   
                 binding="netMsmqBinding"   
                 bindingConfiguration="SystemDLQBinding"   
                 contract="IOrderProcessor" />  
    </client>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="DefaultBinding" />  
        <binding name="SystemDLQBinding"  
                 deadLetterQueue="System"/>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f0240-161">Örnek çalışır durumda sahipsiz sırayı her uygulama için nasıl çalıştığını görmek için 3 yürütülebilir dosyaların vardır; İstemci, hizmet ve her uygulama için teslim edilemeyen kuyruktaki iletileri okur ve hizmet iletiye yeniden gönderir sahipsiz hizmet.</span><span class="sxs-lookup"><span data-stu-id="f0240-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="f0240-162">Tüm konsol uygulamaları konsol pencerelerinin çıktısında ile görüşün.</span><span class="sxs-lookup"><span data-stu-id="f0240-162">All are console applications with output in console windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0240-163">Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f0240-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f0240-164">İstemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala kendi iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="f0240-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="f0240-165">Hizmeti başlatmak ve böylece sıranın oluşturulabilir kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="f0240-165">You should start the service and shut it down so that the queue can be created.</span></span>  
  
 <span data-ttu-id="f0240-166">İstemci çalıştırırken, istemci iletisini görüntüler:</span><span class="sxs-lookup"><span data-stu-id="f0240-166">When running the client, the client displays the message:</span></span>  
  
```  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f0240-167">İstemci ileti göndermeye çalıştı, ancak kısa bir zaman aşımı iletisi süresi ve her uygulama için teslim edilemeyen sırasındaki şimdi sıraya.</span><span class="sxs-lookup"><span data-stu-id="f0240-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>  
  
 <span data-ttu-id="f0240-168">Ardından, iletiyi okur ve hata kodunu görüntüler ve iletiye hizmeti yeniden gönderir sahipsiz hizmeti de çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f0240-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>  
  
```  
The dead letter service is ready.  
Press <ENTER> to terminate service.  
  
Submitting purchase order did not succeed  
Message Delivery Status: InDoubt  
Message Delivery Failure: ReachQueueTimeout  
  
Purchase order Time To Live expired  
Trying to resend the message  
Purchase order resent  
```  
  
 <span data-ttu-id="f0240-169">Hizmet başlatır ve ardından yakın iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="f0240-169">The service starts and then reads the resent message and processes it.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f0240-170">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f0240-170">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f0240-171">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0240-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f0240-172">Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="f0240-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f0240-173">Hizmet sırası mevcut değilse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0240-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f0240-174">İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0240-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f0240-175">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="f0240-175">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="f0240-176">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f0240-176">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="f0240-177">Genişletme **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f0240-177">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="f0240-178">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="f0240-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="f0240-179">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="f0240-179">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="f0240-180">Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.</span><span class="sxs-lookup"><span data-stu-id="f0240-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="f0240-181">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0240-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f0240-182">Örnek tek veya çapraz bilgisayar yapılandırması değişikliği kuyrukta adları uygun şekilde, localhost bilgisayarın tam adıyla değiştirerek çalıştırın ve yönergeleri izleyin için [Windows Communication Foundation örnekleriçalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0240-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="f0240-183">Örnek bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f0240-183">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="f0240-184">Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="f0240-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="f0240-185">Uç nokta bağlama ile ilişkili uç noktanın ayarlayarak olduğundan emin olun `bindingConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f0240-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>  
  
2.  <span data-ttu-id="f0240-186">Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemci yapılandırmasına değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f0240-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0240-187">Ayarı `security mode` için `None` ayarına eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="f0240-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="f0240-188">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0240-188">Comments</span></span>  
 <span data-ttu-id="f0240-189">Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkindir.</span><span class="sxs-lookup"><span data-stu-id="f0240-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="f0240-190">İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenemedi.</span><span class="sxs-lookup"><span data-stu-id="f0240-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="f0240-191">Varsayılan olarak kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="f0240-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f0240-192">Kimlik doğrulaması ve imzalama özellik MSMQ için bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f0240-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="f0240-193">Bu örnek bir etki alanının parçası olmayan bir bilgisayarda çalıştırmanız gerekiyorsa aşağıdaki hata iletisini: "kullanıcının iç message queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="f0240-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f0240-194">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="f0240-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f0240-195">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f0240-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f0240-196">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f0240-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f0240-197">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f0240-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a><span data-ttu-id="f0240-198">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0240-198">See Also</span></span>