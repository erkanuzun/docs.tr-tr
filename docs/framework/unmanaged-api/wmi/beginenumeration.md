---
title: "BeginEnumeration işlevi (yönetilmeyen API Başvurusu)"
description: "BeginEnumeration işlevi bir numaralandırıcı numaralandırması başlangıcına sıfırlar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginEnumeration
helpviewer_keywords: BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12a742774bff22030bdfaaa34e431059e016a4bf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="4c19d-103">BeginEnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="4c19d-103">BeginEnumeration function</span></span>
<span data-ttu-id="4c19d-104">Bir numaralandırıcı geri numaralandırması başlangıç durumuna sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="4c19d-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4c19d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c19d-105">Syntax</span></span>  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="4c19d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4c19d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4c19d-107">[in] Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="4c19d-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="4c19d-108">`ptr`[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.</span><span class="sxs-lookup"><span data-stu-id="4c19d-108">`ptr` [in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="4c19d-109">[in] Bayrakları veya açıklanan değerlerinin Bitsel bir birleşimi [açıklamalar](#remarks) numaralandırmada bulunan özellikler denetimleri bölümü.</span><span class="sxs-lookup"><span data-stu-id="4c19d-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c19d-110">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="4c19d-110">Return value</span></span>

<span data-ttu-id="4c19d-111">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="4c19d-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4c19d-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="4c19d-112">Constant</span></span>  |<span data-ttu-id="4c19d-113">Değer</span><span class="sxs-lookup"><span data-stu-id="4c19d-113">Value</span></span>  |<span data-ttu-id="4c19d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c19d-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4c19d-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4c19d-115">0x80041008</span></span> | <span data-ttu-id="4c19d-116">Bayrakları birleşimi `lEnumFlags` geçersiz veya geçersiz bir bağımsız değişken belirtildi.</span><span class="sxs-lookup"><span data-stu-id="4c19d-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="4c19d-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="4c19d-117">0x8004101d</span></span> | <span data-ttu-id="4c19d-118">İkinci çağrı `BeginEnumeration` olmadan müdahalede bulunan bir çağrı yapıldı [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4c19d-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4c19d-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4c19d-119">0x80041006</span></span> | <span data-ttu-id="4c19d-120">Yeni bir numaralandırma başlatmak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="4c19d-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4c19d-121">0</span><span class="sxs-lookup"><span data-stu-id="4c19d-121">0</span></span> | <span data-ttu-id="4c19d-122">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="4c19d-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4c19d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c19d-123">Remarks</span></span>

