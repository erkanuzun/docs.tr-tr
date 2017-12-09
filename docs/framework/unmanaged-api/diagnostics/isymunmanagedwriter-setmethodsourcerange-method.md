---
title: "ISymUnmanagedWriter::SetMethodSourceRange Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetMethodSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ed0a73b4862702895e737f2df639b8da7f7679
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="5abc2-102">ISymUnmanagedWriter::SetMethodSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5abc2-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="5abc2-103">Gerçek başlangıç ve bitiş kaynak dosyası içinde yönteminin belirtir.</span><span class="sxs-lookup"><span data-stu-id="5abc2-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="5abc2-104">Yöntemi içinde mevcut sıralama noktaları bağımsız olarak bir yöntem kapsamını belirtmek için bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5abc2-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5abc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5abc2-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5abc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5abc2-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="5abc2-107">[in] Başlangıç konumu içeren belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5abc2-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="5abc2-108">[in] Başlangıç satır numarası.</span><span class="sxs-lookup"><span data-stu-id="5abc2-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="5abc2-109">[in] Başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="5abc2-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="5abc2-110">[in] Bitiş konumunu içeren belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5abc2-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="5abc2-111">[in] Bitiş satır numarası.</span><span class="sxs-lookup"><span data-stu-id="5abc2-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="5abc2-112">[in] Bitiş sütun numarası.</span><span class="sxs-lookup"><span data-stu-id="5abc2-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5abc2-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5abc2-113">Return Value</span></span>  
 <span data-ttu-id="5abc2-114">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5abc2-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5abc2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5abc2-115">Requirements</span></span>  
 <span data-ttu-id="5abc2-116">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5abc2-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5abc2-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5abc2-117">See Also</span></span>  
 [<span data-ttu-id="5abc2-118">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="5abc2-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)