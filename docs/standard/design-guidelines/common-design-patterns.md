---
title: "Ortak tasarım desenleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- design patterns in class libraries
- class library design guidelines [.NET Framework], design patterns
ms.assetid: f7bd1361-4ab2-4132-972d-a044b8f197e1
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dd2d78e675ebc67cc2e49f5bc7141558d462a3e4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="common-design-patterns"></a><span data-ttu-id="9b7ec-102">Ortak tasarım desenleri</span><span class="sxs-lookup"><span data-stu-id="9b7ec-102">Common Design Patterns</span></span>
<span data-ttu-id="9b7ec-103">Çok sayıda books yazılım modelleri, düzeni diller ve desenler çok geniş konusunu adres antipatterns vardır.</span><span class="sxs-lookup"><span data-stu-id="9b7ec-103">There are numerous books on software patterns, pattern languages, and antipatterns that address the very broad subject of patterns.</span></span> <span data-ttu-id="9b7ec-104">Bu nedenle, bu bölümde, kılavuzları ve .NET Framework API'ları tasarımında sık kullanılan desenleri çok sınırlı sayıda ilgili tartışma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b7ec-104">Thus, this chapter provides guidelines and discussion related to a very limited set of patterns that are used frequently in the design of the .NET Framework APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b7ec-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9b7ec-105">In This Section</span></span>  
 [<span data-ttu-id="9b7ec-106">Bağımlılık özellikleri</span><span class="sxs-lookup"><span data-stu-id="9b7ec-106">Dependency Properties</span></span>](../../../docs/standard/design-guidelines/dependency-properties.md)  
 [<span data-ttu-id="9b7ec-107">Desen dispose</span><span class="sxs-lookup"><span data-stu-id="9b7ec-107">Dispose Pattern</span></span>](../../../docs/standard/design-guidelines/dispose-pattern.md)  
 <span data-ttu-id="9b7ec-108">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="9b7ec-108">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9b7ec-109">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="9b7ec-109">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7ec-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b7ec-110">See Also</span></span>  
 [<span data-ttu-id="9b7ec-111">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9b7ec-111">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)