---
title: 'Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4b5e005ddd7bbd598a9da3032574eb2ba7dd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580890"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma
Bu örnek kullanarak işlemleri paralel hale gösterilmiştir <xref:System.Threading.Tasks.Parallel.Invoke%2A> görev paralel Kitaplığı'nda. Üç işlemleri bir paylaşılan veri kaynağı üzerinde gerçekleştirilir. İşlemlerin hiçbiri kaynak değiştirdiğinden, bunlar kolay bir şekilde paralel olarak çalıştırılabilir.  
  
> [!NOTE]
>  TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 İle unutmayın <xref:System.Threading.Tasks.Parallel.Invoke%2A>, aynı anda çalıştırmak istediğiniz hangi eylemleri yalnızca express ve çalışma zamanı zamanlama ayrıntıları, ana bilgisayarda çekirdek sayısı için otomatik olarak ölçeklendirme dahil olmak üzere tüm iş parçacığı işler.  
  
 Bu örnek veri işlemleri parallelizes. Alternatif bir yaklaşım PLINQ kullanarak LINQ sorgularını paralel hale ve sorguları sırayla çalışır. Alternatif olarak, verileri PLINQ kullanarak paralel hale. Sorgular ve görevleri paralel hale başka bir seçenektir. Elde edilen performansını nispeten az işlemci ile ana bilgisayarlara ek yükü azaltabilir rağmen birçok işlemcilere sahip bilgisayarlarda daha iyi ölçeklendirme.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kopyalama, tüm örnek bir Microsoft Visual Studio 2010 projeye yapıştırın ve F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
