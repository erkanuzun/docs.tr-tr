---
title: "PutClassWmi işlevi (yönetilmeyen API Başvurusu)"
description: "PutClassWmi işlevi yeni bir sınıf oluşturur veya mevcut bir güncelleştirir."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dda7dc4d71b65c8b031f2dca459bd282eef1f270
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="putclasswmi-function"></a><span data-ttu-id="5071b-103">PutClassWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="5071b-103">PutClassWmi function</span></span>
<span data-ttu-id="5071b-104">Yeni bir sınıf oluşturur veya mevcut bir güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="5071b-104">Creates a new class or updates an existing one.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5071b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5071b-105">Syntax</span></span>  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a><span data-ttu-id="5071b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5071b-106">Parameters</span></span>

`pObject`    
<span data-ttu-id="5071b-107">[in] Geçerli bir sınıf tanımı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5071b-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="5071b-108">Gereken tüm özellik değerlerini ile doğru şekilde yeniden başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5071b-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`   
<span data-ttu-id="5071b-109">[in] Bu işlev davranışını etkileyen bayrak birleşimi.</span><span class="sxs-lookup"><span data-stu-id="5071b-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="5071b-110">Aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5071b-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="5071b-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="5071b-111">Constant</span></span>  |<span data-ttu-id="5071b-112">Değer</span><span class="sxs-lookup"><span data-stu-id="5071b-112">Value</span></span>  |<span data-ttu-id="5071b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5071b-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="5071b-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="5071b-114">0x20000</span></span> | <span data-ttu-id="5071b-115">Ayarlama, WMI herhangi niteleyicileri değiştirilmiş özellik ile depolamaz</span><span class="sxs-lookup"><span data-stu-id="5071b-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> </br> <span data-ttu-id="5071b-116">Değilse kümesi varsayılır Bu nesne yerelleştirilmemiş ve tüm niteleyiciler storedwith olduğundan bu örnek.</span><span class="sxs-lookup"><span data-stu-id="5071b-116">If not set, it is assumed that this object is not localized, and all qualifiers are storedwith this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="5071b-117">0</span><span class="sxs-lookup"><span data-stu-id="5071b-117">0</span></span> | <span data-ttu-id="5071b-118">Bunu yok, veya zaten varsa üzerine sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5071b-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="5071b-119">1.</span><span class="sxs-lookup"><span data-stu-id="5071b-119">1</span></span> | <span data-ttu-id="5071b-120">Sınıf güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="5071b-120">Update the class.</span></span> <span data-ttu-id="5071b-121">Sınıfı, çağrı başarılı olması mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5071b-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="5071b-122">2</span><span class="sxs-lookup"><span data-stu-id="5071b-122">2</span></span> | <span data-ttu-id="5071b-123">Sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5071b-123">Create the class.</span></span> <span data-ttu-id="5071b-124">Sınıf zaten varsa çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5071b-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="5071b-125">0x10</span><span class="sxs-lookup"><span data-stu-id="5071b-125">0x10</span></span> | <span data-ttu-id="5071b-126">Bayrağı yarı zaman uyumlu bir çağrı neden olur.</span><span class="sxs-lookup"><span data-stu-id="5071b-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="5071b-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="5071b-127">0x10000</span></span> | <span data-ttu-id="5071b-128">İtme sağlayıcıları, bu bayrak belirtmelisiniz, çağrılırken `PutClassWmi` Bu sınıf değiştiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="5071b-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="5071b-129">0</span><span class="sxs-lookup"><span data-stu-id="5071b-129">0</span></span> | <span data-ttu-id="5071b-130">Türetilmiş sınıfları ve bu sınıfın hiçbir örneği varsa güncelleştirilmesi için bir sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="5071b-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="5071b-131">Değişiklik yalnızca açıklama niteleyici gibi önemli niteleyicileri istiyorsanız tüm durumlarda da güncelleştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5071b-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="5071b-132">Sınıf örnekleri olan veya önemli niteleyicileri değişikliklerdir güncelleştirme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="5071b-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="5071b-133">0x20</span><span class="sxs-lookup"><span data-stu-id="5071b-133">0x20</span></span> | <span data-ttu-id="5071b-134">Olsa bile alt sınıflar değişiklik alt sınıflarla çakışmaları neden olmaz sürece sınıfların güncelleştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5071b-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="5071b-135">Örneğin, bu bayrak herhangi bir alt sınıfı önceden olarak belirtilmeyen temel sınıf eklemek yeni bir özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5071b-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="5071b-136">Sınıf örneği varsa, güncelleştirme başarısız.</span><span class="sxs-lookup"><span data-stu-id="5071b-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="5071b-137">0x40</span><span class="sxs-lookup"><span data-stu-id="5071b-137">0x40</span></span> | <span data-ttu-id="5071b-138">Çakışan alt sınıflar bulunduğunda sınıfların güncelleştirmeleri zorlar.</span><span class="sxs-lookup"><span data-stu-id="5071b-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="5071b-139">Örneğin, bu bayrak, sınıf niteleyici bir alt sınıfında tanımlanır ve olduğu bir varolan thte ile çakışıyor aynı niteleyici eklemek temel sınıf çalışırsa bir güncelleştirme zorlar.</span><span class="sxs-lookup"><span data-stu-id="5071b-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with thte existing one.</span></span> <span data-ttu-id="5071b-140">Zorlama modunda TIS çakışma alt sınıf çakışan niteleyicisinde silerek çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="5071b-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`  
<span data-ttu-id="5071b-141">[in] Bu değer genellikle `null`.</span><span class="sxs-lookup"><span data-stu-id="5071b-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="5071b-142">Aksi takdirde, gösteren bir işaretçidir bir [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) istenen sınıfları sağlayarak sağlayıcı tarafından kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="5071b-142">Otherwise, it is a pointer to an [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppCallResult`  
<span data-ttu-id="5071b-143">[out] Varsa `null`, bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5071b-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="5071b-144">Varsa `lFlags` içeren `WBEM_FLAG_RETURN_IMMEDIATELY`, işlevi ile hemen döndürür `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="5071b-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="5071b-145">`ppCallResult` Parametre alan yeni bir işaretçi [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5071b-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="5071b-146">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5071b-146">Return value</span></span>

<span data-ttu-id="5071b-147">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5071b-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5071b-148">Sabit</span><span class="sxs-lookup"><span data-stu-id="5071b-148">Constant</span></span>  |<span data-ttu-id="5071b-149">Değer</span><span class="sxs-lookup"><span data-stu-id="5071b-149">Value</span></span>  |<span data-ttu-id="5071b-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5071b-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="5071b-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="5071b-151">0x80041003</span></span> | <span data-ttu-id="5071b-152">Kullanıcı oluşturma veya sınıfları değiştirme izni yok.</span><span class="sxs-lookup"><span data-stu-id="5071b-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="5071b-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5071b-153">0x80041001</span></span> | <span data-ttu-id="5071b-154">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5071b-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="5071b-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="5071b-155">0x80041010</span></span> | <span data-ttu-id="5071b-156">Belirtilen sınıf geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5071b-156">The specified class is not valid.</span></span> <span data-ttu-id="5071b-157">Genellikle, bu belirten `pObject` örneği nesneyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5071b-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5071b-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5071b-158">0x80041008</span></span> | <span data-ttu-id="5071b-159">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5071b-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="5071b-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="5071b-160">0x80041016</span></span> | <span data-ttu-id="5071b-161">Belirtilen sınıf adı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="5071b-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="5071b-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="5071b-162">0x80041025</span></span> | <span data-ttu-id="5071b-163">Bir alt sınıfı kılacak bir değişiklik yapılmaya çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="5071b-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="5071b-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="5071b-164">0x80041019</span></span> | <span data-ttu-id="5071b-165">`WBEM_FLAG_CREATE_ONLY` Bayrağı belirtildi, ancak sınıf zaten mevcut.</span><span class="sxs-lookup"><span data-stu-id="5071b-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="5071b-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="5071b-166">0x80041002</span></span> | <span data-ttu-id="5071b-167">`WBEM_FLAG_UPDATE_ONLY`Belirtilen `lFlags`, ve sınıfı bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="5071b-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="5071b-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="5071b-168">0x80041020</span></span> | <span data-ttu-id="5071b-169">Tüm sınıflar için gerekli özellikleri ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="5071b-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5071b-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5071b-170">0x80041006</span></span> | <span data-ttu-id="5071b-171">İşlemi tamamlamak yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="5071b-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="5071b-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="5071b-172">0x80041033</span></span> | <span data-ttu-id="5071b-173">WMI, büyük olasılıkla durduruldu ve yeniden başlatma.</span><span class="sxs-lookup"><span data-stu-id="5071b-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="5071b-174">Çağrı [ConnectServerWmi](connectserverwmi.md) yeniden.</span><span class="sxs-lookup"><span data-stu-id="5071b-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="5071b-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="5071b-175">0x80041015</span></span> | <span data-ttu-id="5071b-176">Geçerli işlem ile WMI arasındaki uzak yordam çağrısı (RPC) bağlantı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5071b-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5071b-177">0</span><span class="sxs-lookup"><span data-stu-id="5071b-177">0</span></span> | <span data-ttu-id="5071b-178">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5071b-178">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5071b-179">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5071b-179">Remarks</span></span>

<span data-ttu-id="5071b-180">Bu işlev çağrısı sarmalar [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5071b-180">This function wraps a call to the [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="5071b-181">Kullanıcı sınıfları başlayamaz ya da bir alt çizgi chacater ile bitemez adlarla oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="5071b-181">The user may not create classes with names that begin or end with an underscore chacater</span></span>

<span data-ttu-id="5071b-182">İşlev çağrısı başarısız olursa, çağırarak ek hata bilgileri elde edebileceğiniz [Geterrorınfo](geterrorinfo.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="5071b-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5071b-183">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5071b-183">Requirements</span></span>  
 <span data-ttu-id="5071b-184">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5071b-184">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5071b-185">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5071b-185">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5071b-186">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5071b-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5071b-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5071b-187">See also</span></span>  
[<span data-ttu-id="5071b-188">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5071b-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)