---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad64d5722df68859e7be9d44b94b95cf1f43823f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="bc2ea-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="bc2ea-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="bc2ea-103">Belgede verilen konumunda kesme noktası içerdiğinden yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc2ea-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc2ea-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc2ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc2ea-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="bc2ea-106">[in] Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="bc2ea-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="bc2ea-107">[in] Belirtilen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="bc2ea-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="bc2ea-108">[in] Belirtilen belge sütun.</span><span class="sxs-lookup"><span data-stu-id="bc2ea-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bc2ea-109">[out] Adresine bir işaretçi bir [Isymunmanagedmethod arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) kesme içeren yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="bc2ea-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc2ea-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc2ea-110">Return Value</span></span>  
 <span data-ttu-id="bc2ea-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bc2ea-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc2ea-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc2ea-112">Requirements</span></span>  
 <span data-ttu-id="bc2ea-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bc2ea-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2ea-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc2ea-114">See Also</span></span>  
 [<span data-ttu-id="bc2ea-115">Isymunmanagedreader arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc2ea-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)