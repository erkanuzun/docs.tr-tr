---
title: "ICLRDataTarget2::FreeVirtual Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.FreeVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1619e9eb02eec1985c3c550626ef955162d1b984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="08314-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08314-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="08314-103">Hedef işlemin adres alanında daha önce ayrılan belleği boşaltmak için ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="08314-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08314-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08314-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08314-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08314-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="08314-106">[in] A `CLRDATA_ADDRESS` boşaltılacak belleğin başlangıç adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="08314-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="08314-107">[in] Boşaltılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="08314-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="08314-108">[in] Bellek boşaltma kontrol bayraklar.</span><span class="sxs-lookup"><span data-stu-id="08314-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="08314-109">Win32 bkz `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="08314-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08314-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08314-110">Remarks</span></span>  
 <span data-ttu-id="08314-111">`FreeVirtual` Yöntemi Win32 için mantıksal bir kapsayıcı olarak hizmet veren `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="08314-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="08314-112">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="08314-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08314-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08314-113">Requirements</span></span>  
 <span data-ttu-id="08314-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08314-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08314-115">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="08314-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="08314-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08314-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08314-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08314-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08314-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08314-118">See Also</span></span>  
 [<span data-ttu-id="08314-119">Iclrdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="08314-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="08314-120">AllocVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="08314-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)