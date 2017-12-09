---
title: "CertTimestampAuthenticodeLicense İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertTimestampAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ec863e9accbd2156b6eeed5857ff86075cf0a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="bc894-102">CertTimestampAuthenticodeLicense İşlevi</span><span class="sxs-lookup"><span data-stu-id="bc894-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="bc894-103">Zaman damgaları Authenticode XrML bir lisans.</span><span class="sxs-lookup"><span data-stu-id="bc894-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc894-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc894-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc894-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc894-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="bc894-106">[in] Zaman damgalı olmasını imzalı Authenticode XrML lisans.</span><span class="sxs-lookup"><span data-stu-id="bc894-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="bc894-107">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="bc894-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="bc894-108">[in] Zaman damgası sunucunun URI.</span><span class="sxs-lookup"><span data-stu-id="bc894-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="bc894-109">[out] Base64 ile kodlanmış zaman damgası imza almaya CRYPT_DATA_BLOB gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc894-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="bc894-110">Bunu serbest yapanın sorumluluğundadır `pTimestampSignatureBlob` -> `pbData` ile `HepFree()` kullandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="bc894-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="bc894-111">Bkz: [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="bc894-111">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc894-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc894-112">Remarks</span></span>  
 <span data-ttu-id="bc894-113">Zaman damgası imza gerçekten içerikleri lisans 's imzasından SignatureValue ikili biçiminde olan bir PKCS #7 SignedData ileti değil.</span><span class="sxs-lookup"><span data-stu-id="bc894-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="bc894-114">Temel olarak, bu lisans karşı imza olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="bc894-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc894-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc894-115">Return Value</span></span>  
 <span data-ttu-id="bc894-116">`S_OK`işlev başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="bc894-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="bc894-117">Aksi takdirde bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc894-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc894-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc894-118">See Also</span></span>  
 [<span data-ttu-id="bc894-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bc894-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)