---
title: ICorProfilerInfo4::GetFunctionFromIP2 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4fe3eec4940b57001b7734c581076388f8ba0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456992"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 Metodu
Yönetilen kod yönerge işaretçisi bir işlev JIT yeniden derlenmesi sürümüne eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ip`  
 [in] Yönetilen kod yönerge işaretçisi.  
  
 `pFunctionId`  
 [out] İşlev kimliği.  
  
 `pReJitId`  
 [out] İşlevin JIT yeniden derlenmesi sürüm kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetFunctionFromIP2` benzer `GetFunctionFromIP`dışında belirtilen IP adresi içeren işlevinin işlev kimliği yerine JIT yeniden derlenmesi Kimliğini alır.  
  
> [!NOTE]
>  `GetFunctionFromIP2` Çöp toplama, ancak tetikleyebilir `GetFunctionFromIP` almayacak.  Daha fazla bilgi için bkz: [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
