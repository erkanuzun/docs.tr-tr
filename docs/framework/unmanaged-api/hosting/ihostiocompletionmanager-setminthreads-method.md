---
title: "IHostIoCompletionManager::SetMinThreads Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.SetMinThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8903aa2f2119ad3c4dceebfaba9ede26200e899
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="725a2-102">IHostIoCompletionManager::SetMinThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="725a2-102">IHostIoCompletionManager::SetMinThreads Method</span></span>
<span data-ttu-id="725a2-103">Konak tahsis et iş parçacıklarının en az sayıda g/ç tamamlama ayarlar.</span><span class="sxs-lookup"><span data-stu-id="725a2-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="725a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="725a2-104">Syntax</span></span>  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="725a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="725a2-105">Parameters</span></span>  
 `dwMinIoCompletionThreads`  
 <span data-ttu-id="725a2-106">[in] Ana bilgisayar oluşturmalısınız g/ç Tamamlama iş parçacığı minimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="725a2-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="725a2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="725a2-107">Return Value</span></span>  
  
|<span data-ttu-id="725a2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="725a2-108">HRESULT</span></span>|<span data-ttu-id="725a2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="725a2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="725a2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="725a2-110">S_OK</span></span>|<span data-ttu-id="725a2-111">`SetMinThreads`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="725a2-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="725a2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="725a2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="725a2-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="725a2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="725a2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="725a2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="725a2-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="725a2-115">The call timed out.</span></span>|  
|<span data-ttu-id="725a2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="725a2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="725a2-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="725a2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="725a2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="725a2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="725a2-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="725a2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="725a2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="725a2-120">E_FAIL</span></span>|<span data-ttu-id="725a2-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="725a2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="725a2-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="725a2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="725a2-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="725a2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="725a2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="725a2-124">E_NOTIMPL</span></span>|<span data-ttu-id="725a2-125">Ana bilgisayar uygulaması sağlamaz `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="725a2-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="725a2-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="725a2-126">Remarks</span></span>  
 <span data-ttu-id="725a2-127">Bir ana bilgisayar uygulaması, performans ve ölçeklenebilirlik gibi nedenlerle g/ç istekleri işlemek için ayrılan iş parçacığı sayısını özel denetime isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="725a2-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="725a2-128">Bu nedenle, ana bilgisayar uygulamak için gerekli olmayan `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="725a2-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="725a2-129">Bu durumda, konak E_NOTIMPL Bu yönteminden döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="725a2-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="725a2-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="725a2-130">Requirements</span></span>  
 <span data-ttu-id="725a2-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="725a2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="725a2-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="725a2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="725a2-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="725a2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="725a2-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="725a2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725a2-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="725a2-135">See Also</span></span>  
 [<span data-ttu-id="725a2-136">Iclrıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="725a2-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="725a2-137">SetMaxThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="725a2-137">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)  
 [<span data-ttu-id="725a2-138">Ihostıocompletionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="725a2-138">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)