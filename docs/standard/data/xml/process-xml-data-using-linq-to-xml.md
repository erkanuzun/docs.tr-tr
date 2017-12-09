---
title: "LINQ-XML kullanılarak XML verilerini işlemek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a6b7a3c452d6b29145b8a2e7b1d2a1e824aaf508
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="fa666-102">LINQ-XML kullanılarak XML verilerini işlemek</span><span class="sxs-lookup"><span data-stu-id="fa666-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="fa666-103">LINQ-XML .NET Framework sürüm 3.5 XML verilerini işlemek için yeni modelidir.</span><span class="sxs-lookup"><span data-stu-id="fa666-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="fa666-104">LINQ-XML geliştiricilerin bekledikleri ile XML verileri her şeyi sağlar: sorgulama, değiştirme, oluşturma, kaydetme ve XML belgelerini seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="fa666-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="fa666-105">Gerçek avantajları sorgu ve oluşturma özellikleri kalan.</span><span class="sxs-lookup"><span data-stu-id="fa666-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="fa666-106">LINQ-XML sorgularında kısa ve açıklayıcı, XPath veya XQuery SQL daha fazla benzer söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="fa666-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="fa666-107">Sorgu sonuçları öğelerin veya özniteliklerin bir koleksiyon olarak döndürülebilecek ve XElement nesneleri için parametre olarak kullanılabilir olduğundan, XML ağaçları kolayca bir şekli'ndan diğerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="fa666-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="fa666-108">LINQ-XML .NET Framework sürüm 3.5 dil ile tümleşik sorgu (LINQ) teknolojisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa666-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="fa666-109">LINQ C# ve Visual Basic olabilecek herhangi bir veri deposuna genişletilmiş güçlü sorgu özellikleri sağlamak üzere dili sözdizimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="fa666-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="fa666-110">Bkz: [LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) , kullanım ve bakın hakkında ayrıntılı bilgi için [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) LINQ framework genel bakış.</span><span class="sxs-lookup"><span data-stu-id="fa666-110">See [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) for a detailed discussion of its use, and see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) for an overview of the LINQ framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa666-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa666-111">See Also</span></span>  
 <xref:System.Xml.Linq>  
 <xref:System.Linq>  
 [<span data-ttu-id="fa666-112">LINQ-XML vs. DOM</span><span class="sxs-lookup"><span data-stu-id="fa666-112">LINQ to XML vs. DOM</span></span>](http://msdn.microsoft.com/library/19b5ed02-feb2-455a-8897-f7f0fd76aca3)  
 [<span data-ttu-id="fa666-113">LINQ-XML vs. Diğer XML teknolojileri</span><span class="sxs-lookup"><span data-stu-id="fa666-113">LINQ to XML vs. Other XML Technologies</span></span>](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)