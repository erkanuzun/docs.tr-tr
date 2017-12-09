---
title: "Find Private Key Aracı (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f542e0ba3bf35319c270fe9f93d3f355cc45ac95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a><span data-ttu-id="c8922-102">Find Private Key Aracı (FindPrivateKey.exe)</span><span class="sxs-lookup"><span data-stu-id="c8922-102">Find Private Key Tool (FindPrivateKey.exe)</span></span>
<span data-ttu-id="c8922-103">Bu komut satırı aracı, sertifika deposundan bir özel anahtar almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8922-103">This command-line tool can be used to retrieve a private key from a certificate store.</span></span> <span data-ttu-id="c8922-104">Örneğin, FindPrivateKey.exe belirli bir X.509 sertifikası sertifika deposunda ilişkili özel anahtar dosyasının adını ve konumunu bulmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c8922-104">For example, FindPrivateKey.exe can be used to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8922-105">FindPrivateKey aracı bir WCF örnek olarak geliyordu.</span><span class="sxs-lookup"><span data-stu-id="c8922-105">The FindPrivateKey tool is shipped as a WCF sample.</span></span> <span data-ttu-id="c8922-106">Örnek nerede bulacağını ve bu derleme hakkında daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="c8922-106">For more information about where to find the sample and how to build it, see</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8922-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8922-107">Syntax</span></span>  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c8922-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8922-108">Remarks</span></span>  
 <span data-ttu-id="c8922-109">Aşağıdaki tablolarda, değişkenler ve özel anahtar Bul Aracı (FindPrivateKey.exe) ile kullanılabilir seçenekler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c8922-109">The following tables describe the arguments and the options that can be used with the Find Private Key tool (FindPrivateKey.exe).</span></span>  
  
|<span data-ttu-id="c8922-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="c8922-110">Argument</span></span>|<span data-ttu-id="c8922-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8922-111">Description</span></span>|  
|--------------|-----------------|  
|`storeName`|<span data-ttu-id="c8922-112">Sertifika deposu adı.</span><span class="sxs-lookup"><span data-stu-id="c8922-112">Name of the certificate store.</span></span>|  
|`storeLocation`|<span data-ttu-id="c8922-113">Sertifika deposu konumu.</span><span class="sxs-lookup"><span data-stu-id="c8922-113">The location of the certificate store.</span></span>|  
  
|<span data-ttu-id="c8922-114">Seçenek</span><span class="sxs-lookup"><span data-stu-id="c8922-114">Option</span></span>|<span data-ttu-id="c8922-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8922-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c8922-116">`/n <`*subjectName*`>`</span><span class="sxs-lookup"><span data-stu-id="c8922-116">`/n <` *subjectName* `>`</span></span>|<span data-ttu-id="c8922-117">Sertifikasının konu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8922-117">Specifies the subject name of the certificate.</span></span>|  
|<span data-ttu-id="c8922-118">`/t <`*parmak izi*`>`</span><span class="sxs-lookup"><span data-stu-id="c8922-118">`/t <` *thumbprint* `>`</span></span>|<span data-ttu-id="c8922-119">Sertifikanın parmak izi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c8922-119">Specifies the thumbprint of the certificate.</span></span> <span data-ttu-id="c8922-120">Certmgr.exe sertifikanın parmak izi almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8922-120">Use Certmgr.exe to retrieve the thumbprint of the certificate.</span></span>|  
|`/f`|<span data-ttu-id="c8922-121">Yalnızca dosya adını çıkarır.</span><span class="sxs-lookup"><span data-stu-id="c8922-121">Outputs the file name only.</span></span>|  
|`/d`|<span data-ttu-id="c8922-122">Dizin yalnızca çıkarır.</span><span class="sxs-lookup"><span data-stu-id="c8922-122">Outputs the directory only.</span></span>|  
|`/a`|<span data-ttu-id="c8922-123">Mutlak dosya adı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="c8922-123">Outputs the absolute file name.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="c8922-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c8922-124">Examples</span></span>  
 <span data-ttu-id="c8922-125">Aşağıdaki komut, John Doe için özel anahtarı alır.</span><span class="sxs-lookup"><span data-stu-id="c8922-125">The following command retrieves the private key for John Doe.</span></span>  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 <span data-ttu-id="c8922-126">Aşağıdaki komut, özel anahtarı yerel makinede alır.</span><span class="sxs-lookup"><span data-stu-id="c8922-126">The following command retrieves the private key for the local machine.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```