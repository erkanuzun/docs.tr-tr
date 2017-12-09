---
title: "Nasıl yapılır: (LINQ) (Visual Basic) bir klasördeki dosyaların içeriğini sorgulama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053a0b206b5e5fc71fb83967a70da205a8988978
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="37fe2-102">Nasıl yapılır: (LINQ) (Visual Basic) bir klasördeki dosyaların içeriğini sorgulama</span><span class="sxs-lookup"><span data-stu-id="37fe2-102">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="37fe2-103">Bu örnek, belirtilen dizin ağacındaki tüm dosyalar üzerinde sorgu, her dosyayı açın ve içeriğini inceleyin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="37fe2-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="37fe2-104">Bu tür bir teknik dizinler oluşturmak veya bir dizin ağacında içeriğini dizinlerini tersine çevirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37fe2-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="37fe2-105">Bu örnekte, bir basit bir dize araması gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="37fe2-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="37fe2-106">Ancak, daha karmaşık tür desen eşleştirme bir normal ifade ile gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="37fe2-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="37fe2-107">Daha fazla bilgi için bkz: [nasıl yapılır: LINQ sorgularını birleştirme (Visual Basic) Normal ifadelerle](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="37fe2-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37fe2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="37fe2-108">Example</span></span>  
  
```vb  
Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "c:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        Dim searchTerm = "Visual Studio"  
  
        ' Search the contents of each file.  
        ' A regular expression created with the RegEx class  
        ' could be used instead of the Contains method.  
        Dim queryMatchingFiles = From file In fileList _  
                                 Where file.Extension = ".htm" _  
                                 Let fileText = GetFileText(file.FullName) _  
                                 Where fileText.Contains(searchTerm) _  
                                 Select file.FullName  
  
        Console.WriteLine("The term " & searchTerm & " was found in:")  
  
        ' Execute the query.  
        For Each filename In queryMatchingFiles  
            Console.WriteLine(filename)  
        Next  
  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit")  
        Console.ReadKey()  
  
    End Sub  
  
    ' Read the contents of the file. This is done in a separate  
    ' function in order to handle potential file system errors.  
    Function GetFileText(ByVal name As String) As String  
  
        ' If the file has been deleted, the right thing  
        ' to do in this case is return an empty string.  
        Dim fileContents = String.Empty  
  
        ' If the file has been deleted since we took   
        ' the snapshot, ignore it and return the empty string.  
        If System.IO.File.Exists(name) Then  
            fileContents = System.IO.File.ReadAllText(name)  
        End If  
  
        Return fileContents  
  
    End Function  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37fe2-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="37fe2-109">Compiling the Code</span></span>  
 <span data-ttu-id="37fe2-110">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="37fe2-110">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fe2-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37fe2-111">See Also</span></span>  
 [<span data-ttu-id="37fe2-112">LINQ to nesneler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37fe2-112">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="37fe2-113">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37fe2-113">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)