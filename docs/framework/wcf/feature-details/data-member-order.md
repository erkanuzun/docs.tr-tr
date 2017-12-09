---
title: "Veri Üye Sırası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8a838b2dd2367bed3fb3ffa3248e67c23f7917d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="data-member-order"></a><span data-ttu-id="a9f42-102">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="a9f42-102">Data Member Order</span></span>
<span data-ttu-id="a9f42-103">Bazı uygulamalarda, verileri çeşitli veri üyelerinden gönderilir veya (örneğin, veri seri hale getirilmiş XML'de gösterilen sırada) alınabilmesi için beklenen sırasını bilmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a9f42-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="a9f42-104">Bazen bu sırayı değiştirmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9f42-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="a9f42-105">Bu konuda sıralama kuralları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a9f42-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="a9f42-106">Temel kurallar</span><span class="sxs-lookup"><span data-stu-id="a9f42-106">Basic Rules</span></span>  
 <span data-ttu-id="a9f42-107">Verileri sıralama için temel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a9f42-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="a9f42-108">Bir veri sözleşmesi türü bir devralma hiyerarşisini bir parçası ise, veri temel türlerinden her zaman sırayla ilk üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="a9f42-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="a9f42-109">Sonraki sırada olmayan geçerli tür veri üyesi <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik alfabetik sırada kümesi.</span><span class="sxs-lookup"><span data-stu-id="a9f42-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="a9f42-110">Sonraki sahip herhangi bir veri üyesi olan <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi.</span><span class="sxs-lookup"><span data-stu-id="a9f42-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="a9f42-111">Bu değeri tarafından sıralanır `Order` özelliği ilk ardından alfabetik olarak birden fazla belirli bir üyesi ise `Order` değeri.</span><span class="sxs-lookup"><span data-stu-id="a9f42-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="a9f42-112">Sırası değerlerinin atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a9f42-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="a9f42-113">Alfabetik çağırarak kurulduğunda <xref:System.String.CompareOrdinal%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a9f42-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a9f42-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a9f42-114">Examples</span></span>  
 <span data-ttu-id="a9f42-115">Aşağıdaki kod göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a9f42-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="a9f42-116">Üretilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="a9f42-116">The XML produced is similar to the following.</span></span>  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9f42-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9f42-117">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [<span data-ttu-id="a9f42-118">Veri sözleşmesi eşitliği</span><span class="sxs-lookup"><span data-stu-id="a9f42-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="a9f42-119">Veri sözleşmelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="a9f42-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)