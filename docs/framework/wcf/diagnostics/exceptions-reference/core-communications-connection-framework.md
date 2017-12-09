---
title: "Temel İletişimler: Bağlantı Çerçevesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 878d2b01ee22d339115925e101f7349ecd5207bd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="core-communications-connection-framework"></a><span data-ttu-id="e51a4-102">Temel İletişimler: Bağlantı Çerçevesi</span><span class="sxs-lookup"><span data-stu-id="e51a4-102">Core Communications: Connection Framework</span></span>
<span data-ttu-id="e51a4-103">Bu konu tarafından oluşturulan tüm özel durumları listeler [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bağlantı çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="e51a4-103">This topic lists all exceptions generated by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Connection Framework.</span></span>  
  
## <a name="exception-list"></a><span data-ttu-id="e51a4-104">Özel durum listesi</span><span class="sxs-lookup"><span data-stu-id="e51a4-104">Exception List</span></span>  
  
|<span data-ttu-id="e51a4-105">Kaynak kodu</span><span class="sxs-lookup"><span data-stu-id="e51a4-105">Resource Code</span></span>|<span data-ttu-id="e51a4-106">Kaynak dizesi</span><span class="sxs-lookup"><span data-stu-id="e51a4-106">Resource String</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="e51a4-107">CloseTimedOut</span><span class="sxs-lookup"><span data-stu-id="e51a4-107">CloseTimedOut</span></span>|<span data-ttu-id="e51a4-108">Close yöntemi belirlenen süre sonunda zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e51a4-108">The Close method timed out after the specified time.</span></span> <span data-ttu-id="e51a4-109">Close çağrısına iletilen zaman aşımı değerini artırın veya bağlama üzerinde CloseTimeout değerini artırın.</span><span class="sxs-lookup"><span data-stu-id="e51a4-109">Increase the timeout value that is passed to the call to Close or increase the CloseTimeout value on the binding.</span></span> <span data-ttu-id="e51a4-110">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e51a4-110">The time allotted to this operation may have been a portion of a longer timeout.</span></span>|  
|<span data-ttu-id="e51a4-111">ContentTypeMismatch</span><span class="sxs-lookup"><span data-stu-id="e51a4-111">ContentTypeMismatch</span></span>|<span data-ttu-id="e51a4-112">Belirtilen içerik türü belirtilen bekliyordu bir hizmete gönderildi.</span><span class="sxs-lookup"><span data-stu-id="e51a4-112">The specified content type was sent to a service that was expecting the specified.</span></span> <span data-ttu-id="e51a4-113">İstemci ve hizmet bağlamaları eşleşmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e51a4-113">The client and service bindings may be mismatched.</span></span>|  
|<span data-ttu-id="e51a4-114">DuplexChannelAbortedDuringOpen</span><span class="sxs-lookup"><span data-stu-id="e51a4-114">DuplexChannelAbortedDuringOpen</span></span>|<span data-ttu-id="e51a4-115">Belirtilen çift yönlü kanalı açma işlemi sırasında sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="e51a4-115">The duplex channel to the specified terminated during the Open process.</span></span>|  
|<span data-ttu-id="e51a4-116">FramingValueNotAvailable</span><span class="sxs-lookup"><span data-stu-id="e51a4-116">FramingValueNotAvailable</span></span>|<span data-ttu-id="e51a4-117">Bunu değil tam kodunu çözdü için değer erişilemez.</span><span class="sxs-lookup"><span data-stu-id="e51a4-117">The value cannot be accessed because it is not fully decoded.</span></span>|  
|<span data-ttu-id="e51a4-118">OperationAbortedDuringConnectionEstablishment</span><span class="sxs-lookup"><span data-stu-id="e51a4-118">OperationAbortedDuringConnectionEstablishment</span></span>|<span data-ttu-id="e51a4-119">Belirtilen bağlantı kurulurken işlemi sona erdirildi.</span><span class="sxs-lookup"><span data-stu-id="e51a4-119">The operation was terminated while establishing a connection to the specified.</span></span>|  
|<span data-ttu-id="e51a4-120">ReceiveTimedOut2</span><span class="sxs-lookup"><span data-stu-id="e51a4-120">ReceiveTimedOut2</span></span>|<span data-ttu-id="e51a4-121">Alma işlemi belirlenen süre sonunda zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e51a4-121">The receive operation has timed out after the specified time.</span></span> <span data-ttu-id="e51a4-122">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e51a4-122">The time allotted to this operation may have been a portion of a longer timeout.</span></span>|  
|<span data-ttu-id="e51a4-123">SendCannotBeCalledAfterCloseOutputSession</span><span class="sxs-lookup"><span data-stu-id="e51a4-123">SendCannotBeCalledAfterCloseOutputSession</span></span>|<span data-ttu-id="e51a4-124">CloseOutputSession çağrıldıktan sonra bir kanalda iletileri gönderemez.</span><span class="sxs-lookup"><span data-stu-id="e51a4-124">You cannot send messages on a channel after CloseOutputSession has been called.</span></span>|