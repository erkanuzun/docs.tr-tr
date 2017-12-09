---
title: "İş Akışı Denetim Uç Noktası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5894a8b5d4d0873a231927498a8d1e2c4e18afd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-control-endpoint"></a><span data-ttu-id="8a7b4-102">İş Akışı Denetim Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="8a7b4-102">Workflow Control Endpoint</span></span>
<span data-ttu-id="8a7b4-103">İş akışı denetim uç noktası uzaktan kullanarak barındırılan iş akışı örnekleri denetlemek için denetimi işlemleri çağırmak geliştiricilerin sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-103">The workflow control endpoint allows developers to call control operations to remotely control workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8a7b4-104">Bu özellik, programlı olarak askıya alma, sürdürme ve sonlandırma gibi denetim işlemleri gerçekleştirmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-104">This feature can be used to programmatically perform control operations like suspend, resume, and terminate.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8a7b4-105">Kullanarak bir işlem ve denetlenen iş akışı içinde iş akışı denetim uç noktası içeriyorsa, bir <xref:System.Activities.Statements.Persist> etkinlik, iş akışı örneği askıda işlem zaman aşımına uğrayana kadar.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-105">If using the workflow control endpoint within a transaction and the workflow being controlled contains a <xref:System.Activities.Statements.Persist> activity, the workflow instance will hang until the transaction times out.</span></span>  
  
## <a name="workflow-instance-management"></a><span data-ttu-id="8a7b4-106">İş akışı örneği Yönetimi</span><span class="sxs-lookup"><span data-stu-id="8a7b4-106">Workflow Instance Management</span></span>  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="8a7b4-107">adlı yeni bir sözleşmesini tanımlayan <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-107"> defines a new contract called <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>.</span></span> <span data-ttu-id="8a7b4-108">Bu sözleşmeyi tanımlayan bir dizi uzaktan izin işlemleri tarafından barındırılan iş akışı örnekleri denetim <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-108">This contract defines a series of control operations that allow you remotely control workflow instances hosted by <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8a7b4-109"><xref:System.ServiceModel.Activities.WorkflowControlEndpoint>uygulaması sağlayan standart bir uç nokta <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> sözleşme.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-109"><xref:System.ServiceModel.Activities.WorkflowControlEndpoint> is a standard endpoint that provides an implementation of the <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contract.</span></span> <span data-ttu-id="8a7b4-110"><xref:System.ServiceModel.Activities.WorkflowControlClient>denetim işlemleri göndermek için kullanılan bir sınıftır <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-110"><xref:System.ServiceModel.Activities.WorkflowControlClient> is a class that is used to send the control operations to the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span>  
  
 <span data-ttu-id="8a7b4-111">İş akışı örnekleri şu durumlardan birinde olabilir:</span><span class="sxs-lookup"><span data-stu-id="8a7b4-111">Workflow instances can be in one of the following states:</span></span>  
  
 <span data-ttu-id="8a7b4-112">Etkin</span><span class="sxs-lookup"><span data-stu-id="8a7b4-112">Active</span></span>  
 <span data-ttu-id="8a7b4-113">Tamamlanan durumu ve ne zaman askıya alınmış durumda değil erişmeden önce bir iş akışı örneği durumu.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-113">The state of a workflow instance before it reaches the completed state and when it is not in the suspended state.</span></span> <span data-ttu-id="8a7b4-114">Bu durumundayken, iş akışı örneği çalışır ve uygulama iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-114">While in this state, the workflow instance runs and processes application messages.</span></span>  
  
 <span data-ttu-id="8a7b4-115">Askıya alındı</span><span class="sxs-lookup"><span data-stu-id="8a7b4-115">Suspended</span></span>  
 <span data-ttu-id="8a7b4-116">Bu durumundayken, çalışan başlatılmamış veya kısmen çalıştıran etkinlikleri olsa bile iş akışı örneği çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-116">While in this state, the workflow instance does not run even if there are activities that have not started running or have partially run.</span></span>  
  
 <span data-ttu-id="8a7b4-117">Tamamlandı</span><span class="sxs-lookup"><span data-stu-id="8a7b4-117">Completed</span></span>  
 <span data-ttu-id="8a7b4-118">Bir iş akışı örneği son durumu.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-118">The final state of a workflow instance.</span></span> <span data-ttu-id="8a7b4-119">İş akışı örneği tamamlandı durumuna eriştikten sonra çalıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-119">The workflow instance cannot run after reaching the completed state.</span></span>  
  
