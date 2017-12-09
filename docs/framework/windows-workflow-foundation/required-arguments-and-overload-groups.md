---
title: "Gerekli bağımsız değişkenleri ve aşırı grupları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5d94c64c25f1b50601888eccbe8b4522d7b618c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="9291e-102">Gerekli bağımsız değişkenleri ve aşırı grupları</span><span class="sxs-lookup"><span data-stu-id="9291e-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="9291e-103">Böylece bazı bağımsız değişkenler için yürütme geçerli olması etkinliği bağlanması için gerekli olan etkinlikleri yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9291e-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="9291e-104">`RequiredArgument` Özniteliği bazı bağımsız değişkenler bir etkinlikte gerekli olduğunu belirtmek için kullanılır ve `OverloadGroup` özniteliği gerekli bağımsız kategorilerini gruplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9291e-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="9291e-105">Öznitelikleri kullanarak, etkinlik yazarlar basit veya karmaşık etkinlik doğrulama yapılandırmaları sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9291e-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="9291e-106">Gerekli bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="9291e-106">Using Required Arguments</span></span>  
 <span data-ttu-id="9291e-107">Kullanılacak `RequiredArgument` özniteliği bir etkinlikte, kullanmak istediğiniz bağımsız değişkenleri belirtmek <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9291e-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="9291e-108">Bu örnekte, bir `Add` etkinlik tanımlanmış iki bağımsız değişken gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9291e-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="9291e-109">XAML'de gerekli bağımsız değişkenler de kullanarak belirtilir <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9291e-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="9291e-110">Bu örnekte `Add` etkinlik üç bağımsız değişkenleri ve kullandığı kullanılarak tanımlanmış bir <xref:System.Activities.Statements.Assign%601> ekleme işlemi gerçekleştirme etkinliği.</span><span class="sxs-lookup"><span data-stu-id="9291e-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 <span data-ttu-id="9291e-111">Etkinlik kullanılıyorsa ve gerekli bağımsız değişkenlerin ya da bağlı olmayan aşağıdaki doğrulama hatasını döndürdü.</span><span class="sxs-lookup"><span data-stu-id="9291e-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="9291e-112">**Gerekli etkinlik bağımsız değişkeni 'Operand1' için değer girilmedi.**</span><span class="sxs-lookup"><span data-stu-id="9291e-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9291e-113">denetleme ve doğrulama hataları ve Uyarıları işleme hakkında bkz: [çağırma etkinlik doğrulama](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="9291e-113"> about checking for and handling validation errors and warnings, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="9291e-114">Aşırı grupları kullanma</span><span class="sxs-lookup"><span data-stu-id="9291e-114">Using Overload Groups</span></span>  
 <span data-ttu-id="9291e-115">Aşırı grupları engellenecek bağımsız olan bir etkinlikte geçerli olmadığını belirten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="9291e-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="9291e-116">Bağımsız değişkenler gruplandırılır birlikte kullanarak <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9291e-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="9291e-117">Her grubu tarafından belirtilen bir ad verilir <xref:System.Activities.OverloadGroupAttribute>, etkinlik bir aşırı yüklemesini grubundaki bağımsız değişkenler tek kümesine bağlı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9291e-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>, The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="9291e-118">Aşağıdaki örnekte, geçen [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) örnek, bir `CreateLocation` sınıfı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9291e-118">In the following example, taken from the [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) sample, a `CreateLocation` class is defined.</span></span>  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }                  
}  
```  
  
 <span data-ttu-id="9291e-119">ABD'de bir konum belirtmek için bu etkinliği amacı olan.</span><span class="sxs-lookup"><span data-stu-id="9291e-119">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="9291e-120">Bunu yapmak için kullanıcı etkinliğinin bağımsız değişkenlerinin üç gruplarından birini kullanarak konum belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9291e-120">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="9291e-121">Bağımsız değişkenler geçerli birleşimlerini belirtmek için üç aşırı grupları tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9291e-121">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="9291e-122">`G1`içeren `Latitude` ve `Longitude` bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="9291e-122">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="9291e-123">`G2`içeren `Street`, `City`, ve `State`.</span><span class="sxs-lookup"><span data-stu-id="9291e-123">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="9291e-124">`G3`içeren `Street` ve `Zip`.</span><span class="sxs-lookup"><span data-stu-id="9291e-124">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="9291e-125">`Name`da gerekli bir bağımsız değişken, ancak bir aşırı yüklemesini grubunun bir parçası değil.</span><span class="sxs-lookup"><span data-stu-id="9291e-125">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="9291e-126">Geçerli olması bu etkinliği `Name` tüm bağımsız değişkenler ile birlikte tek bir aşırı yüklemesini grubundan bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9291e-126">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="9291e-127">Aşağıdaki örnekte, geçen [veritabanı erişimi etkinliklerini](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) örnek, iki aşırı grupları vardır: `ConnectionString` ve `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="9291e-127">In the following example, taken from the [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="9291e-128">Ya da geçerli olması bu etkinliği `ProviderName` ve `ConnectionString` bağımsız değişkenleri bağlı olmalıdır, veya `ConfigName` bağımsız değişkeni, ancak ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="9291e-128">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
 <span data-ttu-id="9291e-129">Aşırı Grup tanımlarken:</span><span class="sxs-lookup"><span data-stu-id="9291e-129">When defining an overload group:</span></span>  
  
-   <span data-ttu-id="9291e-130">Aşırı grubu, bir alt veya başka bir aşırı yüklemesini Grup eşdeğer bir dizi olamaz.</span><span class="sxs-lookup"><span data-stu-id="9291e-130">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9291e-131">Bu kural için bir istisna vardır.</span><span class="sxs-lookup"><span data-stu-id="9291e-131">There is one exception to this rule.</span></span> <span data-ttu-id="9291e-132">Başka bir aşırı yüklemesini grubun alt kümesini aşırı grubudur ve yalnızca bağımsız değişken alt içeriyorsa nerede `RequiredArgument` olan `false`, aşırı Grup geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="9291e-132">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
-   <span data-ttu-id="9291e-133">Aşırı grupları binebilir ancak grupları kesişimi tüm gerekli bağımsız birini veya her ikisini aşırı grupları içeriyorsa bir hata değildir.</span><span class="sxs-lookup"><span data-stu-id="9291e-133">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="9291e-134">Önceki örnekte `G2` ve `G3` çakışan grupları aşırı ancak kesişimi birine veya ikisine de grupları, tüm bağımsız değişkenler içermediğinden Bu geçerli.</span><span class="sxs-lookup"><span data-stu-id="9291e-134">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="9291e-135">Bağımsız değişkenler bir aşırı yüklemesini grubunda bağlanırken:</span><span class="sxs-lookup"><span data-stu-id="9291e-135">When binding arguments in an overload group:</span></span>  
  
-   <span data-ttu-id="9291e-136">Aşırı Grup bağlı olarak tüm değerlendirilir `RequiredArgument` Grup değişkenlerinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9291e-136">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
-   <span data-ttu-id="9291e-137">Bir grup sıfır varsa `RequiredArgument` bağımsız değişkenleri ve en az bir değişken bağlı, sonra da Grup bağlı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="9291e-137">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
-   <span data-ttu-id="9291e-138">Bir aşırı yüklemesini Grup no olmadıkça hiçbir aşırı yüklemesi grupları bağlıysa bir doğrulama hatası olan `RequiredArgument` da bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="9291e-138">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
-   <span data-ttu-id="9291e-139">Bağlı, birden fazla aşırı grup için bir hata olduğundan, aşırı yüklemesiyle grubundaki tüm gerekli bağımsız bağlı olan ve başka bir aşırı yüklemesini grubunda herhangi bir bağımsız değişken de bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9291e-139">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>