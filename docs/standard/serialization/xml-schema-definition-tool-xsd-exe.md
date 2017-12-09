---
title: "XML şema tanımı Aracı (XSD.exe'nin)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bb350d454d2fcb0f38d092240c98c1b87966be
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="249ae-102">XML şema tanımı Aracı (XSD.exe'nin)</span><span class="sxs-lookup"><span data-stu-id="249ae-102">XML Schema Definition Tool (Xsd.exe)</span></span>
<span data-ttu-id="249ae-103">XML şema tanımı (XSD.exe'nin) aracı XDR, XML ve XSD dosyalarından veya bir çalışma zamanı derleme sınıflarda XML Şeması veya ortak dil çalışma zamanı sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-103">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="249ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="249ae-104">Syntax</span></span>  
  
```  
xsd file.xdr [/outputdir:directory][/parameters:file.xml]  
xsd file.xml [/outputdir:directory] [/parameters:file.xml]  
xsd file.xsd {/classes | /dataset} [/element:element]   
             [/enableLinqDataSet] [/language:language]   
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]   
                          [/parameters:file.xml]  
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]  
```  
  
## <a name="argument"></a><span data-ttu-id="249ae-105">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="249ae-105">Argument</span></span>  
  
|<span data-ttu-id="249ae-106">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="249ae-106">Argument</span></span>|<span data-ttu-id="249ae-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="249ae-108">*File.Extension*</span><span class="sxs-lookup"><span data-stu-id="249ae-108">*file.extension*</span></span>|<span data-ttu-id="249ae-109">Dönüştürülecek giriş dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-109">Specifies the input file to convert.</span></span> <span data-ttu-id="249ae-110">Extensionas şunlardan birini belirtmeniz gerekir: .xdr, .xml, .xsd, .dll veya .exe.</span><span class="sxs-lookup"><span data-stu-id="249ae-110">You must specify the extensionas one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="249ae-111">XDR şema dosyası (.xdr uzantısı) belirtirseniz, xsd.exe'nin bir XSD şemasına XDR şeması dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="249ae-111">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="249ae-112">Çıkış dosyası XDR şeması, ancak .xsd uzantısı ile aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="249ae-112">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="249ae-113">Bir XML dosyası (.xml uzantısı) belirtirseniz, xsd.exe'nin veri dosyasındaki bir şema öğesinin ve bir XSD şeması üretir.</span><span class="sxs-lookup"><span data-stu-id="249ae-113">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="249ae-114">Çıkış dosyası XML dosyası olarak, ancak .xsd uzantısı ile aynı ada sahip.</span><span class="sxs-lookup"><span data-stu-id="249ae-114">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="249ae-115">Bir XML şema dosyası (.xsd uzantısı) belirtirseniz, xsd.exe'nin için XML Şeması karşılık gelen çalışma zamanı nesneler için kaynak kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-115">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="249ae-116">Bir çalışma zamanı derleme dosyası (.exe veya .dll uzantısı) belirtirseniz, xsd.exe'nin şemaları bir veya daha fazla türleri için bu derlemede oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-116">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="249ae-117">Kullanabilirsiniz `/type` şemaları oluşturulacak türlerini belirtmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="249ae-117">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="249ae-118">Çıkış şemaları schema0.xsd, schema1.xsd vb. adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="249ae-118">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="249ae-119">XSD.exe'nin üreten birden çok şema ad alanını kullanarak verilen türleri yalnızca belirtirseniz, `XMLRoot` özel öznitelik.</span><span class="sxs-lookup"><span data-stu-id="249ae-119">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|  
  
## <a name="general-options"></a><span data-ttu-id="249ae-120">Genel seçenekleri</span><span class="sxs-lookup"><span data-stu-id="249ae-120">General Options</span></span>  
  
|<span data-ttu-id="249ae-121">Seçenek</span><span class="sxs-lookup"><span data-stu-id="249ae-121">Option</span></span>|<span data-ttu-id="249ae-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="249ae-123">**/h**[**ardım**]</span><span class="sxs-lookup"><span data-stu-id="249ae-123">**/h**[**elp**]</span></span>|<span data-ttu-id="249ae-124">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="249ae-124">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="249ae-125">**/o**[**utputdir**]**:***dizini*</span><span class="sxs-lookup"><span data-stu-id="249ae-125">**/o**[**utputdir**]**:***directory*</span></span>|<span data-ttu-id="249ae-126">Çıktı dosyaları dizinini belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-126">Specifies the directory for output files.</span></span> <span data-ttu-id="249ae-127">Bu bağımsız değişken yalnızca bir kez görünebilir.</span><span class="sxs-lookup"><span data-stu-id="249ae-127">This argument can appear only once.</span></span> <span data-ttu-id="249ae-128">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="249ae-128">The default is the current directory.</span></span>|  
|<span data-ttu-id="249ae-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="249ae-129">**/?**</span></span>|<span data-ttu-id="249ae-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="249ae-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="249ae-131">**/P [parametreleri]:** *file.xml*</span><span class="sxs-lookup"><span data-stu-id="249ae-131">**/P[arameters]:** *file.xml*</span></span>|<span data-ttu-id="249ae-132">Çeşitli işlem modları için seçenekler belirtilen .xml dosyasından okuyun.</span><span class="sxs-lookup"><span data-stu-id="249ae-132">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="249ae-133">Kısa form ' / p:'.</span><span class="sxs-lookup"><span data-stu-id="249ae-133">The short form is '/p:'.</span></span> <span data-ttu-id="249ae-134">Daha fazla bilgi için aşağıdaki Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="249ae-134">For more information, see the following Remarks section.</span></span>|  
  
## <a name="xsd-file-options"></a><span data-ttu-id="249ae-135">XSD dosyası seçenekleri</span><span class="sxs-lookup"><span data-stu-id="249ae-135">XSD File Options</span></span>  
 <span data-ttu-id="249ae-136">.Xsd dosyaları için aşağıdaki seçeneklerden birini belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="249ae-136">You must specify only one of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="249ae-137">Seçenek</span><span class="sxs-lookup"><span data-stu-id="249ae-137">Option</span></span>|<span data-ttu-id="249ae-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="249ae-139">**/c**[**sınıfları**]</span><span class="sxs-lookup"><span data-stu-id="249ae-139">**/c**[**lasses**]</span></span>|<span data-ttu-id="249ae-140">Belirtilen şemaya karşılık gelen sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-140">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="249ae-141">XML veri nesnesine okumak için kullandığınız `System.Xml.Serialization.XmlSerializer.Deserializer` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="249ae-141">To read XML data into the object, use the `System.Xml.Serialization.XmlSerializer.Deserializer` method.</span></span>|  
|<span data-ttu-id="249ae-142">**/d**[**ataset**]</span><span class="sxs-lookup"><span data-stu-id="249ae-142">**/d**[**ataset**]</span></span>|<span data-ttu-id="249ae-143">Türetilen bir sınıf oluşturur <xref:System.Data.DataSet> belirtilen şemaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="249ae-143">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="249ae-144">Türetilmiş sınıf XML verileri okumak için kullandığınız `System.Data.DataSet.ReadXml` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="249ae-144">To read XML data into the derived class, use the `System.Data.DataSet.ReadXml` method.</span></span>|  
  
 <span data-ttu-id="249ae-145">.Xsd dosyaları için aşağıdaki seçeneklerden birini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="249ae-145">You can also specify any of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="249ae-146">Seçenek</span><span class="sxs-lookup"><span data-stu-id="249ae-146">Option</span></span>|<span data-ttu-id="249ae-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="249ae-148">**/e**[**öğesine**]**:***öğesi*</span><span class="sxs-lookup"><span data-stu-id="249ae-148">**/e**[**lement**]**:***element*</span></span>|<span data-ttu-id="249ae-149">Öğe için kod oluşturmak için şema belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-149">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="249ae-150">Varsayılan olarak tüm öğeler yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="249ae-150">By default all elements are typed.</span></span> <span data-ttu-id="249ae-151">Bu bağımsız değişken birden çok kez belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="249ae-151">You can specify this argument more than once.</span></span>|  
|<span data-ttu-id="249ae-152">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="249ae-152">**/enableDataBinding**</span></span>|<span data-ttu-id="249ae-153">Uygular <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama etkinleştirmek için oluşturulan tüm türleri arabirimi.</span><span class="sxs-lookup"><span data-stu-id="249ae-153">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="249ae-154">Kısa form `/edb`.</span><span class="sxs-lookup"><span data-stu-id="249ae-154">The short form is `/edb`.</span></span>|  
|<span data-ttu-id="249ae-155">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="249ae-155">**/enableLinqDataSet**</span></span>|<span data-ttu-id="249ae-156">(Kısa form: `/eld`.) Oluşturulan veri kümesi LINQ to DataSet kullanarak karşı sorgulanabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-156">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="249ae-157">Bu seçenek /dataset seçeneği de belirtildiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="249ae-157">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="249ae-158">Daha fazla bilgi için bkz: [LINQ veri kümesi'ne genel bakış-](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) ve [yazılan veri kümeleri sorgulama](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="249ae-158">For more information, see [LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="249ae-159">LINQ kullanma hakkında genel bilgi için bkz: [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="249ae-159">For general information about using LINQ, see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span>|  
|<span data-ttu-id="249ae-160">**/f**[**lanları**]</span><span class="sxs-lookup"><span data-stu-id="249ae-160">**/f**[**ields**]</span></span>|<span data-ttu-id="249ae-161">Alanları özellikleri yerine oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-161">Generates fields instead of properties.</span></span> <span data-ttu-id="249ae-162">Varsayılan olarak, özellikleri üretilir.</span><span class="sxs-lookup"><span data-stu-id="249ae-162">By default, properties are generated.</span></span>|  
|<span data-ttu-id="249ae-163">**/l**[**dil**]**:***dili*</span><span class="sxs-lookup"><span data-stu-id="249ae-163">**/l**[**anguage**]**:***language*</span></span>|<span data-ttu-id="249ae-164">Kullanmak için programlama dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-164">Specifies the programming language to use.</span></span> <span data-ttu-id="249ae-165">Aralarından seçim `CS` (C varsayılan değer olan #), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="249ae-165">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="249ae-166">Ayrıca bir sınıf uygulamak için tam bir ad belirtin<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="249ae-166">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|  
|<span data-ttu-id="249ae-167">**/n**[**amespace**]**:***ad alanı*</span><span class="sxs-lookup"><span data-stu-id="249ae-167">**/n**[**amespace**]**:***namespace*</span></span>|<span data-ttu-id="249ae-168">Oluşturulan türleri için çalışma zamanı ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-168">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="249ae-169">Varsayılan ad alanı `Schemas`.</span><span class="sxs-lookup"><span data-stu-id="249ae-169">The default namespace is `Schemas`.</span></span>|  
|<span data-ttu-id="249ae-170">**/ nologo**</span><span class="sxs-lookup"><span data-stu-id="249ae-170">**/nologo**</span></span>|<span data-ttu-id="249ae-171">Başlık göstermez.</span><span class="sxs-lookup"><span data-stu-id="249ae-171">Suppresses the banner.</span></span>|  
|<span data-ttu-id="249ae-172">**/ORDER**</span><span class="sxs-lookup"><span data-stu-id="249ae-172">**/order**</span></span>|<span data-ttu-id="249ae-173">Tüm parçacık üyeleri açık sipariş tanımlayıcılarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-173">Generates explicit order identifiers on all particle members.</span></span>|  
|<span data-ttu-id="249ae-174">**/o [ut]:** *directoryName*</span><span class="sxs-lookup"><span data-stu-id="249ae-174">**/o[ut]:** *directoryName*</span></span>|<span data-ttu-id="249ae-175">Dosyalarında yerleştirmek için çıktı dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-175">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="249ae-176">Geçerli dizin varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="249ae-176">The default is the current directory.</span></span>|  
|<span data-ttu-id="249ae-177">**/u**[**RI**]**:***URI*</span><span class="sxs-lookup"><span data-stu-id="249ae-177">**/u**[**ri**]**:***uri*</span></span>|<span data-ttu-id="249ae-178">Öğeler için URI için kod oluşturmak için şema belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-178">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="249ae-179">Bu URI varsa, ile belirtilen tüm öğelere uygulanır `/element` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="249ae-179">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|  
  
## <a name="dll-and-exe-file-options"></a><span data-ttu-id="249ae-180">DLL ve EXE dosya seçenekleri</span><span class="sxs-lookup"><span data-stu-id="249ae-180">DLL and EXE File Options</span></span>  
  
|<span data-ttu-id="249ae-181">Seçenek</span><span class="sxs-lookup"><span data-stu-id="249ae-181">Option</span></span>|<span data-ttu-id="249ae-182">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-182">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="249ae-183">**/t**[**türü**]**:***typename*</span><span class="sxs-lookup"><span data-stu-id="249ae-183">**/t**[**ype**]**:***typename*</span></span>|<span data-ttu-id="249ae-184">Şema için oluşturulacak tür adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-184">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="249ae-185">Birden çok tür bağımsız değişkeni belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="249ae-185">You can specify multiple type arguments.</span></span> <span data-ttu-id="249ae-186">Varsa *typename* belirtilen türle tüm türleri bütünleştirilmiş kodunda XSD.exe'nin eşleşen bir ad alanı belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="249ae-186">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="249ae-187">Varsa *typename* türü eşleştiğini bir ad alanı, yalnızca belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-187">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="249ae-188">Varsa *typename* bir yıldız işareti karakteri ile sona erer (\*), yukarıdaki dize ile başlayan tüm türleri aracı eşleştirir \*.</span><span class="sxs-lookup"><span data-stu-id="249ae-188">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="249ae-189">Unutursanız, `/type` seçeneği XSD.exe'nin derlemesinde tüm türler için şemalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-189">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="249ae-190">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="249ae-190">Remarks</span></span>  
 <span data-ttu-id="249ae-191">Aşağıdaki tablo operasyonları XSD.exe'nin gerçekleştireceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="249ae-191">The following table shows the operations that Xsd.exe performs.</span></span>  
  
 <span data-ttu-id="249ae-192">XDR XSD için</span><span class="sxs-lookup"><span data-stu-id="249ae-192">XDR to XSD</span></span>  
 <span data-ttu-id="249ae-193">Bir XML şeması bir XML veri azaltılmış şema dosyasından oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-193">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="249ae-194">XDR erken bir XML tabanlı şema biçimidir.</span><span class="sxs-lookup"><span data-stu-id="249ae-194">XDR is an early XML-based schema format.</span></span>  
  
 <span data-ttu-id="249ae-195">XML için XSD</span><span class="sxs-lookup"><span data-stu-id="249ae-195">XML to XSD</span></span>  
 <span data-ttu-id="249ae-196">Bir XML Şeması XML dosyasından oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-196">Generates an XML schema from an XML file.</span></span>  
  
 <span data-ttu-id="249ae-197">Veri kümesi için XSD</span><span class="sxs-lookup"><span data-stu-id="249ae-197">XSD to DataSet</span></span>  
 <span data-ttu-id="249ae-198">Ortak dil çalışma zamanı oluşturur <xref:System.Data.DataSet> bir XSD şema dosyasından sınıfları.</span><span class="sxs-lookup"><span data-stu-id="249ae-198">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="249ae-199">Oluşturulan sınıflar için normal XML verileri zengin nesne modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="249ae-199">The generated classes provide a rich object model for regular XML data.</span></span>  
  
 <span data-ttu-id="249ae-200">XSD sınıflar için</span><span class="sxs-lookup"><span data-stu-id="249ae-200">XSD to Classes</span></span>  
 <span data-ttu-id="249ae-201">Bir XSD şema dosyasından çalışma zamanı sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-201">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="249ae-202">Oluşturulan sınıflar birlikte kullanılabilecek <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> okuma ve yazma şema izleyen XML kodu.</span><span class="sxs-lookup"><span data-stu-id="249ae-202">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>  
  
 <span data-ttu-id="249ae-203">XSD için sınıflar</span><span class="sxs-lookup"><span data-stu-id="249ae-203">Classes to XSD</span></span>  
 <span data-ttu-id="249ae-204">Bir XML şeması bir türü veya türleri bir çalışma zamanı derleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-204">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="249ae-205">Oluşturulan şema tarafından kullanılan XML biçiminde tanımlar `System.Xml.Serialization.XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="249ae-205">The generated schema defines the XML format used by `System.Xml.Serialization.XmlSerializer`.</span></span>  
  
 <span data-ttu-id="249ae-206">XSD.exe'nin yalnızca World Wide Web Konsorsiyumu (W3C) tarafından önerilen XML şema tanımı (XSD) dil izleyin XML şemaları yönetmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="249ae-206">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="249ae-207">Http://w3.org XML şema tanımı teklif veya XML standart hakkında daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="249ae-207">For more information on the XML Schema Definition proposal or the XML standard, see http://w3.org.</span></span>  
  
## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="249ae-208">Bir XML dosyası ile seçenekleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="249ae-208">Setting Options with an XML File</span></span>  
 <span data-ttu-id="249ae-209">Kullanarak `/parameters` anahtarı, çeşitli seçenekleri ayarlar tek bir XML dosyası belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="249ae-209">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="249ae-210">Nasıl XSD.exe'nin aracını kullanarak ayarlayabilirsiniz seçenekler bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="249ae-210">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="249ae-211">Seçenekler şunlardır şemaları oluşturmak, kod dosyaları oluşturmak veya dahil kod dosyaları oluşturmak `DataSet` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="249ae-211">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="249ae-212">Örneğin, ayarlayabilirsiniz `<assembly\>` öğesi için bir yürütülebilir (.exe) veya bir şema oluşturulurken türü kitaplık (.dll) dosyası, ancak bir kod dosyası değil oluşturulurken adı.</span><span class="sxs-lookup"><span data-stu-id="249ae-212">For example, you can set the `<assembly\>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="249ae-213">Aşağıdaki XML nasıl kullanılacağı gösterilmiştir `<generateSchemas\>` belirtilen yürütülebilir öğe:</span><span class="sxs-lookup"><span data-stu-id="249ae-213">The following XML shows how to use the `<generateSchemas\>` element with a specified executable:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemas.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <assembly>ConsoleApplication1.exe</assembly>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="249ae-214">Önceki XML GenerateSchemas.xml adındaki bir dosyada yer alıyorsa, daha sonra kullanmak `/parameters` bir komut istemine aşağıdakileri yazıp ENTER tuşuna basarak geçiş yapın:</span><span class="sxs-lookup"><span data-stu-id="249ae-214">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing ENTER:</span></span>  
  
 `xsd /p:GenerateSchemas.xml`  
  
 <span data-ttu-id="249ae-215">Diğer yandan, derlemede bulunan tek bir tür için bir şema oluşturuyorsanız, aşağıdaki XML kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="249ae-215">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemaFromType.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <type>IDItems</type>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="249ae-216">Ancak, önceki kodu kullanmak için da komut isteminde derlemenin adı sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="249ae-216">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="249ae-217">(Pek fazla XML dosyası GenerateSchemaFromType.xml adlı) bir komut istemine şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="249ae-217">Type the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>  
  
 `xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe`  
  
 <span data-ttu-id="249ae-218">İçin aşağıdaki seçeneklerden birini belirtmelisiniz `\<generateSchemas>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="249ae-218">You must specify only one of the following options for the `\<generateSchemas>` element.</span></span>  
  
|<span data-ttu-id="249ae-219">Öğe</span><span class="sxs-lookup"><span data-stu-id="249ae-219">Element</span></span>|<span data-ttu-id="249ae-220">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-220">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="249ae-221">\<derleme ></span><span class="sxs-lookup"><span data-stu-id="249ae-221">\<assembly></span></span>|<span data-ttu-id="249ae-222">Şema oluşturmak için bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-222">Specifies an assembly to generate the schema from.</span></span>|  
|<span data-ttu-id="249ae-223">\<türü ></span><span class="sxs-lookup"><span data-stu-id="249ae-223">\<type></span></span>|<span data-ttu-id="249ae-224">Bir türü için bir şema oluşturmak için bir derleme bulundu belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-224">Specifies a type found in an assembly to generate a schema for.</span></span>|  
|<span data-ttu-id="249ae-225">\<XML ></span><span class="sxs-lookup"><span data-stu-id="249ae-225">\<xml></span></span>|<span data-ttu-id="249ae-226">Bir XML dosyası için bir şema oluşturmak için belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-226">Specifies an XML file to generate a schema for.</span></span>|  
|<span data-ttu-id="249ae-227">\<XDR ></span><span class="sxs-lookup"><span data-stu-id="249ae-227">\<xdr></span></span>|<span data-ttu-id="249ae-228">İçin bir şema oluşturmak için bir XDR dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-228">Specifies an XDR file to generate a schema for.</span></span>|  
  
 <span data-ttu-id="249ae-229">Bir kod dosyası oluşturmak için kullanılan `<generateClasses\>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="249ae-229">To generate a code file, use the `<generateClasses\>` element.</span></span> <span data-ttu-id="249ae-230">Aşağıdaki örnek, bir kod dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-230">The following example generates a code file.</span></span> <span data-ttu-id="249ae-231">Bu ad alanı oluşturulan dosyanın ve programlama dili ayarlamanıza olanak sağlar, iki öznitelik aynı zamanda gösterilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="249ae-231">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>  
</xsd>  
<!-- You must supply an .xsd file when typing in the command line.-->  
<!-- For example: xsd /p:genClasses mySchema.xsd -->  
```  
  
 <span data-ttu-id="249ae-232">Seçenekleri için Ayarla `\<generateClasses>` öğesi şunlar.</span><span class="sxs-lookup"><span data-stu-id="249ae-232">Options you can set for the `\<generateClasses>` element include the following.</span></span>  
  
|<span data-ttu-id="249ae-233">Öğe</span><span class="sxs-lookup"><span data-stu-id="249ae-233">Element</span></span>|<span data-ttu-id="249ae-234">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-234">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="249ae-235">\<Öğe ></span><span class="sxs-lookup"><span data-stu-id="249ae-235">\<element></span></span>|<span data-ttu-id="249ae-236">Bir öğe için kod oluşturmak üzere .xsd dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-236">Specifies an element in the .xsd file to generate code for.</span></span>|  
|<span data-ttu-id="249ae-237">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="249ae-237">\<schemaImporterExtensions></span></span>|<span data-ttu-id="249ae-238">Türetilen bir türü belirtiyor. <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="249ae-238">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|  
|<span data-ttu-id="249ae-239">\<Şema ></span><span class="sxs-lookup"><span data-stu-id="249ae-239">\<schema></span></span>|<span data-ttu-id="249ae-240">Kodunu oluşturmak için bir XML şema dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-240">Specifies a XML Schema file to generate code for.</span></span>  <span data-ttu-id="249ae-241">Birden çok XML şema dosyaları, birden çok kullanılarak belirtilebilir \<şema > öğeleri.</span><span class="sxs-lookup"><span data-stu-id="249ae-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="249ae-242">Aşağıdaki tablo ile de kullanılabilir öznitelikleri gösterir `<generateClasses\>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="249ae-242">The following table shows the attributes that can also be used with the `<generateClasses\>` element.</span></span>  
  
|<span data-ttu-id="249ae-243">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="249ae-243">Attribute</span></span>|<span data-ttu-id="249ae-244">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-244">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="249ae-245">dil</span><span class="sxs-lookup"><span data-stu-id="249ae-245">language</span></span>|<span data-ttu-id="249ae-246">Kullanmak için programlama dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-246">Specifies the programming language to use.</span></span> <span data-ttu-id="249ae-247">Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="249ae-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="249ae-248">Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="249ae-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="249ae-249">ad alanı</span><span class="sxs-lookup"><span data-stu-id="249ae-249">namespace</span></span>|<span data-ttu-id="249ae-250">Oluşturulan kodun ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="249ae-251">Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.</span><span class="sxs-lookup"><span data-stu-id="249ae-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
|<span data-ttu-id="249ae-252">seçenekler</span><span class="sxs-lookup"><span data-stu-id="249ae-252">options</span></span>|<span data-ttu-id="249ae-253">Aşağıdaki değerlerden birini: `none`, `properties` (genel alanlar yerine özellikleri oluşturur), `order`, veya `enableDataBinding` (bkz `/order` ve `/enableDataBinding` önceki XSD dosyası seçenekleri bölümünde anahtarları.</span><span class="sxs-lookup"><span data-stu-id="249ae-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|  
  
 <span data-ttu-id="249ae-254">Ayrıca denetleyebilirsiniz nasıl `DataSet` kodu kullanarak oluşturulur `<generateDataSets\>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="249ae-254">You can also control how `DataSet` code is generated by using the `<generateDataSets\>` element.</span></span> <span data-ttu-id="249ae-255">Aşağıdaki XML belirleyen oluşturulan codeuses `DataSet` yapıları (gibi <xref:System.Data.DataTable> sınıfı) belirtilen bir öğe için Visual Basic kodu oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="249ae-255">The following XML specifies that the generated codeuses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="249ae-256">Oluşturulan veri kümesi yapıları LINQ sorgularını destekler.</span><span class="sxs-lookup"><span data-stu-id="249ae-256">The generated DataSet structures will support LINQ queries.</span></span>  
  
 `<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>`  
  
 `<generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>`  
  
 `</generateDataSet>`  
  
 `</xsd>`  
  
 <span data-ttu-id="249ae-257">Seçenekleri için Ayarla `<generateDataSet\>` öğesi şunlar.</span><span class="sxs-lookup"><span data-stu-id="249ae-257">Options you can set for the `<generateDataSet\>` element include the following.</span></span>  
  
|<span data-ttu-id="249ae-258">Öğe</span><span class="sxs-lookup"><span data-stu-id="249ae-258">Element</span></span>|<span data-ttu-id="249ae-259">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-259">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="249ae-260">\<Şema ></span><span class="sxs-lookup"><span data-stu-id="249ae-260">\<schema></span></span>|<span data-ttu-id="249ae-261">Kodunu oluşturmak için bir XML şeması dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-261">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="249ae-262">Birden çok XML şema dosyaları, birden çok kullanılarak belirtilebilir \<şema > öğeleri.</span><span class="sxs-lookup"><span data-stu-id="249ae-262">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="249ae-263">Aşağıdaki tabloda kullanılabilir öznitelikleri gösterir `<generateDataSet\>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="249ae-263">The following table shows the attributes that can be used with the `<generateDataSet\>` element.</span></span>  
  
|<span data-ttu-id="249ae-264">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="249ae-264">Attribute</span></span>|<span data-ttu-id="249ae-265">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-265">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="249ae-266">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="249ae-266">enableLinqDataSet</span></span>|<span data-ttu-id="249ae-267">Oluşturulan veri kümesi LINQ to DataSet kullanarak karşı sorgulanabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-267">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="249ae-268">Varsayılan değer false'tur.</span><span class="sxs-lookup"><span data-stu-id="249ae-268">The default value is false.</span></span>|  
|<span data-ttu-id="249ae-269">dil</span><span class="sxs-lookup"><span data-stu-id="249ae-269">language</span></span>|<span data-ttu-id="249ae-270">Kullanmak için programlama dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-270">Specifies the programming language to use.</span></span> <span data-ttu-id="249ae-271">Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="249ae-271">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="249ae-272">Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="249ae-272">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="249ae-273">ad alanı</span><span class="sxs-lookup"><span data-stu-id="249ae-273">namespace</span></span>|<span data-ttu-id="249ae-274">Oluşturulan kodun ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="249ae-274">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="249ae-275">Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.</span><span class="sxs-lookup"><span data-stu-id="249ae-275">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
  
 <span data-ttu-id="249ae-276">En üst düzey ayarlayabilirsiniz öznitelik `<xsd\>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="249ae-276">There are attributes that you can set on the top level `<xsd\>` element.</span></span> <span data-ttu-id="249ae-277">Herhangi bir alt öğelerinin bu seçenekler kullanılabilir (`<generateSchemas\>`, `<generateClasses\>` veya `<generateDataSet\>`).</span><span class="sxs-lookup"><span data-stu-id="249ae-277">These options can be used with any of the child elements (`<generateSchemas\>`, `<generateClasses\>` or `<generateDataSet\>`).</span></span> <span data-ttu-id="249ae-278">Aşağıdaki XML kodu "MyOutputDirectory" adlı Çıktı dizininde "IDItems" adlı bir öğe için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="249ae-278">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>  
<generateClasses>  
<element>IDItems</element>  
</generateClasses>  
</xsd>  
```  
  
 <span data-ttu-id="249ae-279">Aşağıdaki tablo ile de kullanılabilir öznitelikleri gösterir `\<xsd>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="249ae-279">The following table shows the attributes that can also be used with the `\<xsd>` element.</span></span>  
  
|<span data-ttu-id="249ae-280">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="249ae-280">Attribute</span></span>|<span data-ttu-id="249ae-281">Açıklama</span><span class="sxs-lookup"><span data-stu-id="249ae-281">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="249ae-282">çıktı</span><span class="sxs-lookup"><span data-stu-id="249ae-282">output</span></span>|<span data-ttu-id="249ae-283">Oluşturulan şema veya kod dosyanın yerleştirileceği bir dizinin adı.</span><span class="sxs-lookup"><span data-stu-id="249ae-283">The name of a directory where the generated schema or code file will be placed.</span></span>|  
|<span data-ttu-id="249ae-284">nologo</span><span class="sxs-lookup"><span data-stu-id="249ae-284">nologo</span></span>|<span data-ttu-id="249ae-285">Başlık göstermez.</span><span class="sxs-lookup"><span data-stu-id="249ae-285">Suppresses the banner.</span></span> <span data-ttu-id="249ae-286">Ayarlanan `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="249ae-286">Set to `true` or `false`.</span></span>|  
|<span data-ttu-id="249ae-287">Yardım</span><span class="sxs-lookup"><span data-stu-id="249ae-287">help</span></span>|<span data-ttu-id="249ae-288">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="249ae-288">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="249ae-289">Ayarlanan `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="249ae-289">Set to `true` or `false`.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="249ae-290">Örnekler</span><span class="sxs-lookup"><span data-stu-id="249ae-290">Examples</span></span>  
 <span data-ttu-id="249ae-291">Aşağıdaki komutu bir XML şema oluşturur `myFile.xdr` ve geçerli dizine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="249ae-291">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>  
  
```  
xsd myFile.xdr   
```  
  
 <span data-ttu-id="249ae-292">Aşağıdaki komutu bir XML şema oluşturur `myFile.xml` ve belirtilen dizine kaydeder.</span><span class="sxs-lookup"><span data-stu-id="249ae-292">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>  
  
```  
xsd myFile.xml /outputdir:myOutputDir  
```  
  
 <span data-ttu-id="249ae-293">Aşağıdaki komutu olarak kaydeder ve C# dili belirtilen şemada karşılık gelen bir veri kümesi oluşturur `XSDSchemaFile.cs` geçerli dizin.</span><span class="sxs-lookup"><span data-stu-id="249ae-293">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>  
  
```  
xsd /dataset /language:CS XSDSchemaFile.xsd  
```  
  
 <span data-ttu-id="249ae-294">Aşağıdaki komutu tüm türleri için XML şemaları derlemesinde oluşturur `myAssembly.dll` ve bunları olarak kaydeder `schema0.xsd` geçerli dizin.</span><span class="sxs-lookup"><span data-stu-id="249ae-294">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>  
  
```  
xsd myAssembly.dll    
```  
  
## <a name="see-also"></a><span data-ttu-id="249ae-295">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="249ae-295">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>  
 <span data-ttu-id="249ae-296">[Araçları](../../../docs/framework/tools/index.md)    </span><span class="sxs-lookup"><span data-stu-id="249ae-296">[Tools](../../../docs/framework/tools/index.md)    </span></span>  
 [<span data-ttu-id="249ae-297">Komut istemleri</span><span class="sxs-lookup"><span data-stu-id="249ae-297">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)  
 [<span data-ttu-id="249ae-298">LINQ-DataSet genel bakış</span><span class="sxs-lookup"><span data-stu-id="249ae-298">LINQ to DataSet Overview</span></span>](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="249ae-299">Yazılan veri kümeleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="249ae-299">Querying Typed DataSets</span></span>](../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="249ae-300">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="249ae-300">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)