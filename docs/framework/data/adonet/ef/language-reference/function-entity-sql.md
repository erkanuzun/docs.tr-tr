---
title: İŞLEVİ (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: c101032aed3e94e6bbf1d16319a616131fa6b60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760680"
---
# <a name="function-entity-sql"></a>İŞLEVİ (varlık SQL)
Varlık SQL sorgu komutunu kapsamında bir işlevi tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Arguments  
 `function-name`  
 İşlevin adı.  
  
 `parameter-name`  
 İşlev içindeki bir parametre adı.  
  
 `function_expression`  
 İşlev geçerli bir varlık SQL ifadesi. İşlev komutta çalışabilmek için `parameter_name` işlevine geçirilen parametreleri.  
  
 `data_type`  
 Desteklenen bir tür adı.  
  
 KOLEKSİYON (< type_definition`>` )  
 Desteklenen türler, satır veya başvuruları koleksiyonu döndüren bir ifade.  
  
 REF **(**`data_type`**)**  
 Bir varlık türü referansı döndüren bir ifade.  
  
 SATIR **(**`row_expression`**)**  
 Anonim, döndüren bir ifadeye yapısal olarak bir veya daha fazla değer kayıtlarından belirtilmiş. Daha fazla bilgi için bkz: [satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev imzalarında farklı olduğu sürece aynı ada sahip birden çok işlev satır içi, bildirilebilir. Daha fazla bilgi için bkz: [işlevi aşırı yükleme çözümü](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Bu komutta yalnızca tanımlandıktan sonra bir satır içi işlevi bir varlık SQL komutunu çağrılabilir. Ancak, bir satır içi işlev önce ya da çağrılan işlev tanımlandıktan sonra başka bir satır içi işlev içinde çağrılabilir. B işlevi tanımlanmadan önce aşağıdaki örnekte, işlevi A B işlev çağrıları:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: bir kullanıcı tanımlı işlev çağrısı](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02).  
  
 İşlevler de modelinde bildirilebilir. Model içinde bildirilen işlevler komutta bildirilen satır içi işlevleri gibi aynı şekilde yürütülür. Daha fazla bilgi için bkz: [kullanıcı tanımlı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL komutunu işlevini tanımlar `Products` döndürülen ürünleri filtrelemek için bir tamsayı değeri alır.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL komutunu işlevini tanımlar `StringReturnsCollection` döndürülen kişiler filtrelemek için dizeleri koleksiyonu alır.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL Dili](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
