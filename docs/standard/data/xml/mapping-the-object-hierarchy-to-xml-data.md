---
title: "XML verilerine nesne hiyerarşisi eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bf43922fb702988e9057f541833cd58d33c820a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="4bcbd-102">XML verilerine nesne hiyerarşisi eşleme</span><span class="sxs-lookup"><span data-stu-id="4bcbd-102">Mapping the Object Hierarchy to XML Data</span></span>
<span data-ttu-id="4bcbd-103">Bir XML belgesi bellekte kavramsal temsili bir ağaç olur.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-103">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="4bcbd-104">Programlama için ağaç düğümleri erişmek için bir nesne hiyerarşisi vardır.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-104">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="4bcbd-105">Aşağıdaki örnekte nasıl XML içeriği düğümleri duruma gösterir.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-105">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="4bcbd-106">XML XML belge nesne modeli (DOM) içine okurken parçaları düğümlerin içine dönüştürülür ve bu düğümler, düğüm türü ve değerleri gibi kendileri hakkında ek meta veriler korumak.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-106">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="4bcbd-107">Düğüm türü, nesne ve hangi eylemleri gerçekleştirilebilir belirler ve hangi özelliklerin ayarlayın veya alınır.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-107">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="4bcbd-108">Aşağıdaki basit XML varsa:</span><span class="sxs-lookup"><span data-stu-id="4bcbd-108">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="4bcbd-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="4bcbd-109">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="4bcbd-110">Giriş bellekte atanan düğüm türü özelliği aşağıdaki düğüm ağacıyla olarak temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="4bcbd-110">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="4bcbd-111">![örnek düğüm ağacı](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="4bcbd-111">![example node tree](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="4bcbd-112">Kitap ve başlık düğümü ağaç gösterimi</span><span class="sxs-lookup"><span data-stu-id="4bcbd-112">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="4bcbd-113">`book` Öğe haline gelir bir **XmlElement** nesnesi, sonraki öğeye `title`, haline bir **XmlElement**, öğe içeriği olurken bir **XmlText** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-113">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="4bcbd-114">Bakarak içinde **XmlElement** yöntemleri ve özellikleri, yöntemleri ve özellikleri yöntemleri ve özellikleri kullanılabilir farklı bir **XmlText** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-114">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="4bcbd-115">Bu nedenle gerçekleştirilecek eylemler düğüm türünü belirleyen XML Biçimlendirme hale hangi düğüm türü önemlidir bilerek.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-115">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="4bcbd-116">Aşağıdaki örnekte, XML verileri okur ve düğüm türüne bağlı olarak farklı bir metin çıkışı yazar.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-116">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="4bcbd-117">Girdi olarak şu XML veri dosyası kullanarak **items.xml**:</span><span class="sxs-lookup"><span data-stu-id="4bcbd-117">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="4bcbd-118">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="4bcbd-118">**Input**</span></span>  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 <span data-ttu-id="4bcbd-119">Aşağıdaki kod örneği okuma **items.xml** dosya ve her düğüm türünün bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-119">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and   
            'ignore all white space nodes.   
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore   
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 <span data-ttu-id="4bcbd-120">Örneğin çıktısını düğüm türleri için verilerin eşleşmesini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-120">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="4bcbd-121">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="4bcbd-121">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 <span data-ttu-id="4bcbd-122">Aynı anda tek bir giriş çizgi alma ve koddan oluşturulan çıktı kullanarak, böylece XML verileri ne tür bir düğüm türü hale geldiğini anlamak hangi düğümü test çıkışı, hangi satırların üretilen çözümlemek için aşağıdaki tabloda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-122">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="4bcbd-123">Giriş</span><span class="sxs-lookup"><span data-stu-id="4bcbd-123">Input</span></span>|<span data-ttu-id="4bcbd-124">Çıkış</span><span class="sxs-lookup"><span data-stu-id="4bcbd-124">Output</span></span>|<span data-ttu-id="4bcbd-125">Düğüm türü sınaması</span><span class="sxs-lookup"><span data-stu-id="4bcbd-125">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|<span data-ttu-id="4bcbd-126">\<? xml version = "1.0"? ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-126">\<?xml version="1.0"?></span></span>|<span data-ttu-id="4bcbd-127">\<? xml sürümü ='1.0 '? ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-127">\<?xml version='1.0'?></span></span>|<span data-ttu-id="4bcbd-128">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="4bcbd-128">XmlNodeType.XmlDeclaration</span></span>|  
|<span data-ttu-id="4bcbd-129">\<!--Örnek bir XML belgesi budur--></span><span class="sxs-lookup"><span data-stu-id="4bcbd-129">\<!-- This is a sample XML document --></span></span>|<span data-ttu-id="4bcbd-130">\<!--Örnek bir XML belgesi budur--></span><span class="sxs-lookup"><span data-stu-id="4bcbd-130">\<!--This is a sample XML document --></span></span>|<span data-ttu-id="4bcbd-131">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="4bcbd-131">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="4bcbd-132">\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >] ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-132">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="4bcbd-133">\<! DOCTYPE öğeleri [\<! Varlık numarası "123" >]</span><span class="sxs-lookup"><span data-stu-id="4bcbd-133">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="4bcbd-134">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="4bcbd-134">XmlNodeType.DocumentType</span></span>|  
|<span data-ttu-id="4bcbd-135">\<Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-135">\<Items></span></span>|<span data-ttu-id="4bcbd-136">\<Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-136">\<Items></span></span>|<span data-ttu-id="4bcbd-137">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4bcbd-137">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4bcbd-138">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-138">\<Item></span></span>|<span data-ttu-id="4bcbd-139">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-139">\<Item></span></span>|<span data-ttu-id="4bcbd-140">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4bcbd-140">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4bcbd-141">Bir varlık ile test edin:&number;</span><span class="sxs-lookup"><span data-stu-id="4bcbd-141">Test with an entity: &number;</span></span>|<span data-ttu-id="4bcbd-142">Bir varlığı olan test: 123</span><span class="sxs-lookup"><span data-stu-id="4bcbd-142">Test with an entity: 123</span></span>|<span data-ttu-id="4bcbd-143">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4bcbd-143">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4bcbd-144">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-144">\</Item></span></span>|<span data-ttu-id="4bcbd-145">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-145">\</Item></span></span>|<span data-ttu-id="4bcbd-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4bcbd-146">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4bcbd-147">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-147">\<Item></span></span>|<span data-ttu-id="4bcbd-148">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-148">\<Item></span></span>|<span data-ttu-id="4bcbd-149">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4bcbd-149">XmNodeType.Element</span></span>|  
|<span data-ttu-id="4bcbd-150">bir alt öğesi ile test</span><span class="sxs-lookup"><span data-stu-id="4bcbd-150">test with a child element</span></span>|<span data-ttu-id="4bcbd-151">bir alt öğesi ile test</span><span class="sxs-lookup"><span data-stu-id="4bcbd-151">test with a child element</span></span>|<span data-ttu-id="4bcbd-152">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4bcbd-152">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4bcbd-153">\<Daha fazla ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-153">\<more></span></span>|<span data-ttu-id="4bcbd-154">\<Daha fazla ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-154">\<more></span></span>|<span data-ttu-id="4bcbd-155">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4bcbd-155">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4bcbd-156">Hizmetler</span><span class="sxs-lookup"><span data-stu-id="4bcbd-156">stuff</span></span>|<span data-ttu-id="4bcbd-157">Hizmetler</span><span class="sxs-lookup"><span data-stu-id="4bcbd-157">stuff</span></span>|<span data-ttu-id="4bcbd-158">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4bcbd-158">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4bcbd-159">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-159">\</Item></span></span>|<span data-ttu-id="4bcbd-160">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-160">\</Item></span></span>|<span data-ttu-id="4bcbd-161">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4bcbd-161">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4bcbd-162">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-162">\<Item></span></span>|<span data-ttu-id="4bcbd-163">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-163">\<Item></span></span>|<span data-ttu-id="4bcbd-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4bcbd-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4bcbd-165">CDATA bölümü ile test</span><span class="sxs-lookup"><span data-stu-id="4bcbd-165">test with a CDATA section</span></span>|<span data-ttu-id="4bcbd-166">CDATA bölümü ile test</span><span class="sxs-lookup"><span data-stu-id="4bcbd-166">test with a CDATA section</span></span>|<span data-ttu-id="4bcbd-167">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="4bcbd-167">XmlTest.Text</span></span>|  
|<span data-ttu-id="4bcbd-168"><! [CDATA [\<456 >]]\></span><span class="sxs-lookup"><span data-stu-id="4bcbd-168"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="4bcbd-169"><! [CDATA [\<456 >]]\></span><span class="sxs-lookup"><span data-stu-id="4bcbd-169"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="4bcbd-170">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="4bcbd-170">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="4bcbd-171">def</span><span class="sxs-lookup"><span data-stu-id="4bcbd-171">def</span></span>|<span data-ttu-id="4bcbd-172">def</span><span class="sxs-lookup"><span data-stu-id="4bcbd-172">def</span></span>|<span data-ttu-id="4bcbd-173">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4bcbd-173">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4bcbd-174">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-174">\</Item></span></span>|<span data-ttu-id="4bcbd-175">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-175">\</Item></span></span>|<span data-ttu-id="4bcbd-176">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4bcbd-176">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4bcbd-177">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-177">\<Item></span></span>|<span data-ttu-id="4bcbd-178">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-178">\<Item></span></span>|<span data-ttu-id="4bcbd-179">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4bcbd-179">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4bcbd-180">Char varlığı ile test: &\#65;</span><span class="sxs-lookup"><span data-stu-id="4bcbd-180">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="4bcbd-181">Char varlığı ile test: A</span><span class="sxs-lookup"><span data-stu-id="4bcbd-181">Test with a char entity: A</span></span>|<span data-ttu-id="4bcbd-182">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4bcbd-182">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4bcbd-183">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-183">\</Item></span></span>|<span data-ttu-id="4bcbd-184">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-184">\</Item></span></span>|<span data-ttu-id="4bcbd-185">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4bcbd-185">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4bcbd-186">\<!----> On dört karakter bu öğesi.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-186">\<!-- Fourteen chars in this element.--></span></span>|<span data-ttu-id="4bcbd-187">\<--Bu öğe. on dört karakter--></span><span class="sxs-lookup"><span data-stu-id="4bcbd-187">\<--Fourteen chars in this element.--></span></span>|<span data-ttu-id="4bcbd-188">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="4bcbd-188">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="4bcbd-189">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-189">\<Item></span></span>|<span data-ttu-id="4bcbd-190">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-190">\<Item></span></span>|<span data-ttu-id="4bcbd-191">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="4bcbd-191">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="4bcbd-192">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="4bcbd-192">1234567890ABCD</span></span>|<span data-ttu-id="4bcbd-193">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="4bcbd-193">1234567890ABCD</span></span>|<span data-ttu-id="4bcbd-194">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="4bcbd-194">XmlNodeType.Text</span></span>|  
|<span data-ttu-id="4bcbd-195">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-195">\</Item></span></span>|<span data-ttu-id="4bcbd-196">\</ Öğesi ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-196">\</Item></span></span>|<span data-ttu-id="4bcbd-197">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4bcbd-197">XmlNodeType.EndElement</span></span>|  
|<span data-ttu-id="4bcbd-198">\</ Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-198">\</Items></span></span>|<span data-ttu-id="4bcbd-199">\</ Öğeleri ></span><span class="sxs-lookup"><span data-stu-id="4bcbd-199">\</Items></span></span>|<span data-ttu-id="4bcbd-200">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="4bcbd-200">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="4bcbd-201">Düğüm türü atanmış bilmeniz gerekir, hangi tür Eylemler geçerli olduğunu ve ne tür bir ayarlamak ve almak özellikleri düğüm olarak türü denetler.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-201">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="4bcbd-202">Boşluk düğüm oluşturma, veri tarafından DOM içine yüklendiğinde denetlenir **PreserveWhitespace** bayrağı.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-202">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="4bcbd-203">Daha fazla bilgi için bkz: [boşluk ve önemli boşluk DOM yüklenirken işleme](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="4bcbd-203">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="4bcbd-204">DOM yeni düğümler eklemek için bkz: [ekleme düğümlerin bir XML belgesi içine](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4bcbd-204">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="4bcbd-205">DOM düğümleri kaldırmak için bkz: [düğümleri kaldırma, içerik ve bir XML belgesi değerlerinden](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4bcbd-205">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="4bcbd-206">DOM düğümler içeriğini değiştirmek için bkz: [değiştirme düğümleri, içerik ve bir XML belgesi değerleri](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="4bcbd-206">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bcbd-207">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4bcbd-207">See Also</span></span>  
 [<span data-ttu-id="4bcbd-208">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="4bcbd-208">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)