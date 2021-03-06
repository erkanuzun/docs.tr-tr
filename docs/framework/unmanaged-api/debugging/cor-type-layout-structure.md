---
title: COR_TYPE_LAYOUT Yapısı
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b88a7b0672e15097c60afbe069ce5b78bd5c38d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408150"
---
# <a name="cortypelayout-structure"></a>COR_TYPE_LAYOUT Yapısı
Bir nesnenin bellekte Düzen hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`parentID`|Bu tür için üst tür tanımlayıcısı. Bu NULL tür kimliği olacaktır (token1 = 0, token2 = 0) için türü kimliği karşılık geliyorsa <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|Bu tür bir nesne temel boyutu. Bu değişken olmayan boyutlu nesneler için toplam boyutudur.|  
|`numFields`|Bu tür nesneler dahil alanları sayısı.|  
|`boxOffset`|Bu tür Kutulu, nesnenin alanlarının başlangıç uzaklığı. Bu alan yalnızca ilkel ve yapıları gibi değer türleri için geçerli değil.|  
|`type`|Bu tür ait olduğu CorElementType.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `numFields` , sıfırdan büyük çağırabilirsiniz [Icordebugprocess5::gettypefields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) bu tür alanları hakkında bilgi edinmek için yöntem. Varsa `type` olan `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, veya `ELEMENT_TYPE_SZARRAY`, bu tür nesneler boyutunu değişkendir ve geçirebilirsiniz [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) için yapı [Icordebugprocess5::getarraylayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
