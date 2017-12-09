---
title: Visual Basic'de IEnumerable arabirimini uygulama
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45b4008f0bf3ae0f303aa029e7bff5b82ab6f259
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a><span data-ttu-id="876f0-102">İzlenecek yol: Visual Basic'de IEnumerable(Of T) Uygulama</span><span class="sxs-lookup"><span data-stu-id="876f0-102">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>
<span data-ttu-id="876f0-103"><xref:System.Collections.Generic.IEnumerable%601> Arabirimi değerleri bir öğe dizisi aynı anda geri dönebilirsiniz sınıflar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="876f0-103">The <xref:System.Collections.Generic.IEnumerable%601> interface is implemented by classes that can return a sequence of values one item at a time.</span></span> <span data-ttu-id="876f0-104">Bir seferde bir öğe ile çalışması belleğe eksiksiz veri yüklemek gerekmez veri döndüren avantajı.</span><span class="sxs-lookup"><span data-stu-id="876f0-104">The advantage of returning data one item at a time is that you do not have to load the complete set of data into memory to work with it.</span></span> <span data-ttu-id="876f0-105">Yalnızca tek bir öğe verileri yüklemek için yeterli bellek kullanmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="876f0-105">You only have to use sufficient memory to load a single item from the data.</span></span> <span data-ttu-id="876f0-106">Sınıfları uygulayan `IEnumerable(T)` arabirimi ile kullanılabilir `For Each` döngüler veya LINQ sorgularını.</span><span class="sxs-lookup"><span data-stu-id="876f0-106">Classes that implement the `IEnumerable(T)` interface can be used with `For Each` loops or LINQ queries.</span></span>  
  
 <span data-ttu-id="876f0-107">Örneğin, gereken büyük metin dosyası okuma ve her satırın belirli arama ölçütleriyle eşleşen dosyasından bir uygulama göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="876f0-107">For example, consider an application that must read a large text file and return each line from the file that matches particular search criteria.</span></span> <span data-ttu-id="876f0-108">Uygulama, belirtilen ölçütlerle eşleşen dosyasından satırlar döndürülecek LINQ sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="876f0-108">The application uses a LINQ query to return lines from the file that match the specified criteria.</span></span> <span data-ttu-id="876f0-109">Dosya içeriğini bir LINQ Sorgu kullanarak sorgulamak için uygulama dosyasının içeriğini bir dizi veya bir koleksiyon yükleyemedik.</span><span class="sxs-lookup"><span data-stu-id="876f0-109">To query the contents of the file by using a LINQ query, the application could load the contents of the file into an array or a collection.</span></span> <span data-ttu-id="876f0-110">Ancak, bir dizi veya koleksiyon dosyanın tamamını yüklenirken gerekenden çok daha fazla bellek kullanılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="876f0-110">However, loading the whole file into an array or collection would consume far more memory than is required.</span></span> <span data-ttu-id="876f0-111">LINQ sorgusu, bunun yerine arama ölçütleriyle eşleşen değerler döndüren bir numaralandırılabilir sınıfını kullanarak dosya içeriklerini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="876f0-111">The LINQ query could instead query the file contents by using an enumerable class, returning only values that match the search criteria.</span></span> <span data-ttu-id="876f0-112">Yalnızca birkaç döndüren sorgular eşleşen değerleri çok daha az bellek kullanmak.</span><span class="sxs-lookup"><span data-stu-id="876f0-112">Queries that return only a few matching values would consume far less memory.</span></span>  
  
 <span data-ttu-id="876f0-113">Uygulayan bir sınıf oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> kaynak veri numaralandırılabilir veri olarak kullanıma sunmak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="876f0-113">You can create a class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface to expose source data as enumerable data.</span></span> <span data-ttu-id="876f0-114">Uygulayan sınıfınız `IEnumerable(T)` arabirimi uygulayan başka bir sınıf gerektirecektir <xref:System.Collections.Generic.IEnumerator%601> kaynak verilerine yinelemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="876f0-114">Your class that implements the `IEnumerable(T)` interface will require another class that implements the <xref:System.Collections.Generic.IEnumerator%601> interface to iterate through the source data.</span></span> <span data-ttu-id="876f0-115">Bu iki sınıf veri öğeleri belirli bir tür olarak sıralı olarak döndürmek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="876f0-115">These two classes enable you to return items of data sequentially as a specific type.</span></span>  
  
 <span data-ttu-id="876f0-116">Bu kılavuzda, uygulayan bir sınıf oluşturacak `IEnumerable(Of String)` arabirimi ve uygulayan bir sınıf `IEnumerator(Of String)` aynı anda metin dosyası tek bir çizgi okumak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="876f0-116">In this walkthrough, you will create a class that implements the `IEnumerable(Of String)` interface and a class that implements the `IEnumerator(Of String)` interface to read a text file one line at a time.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a><span data-ttu-id="876f0-117">Numaralandırılabilir sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="876f0-117">Creating the Enumerable Class</span></span>  
  
