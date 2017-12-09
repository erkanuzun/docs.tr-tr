---
title: "Hizmet Performansı Sayaçları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2bc29ace454c6c41d3ad6ec11f98a9e6fb3e7d0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="service-performance-counters"></a><span data-ttu-id="40e3d-102">Hizmet Performansı Sayaçları</span><span class="sxs-lookup"><span data-stu-id="40e3d-102">Service Performance Counters</span></span>
<span data-ttu-id="40e3d-103">Hizmeti performans sayaçları hizmet davranışı bir bütün olarak ölçmek ve tüm hizmet performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40e3d-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="40e3d-104">Altında bulunabilir `ServiceModelService 4.0.0.0` Performans İzleyicisi (Perfmon.exe) görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="40e3d-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="40e3d-105">Örnekleri şu biçimi kullanarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="40e3d-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="40e3d-106">Bir performans sayacı örneğinin adının uzunluğu bir sınırı yoktur.</span><span class="sxs-lookup"><span data-stu-id="40e3d-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="40e3d-107">Zaman bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sayaç örneği adı en fazla uzunluğu aşıyor [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] örnek adının bir kısmını karma değeri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="40e3d-107">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e3d-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40e3d-108">See Also</span></span>  
 [<span data-ttu-id="40e3d-109">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="40e3d-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)