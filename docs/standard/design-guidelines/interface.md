---
title: Arabirimi
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dea5877f952869d5c84d6019617fcdc52d8ee0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573045"
---
# <a name="interface-design"></a>Arabirimi
Çoğu API'leri sınıfları ve yapıları kullanarak en iyi Modellenen rağmen arabirimler daha uygun olan veya tek seçenektir durumlar vardır.  
  
 CLR birden çok devralma desteklemez (yani, CLR sınıflarına birden çok taban sınıftan devralın olamaz), ancak bir taban sınıftan devralmayı yanı sıra bir veya daha fazla arabirimlerini türleri izin vermiyor. Bu nedenle, arabirimler, genellikle birden çok devralma etkisini elde etmek için kullanılır. Örneğin, <xref:System.IDisposable> disposability içinde istedikleri katılmak diğer tüm Devralma Hiyerarşisi bağımsız desteklemek için türleri sağlayan bir arabirimdir.  
  
 Hangi tanımlama arabirim uygun olan diğer bazı değer türleri dahil olmak üzere çeşitli türleri tarafından desteklenen ortak bir arabirim oluşturmada durumdur. Değer türleri olamaz devral türlerinden dışında <xref:System.ValueType>, ancak arabirimleri uygulayabilir, bunu bir arabirimi kullanarak ortak bir taban türü sunmak için tek seçenek.  
  
 **✓ YAPMAK** değer türleri içeren bir dizi türleri tarafından desteklenen bazı ortak API gerekiyorsa bir arabirim tanımlayın.  
  
 **✓ DÜŞÜNÜN** önceden başka bazı türünden devralan türleri işlevselliği desteklemek gereksinim duyarsanız bir arabirim tanımlama.  
  
 **KAÇININ x** işaret arabirimleri (hiçbir üye arabirimleriyle) kullanarak.  
  
 Genel olarak, bir sınıfın belirli bir karakteristik (işaret) sahip olarak işaretlemek gerekiyorsa, bir arabirim yerine özel bir öznitelik kullanın.  
  
 **✓ YAPMAK** bir arabirim uygulaması en az bir türü sağlar.  
  
 Yaptıktan arabirimi tasarımını doğrulamak için bu yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601> uygulamasıdır <xref:System.Collections.Generic.IList%601> arabirimi.  
  
 **✓ YAPMAK** tanımladığınız her bir arabirime tüketir en az bir API sağlar (bir parametre veya bir özellik arabirimi alma yöntemi yazılan arabirimi olarak).  
  
 Yaptıktan arabirimi tasarımı doğrulamak için bu yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> tüketir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> arabirimi.  
  
 **X yok** önceden sevk edilmiş bir arabirim üye ekleyin.  
  
 Bunun yapılması arabirimin uygulamaları çalışmamasına neden. Sürüm oluşturma sorunları önlemek için yeni bir arabirimi oluşturmanız gerekir.  
  
 Bu yönergeleri bölümünde açıklanan durumlar dışında genel olarak, arabirimleri yerine sınıfları yönetilen kodu yeniden kullanılabilir kitaplıkları tasarlarken seçtiğiniz gerekir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
