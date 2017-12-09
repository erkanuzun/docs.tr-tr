---
title: "IHostTaskManager::ReverseLeaveRuntime Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseLeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db8a9114cd15a4e7d42e8f99941d4bcbb9faa842
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="7d8ed-102">IHostTaskManager::ReverseLeaveRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="7d8ed-103">Ana bilgisayar denetimi ortak dil çalışma zamanı (CLR) bırakarak ve buna karşılık, yönetilen koddan çağrıldı bir yönetilmeyen işlevi giriliyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7d8ed-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d8ed-105">Return Value</span></span>  
  
|<span data-ttu-id="7d8ed-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d8ed-106">HRESULT</span></span>|<span data-ttu-id="7d8ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d8ed-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d8ed-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d8ed-108">S_OK</span></span>|<span data-ttu-id="7d8ed-109">`ReverseLeaveRuntime`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="7d8ed-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d8ed-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d8ed-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d8ed-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d8ed-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d8ed-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-113">The call timed out.</span></span>|  
|<span data-ttu-id="7d8ed-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d8ed-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d8ed-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d8ed-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d8ed-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d8ed-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d8ed-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d8ed-118">E_FAIL</span></span>|<span data-ttu-id="7d8ed-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d8ed-120">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d8ed-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7d8ed-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7d8ed-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7d8ed-123">İstenen kaynak ayırma tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d8ed-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d8ed-124">Remarks</span></span>  
 <span data-ttu-id="7d8ed-125">CLR çağrıları `ReverseLeaveRuntime` şu anda yürütülen görev döndürme konak bildirmek için sırasıyla platform aracılığıyla yönetilen koddan çağrıldı yönetilmeyen bir işleve denetim çağırma.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="7d8ed-126">Her çağrı `ReverseLeaveRuntime` karşılık gelen çağrıyı eşleşen [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="7d8ed-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d8ed-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d8ed-127">Requirements</span></span>  
 <span data-ttu-id="7d8ed-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d8ed-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d8ed-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d8ed-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d8ed-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d8ed-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d8ed-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d8ed-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d8ed-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d8ed-132">See Also</span></span>  
 [<span data-ttu-id="7d8ed-133">CallNeedsHostHook yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="7d8ed-134">EnterRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="7d8ed-135">Iclrtask arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7d8ed-136">Iclrtaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7d8ed-137">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7d8ed-138">Ihosttaskmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="7d8ed-139">LeaveRuntime yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d8ed-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="7d8ed-140">Yakından Platform çağırma</span><span class="sxs-lookup"><span data-stu-id="7d8ed-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)