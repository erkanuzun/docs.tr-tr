---
title: ICLRStrongName::GetHashFromAssemblyFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95fbab459355c237157d43cee0211e42f6d26c62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432631"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a>ICLRStrongName::GetHashFromAssemblyFile Metodu
Belirtilen karma algoritması kullanılarak belirtilen derleme dosyası karmasını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `szFilePath`  
 [in] Karma hale getirilmesi için dosya yolu.  
  
 `piHashAlg`  
 [içinde out] Karma algoritmasını belirtir sabiti. Varsayılan karma algoritma için sıfır değerini kullanın.  
  
 `pbHash`  
 [out] Döndürülen karma arabellek.  
  
 `cchHash`  
 [in] İstenen en büyük boyutunu `pbHash`.  
  
 `pchHash`  
 [out] Bayt cinsinden boyutu döndürülen `pbHash`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK` Yöntem başarıyla tamamlandı Aksi takdirde hata belirten bir HRESULT değeri (bkz [ortak HRESULT değerleri](http://go.microsoft.com/fwlink/?LinkId=213878) bir listesi için).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MetaHost.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [GetHashFromAssemblyFileW Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [ICLRStrongName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
