---
title: System.Uri ad alanında sürümü 2.0 yapılan değişiklikler
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 169454edd04bfdb55affcc2be12140f42dd2f7ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392454"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>System.Uri ad alanında sürümü 2.0 yapılan değişiklikler
Birkaç değişiklik yapılan <xref:System.Uri?displayProperty=nameWithType> sınıfı. Bu değişiklikler yanlış davranışa sabit, kullanılabilirlik ve geliştirilmiş Gelişmiş Güvenlik.  
  
## <a name="obsolete-and-deprecated-members"></a>Artık kullanılmayan ve kullanım dışı üyeleri  
 Oluşturucular:  
  
-   Sahip tüm oluşturucular bir `dontEscape` parametresi.  
  
 Yöntemleri:  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a>Değişiklikler  
  
-   (Dosya, ftp ve diğerleri), sorgu parçası almamayı bilinen URI şemaları için '?' karakteri her zaman Atlanan ve başlangıcı sayılmaz bir <xref:System.Uri.Query%2A> bölümü.  
  
-   Örtük dosyası URI'ler için (formun "c:\directory\file@name.txt"), tam unescaping istenen sürece parça karakteri ('#') her zaman Atlanan veya <xref:System.Uri.LocalPath%2A> olan `true`.  
  
-   UNC hostname Desteği kaldırılmıştır; Uluslararası ana bilgisayar adları temsil etmek için IDN belirtimi benimsenen.  
  
-   <xref:System.Uri.LocalPath%2A> her zaman tamamen atlanmayan bir dize döndürür.  
  
-   <xref:System.Uri.ToString%2A> bir kaçış karakterli '%', unescape değil '?', veya '#' karakteri.  
  
-   <xref:System.Uri.Equals%2A> artık içerir <xref:System.Uri.Query%2A> eşitlik kontrolüne bölümün.  
  
-   İşleçler "=="ve"! =" geçersiz kılındı ve bağlantılı <xref:System.Uri.Equals%2A> yöntemi.  
  
-   <xref:System.Uri.IsLoopback%2A> Şimdi tutarlı sonuçlar üretir.  
  
-   URI "`file:///path`" "file://path" artık çevrilir.  
  
-   "#" şimdi bir ana bilgisayar adı Sonlandırıcı kabul edilir. Diğer bir deyişle, "http://consoto.com#fragment"şimdi dönüştürülür"http://contoso.com/#fragment".  
  
-   Taban URI ile bir parça birleştirilirken hata düzeltildi.  
  
-   Bir hata <xref:System.Uri.HostNameType%2A> sabittir.  
  
-   NNTP ayrıştırılırken bir hata düzeltildi.  
  
-   URI biçiminde HTTP:contoso.com şimdi bir ayrıştırma özel durum oluşturur.  
  
-   Framework doğru kullanıcı bilgisi bir URI olarak işler.  
  
-   Kopuk bir URI Kökü yukarıda dosya sistemi çapraz geçiş yapamazsınız böylece URI yolu sıkıştırma düzeltilmiştir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Uri?displayProperty=nameWithType>
