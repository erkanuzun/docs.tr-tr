---
title: "GetPropertyQualifierSet işlevi (yönetilmeyen API Başvurusu)"
description: "GetPropertyQualifierSet işlevi için bir özellik Ayarla niteleyicisi alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyQualifierSet
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyQualifierSet
helpviewer_keywords: GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd8abdb34f37273e469bdf5fc659b261bb2b9304
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyqualifierset-function"></a><span data-ttu-id="b0f92-103">GetPropertyQualifierSet işlevi</span><span class="sxs-lookup"><span data-stu-id="b0f92-103">GetPropertyQualifierSet function</span></span>
<span data-ttu-id="b0f92-104">Belirli bir özelliği için belirlenen niteleyicisi alır.</span><span class="sxs-lookup"><span data-stu-id="b0f92-104">Retrieves the qualifier set for a particular property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b0f92-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0f92-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
); 
```  

## <a name="parameters"></a><span data-ttu-id="b0f92-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0f92-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b0f92-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b0f92-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b0f92-108">[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="b0f92-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethod`  
<span data-ttu-id="b0f92-109">[in] Özellik adı.</span><span class="sxs-lookup"><span data-stu-id="b0f92-109">[in] The property  name.</span></span> <span data-ttu-id="b0f92-110">`wszProperty`Geçerli bir işaret etmelidir `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="b0f92-110">`wszProperty` must point to a valid `LPCWSTR`.</span></span> 

`ppQualSet`  
<span data-ttu-id="b0f92-111">[out] Özelliğin niteleyicileri erişmesini sağlayan arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b0f92-111">[out] Receives the interface pointer that allows access to the qualifiers of the property.</span></span> <span data-ttu-id="b0f92-112">`ppQualSet`olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="b0f92-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="b0f92-113">Bir hata oluştuğunda yeni bir nesne değil döndürülür ve işaretçi işaret edecek şekilde ayarlanır `null`.</span><span class="sxs-lookup"><span data-stu-id="b0f92-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="b0f92-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="b0f92-114">Return value</span></span>

<span data-ttu-id="b0f92-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="b0f92-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b0f92-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="b0f92-116">Constant</span></span>  |<span data-ttu-id="b0f92-117">Değer</span><span class="sxs-lookup"><span data-stu-id="b0f92-117">Value</span></span>  |<span data-ttu-id="b0f92-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0f92-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="b0f92-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b0f92-119">0x80041001</span></span> | <span data-ttu-id="b0f92-120">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b0f92-120">There has been a general failure.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="b0f92-121">0x80041002</span><span class="sxs-lookup"><span data-stu-id="b0f92-121">0x80041002</span></span> | <span data-ttu-id="b0f92-122">Belirtilen yöntem yok.</span><span class="sxs-lookup"><span data-stu-id="b0f92-122">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b0f92-123">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b0f92-123">0x80041006</span></span> | <span data-ttu-id="b0f92-124">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b0f92-124">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b0f92-125">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b0f92-125">0x80041008</span></span> | <span data-ttu-id="b0f92-126">Parametre `null`.</span><span class="sxs-lookup"><span data-stu-id="b0f92-126">A parameter is `null`.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | <span data-ttu-id="b0f92-127">0x80041030</span><span class="sxs-lookup"><span data-stu-id="b0f92-127">0x80041030</span></span> | <span data-ttu-id="b0f92-128">İşlev sistem özelliğinin niteleyicileri almaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="b0f92-128">The function attempts to get qualifiers of a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b0f92-129">0</span><span class="sxs-lookup"><span data-stu-id="b0f92-129">0</span></span> | <span data-ttu-id="b0f92-130">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="b0f92-130">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b0f92-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0f92-131">Remarks</span></span>

<span data-ttu-id="b0f92-132">Bu işlev çağrısı sarmalar [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b0f92-132">This function wraps a call to the [IWbemClassObject::GetPropertyQualifierSet](https://msdn.microsoft.com/library/aa391450(v=vs.85).aspx) method.</span></span> 

<span data-ttu-id="b0f92-133">Yalnızca geçerli nesne bir CIM sınıfı tanımı ise bu işlev için bir çağrı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b0f92-133">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="b0f92-134">Yöntem işleme için kullanılabilir olmadığından [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) CIM örneklerine noktası ponters.</span><span class="sxs-lookup"><span data-stu-id="b0f92-134">Method manipulation is not available for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponters that point to CIM instances.</span></span>

<span data-ttu-id="b0f92-135">Her yöntemin kendi niteleyicileri olabileceğinden [IWbemQualifierSet işaretçi](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) eklemek, düzenlemek veya silmek bu niteleyicileri çağıran olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0f92-135">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) lets the caller add, edit, or delete these qualifiers.</span></span>

<span data-ttu-id="b0f92-136">Sistem özellikleri hiçbir niteleyicileri bulunduğundan, işlevi döndürür `WBEM_E_SYSTEM_PROPERTY` elde çalışırsanız, bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) sistem özelliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0f92-136">Because system properties have no qualifiers, the function returns `WBEM_E_SYSTEM_PROPERTY` if you attempt to obtain a [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) pointer for a system property.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0f92-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0f92-137">Requirements</span></span>  
<span data-ttu-id="b0f92-138">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0f92-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0f92-139">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b0f92-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b0f92-140">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b0f92-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f92-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0f92-141">See also</span></span>  
[<span data-ttu-id="b0f92-142">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b0f92-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)