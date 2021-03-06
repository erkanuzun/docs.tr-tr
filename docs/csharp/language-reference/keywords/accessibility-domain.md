---
title: Erişilebilirlik Etki Alanı (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 8e6af35ea41f6d062bc2b8ee771a1fac21667462
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208413"
---
# <a name="accessibility-domain-c-reference"></a>Erişilebilirlik Etki Alanı (C# Başvurusu)
Erişilebilirlik etki alanı üyesi hangi program bölümlerde üyesi başvurulabilir belirtir. Üye içinde başka bir tür geçmişse erişilebilirlik etki alanı her ikisi için de belirlenir [erişilebilirlik düzeyi](../../../csharp/language-reference/keywords/accessibility-levels.md) üye ve erişilebilirlik etki alanı hemen içeren türü.  
  
 Erişilebilirlik etki alanı en üst düzey bir türde en az içinde bildirilen projesinin program metindir. Diğer bir deyişle, etki alanı tüm bu projenin kaynak dosyalarını içerir. Erişilebilirlik etki alanı iç içe bir türde en az hangi bildirilmiş türü program metindir. Diğer bir deyişle, tüm iç içe geçmiş türler içeren türü gövdesi etki alanıdır. Erişilebilirlik etki alanı iç içe geçmiş tür hiçbir zaman, kapsayan tür aşıyor. Bu kavram aşağıdaki örnekte gösterilmiştir.  
  
## <a name="example"></a>Örnek  
 Bu örnek bir üst düzey türünü içeren `T1`ve iki iç içe geçmiş sınıflar `M1` ve `M2`. Sınıfları farklı bildirilen eriþebilirlik sahip alanlar içeriyor. İçinde `Main` yöntemi, bir açıklamayı izleyen her üyesinin erişilebilirlik etki alanı belirtmek için her bir deyimi. Erişilemez üyeleri başvurmak için deneyin deyimleri kılınmıştır dikkat edin. Erişilemez bir üye başvurarak kaynaklanan derleyici hataları görmek istiyorsanız, bir açıklama aynı anda kaldırın.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Erişim Değiştiricileri](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Erişilebilirlik Düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
