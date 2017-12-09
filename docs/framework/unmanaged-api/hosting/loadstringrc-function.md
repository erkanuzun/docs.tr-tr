---
title: "LoadStringRC İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc93adf575af7f2803b20f24a3261a447772ffd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrc-function"></a><span data-ttu-id="792a2-102">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="792a2-102">LoadStringRC Function</span></span>
<span data-ttu-id="792a2-103">Bir HRESULT değeri, geçerli iş parçacığının varsayılan kültürü kullanarak hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="792a2-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="792a2-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="792a2-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="792a2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="792a2-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="792a2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="792a2-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="792a2-107">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="792a2-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="792a2-108">[out] İşlem başarıyla tamamlandıktan sonra hata iletisini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="792a2-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="792a2-109">[in] Hata iletisi arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="792a2-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="792a2-110">[in] Yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="792a2-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="792a2-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="792a2-111">Return Value</span></span>  
 <span data-ttu-id="792a2-112">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="792a2-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="792a2-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="792a2-113">Return code</span></span>|<span data-ttu-id="792a2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="792a2-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="792a2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="792a2-115">S_OK</span></span>|<span data-ttu-id="792a2-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="792a2-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="792a2-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="792a2-117">E_INVALIDARG</span></span>|<span data-ttu-id="792a2-118">`szBuffer`null veya `iMax` sıfır (0).</span><span class="sxs-lookup"><span data-stu-id="792a2-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="792a2-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="792a2-119">Remarks</span></span>  
 <span data-ttu-id="792a2-120">Yöntem başarıyla tamamlanmazsa `szBuffer` boş bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="792a2-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="792a2-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="792a2-121">Requirements</span></span>  
 <span data-ttu-id="792a2-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="792a2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="792a2-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="792a2-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="792a2-124">**Kitaplığı:** MSCorEE.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="792a2-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="792a2-125">MSCorEE.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="792a2-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="792a2-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="792a2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="792a2-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="792a2-127">See Also</span></span>  
 [<span data-ttu-id="792a2-128">LoadStringRCEx işlevi</span><span class="sxs-lookup"><span data-stu-id="792a2-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [<span data-ttu-id="792a2-129">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="792a2-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)