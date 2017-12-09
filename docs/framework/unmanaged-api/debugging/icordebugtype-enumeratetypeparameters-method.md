---
title: "ICorDebugType::EnumerateTypeParameters Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9dd00b0a5f28821112621a54c97551c71e1acc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="e8d53-102">ICorDebugType::EnumerateTypeParameters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8d53-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="e8d53-103">Arabirim işaretçisi içeren bir Icordebugtypeenum alır <xref:System.Type> bu Icordebugtype tarafından başvurulan sınıfının parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e8d53-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8d53-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8d53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8d53-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="e8d53-106">[out] Adresine bir işaretçi bir `ICorDebugTypeEnum` türünün parametrelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e8d53-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8d53-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8d53-107">Remarks</span></span>  
 <span data-ttu-id="e8d53-108">Kullanabileceğiniz `EnumerateTypeParameters` CorElementType değeri tarafından döndürülürse [Icordebugtype::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) olan ELEMENT_TYPE_CLASS ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_ PTR veya ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="e8d53-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="e8d53-109">Parametreler ve bunların sırası sayısı türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="e8d53-109">The number of parameters and their order depends on the type:</span></span>  
  
-   <span data-ttu-id="e8d53-110">ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE: içinde yer alan türü parametre sayısı `ICorDebugTypeEnum` bu yöntem döndürdüğünü, karşılık gelen sınıf için biçimsel türündeki parametrelerin sayısı bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8d53-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="e8d53-111">Örneğin, tür ise `class Dict<String,int32>`, sonra `EnumerateTypeParameters` döndürür bir `ICorDebugTypeEnum` temsil eden nesneleri içeren `String` ve `int32` dizisindeki.</span><span class="sxs-lookup"><span data-stu-id="e8d53-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
-   <span data-ttu-id="e8d53-112">ELEMENT_TYPE_FNPTR: Tür parametreleri içinde yer alan sayısını `ICorDebugTypeEnum` bir işlev tarafından kabul bağımsız değişken sayısı büyük olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e8d53-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="e8d53-113">İçinde yer alan ilk tür parametresi `ICorDebugTypeEnum` işlevi için dönüş türü ve sonraki tür parametreleri işlevin parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="e8d53-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
-   <span data-ttu-id="e8d53-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR: bir tür parametresi döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="e8d53-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="e8d53-115">Örneğin, bir dizi türü gibi türündeyse `int32[]`,`EnumerateTypeParameters` döndürülecek bir `ICorDebugTypeEnum` içeren bir nesneyi temsil eden `int32`.</span><span class="sxs-lookup"><span data-stu-id="e8d53-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d53-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8d53-116">Requirements</span></span>  
 <span data-ttu-id="e8d53-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8d53-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8d53-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8d53-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8d53-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8d53-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8d53-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8d53-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>