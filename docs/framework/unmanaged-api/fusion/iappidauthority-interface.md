---
title: IAppIdAuthority Arabirimi
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819afec2c448e5f396ab54e2dde00c01da310b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433756"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority Arabirimi
Oluşturma ve uygulama kimlikleri ve başvurular tuşları karşılaştırmak yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|İki belirtilen olup olmadığını belirten bir değer alır [Idefinitionappıd](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) örnekleri eşit. Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.|  
|`IAppIdAuthority::AreReferencesEqual`|İki belirtilen olup olmadığını belirten bir değer alır [Ireferenceappıd](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) örnekleri eşit. Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|İki belirtilen dize tanımları eşit olup olmadığını belirten bir değer alır. Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|İki belirtilen dize başvuru eşit olup olmadığını belirten bir değer alır. Bayrak değeri, ilgili sürüm bilgilerini yoksaymak için IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION geçirebilirsiniz.|  
|`IAppIdAuthority::CreateDefinition`|Arabirim işaretçisi yeni oluşturulan alır `IDefinitionAppId` geçerli kapsamdaki derleme temsil eden örneği.|  
|`IAppIdAuthority::CreateReference`|Arabirim işaretçisi yeni oluşturulan alır `IReferenceAppId` , geçerli kapsamdaki derleme temsil eder.|  
|`IAppIdAuthority::DefinitionToText`|Dize sürümünü belirtilen alır `IDefinitionAppId`, belirtilen bayrak değerleri kullanarak.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Gösteren bir değer alır olup belirtilen `IDefinitionAppId` ve `IReferenceAppId` aynı bütünleştirilmiş kodda temsil eder.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Başvuru dizesi ve belirtilen tanımı dize aynı bütünleştirilmiş kodda gösterip göstermediğini belirten bir değer alır.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Belirtilen temsil eden bir dize anahtarı alır `IDefinitionAppId` örneği.|  
|`IAppIdAuthority::GenerateReferenceKey`|Belirtilen temsil eden bir dize anahtarı alır `IReferenceAppId` örneği.|  
|`IAppIdAuthority::HashDefinition`|Karma anahtar için belirtilen alır `IDefinitionAppId` örneği.|  
|`IAppIdAuthority::HashReference`|Karma anahtar için belirtilen alır `IReferenceAppId` örneği.|  
|`IAppIdAuthority::ReferenceToText`|Dize sürümünü belirtilen alır `IReferenceAppId`, belirtilen bayrak değerleri kullanarak.|  
|`IAppIdAuthority::TextToDefinition`|Bir arabirim işaretçisi alır bir `IDefinitionAppId` belirtilen dizeyi anahtarı tarafından başvurulan derlemeyi temsil eden örneği.|  
|`IAppIdAuthority::TextToReference`|Bir arabirim işaretçisi alır bir `IReferenceAppId` belirtilen dizeyi anahtarı tarafından başvurulan derlemeyi temsil eden örneği.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
