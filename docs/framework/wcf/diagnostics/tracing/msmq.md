---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15be4b6bfb84a0aa843e3d62861a9195e125a04e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="msmq"></a><span data-ttu-id="7ad08-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="7ad08-102">MSMQ</span></span>
<span data-ttu-id="7ad08-103">MSMQ uygulamada hiçbir ek etkinlik MSMQ sıraya alınan kanala ve sıraya alınan kanal MSMQ aktarılır.</span><span class="sxs-lookup"><span data-stu-id="7ad08-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="7ad08-104">Ayrıca, MSMQ ileti kimliği ve SOAP iletisi kimliği (birlikte etkinlik varsa kimliği) gönderme işlemi üzerinde sıraya alınan kanal izlemeleri bir parçası olarak izlenecek.</span><span class="sxs-lookup"><span data-stu-id="7ad08-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="7ad08-105">MSMQ ileti kimliği ve SOAP iletisi kimliği (birlikte etkinliği kimliği, varsa mevcut) bir alma işlemi üzerinde sıraya alınan kanal izlemeleri bir parçası olarak izlenmesini.</span><span class="sxs-lookup"><span data-stu-id="7ad08-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="7ad08-106">Alma işlemi üzerinde gerekli aktarımları için herhangi bir aktarım benzer şekilde yürütülür (almak bayt -> işlemi iletisi işlemi ->).</span><span class="sxs-lookup"><span data-stu-id="7ad08-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>