---
title: Seri hale getirme (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 704ff2bf-02ab-4fea-94ea-594107825645
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b045f092bef837d1345b5f3b31df0a5ec22fc010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="serialization-c-"></a><span data-ttu-id="9e7a2-102">Seri hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="9e7a2-102">Serialization (C# )</span></span>
<span data-ttu-id="9e7a2-103">Seri hale getirme bir nesne, nesne depolamak veya bellek, bir veritabanı veya dosya aktarmak için baytı bir akışa dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-103">Serialization is the process of converting an object into a stream of bytes in order to store the object or transmit it to memory, a database, or a file.</span></span> <span data-ttu-id="9e7a2-104">Asıl amacı, gerektiğinde yeniden oluşturmak için bir nesnenin durumu tasarruf etmektir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-104">Its main purpose is to save the state of an object in order to be able to recreate it when needed.</span></span> <span data-ttu-id="9e7a2-105">Ters işlemi seri durumdan çıkarma adı verilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-105">The reverse process is called deserialization.</span></span>  
  
## <a name="how-serialization-works"></a><span data-ttu-id="9e7a2-106">Seri hale getirme nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="9e7a2-106">How Serialization Works</span></span>  
 <span data-ttu-id="9e7a2-107">Bu çizim serileştirme genel işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-107">This illustration shows the overall process of serialization.</span></span>  
  
 <span data-ttu-id="9e7a2-108">![Serileştirme Grafiği](../../../../csharp/programming-guide/concepts/serialization/media/serialization.gif "seri hale getirme")</span><span class="sxs-lookup"><span data-stu-id="9e7a2-108">![Serialization Graphic](../../../../csharp/programming-guide/concepts/serialization/media/serialization.gif "serialization")</span></span>  
  
 <span data-ttu-id="9e7a2-109">Yalnızca veri ancak sürüm, kültür ve derleme adı gibi nesnenin türü hakkında bilgi taşıyan bir akışa nesne seri.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-109">The object is serialized to a stream, which carries not just the data, but information about the object's type, such as its version, culture, and assembly name.</span></span> <span data-ttu-id="9e7a2-110">Bu akıştan, bir veritabanı, bir dosya veya bellek depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-110">From that stream, it can be stored in a database, a file, or memory.</span></span>  
  
### <a name="uses-for-serialization"></a><span data-ttu-id="9e7a2-111">Serileştirme için de kullanır</span><span class="sxs-lookup"><span data-stu-id="9e7a2-111">Uses for Serialization</span></span>  
 <span data-ttu-id="9e7a2-112">Seri hale getirme bir nesnenin durumunu kaydetmek ve gerekirse, veri değişimi yanı sıra nesneleri depolama sağlama yeniden oluşturmak geliştiricinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-112">Serialization allows the developer to save the state of an object and recreate it as needed, providing storage of objects as well as data exchange.</span></span> <span data-ttu-id="9e7a2-113">Seri hale getirme bir geliştirici nesne uzak uygulama için bir Web hizmeti aracılığıyla gönderme, bir nesne bir etki alanından diğerine geçirme, bir nesne bir güvenlik duvarı üzerinden XML dizesi olarak geçirme veya güvenliğini sağlama gibi eylemleri gerçekleştirebilir veya uygulamalar arasında kullanıcıya özgü bilgileri.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-113">Through serialization, a developer can perform actions like sending the object to a remote application by means of a Web Service, passing an object from one domain to another, passing an object through a firewall as an XML string, or maintaining security or user-specific information across applications.</span></span>  
  
### <a name="making-an-object-serializable"></a><span data-ttu-id="9e7a2-114">Bir nesne seri hale getirilebilir yapma</span><span class="sxs-lookup"><span data-stu-id="9e7a2-114">Making an Object Serializable</span></span>  
 <span data-ttu-id="9e7a2-115">Nesnenin seri hale getirilebilmesi için ihtiyacınız nesneyi serileştirmek için akış serileştirilmiş nesne içeren bir ve bir <xref:System.Runtime.Serialization.Formatter>.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-115">To serialize an object, you need the object to be serialized, a stream to contain the serialized object, and a <xref:System.Runtime.Serialization.Formatter>.</span></span> <span data-ttu-id="9e7a2-116"><xref:System.Runtime.Serialization>seri hale getirme ve nesneleri seri durumdan çıkarmak için gerekli olan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-116"><xref:System.Runtime.Serialization> contains the classes necessary for serializing and deserializing objects.</span></span>  
  
 <span data-ttu-id="9e7a2-117">Uygulama <xref:System.SerializableAttribute> özniteliği, bu türdeki örneklerin serileştirilebilir belirtmek için bir tür.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-117">Apply the <xref:System.SerializableAttribute> attribute to a type to indicate that instances of this type can be serialized.</span></span> <span data-ttu-id="9e7a2-118">A <xref:System.Runtime.Serialization.SerializationException> serileştirmek girişiminde bulunan ancak türüne sahip değil, özel durum <xref:System.SerializableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-118">A <xref:System.Runtime.Serialization.SerializationException> exception is thrown if you attempt to serialize but the type does not have the <xref:System.SerializableAttribute> attribute.</span></span>  
  
 <span data-ttu-id="9e7a2-119">Seri hale getirilebilir sınıfınız bir alanı istemiyorsanız uygulamak <xref:System.NonSerializedAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-119">If you do not want a field within your class to be serializable, apply the <xref:System.NonSerializedAttribute> attribute.</span></span> <span data-ttu-id="9e7a2-120">Seri hale getirilebilir türünde bir alan bir işaretçi, bir tanıtıcı ya da belirli bir ortama özgü bazı bir veri yapısı içeren ve alan anlamlı farklı bir ortamda reconstituted olamaz, nonserializable yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-120">If a field of a serializable type contains a pointer, a handle, or some other data structure that is specific to a particular environment, and the field cannot be meaningfully reconstituted in a different environment, then you may want to make it nonserializable.</span></span>  
  
 <span data-ttu-id="9e7a2-121">Seri hale getirilmiş bir sınıf işaretlenen diğer sınıfların nesnelerini başvurular içeriyorsa <xref:System.SerializableAttribute>, bu nesneler de seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-121">If a serialized class contains references to objects of other classes that are marked <xref:System.SerializableAttribute>, those objects will also be serialized.</span></span>  
  
## <a name="binary-and-xml-serialization"></a><span data-ttu-id="9e7a2-122">İkili ve XML serileştirme</span><span class="sxs-lookup"><span data-stu-id="9e7a2-122">Binary and XML Serialization</span></span>  
 <span data-ttu-id="9e7a2-123">İkili veya XML serileştirme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-123">Either binary or XML serialization can be used.</span></span> <span data-ttu-id="9e7a2-124">İkili seri hale getirme, tüm üyeleri, salt okunur olanlar bile serileştirilen ve performansı geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-124">In binary serialization, all members, even those that are read-only, are serialized, and performance is enhanced.</span></span> <span data-ttu-id="9e7a2-125">XML serileştirme, daha okunabilir kod gibi nesne paylaşımı ve birlikte çalışabilirlik amacıyla kullanımı daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-125">XML serialization provides more readable code, as well as greater flexibility of object sharing and usage for interoperability purposes.</span></span>  
  
### <a name="binary-serialization"></a><span data-ttu-id="9e7a2-126">İkili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9e7a2-126">Binary Serialization</span></span>  
 <span data-ttu-id="9e7a2-127">İkili seri hale getirme, depolama veya ağ yuva tabanlı akışları gibi kullanımlar için compact serileştirme üretmek için ikili kodlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-127">Binary serialization uses binary encoding to produce compact serialization for uses such as storage or socket-based network streams.</span></span>  
  
### <a name="xml-serialization"></a><span data-ttu-id="9e7a2-128">XML seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9e7a2-128">XML Serialization</span></span>  
 <span data-ttu-id="9e7a2-129">XML serileştirme, belirli bir XML Şeması Tanım Dili (XSD) belge uyan bir XML akışı içine genel alanlar ve bir nesne veya özelliklerini parametreler ve dönüş değerleri yöntemlerden serileştirir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-129">XML serialization serializes the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="9e7a2-130">XML serileştirme sonuçlarında genel özellikleri ve XML biçimine dönüştürülür alanları sınıflarıyla kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-130">XML serialization results in strongly typed classes with public properties and fields that are converted to XML.</span></span> <span data-ttu-id="9e7a2-131"><xref:System.Xml.Serialization>seri hale getirme ve XML seri durumdan çıkarmak için gerekli olan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-131"><xref:System.Xml.Serialization> contains the classes necessary for serializing and deserializing XML.</span></span>  
  
 <span data-ttu-id="9e7a2-132">Öznitelikler sınıflar ve sınıf üyeleri için şeklini denetlemek için uygulayabileceğiniz <xref:System.Xml.Serialization.XmlSerializer> serileştiren veya sınıfının bir örneği seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-132">You can apply attributes to classes and class members in order to control the way the <xref:System.Xml.Serialization.XmlSerializer> serializes or deserializes an instance of the class.</span></span>  
  
## <a name="basic-and-custom-serialization"></a><span data-ttu-id="9e7a2-133">Temel ve özel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9e7a2-133">Basic and Custom Serialization</span></span>  
 <span data-ttu-id="9e7a2-134">İki yolla temel ve özel serileştirme gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-134">Serialization can be performed in two ways, basic and custom.</span></span> <span data-ttu-id="9e7a2-135">Temel serileştirme .NET Framework otomatik olarak nesneyi serileştirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-135">Basic serialization uses the .NET Framework to automatically serialize the object.</span></span>  
  
### <a name="basic-serialization"></a><span data-ttu-id="9e7a2-136">Temel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9e7a2-136">Basic Serialization</span></span>  
 <span data-ttu-id="9e7a2-137">Yalnızca temel serileştirmede nesnesinde olduğunu gereksinimdir <xref:System.SerializableAttribute> özniteliği uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-137">The only requirement in basic serialization is that the object has the <xref:System.SerializableAttribute> attribute applied.</span></span> <span data-ttu-id="9e7a2-138"><xref:System.NonSerializedAttribute> Seri hale belirli alanları korumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-138">The <xref:System.NonSerializedAttribute> can be used to keep specific fields from being serialized.</span></span>  
  
 <span data-ttu-id="9e7a2-139">Temel serileştirme kullandığınızda, nesnelerin sürüm oluşturma, bu durumda özel seri duruma getirmeyi tercih edilebilir sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-139">When you use basic serialization, the versioning of objects may create problems, in which case custom serialization may be preferable.</span></span> <span data-ttu-id="9e7a2-140">Temel serileştirme serileştirme gerçekleştirmek için en kolay yoludur ancak işlem üzerinde kadar denetim sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-140">Basic serialization is the easiest way to perform serialization, but it does not provide much control over the process.</span></span>  
  
### <a name="custom-serialization"></a><span data-ttu-id="9e7a2-141">Özel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9e7a2-141">Custom Serialization</span></span>  
 <span data-ttu-id="9e7a2-142">İçinde özel serileştirme, tam olarak hangi nesneleri seri hale getirilir ve nasıl yapılacağıyla belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-142">In custom serialization, you can specify exactly which objects will be serialized and how it will be done.</span></span> <span data-ttu-id="9e7a2-143">Sınıf işaretlenmelidir <xref:System.SerializableAttribute> ve uygulamanıza <xref:System.Runtime.Serialization.ISerializable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-143">The class must be marked <xref:System.SerializableAttribute> and implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="9e7a2-144">Bir özel biçimde seri durumdan çıkarılacak nesnenizin istiyorsanız, bir özel Oluşturucu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-144">If you want your object to be deserialized in a custom manner as well, you must use a custom constructor.</span></span>  
  
## <a name="designer-serialization"></a><span data-ttu-id="9e7a2-145">Tasarımcı seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9e7a2-145">Designer Serialization</span></span>  
 <span data-ttu-id="9e7a2-146">Tasarımcı serileştirme genellikle geliştirme araçları ile ilişkilendirilmiş nesne Kalıcılık türü içerir serileştirme özel biçimidir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-146">Designer serialization is a special form of serialization that involves the kind of object persistence usually associated with development tools.</span></span> <span data-ttu-id="9e7a2-147">Tasarımcı serileştirme bir nesne grafiğinin nesne grafiğinin kurtarmak için daha sonra kullanılabilir bir kaynak dosyasına dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-147">Designer serialization is the process of converting an object graph into a source file that can later be used to recover the object graph.</span></span> <span data-ttu-id="9e7a2-148">Bir kaynak dosyası kodu, biçimlendirme veya hatta SQL tablo bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-148">A source file can contain code, markup, or even SQL table information.</span></span>  
  
##  <a name="BKMK_RelatedTopics"></a><span data-ttu-id="9e7a2-149">İlgili Konular ve örnekler</span><span class="sxs-lookup"><span data-stu-id="9e7a2-149">Related Topics and Examples</span></span>  
 [<span data-ttu-id="9e7a2-150">İzlenecek yol: Visual Studio'da (C#) bir nesneyi kalıcı kılma</span><span class="sxs-lookup"><span data-stu-id="9e7a2-150">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 <span data-ttu-id="9e7a2-151">Bir nesnenin veri değerlerini depolamak ve nesne örneği sonraki açışınızda almak sağlayarak örnekleri arasında kalıcı hale getirmek için seri hale getirme'nın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-151">Demonstrates how serialization can be used to persist an object's data between instances, allowing you to store values and retrieve them the next time the object is instantiated.</span></span>  
  
 [<span data-ttu-id="9e7a2-152">Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma</span><span class="sxs-lookup"><span data-stu-id="9e7a2-152">How to: Read Object Data from an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 <span data-ttu-id="9e7a2-153">Daha önce bir XML dosyası kullanmaya yazıldı nesne verilerini okuma gösterilmektedir <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-153">Shows how to read object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
 [<span data-ttu-id="9e7a2-154">Nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma</span><span class="sxs-lookup"><span data-stu-id="9e7a2-154">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 <span data-ttu-id="9e7a2-155">Bir XML dosyası kullanarak bir sınıftan nesne yazmak gösterilmiştir <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9e7a2-155">Shows how to write the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>