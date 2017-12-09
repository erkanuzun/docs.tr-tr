---
title: "Runnable örnekleri algılama süresi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18b016cdf51ec95ab8457ded2949b980fc66fad0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="runnable-instances-detection-period"></a><span data-ttu-id="99e16-102">Runnable örnekleri algılama süresi</span><span class="sxs-lookup"><span data-stu-id="99e16-102">Runnable Instances Detection Period</span></span>
<span data-ttu-id="99e16-103">SQL iş akışı örneği deposuna düzenli aralıklarla uyanır ve kalıcılığı veritabanında runnable veya activatable örneklerini algılayan bir iç görev çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="99e16-103">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects runnable or activatable instances in the persistence database.</span></span> <span data-ttu-id="99e16-104">**Runnable örnekleri algılama süresi** özelliği SQL iş akışı örneği deposunun SQL iş akışı örneği deposuna sonra hiçbir runnable veya activatable iş akışı algılamak için algılama görev çalıştırır süre belirtir Önceki algılama döngüsü sonra Kalıcılık veritabanındaki örnekleri.</span><span class="sxs-lookup"><span data-stu-id="99e16-104">The **Runnable Instances Detection Period** property of the SQL Workflow Instance Store specifies the time period after which the SQL Workflow Instance Store runs a detection task to detect any runnable or activatable workflow instances in the persistence database after the previous detection cycle.</span></span>  
  
 <span data-ttu-id="99e16-105">Bu özellik için daha kısa bir aralığı ayarını bir iş akışı örneği ve olay ve sonraki yükleme örneğinin sinyal ilişkili bir süreölçer sona erme tarihi arasındaki süreyi azaltır.</span><span class="sxs-lookup"><span data-stu-id="99e16-105">Setting a shorter interval for this property reduces the time between the expiration of a timer associated with a workflow instance and the signaling of the event and subsequent loading of the instance.</span></span> <span data-ttu-id="99e16-106">Ancak, aynı zamanda bir ana bilgisayar üzerindeki işlem yükü artırır ve dayanıklı zamanlayıcılar ve/veya ana bilgisayar hataları nadir olduğu senaryolarda tercih edilebilir değil.</span><span class="sxs-lookup"><span data-stu-id="99e16-106">However, it also increases the processing load on a host and may not be desirable in scenarios where durable timers and/or host failures are rare.</span></span> <span data-ttu-id="99e16-107">Özelliğin türü TimeSpan ve özelliğinin değeri biçimdedir: ss: dd:.</span><span class="sxs-lookup"><span data-stu-id="99e16-107">The type of the property is TimeSpan and the value of the property follows the format: hh:mm:ss.</span></span> <span data-ttu-id="99e16-108">Bu özellik için en düşük değer 00:00:01 ' dir.</span><span class="sxs-lookup"><span data-stu-id="99e16-108">The minimum value for this property is 00:00:01.</span></span> <span data-ttu-id="99e16-109">Özelliği için varsayılan değer 00:00:05 ' dir.</span><span class="sxs-lookup"><span data-stu-id="99e16-109">The default value for the property is 00:00:05.</span></span>  
  
 <span data-ttu-id="99e16-110">Daha fazla bilgi için bkz: algılama ve runnable ve activatable iş akışı örnekleri, etkinleştirme [örneği etkinleştirme](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="99e16-110">For more information detecting and activating runnable and activatable workflow instances, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span>