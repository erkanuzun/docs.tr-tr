---
title: "WF etkinlikleri hata işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8b7ed6837e9ee88e85324ed5d7a2b9ff3e419a9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="d34a8-102">WF etkinlikleri hata işleme</span><span class="sxs-lookup"><span data-stu-id="d34a8-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="d34a8-103">hata işleme ve kurtarma uygulamak için birkaç sistem tarafından sağlanan etkinlikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d34a8-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d34a8-104">[Özel durumları](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="d34a8-104"> [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="d34a8-105">Hata işleme etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="d34a8-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="d34a8-106">İçinden son durum bloğunu bir `TryCatch` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d34a8-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="d34a8-107">Bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d34a8-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="d34a8-108">Özel durum işleme uygular.</span><span class="sxs-lookup"><span data-stu-id="d34a8-108">Implements exception handling.</span></span>|