---
title: "Visual Basic'de XML'e Erişme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="d95f6-102">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="d95f6-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="d95f6-103">XML eksen özellikleri erişme ve gezinme sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapıları.</span><span class="sxs-lookup"><span data-stu-id="d95f6-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="d95f6-104">Bu özellikler, öğeleri ve özniteliklerinin XML adları belirterek erişim sağlamak için özel bir sözdizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d95f6-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="d95f6-105">XML öğeleri ve öznitelikleri erişmenize olanak sağlayan dil özellikler aşağıdaki tabloda listelenmektedir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d95f6-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="d95f6-106">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="d95f6-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="d95f6-107">Özellik açıklaması</span><span class="sxs-lookup"><span data-stu-id="d95f6-107">Property description</span></span>|<span data-ttu-id="d95f6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d95f6-108">Example</span></span>|<span data-ttu-id="d95f6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d95f6-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="d95f6-110">*alt eksen*</span><span class="sxs-lookup"><span data-stu-id="d95f6-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="d95f6-111">Tüm alır `phone` alt öğeleri olan öğeler `contact` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d95f6-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="d95f6-112">*öznitelik eksen*</span><span class="sxs-lookup"><span data-stu-id="d95f6-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="d95f6-113">Tüm alır `type` özniteliklerini `phone` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d95f6-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="d95f6-114">*descendant axis*</span><span class="sxs-lookup"><span data-stu-id="d95f6-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="d95f6-115">Tüm alır `name` öğeleri `contacts` oluşma hiyerarşideki nasıl derin bakılmaksızın öğesi.</span><span class="sxs-lookup"><span data-stu-id="d95f6-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="d95f6-116">*uzantı dizin oluşturucu*</span><span class="sxs-lookup"><span data-stu-id="d95f6-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="d95f6-117">İlk alır `name` serisinden öğesi.</span><span class="sxs-lookup"><span data-stu-id="d95f6-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="d95f6-118">*değer*</span><span class="sxs-lookup"><span data-stu-id="d95f6-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="d95f6-119">İlk nesnenin dize gösterimini sırayla alır veya `Nothing` dizisi boşsa.</span><span class="sxs-lookup"><span data-stu-id="d95f6-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="d95f6-120">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d95f6-120">In This Section</span></span>  
 [<span data-ttu-id="d95f6-121">Nasıl yapılır: XML bağımlı öğelerine erişme</span><span class="sxs-lookup"><span data-stu-id="d95f6-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="d95f6-122">Descendant axis özelliği, belirtilen ada sahip ve belirtilen bir XML öğesi altında bulunan tüm XML öğeleri erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d95f6-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="d95f6-123">Nasıl yapılır: XML alt öğelerine erişme</span><span class="sxs-lookup"><span data-stu-id="d95f6-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="d95f6-124">Bir alt kullanmak bir XML öğesi belirtilen ada sahip tüm XML alt öğelerine erişmek için axis özelliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d95f6-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="d95f6-125">Nasıl yapılır: XML özniteliklerine erişme</span><span class="sxs-lookup"><span data-stu-id="d95f6-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="d95f6-126">Attribute axis özelliği bir XML öğesi belirtilen ada sahip tüm XML öznitelikleri erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d95f6-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="d95f6-127">Nasıl yapılır: XML Namespace öneklerini bildirme ve kullanma</span><span class="sxs-lookup"><span data-stu-id="d95f6-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="d95f6-128">Bir XML ad alanı öneki bildirme ve oluşturma ve XML öğeleri erişmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d95f6-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d95f6-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d95f6-129">Related Sections</span></span>  
 [<span data-ttu-id="d95f6-130">XML eksen özellikleri</span><span class="sxs-lookup"><span data-stu-id="d95f6-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="d95f6-131">Çeşitli XML erişim özelliklerini açıklayan bölümlerin bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d95f6-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="d95f6-132">LINQ-XML Visual Basic'de genel bakış</span><span class="sxs-lookup"><span data-stu-id="d95f6-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="d95f6-133">Kullanarak bir giriş sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="d95f6-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="d95f6-134">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="d95f6-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="d95f6-135">Visual Basic'te XML değişmez değerleri kullanmaya giriş bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d95f6-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="d95f6-136">Visual Basic'te XML düzenleme</span><span class="sxs-lookup"><span data-stu-id="d95f6-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="d95f6-137">Yükleme ve Visual Basic'te XML değiştirme hakkında bölümlerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d95f6-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="d95f6-138">XML</span><span class="sxs-lookup"><span data-stu-id="d95f6-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="d95f6-139">Nasıl kullanılacağını açıklayan bölümlerin bağlantılarını sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="d95f6-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>