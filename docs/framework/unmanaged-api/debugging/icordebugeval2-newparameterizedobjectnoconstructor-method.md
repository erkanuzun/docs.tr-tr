---
title: "ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94cf9e0596e8e5cbd59da319247ced6780d0accb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="77fc5-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77fc5-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="77fc5-103">Belirtilen sınıfının yeni bir parametreli türü nesne Oluşturucusu yöntemini çağırmak çalışırken olmadan başlatır.</span><span class="sxs-lookup"><span data-stu-id="77fc5-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77fc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77fc5-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77fc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77fc5-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="77fc5-106">[in] Bir işaretçi Icordebugclass nesneye örneğinin oluşturulması için nesnenin sınıfını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="77fc5-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="77fc5-107">[in] Tür bağımsız değişkenleri sayıda geçirildi.</span><span class="sxs-lookup"><span data-stu-id="77fc5-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="77fc5-108">[in] Her biri noktalarını oluşturulmasını nesne için bir tür bağımsız değişkeni temsil eden bir Icordebugtype nesnesi için bir dizi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="77fc5-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77fc5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77fc5-109">Remarks</span></span>  
 <span data-ttu-id="77fc5-110">`NewParameterizedObjectNoConstructor` Yöntemi yanlış sayıda tür bağımsız değişkeni, başarısız olur veya tür bağımsız değişkeni yanlış tür geçirildi.</span><span class="sxs-lookup"><span data-stu-id="77fc5-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77fc5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77fc5-111">Requirements</span></span>  
 <span data-ttu-id="77fc5-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77fc5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77fc5-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77fc5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77fc5-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77fc5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77fc5-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77fc5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>