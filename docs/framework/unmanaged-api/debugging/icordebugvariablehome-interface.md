---
title: ICorDebugVariableHome arabirimi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae11cdbbdb0fa63d1b903d18aff133344fd17f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422539"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome arabirimi
Yerel bir değişken veya işlev bağımsız değişkeni temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetArgumentIndex Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|Bir işlev bağımsız değişkeni dizinini alır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|Bu içeren "ICorDebugCode" örneği alır `ICorDebugVariableHome` nesnesi.|  
|[GetLiveRange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|Bu değişken Canlı yerel aralığı alır.|  
|[GetLocationType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|Değişkenin yerel konum türünü alır.|  
|[GetOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|Uzaklık bir değişken için temel kasadan alır.|  
|[GetRegister Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|Konum türüne sahip bir değişken içeriyor kayıt alır `VLT_REGISTER`ve temel kaydetme konumu türüne sahip bir değişken için `VLT_REGISTER_RELATIVE`.|  
|[GetSlotIndex Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|Yönetilen yuvası dizin yerel değişken alır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod parçası kullanan [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) adlı nesne `pCode4`.  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugVariableHomeEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
