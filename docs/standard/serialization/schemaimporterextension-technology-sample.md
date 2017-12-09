---
title: "SchemaImporterExtension teknoloji örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 862bea7fa17638b6f3c5ca8afb43a76dc7ed85b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="a1e3c-102">SchemaImporterExtension teknoloji örnek</span><span class="sxs-lookup"><span data-stu-id="a1e3c-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="a1e3c-103">Örnek indirme</span><span class="sxs-lookup"><span data-stu-id="a1e3c-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="a1e3c-104">Bu örnek özel bir gösteren <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> bir XML Şeması aktarıldığında kod oluşturma üzerinde ayrıntılı denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="a1e3c-105">Uygulama oluşturmak, kaydedin ve bu uzantı çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="a1e3c-106">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a1e3c-106">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="a1e3c-107">Bir komut istemi penceresi açın ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="a1e3c-108">Tür **msbuild.exe OrderSchemaImporterExtension.sln** komut satırında.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="a1e3c-109">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a1e3c-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="a1e3c-110">Açık [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="a1e3c-111">Visual Studio'da dosyayı açmak OrderSchemaImporterExtension.sln simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="a1e3c-112">Üzerinde **yapı** menüsünde tıklatın **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="a1e3c-113">Uygulamayı varsayılan \bin veya \bin\debug'dır dizininde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="a1e3c-114">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a1e3c-114">To run the sample</span></span>  
  
1.  <span data-ttu-id="a1e3c-115">Komut istemi kullanarak yeni yürütülebilir dosyayı içeren dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="a1e3c-116">Tür **[exe adı]** komut satırında.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1e3c-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1e3c-117">Remarks</span></span>  
 <span data-ttu-id="a1e3c-118">Kaynak kodu ve build.proj dosyalardaki açıklamalar örnek ikili oluşturma ve kayıt adımları hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e3c-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1e3c-119">See Also</span></span>  
 <xref:System.CodeDom.CodeCompileUnit>  
 <xref:System.CodeDom.CodeNamespace>  
 <xref:System.CodeDom.CodeNamespaceImport>  
 <xref:Microsoft.CSharp.CSharpCodeProvider>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 <xref:System.Web.Services.Description>  
 <xref:System.Web.Services.Discovery>  
 <xref:System.Xml.Serialization>  
 <xref:System.Uri>  
 <xref:Microsoft.VisualBasic.VBCodeProvider>  
 <xref:System.Web.Services.Description.WebReference>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>