<span data-ttu-id="4c19d-124">Bu işlev çağrısı sarmalar [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4c19d-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="4c19d-125">Olarak geçirilen bayraklar `lEnumFlags` bağımsız değişkeni tanımlanmış *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="4c19d-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="4c19d-126">Diğer bir gruptaki tüm bayrağıyla her grubundan bir bayrak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c19d-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="4c19d-127">Ancak, aynı gruptan bayrakları karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="4c19d-127">However, flags from the same group are mutually exclusive.</span></span> 

<span data-ttu-id="4c19d-128">**Grup 1**</span><span class="sxs-lookup"><span data-stu-id="4c19d-128">**Group 1**</span></span>

|<span data-ttu-id="4c19d-129">Sabit</span><span class="sxs-lookup"><span data-stu-id="4c19d-129">Constant</span></span>  |<span data-ttu-id="4c19d-130">Değer</span><span class="sxs-lookup"><span data-stu-id="4c19d-130">Value</span></span>  |<span data-ttu-id="4c19d-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c19d-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="4c19d-132">0x4</span><span class="sxs-lookup"><span data-stu-id="4c19d-132">0x4</span></span> | <span data-ttu-id="4c19d-133">Yalnızca anahtar oluşturan özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4c19d-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="4c19d-134">0x8</span><span class="sxs-lookup"><span data-stu-id="4c19d-134">0x8</span></span> | <span data-ttu-id="4c19d-135">Yalnızca nesne başvuruları özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="4c19d-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="4c19d-136">**Grubu 2**</span><span class="sxs-lookup"><span data-stu-id="4c19d-136">**Group 2**</span></span>

<span data-ttu-id="4c19d-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="4c19d-137">Constant</span></span>  |<span data-ttu-id="4c19d-138">Değer</span><span class="sxs-lookup"><span data-stu-id="4c19d-138">Value</span></span>  |<span data-ttu-id="4c19d-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c19d-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="4c19d-140">0x30</span><span class="sxs-lookup"><span data-stu-id="4c19d-140">0x30</span></span> | <span data-ttu-id="4c19d-141">Sistem özellikleri yalnızca numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="4c19d-142">0x40</span><span class="sxs-lookup"><span data-stu-id="4c19d-142">0x40</span></span> | <span data-ttu-id="4c19d-143">Yerel ve yayılan özellikler içerir, ancak Sistem özellikleri numaralandırma içinden çıkarın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="4c19d-144">Sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="4c19d-144">For classes:</span></span>

<span data-ttu-id="4c19d-145">Sabit</span><span class="sxs-lookup"><span data-stu-id="4c19d-145">Constant</span></span>  |<span data-ttu-id="4c19d-146">Değer</span><span class="sxs-lookup"><span data-stu-id="4c19d-146">Value</span></span>  |<span data-ttu-id="4c19d-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c19d-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="4c19d-148">0x100</span><span class="sxs-lookup"><span data-stu-id="4c19d-148">0x100</span></span> | <span data-ttu-id="4c19d-149">Sınıf tanımı'nda geçersiz kılınan özellikleri numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="4c19d-150">0x100</span><span class="sxs-lookup"><span data-stu-id="4c19d-150">0x100</span></span> | <span data-ttu-id="4c19d-151">Geçerli sınıf tanımında geçersiz kılınan özellikleri ve yeni özellikleri sınıfında tanımlanan numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="4c19d-152">0x300</span><span class="sxs-lookup"><span data-stu-id="4c19d-152">0x300</span></span> | <span data-ttu-id="4c19d-153">A karşı uygulamak için (yerine bir bayrak) maske bir `lEnumFlags` ya da denetlemek için değer `WBEM_FLAG_CLASS_OVERRIDES_ONLY` veya `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4c19d-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="4c19d-154">0x10</span><span class="sxs-lookup"><span data-stu-id="4c19d-154">0x10</span></span> | <span data-ttu-id="4c19d-155">Tanımlanan veya sınıfında değiştirilen özellikler numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="4c19d-156">0x20</span><span class="sxs-lookup"><span data-stu-id="4c19d-156">0x20</span></span> | <span data-ttu-id="4c19d-157">Temel sınıflardan devralınır özellikler numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="4c19d-158">İçin örnekleri:</span><span class="sxs-lookup"><span data-stu-id="4c19d-158">For instances:</span></span>

<span data-ttu-id="4c19d-159">Sabit</span><span class="sxs-lookup"><span data-stu-id="4c19d-159">Constant</span></span>  |<span data-ttu-id="4c19d-160">Değer</span><span class="sxs-lookup"><span data-stu-id="4c19d-160">Value</span></span>  |<span data-ttu-id="4c19d-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c19d-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="4c19d-162">0x10</span><span class="sxs-lookup"><span data-stu-id="4c19d-162">0x10</span></span> | <span data-ttu-id="4c19d-163">Tanımlanan veya sınıfında değiştirilen özellikler numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="4c19d-164">0x20</span><span class="sxs-lookup"><span data-stu-id="4c19d-164">0x20</span></span> | <span data-ttu-id="4c19d-165">Temel sınıflardan devralınır özellikler numaralandırma sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="4c19d-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |


## <a name="requirements"></a><span data-ttu-id="4c19d-166">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4c19d-166">Requirements</span></span>  
 <span data-ttu-id="4c19d-167">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c19d-167">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c19d-168">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4c19d-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4c19d-169">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c19d-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c19d-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c19d-170">See also</span></span>  
[<span data-ttu-id="4c19d-171">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4c19d-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)