## <a name="iworkflowinstancemanagement"></a><span data-ttu-id="8a7b4-120">IWorkflowInstanceManagement</span><span class="sxs-lookup"><span data-stu-id="8a7b4-120">IWorkflowInstanceManagement</span></span>  
 <span data-ttu-id="8a7b4-121"><xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Arabirimi denetimi işlemleri zaman uyumlu ve zaman uyumsuz sürümlerini kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-121">The <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> interface defines a set of control operations with synchronous and asynchronous versions.</span></span> <span data-ttu-id="8a7b4-122">İşlenen sürümleri işlem algılayan bir bağlama kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-122">The transacted versions require use of a transaction-aware binding.</span></span> <span data-ttu-id="8a7b4-123">Aşağıdaki tabloda, desteklenen denetimi işlemleri listeler.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-123">The following table lists the control operations supported.</span></span>  
  
|<span data-ttu-id="8a7b4-124">Denetim işlemi</span><span class="sxs-lookup"><span data-stu-id="8a7b4-124">Control Operation</span></span>|<span data-ttu-id="8a7b4-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a7b4-125">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="8a7b4-126">Durdurma</span><span class="sxs-lookup"><span data-stu-id="8a7b4-126">Abort</span></span>|<span data-ttu-id="8a7b4-127">Zorla iş akışı örneğini yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-127">Forcefully stops the execution of the workflow instance.</span></span>|  
|<span data-ttu-id="8a7b4-128">İptal</span><span class="sxs-lookup"><span data-stu-id="8a7b4-128">Cancel</span></span>|<span data-ttu-id="8a7b4-129">Bir iş akışı örneğine etkin veya askıya alınmış durumundan tamamlandı durumuna geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-129">Transitions a workflow instance from the active or suspended state to the completed state.</span></span>|  
|<span data-ttu-id="8a7b4-130">Çalıştır</span><span class="sxs-lookup"><span data-stu-id="8a7b4-130">Run</span></span>|<span data-ttu-id="8a7b4-131">Bir iş akışı örneği yürütme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-131">Provides a workflow instance the opportunity to execute.</span></span>|  
|<span data-ttu-id="8a7b4-132">Askıya alma</span><span class="sxs-lookup"><span data-stu-id="8a7b4-132">Suspend</span></span>|<span data-ttu-id="8a7b4-133">Etkin durumdaki bir iş akışı örneğinden askıya alınmış durumuna geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-133">Transitions a workflow instance from the active state to the suspended state.</span></span>|  
|<span data-ttu-id="8a7b4-134">Sonlandırma</span><span class="sxs-lookup"><span data-stu-id="8a7b4-134">Terminate</span></span>|<span data-ttu-id="8a7b4-135">Bir iş akışı örneğine etkin veya askıya alınmış durumundan tamamlandı durumuna geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-135">Transitions a workflow instance from the active or suspended state to the completed state.</span></span>|  
|<span data-ttu-id="8a7b4-136">Erişimini iade etme</span><span class="sxs-lookup"><span data-stu-id="8a7b4-136">Unsuspend</span></span>|<span data-ttu-id="8a7b4-137">Bir iş akışı örneği askıya alınmış durumundan etkin duruma geçer.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-137">Transitions a workflow instance from the suspended state to the active state.</span></span>|  
|<span data-ttu-id="8a7b4-138">TransactedCancel</span><span class="sxs-lookup"><span data-stu-id="8a7b4-138">TransactedCancel</span></span>|<span data-ttu-id="8a7b4-139">İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında İptal işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-139">Performs the Cancel operation under a transaction (flowed in from the client or created locally).</span></span> <span data-ttu-id="8a7b4-140">Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-140">If the system maintains the durable state of the workflow instance, the workflow instance must be persisted during execution of this operation.</span></span>|  
|<span data-ttu-id="8a7b4-141">TransactedRun</span><span class="sxs-lookup"><span data-stu-id="8a7b4-141">TransactedRun</span></span>|<span data-ttu-id="8a7b4-142">İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında çalıştırma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-142">Performs the Run operation under a transaction (flowed in from the client or created locally).</span></span> <span data-ttu-id="8a7b4-143">Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-143">If the system maintains the durable state of the workflow instance, the workflow instance must be persisted during execution of this operation.</span></span>|  
|<span data-ttu-id="8a7b4-144">TransactedSuspend</span><span class="sxs-lookup"><span data-stu-id="8a7b4-144">TransactedSuspend</span></span>|<span data-ttu-id="8a7b4-145">İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında askıya alma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-145">Performs the Suspend operation under a transaction (flowed in from the client or created locally).</span></span> <span data-ttu-id="8a7b4-146">Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-146">If the system maintains the durable state of the workflow instance, the workflow instance must be persisted during execution of this operation.</span></span>|  
|<span data-ttu-id="8a7b4-147">TransactedTerminate</span><span class="sxs-lookup"><span data-stu-id="8a7b4-147">TransactedTerminate</span></span>|<span data-ttu-id="8a7b4-148">İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında sonlandırma işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-148">Performs the Terminate operation under a transaction (flowed in from the client or created locally).</span></span> <span data-ttu-id="8a7b4-149">Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-149">If the system maintains the durable state of the workflow instance, the workflow instance must be persisted during execution of this operation.</span></span>|  
|<span data-ttu-id="8a7b4-150">TransactedUnsuspend</span><span class="sxs-lookup"><span data-stu-id="8a7b4-150">TransactedUnsuspend</span></span>|<span data-ttu-id="8a7b4-151">İşlem (içinde istemciden aktarılan veya yerel olarak oluşturulan) altında Unsuspend işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-151">Performs the Unsuspend operation under a transaction (flowed in from the client or created locally).</span></span> <span data-ttu-id="8a7b4-152">Sistem iş akışı örneği dayanıklı durumunu koruyorsa, iş akışı örneği bu işlemi yürütme sırasında kalıcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-152">If the system maintains the durable state of the workflow instance, the workflow instance must be persisted during execution of this operation.</span></span>|  
  
 <span data-ttu-id="8a7b4-153"><xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> Sözleşme yalnızca var olan iş akışı örnekleri yönetmek için yeni bir iş akışı örneği oluşturmak için bir yol sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-153">The <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contract does not provide a means to create a new workflow instance, only to manage existing workflow instances.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8a7b4-154">Yeni bir iş akışı örneği uzaktan bkz [iş akışı hizmeti konak genişletilebilirliği](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="8a7b4-154"> remotely creating a new workflow instance, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="workflowcontrolendpoint"></a><span data-ttu-id="8a7b4-155">WorkflowControlEndpoint</span><span class="sxs-lookup"><span data-stu-id="8a7b4-155">WorkflowControlEndpoint</span></span>  
 <span data-ttu-id="8a7b4-156"><xref:System.ServiceModel.Activities.WorkflowControlEndpoint>Standart bir uç nokta sabit bir sözleşme ile <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-156"><xref:System.ServiceModel.Activities.WorkflowControlEndpoint> is a standard endpoint with a fixed contract, <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>.</span></span> <span data-ttu-id="8a7b4-157">Eklendiğinde bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek, bu uç nokta can sonra komut işlemleri ana bilgisayar örneği tarafından barındırılan herhangi bir iş akışı örneği göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-157">When added to a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance, this endpoint can then be used to send command operations to any workflow instance hosted by the host instance.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8a7b4-158">Standart uç noktaları Bkz [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="8a7b4-158"> standard endpoints, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).</span></span>  
  
## <a name="workflowcontrolclient"></a><span data-ttu-id="8a7b4-159">WorkflowControlClient</span><span class="sxs-lookup"><span data-stu-id="8a7b4-159">WorkflowControlClient</span></span>  
 <span data-ttu-id="8a7b4-160"><xref:System.ServiceModel.Activities.WorkflowControlClient>Denetim iletileri göndermenize olanak sağlayan bir sınıf bir <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> üzerinde bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-160"><xref:System.ServiceModel.Activities.WorkflowControlClient> is a class that allows you to send control messages to a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> on a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8a7b4-161">Tarafından desteklenen işlemler her bir yöntemi içeren <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> hizmetteki işlem dışında sözleşme.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-161">It contains a method for each of the operations supported by the <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> contract except for the transacted operations.</span></span> <span data-ttu-id="8a7b4-162"><xref:System.ServiceModel.Activities.WorkflowControlClient>uygulaması yapılan işlem kullanılması gerekip gerekmediğini belirlemek için ortam işlem kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a7b4-162"><xref:System.ServiceModel.Activities.WorkflowControlClient> uses the ambient transaction to determine whether a transacted operation should be used.</span></span>