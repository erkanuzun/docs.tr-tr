---
title: ADO.NET bağlantı dizeleri
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 03d768430139fa1078f39b470403abcf75dd83a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757222"
---
# <a name="connection-strings-in-adonet"></a>ADO.NET bağlantı dizeleri
.NET Framework 2.0 bağlantı dizeleri, yeni anahtar sözcüklerin giriş geçerli bir bağlantı dizeleri çalışma zamanında oluşturma kolaylaştırmak bağlantı dizesi Oluşturucu sınıflarına dahil olmak üzere ile çalışmak için yeni özellikler sunar.  
  
 Bir bağlantı dizesi, parametre olarak bir veri kaynağına veri sağlayıcıdan geçen başlatma bilgileri içerir. Sözdizimi veri sağlayıcısına bağlıdır ve bağlantı dizesini bir bağlantı açmak için girişimi sırasında ayrıştırılır. Sözdizimi hataları bir çalışma zamanı özel durum oluşturur, ancak yalnızca veri kaynağı bağlantı bilgilerini aldıktan sonra diğer hataları oluşur. Doğrulanmış sonra veri kaynağının bağlantı dizesinde belirtilen seçeneklerini uygular ve bağlantı açar.  
  
 Bir bağlantı dizesi biçimi anahtar/değer parametresi çifti noktalı virgülle ayrılmış bir listesi verilmiştir:  
  
 `keyword1=value; keyword2=value;`  
  
 Anahtar sözcükler büyük küçük harfe duyarlı değildir ve anahtar/değer çiftleri arasındaki boşluklar yok sayılır. Ancak, değerleri büyük veri kaynağı bağlı olarak küçük harf duyarlı, olabilir. Noktalı virgül içeren herhangi bir değer tek tırnak işareti ya da çift tırnak işaretleri çift tırnak içine alınmalıdır.  
  
 Geçerli bağlantı dizesi sözdizimi sağlayıcısına bağlıdır ve ODBC gibi önceki API'leri yıl üzerinden gelişmiştir. SQL Server (SqlClient) için .NET Framework veri sağlayıcısı eski sözdizimi birçok öğelerini bir araya getirir ve ortak bağlantı dizesi sözdizimi genellikle daha esnektir. Yoktur sık eşit bağlantı dizesi söz dizimi öğeleri için geçerli eş anlamlı sözcükleri, ancak bazı sözdizimi ve yazım hatalarını sorunlara neden olabilir. Örneğin, "`Integrated Security=true`" geçerlidir, ancak "`IntegratedSecurity=true`" bir hataya neden olur. Ayrıca, doğrulanmamış kullanıcı girişini gelen çalışma zamanında oluşturulan bağlantı dizeleri dize ekleme saldırıları, veri kaynağında güvenliği tehlikeye yol açabilir.  
  
 Bu sorunları gidermek için her .NET Framework veri sağlayıcısı için yeni bağlantı dizesi oluşturucular ADO.NET 2.0 kullanıma sunuldu. Anahtar sözcükler, özellikleri, veri kaynağına gönderilmesinden önce doğrulanacak bağlantı dizesi sözdizimi etkinleştirme olarak sunulur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Nasıl kullanılacağı ortaya `ConnectionStringBuilder` sınıfları geçerli bağlantı dizeleri oluşturmak için çalışma süresi.  
  
 [Bağlantı Dizeleri ve Yapılandırma Dosyaları](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Bağlantı dizelerini yapılandırma dosyalarında depolanıp gösterilmiştir.  
  
 [Bağlantı Dizesi Söz Dizimi](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Sağlayıcıya özgü bağlantı dizeleri için yapılandırmayı açıklar `SqlClient`, `OracleClient`, `OleDb`, ve `Odbc`.  
  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Bir veri kaynağına bağlanmak için kullanılan bilgiler koruyan tekniklerini gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
