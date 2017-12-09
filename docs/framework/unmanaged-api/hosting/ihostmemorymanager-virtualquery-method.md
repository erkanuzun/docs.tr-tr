---
title: "IHostMemoryManager::VirtualQuery Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualQuery
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82c76ce908dd73fba0a2a0039894f51790b46583
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="2520b-102">IHostMemoryManager::VirtualQuery Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2520b-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="2520b-103">Karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="2520b-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="2520b-104">Win32 uygulaması `VirtualQuery` çağırma işleminin sanal adres alanındaki sayfaları bir dizi ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="2520b-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2520b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2520b-105">Syntax</span></span>  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2520b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2520b-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="2520b-107">[in] Sorgulanacak sanal bellek adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2520b-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="2520b-108">[out] Belirtilen bellek bölge hakkında bilgi içeren bir yapı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2520b-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2520b-109">[in] Arabelleğin bayt cinsinden boyutu, `lpBuffer` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="2520b-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="2520b-110">[out] Bilgi arabellek tarafından döndürülen bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2520b-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2520b-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2520b-111">Return Value</span></span>  
  
|<span data-ttu-id="2520b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2520b-112">HRESULT</span></span>|<span data-ttu-id="2520b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2520b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2520b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2520b-114">S_OK</span></span>|<span data-ttu-id="2520b-115">`VirtualQuery`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2520b-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="2520b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2520b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2520b-117">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2520b-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2520b-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2520b-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2520b-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2520b-119">The call timed out.</span></span>|  
|<span data-ttu-id="2520b-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2520b-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2520b-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2520b-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2520b-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2520b-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2520b-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2520b-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2520b-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2520b-124">E_FAIL</span></span>|<span data-ttu-id="2520b-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2520b-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2520b-126">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2520b-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2520b-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2520b-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2520b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2520b-128">Remarks</span></span>  
 <span data-ttu-id="2520b-129">`VirtualQuery`bir dizi çağırma işleminin sanal adres alanındaki sayfaları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2520b-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="2520b-130">Bu uygulama değerini ayarlar `pResult` bayt sayısı parametre bilgileri arabellekte ve bir HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2520b-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="2520b-131">Win32 `VirtualQuery` dönüş değeri işlevidir arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="2520b-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="2520b-132">Daha fazla bilgi için Windows platformu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="2520b-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2520b-133">İşletim sisteminin uyarlamasını `VirtualQuery` kilitlenme tabi değildir ve tamamlanıncaya kadar rastgele iş parçacığı içinde kullanıcı kodu askıya çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2520b-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="2520b-134">Harika bu yöntem barındırılan bir sürümünü uygularken dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="2520b-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2520b-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2520b-135">Requirements</span></span>  
 <span data-ttu-id="2520b-136">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2520b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2520b-137">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2520b-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2520b-138">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2520b-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2520b-139">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2520b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2520b-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2520b-140">See Also</span></span>  
 [<span data-ttu-id="2520b-141">Ihostmemorymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="2520b-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)