|<span data-ttu-id="876f0-118">Numaralandırılabilir sınıfı projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="876f0-118">To create the enumerable class project</span></span>|  
|---|  
|<span data-ttu-id="876f0-119">1.  İçinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], **dosya** menüsündeki **yeni** ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="876f0-119">1.  In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], on the **File** menu, point to **New** and then click **Project**.</span></span><br /><span data-ttu-id="876f0-120">2.  İçinde **yeni proje** iletişim kutusunda **proje türleri** bölmesinde olduğundan emin olun **Windows** seçilir.</span><span class="sxs-lookup"><span data-stu-id="876f0-120">2.  In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="876f0-121">Seçin **sınıf kitaplığı** içinde **şablonları** bölmesi.</span><span class="sxs-lookup"><span data-stu-id="876f0-121">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="876f0-122">İçinde **adı** kutusuna `StreamReaderEnumerable`ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="876f0-122">In the **Name** box, type `StreamReaderEnumerable`, and then click **OK**.</span></span> <span data-ttu-id="876f0-123">Yeni Proje görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="876f0-123">The new project is displayed.</span></span><br /><span data-ttu-id="876f0-124">3.  İçinde **Çözüm Gezgini**, Class1.vb'ye dosyasını sağ tıklatın ve **yeniden adlandırma**.</span><span class="sxs-lookup"><span data-stu-id="876f0-124">3.  In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="876f0-125">Dosyayı Yeniden Adlandır `StreamReaderEnumerable.vb` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="876f0-125">Rename the file to `StreamReaderEnumerable.vb` and press ENTER.</span></span> <span data-ttu-id="876f0-126">Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `StreamReaderEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="876f0-126">Renaming the file will also rename the class to `StreamReaderEnumerable`.</span></span> <span data-ttu-id="876f0-127">Bu sınıf gerçekleştireceksiniz `IEnumerable(Of String)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="876f0-127">This class will implement the `IEnumerable(Of String)` interface.</span></span><br /><span data-ttu-id="876f0-128">4.  StreamReaderEnumerable projeye sağ tıklayın, fareyle **Ekle**ve ardından **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="876f0-128">4.  Right-click the StreamReaderEnumerable project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="876f0-129">Seçin **sınıfı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="876f0-129">Select the **Class** template.</span></span> <span data-ttu-id="876f0-130">İçinde **adı** kutusuna `StreamReaderEnumerator.vb` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="876f0-130">In the **Name** box, type `StreamReaderEnumerator.vb` and click **OK**.</span></span>|  
  
 <span data-ttu-id="876f0-131">İlk sınıf bu projede numaralandırılabilir sınıftır ve gerçekleştireceksiniz `IEnumerable(Of String)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="876f0-131">The first class in this project is the enumerable class and will implement the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="876f0-132">Bu genel arabirimini uygulayan <xref:System.Collections.IEnumerable> arabirimi ve bu sınıfın tüketicileri olarak yazılan değerleri erişebilirsiniz garanti `String`.</span><span class="sxs-lookup"><span data-stu-id="876f0-132">This generic interface implements the <xref:System.Collections.IEnumerable> interface and guarantees that consumers of this class can access values typed as `String`.</span></span>  
  
|<span data-ttu-id="876f0-133">IEnumerable uygulamak üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="876f0-133">To add the code to implement IEnumerable</span></span>|  
|---|  
|<span data-ttu-id="876f0-134">1.  StreamReaderEnumerable.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="876f0-134">1.  Open the StreamReaderEnumerable.vb file.</span></span><br /><span data-ttu-id="876f0-135">2.  Sonra satırındaki `Public Class StreamReaderEnumerable`, aşağıdaki komutu yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="876f0-135">2.  On the line after `Public Class StreamReaderEnumerable`, type the following and press ENTER.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="876f0-136">sınıfı tarafından gerekli üyeleri ile otomatik olarak doldurur `IEnumerable(Of String)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="876f0-136"> automatically populates the class with the members that are required by the `IEnumerable(Of String)` interface.</span></span><br /><span data-ttu-id="876f0-137">3.  Bu numaralandırılabilir sınıf aynı anda bir metin dosyası bir satırından satırları okuyun.</span><span class="sxs-lookup"><span data-stu-id="876f0-137">3.  This enumerable class will read lines from a text file one line at a time.</span></span> <span data-ttu-id="876f0-138">Bir dosya yolu giriş parametresi olarak alan bir public oluşturucuya kullanıma sunmak için sınıfa aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="876f0-138">Add the following code to the class to expose a public constructor that takes a file path as an input parameter.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br /><span data-ttu-id="876f0-139">4.  Uygulamanıza <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi `IEnumerable(Of String)` arabirimi yeni bir örneğini döndürür `StreamReaderEnumerator` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="876f0-139">4.  Your implementation of the <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method of the `IEnumerable(Of String)` interface will return a new instance of the `StreamReaderEnumerator` class.</span></span> <span data-ttu-id="876f0-140">Uygulaması `GetEnumerator` yöntemi `IEnumerable` arabirimi yapılabilir `Private`, yalnızca üyeleri kullanıma sunmak olduğundan `IEnumerable(Of String)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="876f0-140">The implementation of the `GetEnumerator` method of the `IEnumerable` interface can be made `Private`, because you have to expose only members of the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="876f0-141">Kod değiştirin, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] için oluşturulan `GetEnumerator` aşağıdaki kodla yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="876f0-141">Replace the code that [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generated for the `GetEnumerator` methods with the following code.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|<span data-ttu-id="876f0-142">Uygulamak üzere kod eklemek için</span><span class="sxs-lookup"><span data-stu-id="876f0-142">To add the code to implement IEnumerator</span></span>|  
|---|  
|<span data-ttu-id="876f0-143">1.  StreamReaderEnumerator.vb dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="876f0-143">1.  Open the StreamReaderEnumerator.vb file.</span></span><br /><span data-ttu-id="876f0-144">2.  Sonra satırındaki `Public Class StreamReaderEnumerator`, aşağıdaki komutu yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="876f0-144">2.  On the line after `Public Class StreamReaderEnumerator`, type the following and press ENTER.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="876f0-145">sınıfı tarafından gerekli üyeleri ile otomatik olarak doldurur `IEnumerator(Of String)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="876f0-145"> automatically populates the class with the members that are required by the `IEnumerator(Of String)` interface.</span></span><br /><span data-ttu-id="876f0-146">3.  Numaralandırıcı sınıfı metin dosyası açılır ve dosyanın g/ç satırları dosyasını okumaya gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="876f0-146">3.  The enumerator class opens the text file and performs the file I/O to read the lines from the file.</span></span> <span data-ttu-id="876f0-147">Metin dosyası okuma için'ni açın ve bir dosya yolu giriş parametresi olarak alan bir public oluşturucuya kullanıma sunmak için sınıfa aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="876f0-147">Add the following code to the class to expose a public constructor that takes a file path as an input parameter and open the text file for reading.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br /><span data-ttu-id="876f0-148">4.  `Current` Özellikleri her ikisi için de `IEnumerator(Of String)` ve `IEnumerator` arabirimleri metin dosyasından geçerli öğeye dönmesini bir `String`.</span><span class="sxs-lookup"><span data-stu-id="876f0-148">4.  The `Current` properties for both the `IEnumerator(Of String)` and `IEnumerator` interfaces return the current item from the text file as a `String`.</span></span> <span data-ttu-id="876f0-149">Uygulaması `Current` özelliği `IEnumerator` arabirimi yapılabilir `Private`, yalnızca üyeleri kullanıma sunmak olduğundan `IEnumerator(Of String)` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="876f0-149">The implementation of the `Current` property of the `IEnumerator` interface can be made `Private`, because you have to expose only members of the `IEnumerator(Of String)` interface.</span></span> <span data-ttu-id="876f0-150">Kod değiştirin, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] için oluşturulan `Current` aşağıdaki kodla özellikleri.</span><span class="sxs-lookup"><span data-stu-id="876f0-150">Replace the code that [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generated for the `Current` properties with the following code.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br /><span data-ttu-id="876f0-151">5.  `MoveNext` Yöntemi `IEnumerator` arabirimi metin dosyasındaki bir sonraki öğeye gider ve tarafından döndürülen değer güncelleştirmeleri `Current` özelliği.</span><span class="sxs-lookup"><span data-stu-id="876f0-151">5.  The `MoveNext` method of the `IEnumerator` interface navigates to the next item in the text file and updates the value that is returned by the `Current` property.</span></span> <span data-ttu-id="876f0-152">Okumak için daha fazla öğe varsa `MoveNext` yöntemi döndürür `False`; Aksi halde `MoveNext` yöntemi döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="876f0-152">If there are no more items to read, the `MoveNext` method returns `False`; otherwise the `MoveNext` method returns `True`.</span></span> <span data-ttu-id="876f0-153">Aşağıdaki kodu ekleyin `MoveNext` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="876f0-153">Add the following code to the `MoveNext` method.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br /><span data-ttu-id="876f0-154">6.  `Reset` Yöntemi `IEnumerator` arabirimi metin dosyasının başlangıcına işaret edecek şekilde yineleyici yönlendirir ve geçerli öğe değeri temizler.</span><span class="sxs-lookup"><span data-stu-id="876f0-154">6.  The `Reset` method of the `IEnumerator` interface directs the iterator to point to the start of the text file and clears the current item value.</span></span> <span data-ttu-id="876f0-155">Aşağıdaki kodu ekleyin `Reset` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="876f0-155">Add the following code to the `Reset` method.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br /><span data-ttu-id="876f0-156">7.  `Dispose` Yöntemi `IEnumerator` arabirimi garanti yineleyici yok önce tüm yönetilmeyen kaynakları serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="876f0-156">7.  The `Dispose` method of the `IEnumerator` interface guarantees that all unmanaged resources are released before the iterator is destroyed.</span></span> <span data-ttu-id="876f0-157">Tarafından kullanılan dosya tanıtıcısı `StreamReader` nesne yönetilmeyen bir kaynaktır ve yineleyici örneği yok önce kapatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="876f0-157">The file handle that is used by the `StreamReader` object is an unmanaged resource and must be closed before the iterator instance is destroyed.</span></span> <span data-ttu-id="876f0-158">Kod değiştirin, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] için oluşturulan `Dispose` aşağıdaki kod ile yöntemi.</span><span class="sxs-lookup"><span data-stu-id="876f0-158">Replace the code that [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generated for the `Dispose` method with the following code.</span></span><br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a><span data-ttu-id="876f0-159">Örnek yineleyici kullanma</span><span class="sxs-lookup"><span data-stu-id="876f0-159">Using the Sample Iterator</span></span>  
 <span data-ttu-id="876f0-160">Numaralandırılabilir bir sınıf kodunuzda uygulayan bir nesneye gerekli denetim yapıları ile birlikte kullanabileceğiniz `IEnumerable`, gibi bir `For Next` döngü ya da bir LINQ Sorgu.</span><span class="sxs-lookup"><span data-stu-id="876f0-160">You can use an enumerable class in your code together with control structures that require an object that implements `IEnumerable`, such as a `For Next` loop or a LINQ query.</span></span> <span data-ttu-id="876f0-161">Aşağıdaki örnekte gösterildiği `StreamReaderEnumerable` LINQ Sorgu.</span><span class="sxs-lookup"><span data-stu-id="876f0-161">The following example shows the `StreamReaderEnumerable` in a LINQ query.</span></span>  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="876f0-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="876f0-162">See Also</span></span>  
 [<span data-ttu-id="876f0-163">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="876f0-163">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="876f0-164">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="876f0-164">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="876f0-165">Döngü yapıları</span><span class="sxs-lookup"><span data-stu-id="876f0-165">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="876f0-166">For Each... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="876f0-166">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)