---
title: "LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPOVERLAPPED_COMPLETION_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords: LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d50f2058796d4c5c900474cdcbe71d8a5a911ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="6e0e1-102">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6e0e1-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="6e0e1-103">İşaret eden bir çakışan olduğunda ana bilgisayar bildiren bir işlev (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="6e0e1-104">Bu işlev işaretçisi kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e0e1-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e0e1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e0e1-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e0e1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e0e1-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="6e0e1-107">[in] Bir hata kodu cihaz kapattıysanız olan bir değer; Aksi takdirde, bu değer sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="6e0e1-108">Bir aygıt kapatma neden olur. bekleyen g/ç aygıtı için hemen tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="6e0e1-109">[in] G/ç işlemi tarafından aktarılan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="6e0e1-110">[in] G/ç isteği tamamlamak için kullanılacak bilgileri içeren bir yapı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e0e1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e0e1-111">Remarks</span></span>  
 <span data-ttu-id="6e0e1-112">İşleve `LPOVERLAPPED_COMPLETION_ROUTINE` noktaları bir geri çağırma işlevidir ve barındırma uygulama yazıcı tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="6e0e1-113">Tamamlanan g/ç isteği işlemek için ana geri çağırma işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e0e1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e0e1-114">Requirements</span></span>  
 <span data-ttu-id="6e0e1-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e0e1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e0e1-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e0e1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e0e1-117">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="6e0e1-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="6e0e1-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e0e1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e0e1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-119">See Also</span></span>  
 [<span data-ttu-id="6e0e1-120">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="6e0e1-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)