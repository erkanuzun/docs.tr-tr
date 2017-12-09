---
title: "Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme"
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
helpviewer_keywords: parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c21aadf70eaccafc8c8ec9c4efefff1c66abc6b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a><span data-ttu-id="29adf-102">Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme</span><span class="sxs-lookup"><span data-stu-id="29adf-102">How to: Iterate File Directories with the Parallel Class</span></span>
<span data-ttu-id="29adf-103">Çoğu durumda, dosya yineleme kolayca paralel birkaç ölçeklendirin bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="29adf-103">In many cases, file iteration is an operation that can be easily parallelized.</span></span> <span data-ttu-id="29adf-104">Konu [nasıl yapılır: PLINQ ile dosya dizinlerini yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) birçok senaryoları için bu görevi gerçekleştirmek için en kolay yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="29adf-104">The topic [How to: Iterate File Directories with PLINQ](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) shows the easiest way to perform this task for many scenarios.</span></span> <span data-ttu-id="29adf-105">Ancak, kodunuzu türlerde dosya sistemi erişirken ortaya çıkabilecek özel durumlar dağıtılacak olduğunda zorluklar ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="29adf-105">However, complications can arise when your code has to deal with the many types of exceptions that can arise when accessing the file system.</span></span> <span data-ttu-id="29adf-106">Aşağıdaki örnek, soruna yönelik bir yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="29adf-106">The following example shows one approach to the problem.</span></span> <span data-ttu-id="29adf-107">Tüm dosya ve klasörlerin belirtilen dizin altında çapraz geçiş için yığın tabanlı yineleme kullanır ve yakalamak ve çeşitli özel durumları işleme kodunuzu sağlar.</span><span class="sxs-lookup"><span data-stu-id="29adf-107">It uses a stack-based iteration to traverse all files and folders under a specified directory, and it enables your code to catch and handle various exceptions.</span></span> <span data-ttu-id="29adf-108">Elbette, özel durumları işleme biçimini size bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="29adf-108">Of course, the way that you handle the exceptions is up to you.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29adf-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="29adf-109">Example</span></span>  
 <span data-ttu-id="29adf-110">Aşağıdaki örnek, dizinleri sırayla tekrarlanan ancak paralel dosyaları işler.</span><span class="sxs-lookup"><span data-stu-id="29adf-110">The following example iterates the directories sequentially, but processes the files in parallel.</span></span> <span data-ttu-id="29adf-111">Büyük bir dosya dizin oranı varsa, bu büyük olasılıkla en iyi yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="29adf-111">This is probably the best approach when you have a large file-to-directory ratio.</span></span> <span data-ttu-id="29adf-112">Dizin Yineleme paralel hale ve her dosya sıralı olarak erişmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="29adf-112">It is also possible to parallelize the directory iteration, and access each file sequentially.</span></span> <span data-ttu-id="29adf-113">Bu, özellikle çok sayıda işlemciye sahip bir makine hedeflediğiniz sürece her iki döngüler paralel hale verimli büyük olasılıkla değil.</span><span class="sxs-lookup"><span data-stu-id="29adf-113">It is probably not efficient to parallelize both loops unless you are specifically targeting a machine with a large number of processors.</span></span> <span data-ttu-id="29adf-114">Ancak, tüm durumlarda olduğu gibi en iyi yaklaşımı kapsamlı olarak belirlemek için uygulamanızı test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="29adf-114">However, as in all cases, you should test your application thoroughly to determine the best approach.</span></span>  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 <span data-ttu-id="29adf-115">Bu örnekte, dosya g/ç zaman uyumlu olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="29adf-115">In this example, the file I/O is performed synchronously.</span></span> <span data-ttu-id="29adf-116">Büyük dosyaları veya yavaş ağ bağlantıları ile ilgilenirken, dosyaları zaman uyumsuz olarak erişmek için tercih edilebilir.</span><span class="sxs-lookup"><span data-stu-id="29adf-116">When dealing with large files or slow network connections, it might be preferable to access the files asynchronously.</span></span> <span data-ttu-id="29adf-117">Zaman uyumsuz g/ç teknikleri paralel yineleme ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29adf-117">You can combine asynchronous I/O techniques with parallel iteration.</span></span> <span data-ttu-id="29adf-118">Daha fazla bilgi için bkz: [TPL ve geleneksel .NET Framework zaman uyumsuz Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).</span><span class="sxs-lookup"><span data-stu-id="29adf-118">For more information, see [TPL and Traditional .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).</span></span>  
  
 <span data-ttu-id="29adf-119">Yerel örnek kullanan `fileCount` işlenen dosya sayısı toplam sayısını korumak için değişkeni.</span><span class="sxs-lookup"><span data-stu-id="29adf-119">The example uses the local `fileCount` variable to maintain a count of the total number of files processed.</span></span> <span data-ttu-id="29adf-120">Değişkeni eşzamanlı olarak birden çok görev tarafından erişilen çünkü erişimi çağırarak eşitlenir <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29adf-120">Because the variable might be accessed concurrently by multiple tasks, access to it is synchronized by calling the <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="29adf-121">Ana bir özel durum, iş parçacığı tarafından başlatılan iş parçacığı açtıysanız <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemi çalışmaya devam edecek.</span><span class="sxs-lookup"><span data-stu-id="29adf-121">Note that if an exception is thrown on the main thread, the threads that are started by the <xref:System.Threading.Tasks.Parallel.ForEach%2A> method might continue to run.</span></span> <span data-ttu-id="29adf-122">Bu iş parçacıkları durdurmak için özel durum işleyicileri Boole değişkenini ve değerini her döngü paralel üzerinde denetleyin.</span><span class="sxs-lookup"><span data-stu-id="29adf-122">To stop these threads, you can set a Boolean variable in your exception handlers, and check its value on each iteration of the parallel loop.</span></span> <span data-ttu-id="29adf-123">Bir özel durum değeri gösterir kullanırsanız <xref:System.Threading.Tasks.ParallelLoopState> durdurmak veya döngüden ayırmak değişkeni.</span><span class="sxs-lookup"><span data-stu-id="29adf-123">If the value indicates that an exception has been thrown, use the <xref:System.Threading.Tasks.ParallelLoopState> variable to stop or break from the loop.</span></span> <span data-ttu-id="29adf-124">Daha fazla bilgi için bkz: [nasıl yapılır: durdurun ya da bir Parallel.For döngüden bölün](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).</span><span class="sxs-lookup"><span data-stu-id="29adf-124">For more information, see [How to: Stop or Break from a Parallel.For Loop](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29adf-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29adf-125">See Also</span></span>  
 [<span data-ttu-id="29adf-126">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="29adf-126">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)