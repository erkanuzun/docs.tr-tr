---
title: Değer Karşılaştırmaları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649613"
---
# <a name="value-comparisons-visual-basic"></a>Değer Karşılaştırmaları (Visual Basic)
Karşılaştırma işleçleri sayısal değişkenlerin değerleri karşılaştırma ifadeleri oluşturmak için kullanılabilir. Bu deyimler dönüş bir `Boolean` değeri temel karşılaştırma doğru olup ya da yanlış. Bu tür bir ifade örnekleri aşağıdaki gibidir.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 İlk ifade değerlendiren `True`, 45 26 büyük olduğu için. İkinci örnek değerlendiren `False`26 45 büyük olmadığından.  
  
 Bu şekilde sayısal ifadeler de karşılaştırabilirsiniz. Karşılaştırma ifadeleri kendilerini aşağıdaki örnekteki gibi karmaşık ifadeler olabilir.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Önceki karmaşık ifade değişmez değerleri, değişkenler ve işlev çağrılarını içerir. Her iki tarafında ifadeleri karşılaştırma işlecinin değerlendirilir ve kullanılarak elde edilen değerleri karşılaştırılır `>=` karşılaştırma işleci. Sol tarafındaki ifade değerini değerinden daha büyük ya da için sağ taraftaki ifadenin değerine eşit, tüm ifadeyi hesaplar `True`; Aksi takdirde için değerlendirir `False`.  
  
 Değerleri karşılaştırma ifadeleri en sık kullanıldığı `If...Then` aşağıdaki örnekteki gibi kurulumlarını.  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 `=` İşaretidir atama işleci yanı sıra bir karşılaştırma işleci. Aşağıdaki örnekte gösterildiği gibi soldaki değerin sağdaki değerine eşit olup olmadığını bir karşılaştırma işleci kullanıldığında, değerlendirir.  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 Bir karşılaştırma ifadesi yerde kullanabilir bir `Boolean` değerdir gerekli, gibi bir `If`, `While`, `Loop`, veya `ElseIf` deyimi, ya da atama veya bir değere geçirme bir `Boolean` değişkeni. Aşağıdaki örnekte, karşılaştırma ifadesi tarafından döndürülen değer atanmış bir `Boolean` değişkeni.  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [İşleçler ve İfadeler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Nasıl yapılır: Sayısal Değerleri Hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Visual Basic'de İşleç önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
