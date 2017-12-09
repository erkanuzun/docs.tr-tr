---
title: "Nasıl yapılır: sınıfları ve XML Şeması belgeleri oluşturmak üzere XML şema tanımı aracını kullanın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c1f0dd08e820e5433f05c8bc90d85c84eb05972
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="d7576-102">Nasıl yapılır: sınıfları ve XML Şeması belgeleri oluşturmak üzere XML şema tanımı aracını kullanın</span><span class="sxs-lookup"><span data-stu-id="d7576-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="d7576-103">XML şema tanımı Aracı (XSD.exe'nin), bir sınıf açıklayan bir XML şeması oluşturmak veya bir XML şeması tarafından tanımlanan sınıfı oluşturmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7576-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="d7576-104">Aşağıdaki yordamlar bu işlemleri gerçekleştirmek nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d7576-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="d7576-105">Belirli bir şemaya uygun sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d7576-105">To generate classes that conform to a specific schema</span></span>  
  
1.  <span data-ttu-id="d7576-106">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="d7576-106">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="d7576-107">XML şeması için XML Şeması, örneğin tam olarak eşleştirilir sınıf kümesi oluşturur XML şema tanımı aracı için bağımsız değişken olarak geçir:</span><span class="sxs-lookup"><span data-stu-id="d7576-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="d7576-108">Araç yalnızca 16 Mart 2001 World Wide Web Consortium XML belirtimi başvuran şemaları işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d7576-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="d7576-109">Diğer bir deyişle, XML Şema ad alanı aşağıdaki örnekte gösterildiği gibi "http://www.w3.org/2001/XMLSchema" olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d7576-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  <span data-ttu-id="d7576-110">Yöntemler, özellikler veya alanları, sınıflar gerektiği şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d7576-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="d7576-111">Sınıf öznitelikleri ile değiştirme hakkında daha fazla bilgi için bkz: [XML serileştirme kullanarak özniteliklerini denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) ve [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="d7576-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="d7576-112">Genellikle, bir sınıf (veya sınıfları) örneklerini serileştirildiği zaman oluşturan XML akışı şeması incelemek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d7576-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="d7576-113">Örneğin, başkalarının kullanmak şemanızı yayımlayabilir veya uygunluk elde etmek çalıştığınız bir şemaya karşılaştırmak.</span><span class="sxs-lookup"><span data-stu-id="d7576-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="d7576-114">Bir XML Şeması belge sınıfları kümesinden oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d7576-114">To generate an XML Schema document from a set of classes</span></span>  
  
1.  <span data-ttu-id="d7576-115">Sınıf veya sınıfların bir DLL içine derleyin.</span><span class="sxs-lookup"><span data-stu-id="d7576-115">Compile the class or classes into a DLL.</span></span>  
  
2.  <span data-ttu-id="d7576-116">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="d7576-116">Open a command prompt.</span></span>  
  
3.  <span data-ttu-id="d7576-117">DLL bağımsız değişken olarak XSD.exe'nin için örneğin Geçir:</span><span class="sxs-lookup"><span data-stu-id="d7576-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="d7576-118">Şema (veya şemaları) adı "schema0.xsd" ile başlayan yazılır.</span><span class="sxs-lookup"><span data-stu-id="d7576-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7576-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7576-119">See Also</span></span>  
 <xref:System.Data.DataSet>  
 [<span data-ttu-id="d7576-120">XML şema tanımı aracı ve XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="d7576-120">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [<span data-ttu-id="d7576-121">Giriş XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="d7576-121">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="d7576-122">XML şema tanımı aracını (XSD.exe'nin)</span><span class="sxs-lookup"><span data-stu-id="d7576-122">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="d7576-123">Nasıl yapılır: bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="d7576-123">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="d7576-124">Nasıl yapılır: bir nesne seri durumdan</span><span class="sxs-lookup"><span data-stu-id="d7576-124">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)