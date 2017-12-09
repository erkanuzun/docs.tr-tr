---
title: "Nasıl yapılır: belirli bir öznitelik veya ad (C#) sahip dosyaları sorgulama"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8e5ad9f6ea5d6d8ff97389fc6535dc34acca7d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="844bf-102">Nasıl yapılır: belirli bir öznitelik veya ad (C#) sahip dosyaları sorgulama</span><span class="sxs-lookup"><span data-stu-id="844bf-102">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>
<span data-ttu-id="844bf-103">Bu örnek belirtilen dosya adı uzantısını (örneğin, ".txt") sahip tüm dosyaları bulmak belirtilen dizin ağacında gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="844bf-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="844bf-104">Ayrıca oluşturma zamanı temel alınarak ağacında da en yeni veya eski dosya döndürmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="844bf-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="844bf-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="844bf-105">Example</span></span>  
  
```csharp  
class FindFileByExtension  
{  
    // This query will produce the full path for all .txt files  
    // under the specified folder including subfolders.  
    // It orders the list according to the file name.  
    static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Create the query  
        IEnumerable<System.IO.FileInfo> fileQuery =  
            from file in fileList  
            where file.Extension == ".txt"  
            orderby file.Name  
            select file;  
  
        //Execute the query. This might write out a lot of files!  
        foreach (System.IO.FileInfo fi in fileQuery)  
        {  
            Console.WriteLine(fi.FullName);  
        }  
  
        // Create and execute a new query by using the previous   
        // query as a starting point. fileQuery is not   
        // executed again until the call to Last()  
        var newestFile =  
            (from file in fileQuery  
             orderby file.CreationTime  
             select new { file.FullName, file.CreationTime })  
            .Last();  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}",  
            newestFile.FullName, newestFile.CreationTime);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="844bf-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="844bf-106">Compiling the Code</span></span>  
 <span data-ttu-id="844bf-107">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="844bf-107">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to   System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844bf-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="844bf-108">See Also</span></span>  
 [<span data-ttu-id="844bf-109">LINQ to nesneler (C#)</span><span class="sxs-lookup"><span data-stu-id="844bf-109">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="844bf-110">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="844bf-110">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)