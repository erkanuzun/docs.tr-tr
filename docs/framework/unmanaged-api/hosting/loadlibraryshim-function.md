---
title: "LoadLibraryShim İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c56f5a3576c505fd7b7d514e3f2d038e7f8f3ecc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="loadlibraryshim-function"></a><span data-ttu-id="735e4-102">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="735e4-102">LoadLibraryShim Function</span></span>
<span data-ttu-id="735e4-103">.NET Framework yeniden dağıtılabilir paketinde bulunan bir DLL belirtilen sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="735e4-103">Loads a specified version of a DLL that is included in the .NET Framework redistributable package.</span></span>  
  
 <span data-ttu-id="735e4-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="735e4-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="735e4-105">Kullanım [Iclrruntimeınfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="735e4-105">Use the [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="735e4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="735e4-106">Syntax</span></span>  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="735e4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="735e4-107">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="735e4-108">[in] .NET Framework Kitaplığı'ndan yüklenecek DLL adını temsil eden bir sıfır ile sonlandırılan bir dize.</span><span class="sxs-lookup"><span data-stu-id="735e4-108">[in] A zero-terminated string that represents the name of the DLL to be loaded from the .NET Framework library.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="735e4-109">[in] Yüklenecek DLL sürümü temsil eden bir sıfır ile sonlandırılan bir dize.</span><span class="sxs-lookup"><span data-stu-id="735e4-109">[in] A zero-terminated string that represents the version of the DLL to be loaded.</span></span> <span data-ttu-id="735e4-110">Varsa `szVersion` null, yükleme sürüm 4'dan küçük belirtilen DLL Dosyasının en son sürümü için seçtiğiniz sürüm değil.</span><span class="sxs-lookup"><span data-stu-id="735e4-110">If `szVersion` is null, the version selected for loading is the latest version of the specified DLL that is less than version 4.</span></span> <span data-ttu-id="735e4-111">Diğer bir deyişle, tüm sürümleri eşit veya bundan büyük sürüm 4 sayılır `szVersion` null, ve sürüm 4 değerinden küçük bir sürümü yüklüyse, DLL yüklemek başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="735e4-111">That is, all versions equal to or greater than version 4 are ignored if `szVersion` is null, and if no version less than version 4 is installed, the DLL fails to load.</span></span> <span data-ttu-id="735e4-112">Bu yüklemesini sağlamaktır [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] önceden var olan uygulamaları veya bileşenleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="735e4-112">This is to ensure that installation of the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] does not affect pre-existing applications or components.</span></span> <span data-ttu-id="735e4-113">Girişine bakın [işlem dışı SxS ve geçiş Hızlı Başlangıç](http://go.microsoft.com/fwlink/?LinkId=200329) CLR ekip blogu içinde.</span><span class="sxs-lookup"><span data-stu-id="735e4-113">See the entry [In-Proc SxS and Migration Quick Start](http://go.microsoft.com/fwlink/?LinkId=200329) in the CLR team blog.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="735e4-114">Daha sonraki kullanımlar için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="735e4-114">Reserved for future use.</span></span>  
  
 `phModDll`  
 <span data-ttu-id="735e4-115">[out] Modül işleyicisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="735e4-115">[out] A pointer to the handle of the module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="735e4-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="735e4-116">Return Value</span></span>  
 <span data-ttu-id="735e4-117">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="735e4-117">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="735e4-118">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="735e4-118">Return code</span></span>|<span data-ttu-id="735e4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="735e4-119">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="735e4-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="735e4-120">S_OK</span></span>|<span data-ttu-id="735e4-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="735e4-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="735e4-122">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="735e4-122">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="735e4-123">Yükleme `szDllName` ortak dil çalışma zamanı (CLR) ve CLR'nin gereken sürümü yüklenemiyor yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="735e4-123">Loading `szDllName` requires loading the common language runtime (CLR), and the necessary version of the CLR cannot be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="735e4-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="735e4-124">Remarks</span></span>  
 <span data-ttu-id="735e4-125">Bu işlev, .NET Framework yeniden dağıtılabilir paketinin içerdiği DLL'leri yüklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="735e4-125">This function is used to load DLLs that are included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="735e4-126">Kullanıcı tarafından oluşturulan DLL'leri yüklemez.</span><span class="sxs-lookup"><span data-stu-id="735e4-126">It does not load user-generated DLLs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="735e4-127">.NET Framework sürüm 2.0 ile başlayarak, Fusion.dll yüklenirken yüklenecek CLR neden olur.</span><span class="sxs-lookup"><span data-stu-id="735e4-127">Beginning with the .NET Framework version 2.0, loading Fusion.dll causes the CLR to be loaded.</span></span> <span data-ttu-id="735e4-128">Bunun nedeni, Fusion.dll işlevlerde şimdi uygulamaları çalışma zamanı tarafından sağlanan sarmalayıcıları olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="735e4-128">This is because the functions in Fusion.dll are now wrappers whose implementations are provided by the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="735e4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="735e4-129">Requirements</span></span>  
 <span data-ttu-id="735e4-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="735e4-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="735e4-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="735e4-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="735e4-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="735e4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="735e4-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="735e4-133">See Also</span></span>  
 [<span data-ttu-id="735e4-134">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="735e4-134">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)