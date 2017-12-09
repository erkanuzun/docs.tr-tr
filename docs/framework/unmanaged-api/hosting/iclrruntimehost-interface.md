---
title: ICLRRuntimeHost Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost
helpviewer_keywords: ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type: apiref
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 332db2680ca23f34893a6c50c5311d73838bc1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="3ca03-102">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ca03-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="3ca03-103">Benzer işlevsellik sağlar [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) .NET Framework sürüm 1, aşağıdaki değişiklikleri ile sağlanan arabirim:</span><span class="sxs-lookup"><span data-stu-id="3ca03-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
-   <span data-ttu-id="3ca03-104">Eklenmesi [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) ana denetim arabirimi ayarlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3ca03-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
-   <span data-ttu-id="3ca03-105">Tarafından sağlanan bazı yöntemler atlandığını `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="3ca03-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ca03-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3ca03-106">Methods</span></span>  
  
|<span data-ttu-id="3ca03-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3ca03-107">Method</span></span>|<span data-ttu-id="3ca03-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ca03-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ca03-109">ExecuteApplication yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="3ca03-110">ClickOnce dağıtım senaryolarında bildirimi tabanlı yeni bir etki alanına etkinleştirilmesi için uygulamayı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ca03-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="3ca03-111">Executeınappdomain yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="3ca03-112">Belirtir <xref:System.AppDomain> belirtilen yönetilen kod yürütmek üzere.</span><span class="sxs-lookup"><span data-stu-id="3ca03-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="3ca03-113">Executeındefaultappdomain yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="3ca03-114">Belirtilen derlemedeki belirtilen türe ait belirtilen yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="3ca03-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="3ca03-115">GetCLRControl yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="3ca03-116">Arabirim işaretçisi türü alır [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) konakları ortak dil çalışma zamanı (CLR) yönlerini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ca03-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="3ca03-117">Getcurrentappdomainıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="3ca03-118">Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="3ca03-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="3ca03-119">SetHostControl yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="3ca03-120">Ana bilgisayar denetim arabirimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3ca03-120">Sets the host control interface.</span></span> <span data-ttu-id="3ca03-121">Çağırmalısınız `SetHostControl` çağırmadan önce `Start`.</span><span class="sxs-lookup"><span data-stu-id="3ca03-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="3ca03-122">Start yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="3ca03-123">CLR bir işlem başlatır.</span><span class="sxs-lookup"><span data-stu-id="3ca03-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="3ca03-124">Stop yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="3ca03-125">Kod yürütmeyi çalışma zamanı tarafından durdurur.</span><span class="sxs-lookup"><span data-stu-id="3ca03-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="3ca03-126">UnloadAppDomain yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ca03-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="3ca03-127">Bellekten <xref:System.AppDomain> belirtilen sayısal tanımlayıcı karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3ca03-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ca03-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ca03-128">Remarks</span></span>  
 <span data-ttu-id="3ca03-129">İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], kullanın [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) gösteren bir işaretçi almak için arabirimi [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) arabirim ve ardından arama [Iclrruntimeınfo::getınterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) gösteren bir işaretçi almak için yöntemi `ICLRRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="3ca03-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="3ca03-130">Önceki sürümlerde .NET Framework'ün, ana bilgisayar için bir işaretçi alır bir `ICLRRuntimeHost` çağırarak örneği [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="3ca03-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="3ca03-131">Herhangi bir .NET Framework 2.0 sürümünde sağlanan teknolojileri uygulamaları sağlamak için kullanmalısınız `ICLRRuntimeHost` yerine `ICorRuntimeHost`.</span><span class="sxs-lookup"><span data-stu-id="3ca03-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ca03-132">Çağırmayın [Başlat](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) bildirimi tabanlı bir uygulama etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3ca03-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="3ca03-133">Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3ca03-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ca03-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ca03-134">Requirements</span></span>  
 <span data-ttu-id="3ca03-135">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ca03-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ca03-136">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ca03-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ca03-137">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3ca03-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ca03-138">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ca03-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca03-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ca03-139">See Also</span></span>  
 [<span data-ttu-id="3ca03-140">CorBindToCurrentRuntime işlevi</span><span class="sxs-lookup"><span data-stu-id="3ca03-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="3ca03-141">CorBindToRuntimeEx işlevi</span><span class="sxs-lookup"><span data-stu-id="3ca03-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="3ca03-142">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ca03-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3ca03-143">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ca03-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="3ca03-144">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3ca03-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="3ca03-145">Clrruntimehost ortak sınıfı</span><span class="sxs-lookup"><span data-stu-id="3ca03-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)