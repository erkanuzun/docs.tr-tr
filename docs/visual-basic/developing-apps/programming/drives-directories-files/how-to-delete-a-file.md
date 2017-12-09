---
title: "Nasıl Yapılır: Visual Basic'te Dosya Silme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 536c10070ef51044b801fc6a5805741896586dff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="4d6e3-102">Nasıl Yapılır: Visual Basic'te Dosya Silme</span><span class="sxs-lookup"><span data-stu-id="4d6e3-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="4d6e3-103">`DeleteFile` Yöntemi `My.Computer.FileSystem` nesne bir dosyayı silmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="4d6e3-104">Sunduğu seçenekler arasında: silinen dosyanın gönderilip gönderilmeyeceğini **geri dönüşüm kutusu**, dosyanın silinip silinmediğini doğrulamak için kullanıcıya sor verilip ve kullanıcı işlemi iptal ettiğinde yapmanız gerekenler.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="4d6e3-105">Bir metin dosyasını silmek için</span><span class="sxs-lookup"><span data-stu-id="4d6e3-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="4d6e3-106">Kullanım `DeleteFile` dosyayı silmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="4d6e3-107">Aşağıdaki kodda adlı dosyayı silmek gösterilmiştir `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="4d6e3-108">Bir metin dosyası silip dosya silinmiş olduğunu onaylamak için kullanıcıya sor</span><span class="sxs-lookup"><span data-stu-id="4d6e3-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="4d6e3-109">Kullanım `DeleteFile` dosyası ayarı silmek için yöntemi `showUI` için `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="4d6e3-110">Aşağıdaki kodda adlı dosyayı silmek gösterilmiştir `test.txt` ve dosyanın silinip silinmediğini doğrulamak kullanıcı izin verin.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="4d6e3-111">Bir metin dosyasını silin ve Geri Dönüşüm Kutusu'na göndermek için</span><span class="sxs-lookup"><span data-stu-id="4d6e3-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="4d6e3-112">Kullanım `DeleteFile` dosyayı silmek için yöntemi belirtme `SendToRecycleBin` için `recycle` parametresi.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="4d6e3-113">Aşağıdaki kodda adlı dosyayı silmek gösterilmiştir `test.txt` ve göndermeden **geri dönüşüm kutusu**.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="4d6e3-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="4d6e3-114">Robust Programming</span></span>  
 <span data-ttu-id="4d6e3-115">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="4d6e3-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="4d6e3-116">Yolu şu nedenlerden biri için geçerli değil: sıfır uzunlukta bir dize değil, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir aygıt yol olduğundan (ile başlayan \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-117">Çünkü yolu geçerli değil `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-118">Yolu sistem tarafından tanımlanan uzunluk üst sınırını aşıyor (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-119">Yolda bir dosya veya klasör adı biçimi geçersiz veya iki nokta üst üste (:) içerir (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-120">Dosyanın kullanımda olup (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-121">Kullanıcı yolunu görüntülemek için gerekli izinlere sahip değil (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-122">Dosya yok (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-123">Kullanıcının dosyayı silme izni yok ya da dosyanın salt okunurdur (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-124">Kısmi güven durum, kullanıcının yeterli izinleri yok var (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="4d6e3-125">Kullanıcı işlemi iptal edildi ve `onUserCancel` ayarlanır `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="4d6e3-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6e3-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.UIOption>  
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>  
 [<span data-ttu-id="4d6e3-127">Nasıl yapılır: bir dizindeki dosya koleksiyonunu alma</span><span class="sxs-lookup"><span data-stu-id="4d6e3-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)