---
title: "CorDebugBlockingObject Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingObject Structure
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingObject
helpviewer_keywords: CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c47735565c960c2600f7274d0d59d5a6ec6c178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="3404f-102">CorDebugBlockingObject Yapısı</span><span class="sxs-lookup"><span data-stu-id="3404f-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="3404f-103">Bir iş parçacığı ve iş parçacığı engellendi belirli bir nedenle engelleyen bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3404f-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3404f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3404f-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="3404f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3404f-105">Members</span></span>  
  
|<span data-ttu-id="3404f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3404f-106">Member</span></span>|<span data-ttu-id="3404f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3404f-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="3404f-108">İş parçacığı engelleyen nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3404f-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="3404f-109">Bu nesne yalnızca geçerli eşitlenmiş durumuna süre için geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="3404f-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="3404f-110">İki iş parçacığı aynı eşitlenmiş durumuna içinde aynı nesne üzerinde engelliyorsanız bekleyebilir [Icordebugvalue::getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) yöntemi aynı değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3404f-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="3404f-111">Ancak, arabirimler olabilir veya eşdeğer işaretçisi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3404f-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="3404f-112">Engelleme işleminden önce milisaniye sayısını zaman aşımı ya da onu olacağı zaman aşımına gösterir SONSUZ değeri görüntüler. Zaman aşımı değerini değil hala kalan zaman engelleme işlemi için toplam süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3404f-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="3404f-113">İş parçacığı bu nesne üzerinde engellendi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="3404f-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3404f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3404f-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3404f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3404f-115">Requirements</span></span>  
 <span data-ttu-id="3404f-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3404f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3404f-117">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="3404f-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="3404f-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3404f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3404f-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3404f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3404f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3404f-120">See Also</span></span>  
 [<span data-ttu-id="3404f-121">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="3404f-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="3404f-122">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3404f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)