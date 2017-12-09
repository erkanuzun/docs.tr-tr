---
title: "MSMQ Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 904f3a42f8a733546d058c0c4962a50f3c93b5bc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="msmq-transport"></a><span data-ttu-id="e85c3-102">MSMQ Taşıma</span><span class="sxs-lookup"><span data-stu-id="e85c3-102">MSMQ Transport</span></span>
<span data-ttu-id="e85c3-103">Bu konu MSMQ aktarım tarafından oluşturulan tüm özel durumları listeler.</span><span class="sxs-lookup"><span data-stu-id="e85c3-103">This topic lists all exceptions generated by the MSMQ Transport.</span></span>  
  
## <a name="exception-list"></a><span data-ttu-id="e85c3-104">Özel durum listesi</span><span class="sxs-lookup"><span data-stu-id="e85c3-104">Exception List</span></span>  
  
|<span data-ttu-id="e85c3-105">Kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="e85c3-105">Resource Code</span></span>|<span data-ttu-id="e85c3-106">Kaynak dizesi</span><span class="sxs-lookup"><span data-stu-id="e85c3-106">Resource String</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="e85c3-107">MsmqActiveDirectoryRequiresNativeTransfer</span><span class="sxs-lookup"><span data-stu-id="e85c3-107">MsmqActiveDirectoryRequiresNativeTransfer</span></span>|<span data-ttu-id="e85c3-108">İleti için bağlama doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-108">The binding validation for the message failed.</span></span> <span data-ttu-id="e85c3-109">İstemci iletileri gönderemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-109">The client cannot send messages.</span></span> <span data-ttu-id="e85c3-110">Bağlama özelliklerindeki bir çakışma bu hataya neden oldu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-110">A conflict in the binding properties caused this failure.</span></span> <span data-ttu-id="e85c3-111">İse true ve QueueTransferProtocol doğal olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e85c3-111">The UseActiveDirectory is set to true and QueueTransferProtocol is set to Native.</span></span> <span data-ttu-id="e85c3-112">Çakışmayı çözmek için özelliklerden birini düzeltin.</span><span class="sxs-lookup"><span data-stu-id="e85c3-112">To resolve the conflict, correct one of the properties.</span></span>|  
|<span data-ttu-id="e85c3-113">MsmqAuthNoneRequiresProtectionNone</span><span class="sxs-lookup"><span data-stu-id="e85c3-113">MsmqAuthNoneRequiresProtectionNone</span></span>|<span data-ttu-id="e85c3-114">Hizmeti için bağlama doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-114">The binding validation for the service failed.</span></span> <span data-ttu-id="e85c3-115">Hizmet uç noktası ya da istemci başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-115">The service endpoint or the client cannot be started.</span></span> <span data-ttu-id="e85c3-116">Bağlama özelliklerindeki bir çakışma bu hataya neden oldu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-116">A conflict in the binding properties caused this failure.</span></span> <span data-ttu-id="e85c3-117">MsmqAuthenticationMode hiçbiri olarak ayarlanır ve MsmqProtectionLevel None olarak ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="e85c3-117">The MsmqAuthenticationMode is set to None and MsmqProtectionLevel is not set to None.</span></span> <span data-ttu-id="e85c3-118">Çakışmayı gidermek için özelliklerden birini düzeltin.</span><span class="sxs-lookup"><span data-stu-id="e85c3-118">To resolve to conflict, correct one of the properties.</span></span>|  
|<span data-ttu-id="e85c3-119">MsmqCustomRequiresPerAddDLQ</span><span class="sxs-lookup"><span data-stu-id="e85c3-119">MsmqCustomRequiresPerAddDLQ</span></span>|<span data-ttu-id="e85c3-120">İleti için bağlama doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-120">The binding validation for the message failed.</span></span> <span data-ttu-id="e85c3-121">İstemci ileti gönderilemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-121">The client cannot send the message.</span></span> <span data-ttu-id="e85c3-122">DeadLetterQueue özel olarak ayarlanmış, ancak CustomDeadLetterQueue belirtilmemiş.</span><span class="sxs-lookup"><span data-stu-id="e85c3-122">The DeadLetterQueue is set to Custom, but the CustomDeadLetterQueue is not specified.</span></span> <span data-ttu-id="e85c3-123">Sahipsiz sıra her uygulama için URI CustomDeadLetterQueue özelliğinde belirtin.</span><span class="sxs-lookup"><span data-stu-id="e85c3-123">Specify the URI of the dead letter queue for each application in the CustomDeadLetterQueue property.</span></span>|  
|<span data-ttu-id="e85c3-124">MsmqDeserializationError</span><span class="sxs-lookup"><span data-stu-id="e85c3-124">MsmqDeserializationError</span></span>|<span data-ttu-id="e85c3-125">XML iletisini kaldırılırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-125">An error was encountered while deserializing the XML message.</span></span> <span data-ttu-id="e85c3-126">İleti alınamaz ve bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e85c3-126">The message cannot be received and is dropped.</span></span>|  
|<span data-ttu-id="e85c3-127">MsmqDLQNotWriteable</span><span class="sxs-lookup"><span data-stu-id="e85c3-127">MsmqDLQNotWriteable</span></span>|<span data-ttu-id="e85c3-128">İstemci için bağlama doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-128">The binding validation for the client failed.</span></span> <span data-ttu-id="e85c3-129">İstemci bir ileti gönderilemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-129">The client cannot send a message.</span></span> <span data-ttu-id="e85c3-130">Belirtilen sahipsiz sıra yok veya yazılamaz.</span><span class="sxs-lookup"><span data-stu-id="e85c3-130">The specified dead-letter queue does not exist or cannot be written.</span></span> <span data-ttu-id="e85c3-131">Yazma için uygun yetkilere sahip sıranın var olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-131">Ensure the queue exists with the proper authorization to write to it.</span></span>|  
|<span data-ttu-id="e85c3-132">MsmqGetPrivateComputerInformationError</span><span class="sxs-lookup"><span data-stu-id="e85c3-132">MsmqGetPrivateComputerInformationError</span></span>|<span data-ttu-id="e85c3-133">Sürüm denetimi belirtilen hatasıyla başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-133">The version check failed with the specified error.</span></span> <span data-ttu-id="e85c3-134">Sıraya alınan kanalı olmayan tüm işlemleri başarısız olur MSMQ sürümü algılanamıyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-134">The version of MSMQ cannot be detected All operations that are on the queued channel will fail.</span></span> <span data-ttu-id="e85c3-135">MSMQ yüklü olduğundan ve kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-135">Ensure that MSMQ is installed and is available.</span></span>|  
|<span data-ttu-id="e85c3-136">MsmqNoAssurancesForVolatile</span><span class="sxs-lookup"><span data-stu-id="e85c3-136">MsmqNoAssurancesForVolatile</span></span>|<span data-ttu-id="e85c3-137">Hizmeti için bağlama doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-137">The binding validation for the service failed.</span></span> <span data-ttu-id="e85c3-138">Hizmet uç noktası ya da istemci başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-138">The service endpoint or the client cannot be started.</span></span> <span data-ttu-id="e85c3-139">Özelliği true ve sağlam özelliği için ayarlanmış ExactlyOnce false olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e85c3-139">The ExactlyOnce property is set to true and the Durable property is set to false.</span></span> <span data-ttu-id="e85c3-140">Bu işlem desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-140">This is not supported.</span></span> <span data-ttu-id="e85c3-141">Çakışmayı çözmek için bu özelliklerden birini düzeltin.</span><span class="sxs-lookup"><span data-stu-id="e85c3-141">To resolve the conflict, correct one of these properties.</span></span>|  
|<span data-ttu-id="e85c3-142">MsmqNonTransactionalQueueNeeded</span><span class="sxs-lookup"><span data-stu-id="e85c3-142">MsmqNonTransactionalQueueNeeded</span></span>|<span data-ttu-id="e85c3-143">Bağlama ve MSMQ sıra yapılandırması arasında uyumsuzluk algılandı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-143">A mismatch between the binding and MSMQ queue configuration was detected.</span></span> <span data-ttu-id="e85c3-144">Hizmet uç noktası başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-144">The service endpoint cannot be started.</span></span> <span data-ttu-id="e85c3-145">ExactlyOnce özelliği false olarak ayarlandığında ve kuyruğa alınan iletileri okumak için bir işlem sırası.</span><span class="sxs-lookup"><span data-stu-id="e85c3-145">The ExactlyOnce property is set to false and the queue to read messages from is a transactional queue.</span></span> <span data-ttu-id="e85c3-146">Doğru veya işlemsel olmayan bir bağlama oluşturun ExactlyOnce özelliği ayarlanarak hatayı düzeltin.</span><span class="sxs-lookup"><span data-stu-id="e85c3-146">Correct the error by setting the ExactlyOnce property to true or create a non-transactional binding.</span></span>|  
|<span data-ttu-id="e85c3-147">MsmqOpenError</span><span class="sxs-lookup"><span data-stu-id="e85c3-147">MsmqOpenError</span></span>|<span data-ttu-id="e85c3-148">Belirtilen sıra açılırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-148">An error occurred while opening the specified queue.</span></span> <span data-ttu-id="e85c3-149">İleti gönderilen veya alınan sıradan.</span><span class="sxs-lookup"><span data-stu-id="e85c3-149">The message cannot be sent or received from the queue.</span></span> <span data-ttu-id="e85c3-150">MSMQ yüklü olduğundan ve çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-150">Ensure that MSMQ is installed and running.</span></span> <span data-ttu-id="e85c3-151">Ayrıca sıranın gerekli erişim modu ve yetkilendirme açmak kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-151">Also ensure that the queue is available to open with the required access mode and authorization.</span></span>|  
|<span data-ttu-id="e85c3-152">MsmqPathLookupError</span><span class="sxs-lookup"><span data-stu-id="e85c3-152">MsmqPathLookupError</span></span>|<span data-ttu-id="e85c3-153">Belirtilen sıra yol adı biçim adına dönüştürürken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-153">An error occurred when converting the specified queue path name to the format name.</span></span> <span data-ttu-id="e85c3-154">Sıraya alınan kanalındaki tüm işlemleri başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-154">All operations on the queued channel failed.</span></span> <span data-ttu-id="e85c3-155">Sıra adres geçerli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-155">Ensure that the queue address is valid.</span></span> <span data-ttu-id="e85c3-156">MSMQ Active Directory Tümleştirme ile etkinleştirilmiş yüklü olmalıdır ve erişimi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e85c3-156">MSMQ must be installed with Active Directory integration enabled and access to it is available.</span></span>|  
|<span data-ttu-id="e85c3-157">MsmqPerAppDLQRequiresCustom</span><span class="sxs-lookup"><span data-stu-id="e85c3-157">MsmqPerAppDLQRequiresCustom</span></span>|<span data-ttu-id="e85c3-158">İstemci üzerinde bağlama doğrulaması başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-158">The binding validation on the client failed.</span></span> <span data-ttu-id="e85c3-159">İstemci iletileri gönderemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-159">The client cannot send messages.</span></span> <span data-ttu-id="e85c3-160">CustomDeadLetterQueue özelliği ayarlanmış ancak DeadLetterQueue özelliği özel olarak ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-160">The CustomDeadLetterQueue property is set, but the DeadLetterQueue property is not set to Custom.</span></span> <span data-ttu-id="e85c3-161">DeadLetterQueue özelliğini özel olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e85c3-161">Set the DeadLetterQueue property to Custom.</span></span>|  
|<span data-ttu-id="e85c3-162">MsmqPerAppDLQRequiresExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="e85c3-162">MsmqPerAppDLQRequiresExactlyOnce</span></span>|<span data-ttu-id="e85c3-163">İstemci için bağlama doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-163">The binding validation for the client failed.</span></span> <span data-ttu-id="e85c3-164">İstemci iletileri gönderemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-164">The client cannot send messages.</span></span> <span data-ttu-id="e85c3-165">Bağlama özelliklerindeki bir çakışma bu hataya neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-165">A conflict in the binding properties is causing the failure.</span></span> <span data-ttu-id="e85c3-166">Özel sahipsiz sırayı kullanmak için ExactlyOnce çakışmayı gidermek için true olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e85c3-166">To use the custom dead-letter queue, ExactlyOnce must be set to true to resolve to conflict.</span></span>|  
|<span data-ttu-id="e85c3-167">MsmqPerAppDLQRequiresMsmq4</span><span class="sxs-lookup"><span data-stu-id="e85c3-167">MsmqPerAppDLQRequiresMsmq4</span></span>|<span data-ttu-id="e85c3-168">Bağlama ve MSMQ Yapılandırma arasında uyumsuzluk algılandı.</span><span class="sxs-lookup"><span data-stu-id="e85c3-168">A mismatch between the binding and MSMQ configuration was detected.</span></span> <span data-ttu-id="e85c3-169">İstemci iletileri gönderemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-169">The client cannot send messages.</span></span> <span data-ttu-id="e85c3-170">Özel sahipsiz sırayı kullanmak için MSMQ sürüm 4.0 veya üstü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e85c3-170">To use the custom dead-letter queue, you must have MSMQ version 4.0 or higher.</span></span> <span data-ttu-id="e85c3-171">MSMQ sürüm 4.0 veya üstü yoksa DeadLetterQueue özelliği sistem veya None olarak ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="e85c3-171">If you do not have MSMQ version 4.0 or higher set the DeadLetterQueue property to System or None.</span></span>|  
|<span data-ttu-id="e85c3-172">MsmqReceiveError</span><span class="sxs-lookup"><span data-stu-id="e85c3-172">MsmqReceiveError</span></span>|<span data-ttu-id="e85c3-173">Kuyruktan bir ileti alınırken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-173">An error occurred while receiving a message from the queue.</span></span> <span data-ttu-id="e85c3-174">MSMQ yüklü olduğundan ve çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-174">Ensure that MSMQ is installed and running.</span></span> <span data-ttu-id="e85c3-175">Sıraya almak kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-175">Make sure the queue is available to receive from.</span></span>|  
|<span data-ttu-id="e85c3-176">MsmqSameTransactionExpected</span><span class="sxs-lookup"><span data-stu-id="e85c3-176">MsmqSameTransactionExpected</span></span>|<span data-ttu-id="e85c3-177">Bu oturum için bir işlem hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-177">A transaction error occurred for this session.</span></span> <span data-ttu-id="e85c3-178">Oturum kanalı hata döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e85c3-178">The session channel is faulted.</span></span> <span data-ttu-id="e85c3-179">Oturumdaki iletilerin gönderilen veya alınan.</span><span class="sxs-lookup"><span data-stu-id="e85c3-179">Messages in the session cannot be sent or received.</span></span> <span data-ttu-id="e85c3-180">Sıraya alınan bir oturum ile birden fazla işlem ilişkilendirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-180">A queued session cannot be associated with more than one transaction.</span></span> <span data-ttu-id="e85c3-181">Oturumdaki tüm iletilerin gönderilen veya tek bir işlem kullanılarak alınan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-181">Ensure that all messages in the session are sent or received using a single transaction.</span></span>|  
|<span data-ttu-id="e85c3-182">MsmqSendError</span><span class="sxs-lookup"><span data-stu-id="e85c3-182">MsmqSendError</span></span>|<span data-ttu-id="e85c3-183">Belirtilen sıraya gönderilirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-183">An error occurred while sending to the specified queue.</span></span> <span data-ttu-id="e85c3-184">MSMQ yüklü olduğundan ve çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-184">Ensure that MSMQ is installed and running.</span></span> <span data-ttu-id="e85c3-185">Yerel bir sıra gönderiyorsanız, gerekli erişim modu ve yetkilendirme sıranın mevcut emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-185">If you are sending to a local queue, ensure the queue exists with the required access mode and authorization.</span></span>|  
|<span data-ttu-id="e85c3-186">MsmqTimeSpanTooLarge</span><span class="sxs-lookup"><span data-stu-id="e85c3-186">MsmqTimeSpanTooLarge</span></span>|<span data-ttu-id="e85c3-187">İleti yaşam süresi çok büyük.</span><span class="sxs-lookup"><span data-stu-id="e85c3-187">The message time to live is too large.</span></span> <span data-ttu-id="e85c3-188">İleti gönderilemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-188">The message cannot be sent.</span></span> <span data-ttu-id="e85c3-189">İletinin yaşam süresi (TTL) Int32 en büyük değeri aşamaz.</span><span class="sxs-lookup"><span data-stu-id="e85c3-189">The message Time To Live (TTL) cannot exceed the Int32 maximum value.</span></span>|  
|<span data-ttu-id="e85c3-190">MsmqTokenProviderNeededForCertificates</span><span class="sxs-lookup"><span data-stu-id="e85c3-190">MsmqTokenProviderNeededForCertificates</span></span>|<span data-ttu-id="e85c3-191">Bir X509SecurityTokenProvider öğesi bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-191">An X509SecurityTokenProvider cannot be found.</span></span> <span data-ttu-id="e85c3-192">İleti gönderilemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-192">The message cannot be sent.</span></span> <span data-ttu-id="e85c3-193">Sertifika kimlik doğrulama modu, bir X.509 belirteç sağlayıcısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e85c3-193">The certificate authentication mode requires an X.509 token provider.</span></span> <span data-ttu-id="e85c3-194">Bir güvenlik belirteci sağlayıcısı için yüklü sertifikayı kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-194">Make sure a security token provider is available for the installed certificate.</span></span>|  
|<span data-ttu-id="e85c3-195">MsmqTransactedDLQExpected</span><span class="sxs-lookup"><span data-stu-id="e85c3-195">MsmqTransactedDLQExpected</span></span>|<span data-ttu-id="e85c3-196">Bağlama ve MSMQ Yapılandırması arasında bir uyuşmazlığı oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-196">A mismatch occurred between the binding and the MSMQ configuration.</span></span> <span data-ttu-id="e85c3-197">İleti gönderilemiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-197">Messages cannot be sent.</span></span> <span data-ttu-id="e85c3-198">Bağlamada belirtilen özel sahipsiz sırayı iletim sırası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e85c3-198">The custom dead-letter queue specified in the binding must be a transaction queue.</span></span> <span data-ttu-id="e85c3-199">Özel sahipsiz sırayı adresinin doğru olduğundan ve bir işlem sırası olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-199">Ensure that the custom dead-letter queue address is correct and the queue is a transactional queue.</span></span>|  
|<span data-ttu-id="e85c3-200">MsmqTransactionalQueueNeeded</span><span class="sxs-lookup"><span data-stu-id="e85c3-200">MsmqTransactionalQueueNeeded</span></span>|<span data-ttu-id="e85c3-201">Bağlama ve MSMQ sıra yapılandırması arasında bir uyuşmazlık oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-201">A mismatch between the binding and the MSMQ queue configuration occurred.</span></span> <span data-ttu-id="e85c3-202">Hizmet uç noktası başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-202">The service endpoint cannot be started.</span></span> <span data-ttu-id="e85c3-203">Özelliği true ve sıraya alınan iletileri okumak için olarak ayarlanmış ExactlyOnce işlemsel bir sıra değil.</span><span class="sxs-lookup"><span data-stu-id="e85c3-203">The ExactlyOnce property is set to true and the queue to read messages from is not a transactional queue.</span></span> <span data-ttu-id="e85c3-204">Hatayı düzeltmek için ExactlyOnce özelliğini false olarak ayarlayın veya bu bağlama için bir işlem sırası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-204">To correct to the error, set the ExactlyOnce property to false or create a transactional queue for this binding.</span></span>|  
|<span data-ttu-id="e85c3-205">MsmqTransactionCurrentRequired</span><span class="sxs-lookup"><span data-stu-id="e85c3-205">MsmqTransactionCurrentRequired</span></span>|<span data-ttu-id="e85c3-206">Hiçbir işlem oturumda ileti göndermek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e85c3-206">No transaction is available to send messages in the session.</span></span> <span data-ttu-id="e85c3-207">Sıraya alınan bir oturumda ileti göndermek için bir işlem gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-207">To send a message in a queued session requires a transaction.</span></span> <span data-ttu-id="e85c3-208">Bir işlem kapsamı oturumda ileti göndermek için belirtildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-208">Ensure that a transaction scope is specified to send the message in the session.</span></span>|  
|<span data-ttu-id="e85c3-209">MsmqTransactionRequired</span><span class="sxs-lookup"><span data-stu-id="e85c3-209">MsmqTransactionRequired</span></span>|<span data-ttu-id="e85c3-210">Bir işlem gerekiyor ancak yok.</span><span class="sxs-lookup"><span data-stu-id="e85c3-210">A transaction is required but is not available.</span></span> <span data-ttu-id="e85c3-211">İletiler gönderilen veya alınan.</span><span class="sxs-lookup"><span data-stu-id="e85c3-211">Messages cannot be sent or received.</span></span> <span data-ttu-id="e85c3-212">İşlem kapsamı ileti göndermek veya almak için belirtildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e85c3-212">Ensure that the transaction scope is specified to send or receive messages.</span></span>|  
|<span data-ttu-id="e85c3-213">MsmqUnsupportedSerializationFormat</span><span class="sxs-lookup"><span data-stu-id="e85c3-213">MsmqUnsupportedSerializationFormat</span></span>|<span data-ttu-id="e85c3-214">Seri durumundan çıkarma hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="e85c3-214">A deserialization error occurred.</span></span> <span data-ttu-id="e85c3-215">İleti alınamaz ve bırakılır.</span><span class="sxs-lookup"><span data-stu-id="e85c3-215">The message cannot be received and is dropped.</span></span> <span data-ttu-id="e85c3-216">Belirtilen seri hale getirme biçimi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e85c3-216">The specified serialization format is not supported.</span></span>|  
|<span data-ttu-id="e85c3-217">MsmqWrongPrivateQueueSyntax</span><span class="sxs-lookup"><span data-stu-id="e85c3-217">MsmqWrongPrivateQueueSyntax</span></span>|<span data-ttu-id="e85c3-218">URL geçersiz.</span><span class="sxs-lookup"><span data-stu-id="e85c3-218">The URL is invalid.</span></span> <span data-ttu-id="e85c3-219">Sıra için URL '$' karakterini içeremez.</span><span class="sxs-lookup"><span data-stu-id="e85c3-219">The URL for the queue cannot contain the '$' character.</span></span> <span data-ttu-id="e85c3-220">Özel bir sıra adreslemek için.MSMQ://machine/private/queueName sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e85c3-220">Use the syntax in net.msmq://machine/private/queueName to address a private queue.</span></span>|