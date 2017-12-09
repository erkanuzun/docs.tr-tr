---
title: "CreateICeeFileGen İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9162da1b48348da745f8616b5cc643bf3dee97fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="8939c-102">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="8939c-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="8939c-103">Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8939c-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="8939c-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8939c-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8939c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8939c-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8939c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8939c-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="8939c-107">[out] Yeni bir adresini gösteren bir işaretçi `ICeeFileGen` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8939c-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8939c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8939c-108">Return Value</span></span>  
 <span data-ttu-id="8939c-109">Bu yöntem standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8939c-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8939c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8939c-110">Remarks</span></span>  
 <span data-ttu-id="8939c-111">`ICeeFileGen` Nesnesi ortak dil çalışma zamanı (CLR) taşınabilir yürütülebilir (PE) dosyalarını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8939c-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="8939c-112">Çağrı [Destroyıceefilegen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) yok etmek için işlevi `ICeeFileGen` bittiğinde nesne.</span><span class="sxs-lookup"><span data-stu-id="8939c-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8939c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8939c-113">Requirements</span></span>  
 <span data-ttu-id="8939c-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8939c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8939c-115">**Başlık:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="8939c-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="8939c-116">**Kitaplığı:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="8939c-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="8939c-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8939c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8939c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8939c-118">See Also</span></span>  
 [<span data-ttu-id="8939c-119">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="8939c-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)