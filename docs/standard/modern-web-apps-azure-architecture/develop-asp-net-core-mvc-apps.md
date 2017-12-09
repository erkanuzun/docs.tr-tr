---
title: "ASP.NET Core MVC uygulamaları geliştirme"
description: "ASP.NET Core ve Azure ile modern Web uygulamaları mimari | ASP.NET Core MVC uygulamaları geliştirme"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 54e7ed6fff9ac709e411d0ac1e345c63fd753201
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="db788-103">ASP.NET Core MVC uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="db788-103">Develop ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="db788-104">"Bu ilk kez sağ almak önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="db788-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="db788-105">En son ne zaman sağ almak oldukça önemlidir."</span><span class="sxs-lookup"><span data-stu-id="db788-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="db788-106">_-Barış aramaya ve David Thomas_</span><span class="sxs-lookup"><span data-stu-id="db788-106">_- Andrew Hunt and David Thomas_</span></span>

## <a name="summary"></a><span data-ttu-id="db788-107">Özet</span><span class="sxs-lookup"><span data-stu-id="db788-107">Summary</span></span>

<span data-ttu-id="db788-108">ASP.NET Core modern bulut iyileştirilmiş web uygulamaları oluşturmak için platformlar arası, açık kaynaklı bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="db788-108">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="db788-109">ASP.NET Core uygulamaları basit ve modüler, bağımlılık ekleme, büyük sınanabilirlik ve bakımı etkinleştirme için yerleşik destek bulunur.</span><span class="sxs-lookup"><span data-stu-id="db788-109">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling in greater testability and maintainability.</span></span> <span data-ttu-id="db788-110">Modern web API'leri görünüm tabanlı uygulamalar yanı sıra oluşturmayı destekleyen, MVC ile birlikte ASP.NET Core bir güçlü Kurumsal web uygulamaları oluşturmak hangi çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="db788-110">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="db788-111">Eşleme isteklerini yanıtlar</span><span class="sxs-lookup"><span data-stu-id="db788-111">Mapping Requests to Responses</span></span>

<span data-ttu-id="db788-112">Temelinde, ASP.NET Core uygulamaları giden yanıtlar gelen istekleri eşleyin.</span><span class="sxs-lookup"><span data-stu-id="db788-112">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="db788-113">Düşük düzeyde, bu Ara yazılımla yapılır ve basit ASP.NET Core uygulamaları ve mikro hizmetler yalnızca özel ara yazılım oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-113">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="db788-114">ASP.NET Core MVC kullanırken cinsinden düşünüyorum biraz daha yüksek bir düzeyde çalışabilirsiniz *yollar*, *denetleyicileri*, ve *Eylemler*.</span><span class="sxs-lookup"><span data-stu-id="db788-114">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of *routes*, *controllers*, and *actions*.</span></span> <span data-ttu-id="db788-115">Her gelen istek uygulamanın yönlendirme tablosu ile karşılaştırılır ve eşleşen bir rota bulunursa, (bir denetleyiciye ait) ilişkili eylem yöntemi isteği işlemek üzere çağrılır.</span><span class="sxs-lookup"><span data-stu-id="db788-115">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="db788-116">Eşleşen bir rota bulunursa, bir hata işleyicisi (NotFound sonucu döndürerek bu durumda,) adı verilir.</span><span class="sxs-lookup"><span data-stu-id="db788-116">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="db788-117">ASP.NET Core MVC uygulamaları geleneksel yolları, öznitelik rotaları veya her ikisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-117">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="db788-118">Geleneksel yollar yönlendirme belirtme kodda tanımlanmış *kuralları* aşağıdaki örnekte olduğu gibi sözdizimini kullanarak:</span><span class="sxs-lookup"><span data-stu-id="db788-118">Conventional routes are defined in code, specifying routing *conventions* using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="db788-119">Bu örnekte, "varsayılan" adlı bir rota yönlendirme tablosuna eklendi.</span><span class="sxs-lookup"><span data-stu-id="db788-119">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="db788-120">Bir rota şablonuyla yer tutucular tanımlar *denetleyicisi*, *eylem*, ve *kimliği*. Belirtilen varsayılan denetleyici ve eylem yer tutucuları bulunur ("Home" ve "Dizin" sırasıyla), ve kimliği tutucudur isteğe bağlı (tarafından virtue, bir "?" uygulanan).</span><span class="sxs-lookup"><span data-stu-id="db788-120">It defines a route template with placeholders for *controller*, *action*, and *id*. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="db788-121">Kuralı ikinci bölümü eyleme denetleyicinin adı bir isteğin ilk parçası karşılık gelmelidir durumları burada tanımlanan ve ardından gerekirse, üçüncü bir bölümü bir ID parametresi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db788-121">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="db788-122">Geleneksel yollar genellikle uygulama için tek bir yerde gibi başlangıç sınıfı yapılandırma yönteminde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="db788-122">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="db788-123">Öznitelik rotaları denetleyicileri ve eylemleri doğrudan uygulanan yerine genel olarak belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="db788-123">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="db788-124">Bu, belirli bir yöntem arıyorsanız, ancak yönlendirme bilgilerini uygulamadaki tek bir yerde tutulan değil anlamına gelmez, çok daha bulunabilirlik yapma avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="db788-124">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="db788-125">Öznitelik rotaları ile kolayca belirli bir eylem için birden çok rotaları belirtin yanı denetleyicileri ve eylemleri arasındaki yolları birleştirin.</span><span class="sxs-lookup"><span data-stu-id="db788-125">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="db788-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="db788-126">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

<span data-ttu-id="db788-127">Yollar [HttpGet] üzerinde belirtilebilir ve benzer öznitelikler eklemek için gereken önleme, ayrı [rota\] öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="db788-127">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route\] attributes.</span></span> <span data-ttu-id="db788-128">Öznitelik rotaları belirteçleri, denetleyici veya eylem adlarını yinelemek için gereken aşağıda gösterildiği gibi azaltmak için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db788-128">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

<span data-ttu-id="db788-129">Belirtilen bir isteğin rotayla eşleşen, ancak önce eylem yönteminden sonra ASP.NET Core MVC gerçekleştirecek [model bağlama](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) ve [model doğrulama](https://docs.microsoft.com/aspnet/core/mvc/models/validation) istek.</span><span class="sxs-lookup"><span data-stu-id="db788-129">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) and [model validation](https://docs.microsoft.com/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="db788-130">Model bağlama, gelen HTTP veri çağrılacak eylem yönteminin bir parametre olarak belirtilen .NET türlerine dönüştürme için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="db788-130">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="db788-131">Örneğin, bir eylem yönteminin bir int kimliği parametre bekliyor, isteğin bir parçası sağlanan değer bu parametresinden sağlamak model bağlama deneyecek.</span><span class="sxs-lookup"><span data-stu-id="db788-131">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="db788-132">Bunu yapmak için model bağlama gönderilen bir formu değerleri, rota değerleri ve sorgu dizesi değerlerini arar.</span><span class="sxs-lookup"><span data-stu-id="db788-132">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="db788-133">Bir kimlik değeri bulundu varsayıldığında, onu bir tamsayıya eylem yönteminin iletilmeden önce dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="db788-133">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="db788-134">Model bağlama sonra ancak eylem yöntemi çağrılmadan önce model doğrulama oluşur.</span><span class="sxs-lookup"><span data-stu-id="db788-134">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="db788-135">Model doğrulama, model türü üzerinde isteğe bağlı öznitelik kullanır ve sağlanan model nesnesi belirli veri gereksinimleri uymasını sağlamak yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-135">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="db788-136">Belirli değerleri olarak belirtilebilir gerekli veya belirli bir uzunlukta veya sayısal aralığı için sınırlı, vb. Doğrulama öznitelikleri belirtildi ancak model kendi gereksinimlerine uygun değil, özellik ModelState.IsValid false olur ve doğrulama kuralları başarısız kümesi istekte istemciye göndermek kullanılabilir olacak.</span><span class="sxs-lookup"><span data-stu-id="db788-136">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="db788-137">Model doğrulama kullanıyorsanız, her zaman uygulamanızı geçersiz veriler bozuk değil emin olmak için tüm durum değiştirme komutları gerçekleştirmeden önce model geçerli olup olmadığını denetlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="db788-137">If you are using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="db788-138">Kullanabileceğiniz bir [filtre](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) kod bu her eylem eklemek için gereksinimini ortadan kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="db788-138">You can use a [filter](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="db788-139">Böylece ortak ilkeleri ve çapraz kesme sorunları hedeflenen temelinde uygulanabilir ASP.NET Core MVC filtreleri isteklerinin grupları kesintiye uğratan bir yol sunar.</span><span class="sxs-lookup"><span data-stu-id="db788-139">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="db788-140">Filtreler, tek tek Eylemler, tüm denetleyicileri veya genel bir uygulama için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-140">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="db788-141">ASP.NET Core MVC Web API'leri destekleyen [ *içerik anlaşması*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), istekleri yanıtlar nasıl biçimlendirilmiş belirtmek izin verme.</span><span class="sxs-lookup"><span data-stu-id="db788-141">For web APIs, ASP.NET Core MVC supports [*content negotiation*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="db788-142">İstekte sağlanan üstbilgileri bağlı olarak, XML, JSON veya başka bir desteklenen biçiminde yanıt veriyor Eylemler biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="db788-142">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="db788-143">Bu özellik, farklı veri biçim gereksinimleri ile birden çok istemci tarafından kullanılmak üzere aynı API sağlar.</span><span class="sxs-lookup"><span data-stu-id="db788-143">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="db788-144">Başvuruları – isteklerini yanıtlar eşleme</span><span class="sxs-lookup"><span data-stu-id="db788-144">References – Mapping Requests to Responses</span></span>
> - <span data-ttu-id="db788-145">**Denetleyici eylemleri için yönlendirme**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="db788-145">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="db788-146">**Model bağlama** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span><span class="sxs-lookup"><span data-stu-id="db788-146">**Model Binding** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding</span></span>
> - <span data-ttu-id="db788-147">**Model doğrulama**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="db788-147">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="db788-148">**Filtreler** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span><span class="sxs-lookup"><span data-stu-id="db788-148">**Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters</span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="db788-149">Bağımlılıkları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="db788-149">Working with Dependencies</span></span>

<span data-ttu-id="db788-150">ASP.NET Core için yerleşik destek varsa ve dahili olarak kullanır olarak bilinen bir tekniği [bağımlılık ekleme](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="db788-150">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="db788-151">Bağımlılık ekleme gevşek bağlantı uygulamanın farklı bölümleri arasında etkin bir tekniktir.</span><span class="sxs-lookup"><span data-stu-id="db788-151">Dependency injection is a technique that enabled loose coupling between different parts of an application.</span></span> <span data-ttu-id="db788-152">Bazı bağlantı arzu çünkü sınama ya da değiştirme için izin vererek uygulama parçalarını yalıtmak üzere kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="db788-152">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="db788-153">Ayrıca, daha az büyük olasılıkla bir değişiklik uygulamanın bir parçası olarak uygulamada başka bir yere beklenmeyen etkisi olduğunu kılar.</span><span class="sxs-lookup"><span data-stu-id="db788-153">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="db788-154">Bağımlılık ekleme bağımlılık ters çevirmeyi ilkeye dayanarak ve genellikle açık ve kapalı ilkesini ulaşmak için anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-154">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="db788-155">Uygulamanızı bağımlılıklarını ile nasıl çalıştığı değerlendirirken, dikkat [statik cling](http://deviq.com/static-cling/) kod kokusu ve aphorism unutmayın "[Birleştirici yeni](http://ardalis.com/new-is-glue)."</span><span class="sxs-lookup"><span data-stu-id="db788-155">When evaluating how your application works with its dependencies, beware of the [static cling](http://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](http://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="db788-156">Statik cling sınıflarınızı statik yöntemler çağrı yapmak veya yan etkileri veya bağımlılıkları altyapısına sahip statik özelliklerine erişim oluşur.</span><span class="sxs-lookup"><span data-stu-id="db788-156">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="db788-157">Örneğin, sırayla bir veritabanına yazma, bir statik yöntemini çağıran bir yöntemi varsa yönteminizi sıkı şekilde veritabanına bağlı.</span><span class="sxs-lookup"><span data-stu-id="db788-157">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="db788-158">Bu veritabanı çağrısı keser herhangi bir şey yönteminizi çalışmamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="db788-158">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="db788-159">Bu tür sınamalar statik çağrıları mock için ticari mocking kitaplıkları gerektiren ya da yalnızca bir test veritabanı yerinde ile test edilebilir beri tür yöntem sınama notoriously zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-159">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="db788-160">Altyapı, özellikle de tamamen durum bilgisiz herhangi bağımlılığı yok statik çağrıları arayıp bağ veya Test Edilebilirlik (ötesinde kod statik çağrısı kendisini Kuplaj) üzerinde hiçbir etkisi ince.</span><span class="sxs-lookup"><span data-stu-id="db788-160">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="db788-161">Çoğu geliştirici statik cling ve genel durum risklerini anlamak, ancak kendi kodlarını doğrudan oluşturmada size belirli uygulamaları için hala sıkı bir şekilde eşleştiği.</span><span class="sxs-lookup"><span data-stu-id="db788-161">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="db788-162">"Birleştirici yenilikler" Bu bağlantı, anımsatıcı ve değil genel condemnation yeni anahtar sözcük kullanımı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="db788-162">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="db788-163">Gibi statik yöntem çağrılarını genellikle dış bağımlılıkları olmayan türleri yeni örneklerini değil sıkı bir şekilde kod uygulama ayrıntılarını eşleştiği veya test daha zor hale.</span><span class="sxs-lookup"><span data-stu-id="db788-163">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="db788-164">Ancak bir sınıf örneği, her zaman sabit kodlu için belirli Bu örnek, belirli bir konumda mantıklıdır olup olmadığını ya da bu örnek bir bağımlılık olarak istemek için daha iyi bir tasarım olacaksa dikkate alınması gereken yalnızca kısa biraz zaman ayırın.</span><span class="sxs-lookup"><span data-stu-id="db788-164">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="db788-165">Bağımlılıklarınız bildirme</span><span class="sxs-lookup"><span data-stu-id="db788-165">Declare Your Dependencies</span></span>

<span data-ttu-id="db788-166">ASP.NET Core yöntemleri sahip geçici oluşturulur ve bağımsız değişkenler olarak isteyen bağımlılıklarını sınıfları bildirme.</span><span class="sxs-lookup"><span data-stu-id="db788-166">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="db788-167">ASP.NET uygulamaları tipik olarak ayarlandığı bir başlangıç sınıfta kendisi bağımlılık ekleme birkaç noktalarda desteklemek üzere yapılandırıldı.</span><span class="sxs-lookup"><span data-stu-id="db788-167">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="db788-168">Başlangıç sınıfı bir oluşturucu varsa, Oluşturucusu aracılığıyla bağımlılıklar isteyebilir sözlüğüdür:</span><span class="sxs-lookup"><span data-stu-id="db788-168">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

<span data-ttu-id="db788-169">Var olan hiçbir açık tür gereksinimlerin başlangıç sınıfı ilginç olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-169">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="db788-170">Bir özel başlangıç temel sınıfından devralmaz veya herhangi belirli arabirimini uygulayan yapar.</span><span class="sxs-lookup"><span data-stu-id="db788-170">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="db788-171">Ona bir oluşturucu veya verebilirsiniz ve istediğiniz sayıda parametrelere Oluşturucusu belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-171">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="db788-172">Uygulamanız için yapılandırdığınız web ana bilgisayar başlatıldığında kullanacak şekilde söylediyse başlangıç sınıfı çağırır ve bağımlılık ekleme başlangıç sınıfı gerektirir bağımlılıkları doldurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="db788-172">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="db788-173">Doğal olarak, ASP.NET Core tarafından kullanılan hizmetler kapsayıcısında yapılandırılmamışlardır parametreleri isterse bir özel durum alırsınız, ancak bağımlılıkları takılıyor sürece kapsayıcı bilir hakkında istediğinizi isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="db788-173">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="db788-174">Başlangıç örneği oluşturduğunuzda, bağımlılık ekleme ASP.NET Core uygulamalarınızı sağ başından içinde yerleşiktir.</span><span class="sxs-lookup"><span data-stu-id="db788-174">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="db788-175">Ayrıca başlangıç sınıfı var. bitmez.</span><span class="sxs-lookup"><span data-stu-id="db788-175">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="db788-176">Yapılandırma yöntemi bağımlılıkları da isteğinde bulunabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db788-176">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="db788-177">Bu davranış özel durumu ConfigureServices yöntemdir; IServiceCollection türünde yalnızca bir parametre almalıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-177">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="db788-178">Ayrıca, bir yandan hizmet kapsayıcı nesneleri eklemek için sorumlu olduğu ve diğer tüm yapılandırılmış hizmetler IServiceCollection parametresi üzerinden erişimi olan bağımlılık ekleme desteklemek gerçekten gerekmez.</span><span class="sxs-lookup"><span data-stu-id="db788-178">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="db788-179">Bu nedenle, her bir parametre olarak gerekli hizmet isteyen veya IServiceCollection ConfigureServices içinde çalışma başlangıç sınıfı parçası ASP.NET Core services koleksiyonunda içinde tanımlanan bağımlılıklar çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-179">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="db788-180">Belirli hizmetleri başlatma sınıfınıza kullanılabilir olduğundan emin olun ihtiyacınız varsa, bunları yapılandırabilirsiniz WebHostBuilder ve onun ConfigureServices yöntemini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="db788-180">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="db788-181">Başlangıç sınıfı diğer filtreleri kendi hizmetlerine Ara denetleyicilerinden ASP.NET Core uygulamanızın parçalarını nasıl yapılandırdığınızı modelidir.</span><span class="sxs-lookup"><span data-stu-id="db788-181">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="db788-182">Her durumda, uygulamanız gereken [açık bağımlılıkları ilkesine](http://deviq.com/explicit-dependencies-principle/)bağımlılıklarınızı isteyen yerine doğrudan oluşturarak ve bağımlılık ekleme, uygulama boyunca yararlanarak.</span><span class="sxs-lookup"><span data-stu-id="db788-182">In each case, you should follow the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="db788-183">Nerede ve nasıl, doğrudan uygulamaları, özellikle Hizmetleri ve altyapı ile çalışma veya yan etkileri olan nesneleri örneği dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="db788-183">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="db788-184">Uygulama çekirdek içinde tanımlanan ve içinde cmdlet'e kod başvurularını belirli uygulama türleri için bağımsız değişken olarak geçirilen soyutlama ile çalışmayı tercih eder.</span><span class="sxs-lookup"><span data-stu-id="db788-184">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="db788-185">Uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="db788-185">Structuring the Application</span></span>

<span data-ttu-id="db788-186">Tek yapılı uygulamalar genellikle tek giriş noktası vardır.</span><span class="sxs-lookup"><span data-stu-id="db788-186">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="db788-187">Bir ASP.NET Core web uygulaması söz konusu olduğunda, ASP.NET Core web projesi giriş noktası olacaktır.</span><span class="sxs-lookup"><span data-stu-id="db788-187">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="db788-188">Ancak, bu çözüm yalnızca tek bir projenin oluşmalıdır anlamına gelmez.</span><span class="sxs-lookup"><span data-stu-id="db788-188">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="db788-189">Sorunları ayrılması takip etmek için farklı katmanlara uygulamayı oluşturan ayırmak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-189">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="db788-190">Katmanlara parçalanmış sonra daha iyi kapsülleme elde etmeye yardımcı olabilir projeleri ayırmak için klasörleri gitmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-190">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="db788-191">Bir ASP.NET Core uygulamayla bu hedeflere ulaşmak için en iyi yaklaşımı, temiz 5 bölümde tartışılan mimarisi çeşididir.</span><span class="sxs-lookup"><span data-stu-id="db788-191">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="db788-192">Bu yaklaşım uygulamanın çözüm ayrı kitaplıklarının UI, altyapı ve ApplicationCore oluşan.</span><span class="sxs-lookup"><span data-stu-id="db788-192">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="db788-193">Bu projeler ek olarak, ayrı bir test projeleri de dahil edilen (Bölüm 9'test açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="db788-193">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="db788-194">Uygulamanın nesne modeli ve arabirimleri ApplicationCore projesinde yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="db788-194">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="db788-195">Bu proje mümkün olduğunca az bağımlılıkları olacaktır ve çözümdeki diğer projelerin başvurur.</span><span class="sxs-lookup"><span data-stu-id="db788-195">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="db788-196">Altyapı üzerinde doğrudan bağlı olmayan hizmetleri olarak kalıcı olmasını gerektiren iş varlıklarını ApplicationCore projesinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="db788-196">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="db788-197">Kalıcılık nasıl gerçekleştirildiğini veya nasıl bir kullanıcı, bildirimleri gönderilebilir gibi uygulama ayrıntılarını altyapı projesinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="db788-197">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="db788-198">Bu projenin Entity Framework Çekirdek gibi uygulamaya özel paketleri başvurur, ancak proje dışında bu uygulamaların ayrıntılarını açığa çıkarmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-198">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="db788-199">Altyapı hizmetleri ve depoları ApplicationCore proje tanımlanan arabirimi uygulamalıdır ve kendi kalıcılığı ApplicationCore içinde tanımlanan varlıklar saklama ve alma için sorumlu uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-199">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="db788-200">ASP.NET Core proje herhangi bir kullanıcı Arabirimi düzeyi endişelerini sorumlu olduğu, ancak iş mantığı ya da altyapı ayrıntıları içermemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db788-200">The ASP.NET Core project itself is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="db788-201">Aslında, ideal olarak, hatta bir bağımlılık iki proje arasında hiçbir bağımlılık yanlışlıkla sunulan sağlamaya yardımcı olur altyapı projede sahip olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-201">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="db788-202">Bu kayıt defteri sınıfların her projede dı kuralları tanımlamanıza olanak verir StructureMap gibi üçüncü taraf bir dı kapsayıcı kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="db788-202">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="db788-203">Uygulama Ayrıntıları uygulamasından kesilmesi için başka bir yaklaşım, tek tek Docker kapsayıcılarında belki de dağıtılan uygulamayı çağrısı mikro sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="db788-203">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="db788-204">Bu sorunları ve iki projeleri arasında dı yararlanarak daha kesilmesi daha da büyük ayrımı sağlar, ancak ek karmaşıklık sahiptir.</span><span class="sxs-lookup"><span data-stu-id="db788-204">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="db788-205">Özellik kuruluş</span><span class="sxs-lookup"><span data-stu-id="db788-205">Feature Organization</span></span>

<span data-ttu-id="db788-206">Varsayılan olarak, ASP.NET Core uygulamaları denetleyicileri ve görünümler ve sık ViewModels dahil olmak üzere kendi klasör yapısı toplayın.</span><span class="sxs-lookup"><span data-stu-id="db788-206">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="db788-207">Bu sunucu tarafı yapıları desteklemek üzere istemci tarafı kodlar genellikle ayrı olarak wwwroot klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="db788-207">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="db788-208">Ancak, belirli bir özelliği genellikle çalışma bu klasörler arasında atlama gerektirdiğinden büyük uygulamalar bu kuruluşla sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-208">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="db788-209">Dosya ve alt her klasördeki sayısı arttıkça, Çözüm Gezgini aracılığıyla kaydırmanın büyük bir bölümünü sonuçta daha zor alır.</span><span class="sxs-lookup"><span data-stu-id="db788-209">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="db788-210">Bu sorun için bir çözüm olan uygulama kodu tarafından düzenlemek için *özelliği* yerine göre dosya türü.</span><span class="sxs-lookup"><span data-stu-id="db788-210">One solution to this problem is to organize application code by *feature* instead of by file type.</span></span> <span data-ttu-id="db788-211">Bu kuruluş stili genellikle için özellik klasörleri veya özellik dilimler olarak adlandırılır (Ayrıca bkz: [dikey dilimler](http://deviq.com/vertical-slices/)).</span><span class="sxs-lookup"><span data-stu-id="db788-211">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](http://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="db788-212">ASP.NET Core MVC alanları bu amaç için destekler.</span><span class="sxs-lookup"><span data-stu-id="db788-212">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="db788-213">Alanları kullanarak denetleyicileri ve görünümler klasörleri (aynı zamanda ilişkili tüm modelleri) her alanı klasörde ayrı ayrı kümeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-213">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="db788-214">Şekil 7-1 alanları kullanarak bir örnek klasör yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db788-214">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="db788-215">Şekil 7-1 örnek alanı kuruluş</span><span class="sxs-lookup"><span data-stu-id="db788-215">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="db788-216">Alanları kullanırken, ait oldukları alanın adı ile denetleyicilerinizi tasarlamanız öznitelikleri kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="db788-216">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="db788-217">Ayrıca, yolları alan Destek eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="db788-217">You also need to add area support to your routes:</span></span>

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="db788-218">Alanlar için yerleşik destek yanı sıra kendi klasör yapısı ve öznitelikler ve özel yollar yerine kuralları de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-218">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="db788-219">Bu ayrı klasörlerini eklemediniz görünümleri, denetleyicileri, tüm ilgili her özellik için tek bir yerde dosyaları görmeyi kolaylaştırır ve hiyerarşi daha düz tutulması vb. için özellik klasörleri yapmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="db788-219">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="db788-220">ASP.NET Core yerleşik kuralı türleri davranışını denetlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="db788-220">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="db788-221">Bu kuralları değiştirmek ya da değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db788-221">You can modify or replace these conventions.</span></span> <span data-ttu-id="db788-222">Örneğin, özellik adı (genellikle denetleyicisi bulunduğu klasörü karşılık gelen), ad göre belirli bir denetleyici için otomatik olarak alırsınız bir kural oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="db788-222">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

```csharp
FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

<span data-ttu-id="db788-223">Uygulamanıza ConfigureServices MVC desteği eklediğinizde, isteğe bağlı olarak bu kural belirtin:</span><span class="sxs-lookup"><span data-stu-id="db788-223">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="db788-224">ASP.NET Core MVC bir kuralı görünümlerini bulmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db788-224">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="db788-225">Böylece görünümler (yukarıda FeatureConvention tarafından sağlanan özellik adı kullanarak), özellik klasörlerde bulunan bir özel kuralı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-225">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="db788-226">Bu yaklaşımı hakkında daha fazla bilgi ve MSDN makalesinden çalışma örnek indirme [ASP.NET Core MVC özelliği dilimleri](https://msdn.microsoft.com/magazine/mt763233.aspx).</span><span class="sxs-lookup"><span data-stu-id="db788-226">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="db788-227">Çapraz kesme sorunları</span><span class="sxs-lookup"><span data-stu-id="db788-227">Cross-Cutting Concerns</span></span>

<span data-ttu-id="db788-228">Uygulamaları arttıkça, çoğaltma ortadan kaldırmak ve tutarlılık sağlamak için çapraz kesme sorunları faktörü giderek önemli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="db788-228">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="db788-229">Olsa diğer birçok bazı arası kesme sorunları ASP.NET Core uygulamalarında kimlik doğrulama, model doğrulama kuralları, çıktı önbelleği ve hata işleme, gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="db788-229">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="db788-230">ASP.NET Core MVC [filtreleri](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) , önce veya sonra istek işleme ardışık düzeninde belirli adımları kodu çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="db788-230">ASP.NET Core MVC [filters](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="db788-231">Örneğin, bir filtre önce ve sonra model bağlama, önce ve bir eylem veya önce ve sonra bir eylem sonucu çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-231">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="db788-232">Bir yetkilendirme filtresi, kalan ardışık düzenini erişimi denetlemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-232">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="db788-233">Şekil 7-2'de gösterildiği nasıl yürütme akış filtreleri yoluyla yapılandırdıysanız isteyin.</span><span class="sxs-lookup"><span data-stu-id="db788-233">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![Talep yetkilendirme filtreleri, kaynak filtreleri, Model bağlama, eylem filtreleri, eylem yürütme ve eylem sonucu dönüştürme, özel durum filtreleri, sonuç filtreleri ve sonuç yürütme işlenir.](./media/image7-2.png)

<span data-ttu-id="db788-236">Şekil 7-2 İstek Yürütme filtreleri ve istek ardışık düzeni üzerinden.</span><span class="sxs-lookup"><span data-stu-id="db788-236">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="db788-237">Bunları denetleyicileri veya Eylemler uygulayabilmek için filtreleri genellikle öznitelik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="db788-237">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="db788-238">Bu şekilde, eylem düzeyi geçersiz kılma veya denetleyici düzeyinde belirtilen filtreler temel yapı belirtilen filtreler eklendiğinde kendileri genel filtreleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="db788-238">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="db788-239">Örneğin, \[rota\] özniteliği denetleyicileri ve eylemleri arasındaki yolları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-239">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="db788-240">Benzer şekilde, yetkilendirme denetleyici düzeyinde yapılandırılabilir ve aşağıdaki örnek gösterdiği gibi ayrı eylemler tarafından geçersiz kılındı:</span><span class="sxs-lookup"><span data-stu-id="db788-240">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="db788-241">İlk yöntem, oturum açma, AllowAnonymous filtre (özniteliği) Authorize filtresi denetleyici düzeyinde Ayarla geçersiz kılmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="db788-241">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="db788-242">Kimliği doğrulanmış bir isteği ForgotPassword eylem (ve AllowAnonymous özniteliğine sahip değil sınıfı içinde herhangi bir işlem) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="db788-242">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="db788-243">Filtreler, çoğaltma ortak hata ilkeleri API'ler işleme biçiminde ortadan kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-243">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="db788-244">Örneğin, tipik bir API İlkesi model doğrulama başarısız olursa mevcut anahtarları başvuran isteklerin NotFound yanıt ve bir BadRequest yanıt getirmektir.</span><span class="sxs-lookup"><span data-stu-id="db788-244">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="db788-245">Aşağıdaki örnek, bu iki ilke uygulamada gösterir:</span><span class="sxs-lookup"><span data-stu-id="db788-245">The following example demonstrates these two policies in action:</span></span>

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="db788-246">Bu gibi koşullu koduyla kalabalık hale için eylem yöntemlerini izin vermez.</span><span class="sxs-lookup"><span data-stu-id="db788-246">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="db788-247">Bunun yerine, ilkeleri gerektiği ölçüde temeline göre uygulanabilir filtreleri içine alın.</span><span class="sxs-lookup"><span data-stu-id="db788-247">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="db788-248">Bu örnekte, bir komut API için gönderilen dilediğiniz zaman gerçekleşeceğini, model doğrulama denetimi aşağıdaki özniteliği tarafından değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="db788-248">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

<span data-ttu-id="db788-249">Benzer şekilde, bir filtre, bir kaydı var ve bu denetimleri eylemi gerçekleştirmek için gereksinimini eylem yürütülmeden önce bir 404 dönüş denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-249">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="db788-250">Genel kurallar çekilen ve altyapı kodu ve iş mantığı, kullanıcı Arabiriminden ayırmak için çözümünüzün düzenlenmiş sonra MVC eylem yöntemleri son derece ince olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="db788-250">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="db788-251">Daha fazla bilgiyi filtreleri uygulama ve çalışma örnek MSDN makalesinden indirme hakkında [gerçek dünya ASP.NET Core MVC filtreleri](https://msdn.microsoft.com/magazine/mt767699.aspx).</span><span class="sxs-lookup"><span data-stu-id="db788-251">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="db788-252">Başvuruları – uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="db788-252">References – Structuring Applications</span></span>
> - <span data-ttu-id="db788-253">**Alanları**</span><span class="sxs-lookup"><span data-stu-id="db788-253">**Areas**</span></span>  
> <span data-ttu-id="db788-254"><https://docs.microsoft.com/ASPNET/Core/MVC/Controllers/areas></span><span class="sxs-lookup"><span data-stu-id="db788-254"><https://docs.microsoft.com/aspnet/core/mvc/controllers/areas></span></span>
> - <span data-ttu-id="db788-255">**MSDN – ASP.NET Core MVC özelliği dilimleri**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx></span><span class="sxs-lookup"><span data-stu-id="db788-255">**MSDN – Feature Slices for ASP.NET Core MVC**
<https://msdn.microsoft.com/magazine/mt763233.aspx></span></span>
> - <span data-ttu-id="db788-256">**Filtreleri**</span><span class="sxs-lookup"><span data-stu-id="db788-256">**Filters**</span></span>  
> <span data-ttu-id="db788-257"><https://docs.microsoft.com/ASPNET/Core/MVC/Controllers/Filters></span><span class="sxs-lookup"><span data-stu-id="db788-257"><https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>
> - <span data-ttu-id="db788-258">**MSDN – gerçek dünya ASP.NET Core MVC filtreleri**</span><span class="sxs-lookup"><span data-stu-id="db788-258">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
> <span data-ttu-id="db788-259"><https://msdn.microsoft.com/Magazine/mt767699.aspx></span><span class="sxs-lookup"><span data-stu-id="db788-259"><https://msdn.microsoft.com/magazine/mt767699.aspx></span></span>

## <a name="security"></a><span data-ttu-id="db788-260">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="db788-260">Security</span></span>

<span data-ttu-id="db788-261">Web uygulamalarının güvenliğini sağlama birçok göz önünde büyük bir konu ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="db788-261">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="db788-262">En temel düzeyde, belirtilen bir isteğin geldiği ve bu isteği yalnızca gerektiği kaynaklara erişimi olduğundan emin olduktan bildiğiniz sağlayarak güvenlik içerir.</span><span class="sxs-lookup"><span data-stu-id="db788-262">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that that request only has access to resources it should.</span></span> <span data-ttu-id="db788-263">Kimlik doğrulama isteği bilinen bir varlıktan geliyormuş gibi değerlendirilip değerlendirilmeyeceğini görmek için bir istek bu güvenilir veri deposunda ile sağlanan kimlik bilgileri karşılaştırma işlemidir.</span><span class="sxs-lookup"><span data-stu-id="db788-263">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="db788-264">Yetkilendirme kullanıcı kimliğine göre belirli kaynaklara erişimi kısıtlama işlemidir.</span><span class="sxs-lookup"><span data-stu-id="db788-264">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="db788-265">Üçüncü güvenlik sorunu istekleri için size gereken en az üçüncü taraflar tarafından gizli dinleme koruma [SSL, uygulamanız tarafından kullanıldığından emin olun](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span><span class="sxs-lookup"><span data-stu-id="db788-265">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="db788-266">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="db788-266">Authentication</span></span>

<span data-ttu-id="db788-267">ASP.NET Core, uygulamanız için oturum açma işlevleri desteklemek için kullanabileceğiniz bir üyelik sistemi kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="db788-267">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="db788-268">Yerel kullanıcı hesapları için destek ve aynı zamanda Microsoft Account, Twitter, Facebook, Google ve daha fazlası gibi sağlayıcılarından dış oturum açma sağlayıcısı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="db788-268">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="db788-269">ASP.NET Core kimliği ek olarak, windows kimlik doğrulaması, uygulamanızın kullanabilir veya bir üçüncü taraf kimlik sağlayıcısı ister [kimlik sunucusunu](https://github.com/IdentityServer/IdentityServer4).</span><span class="sxs-lookup"><span data-stu-id="db788-269">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="db788-270">Bireysel kullanıcı hesapları seçeneği seçili değilse ASP.NET Core kimlik yeni proje şablonlarını dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="db788-270">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="db788-271">Bu şablon, kayıt, oturum açma, dış oturum açma bilgileri, unutulan parolaları ve ek işlevsellik için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="db788-271">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="db788-272">Şekil 7-3 seçin bireysel kullanıcı kimliği önceden yapılandırılmış olmasını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="db788-272">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="db788-273">Kimlik desteği, başlangıç, hem de ConfigureServices ve yapılandırma yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="db788-273">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="db788-274">UseIdentity yapılandırma yönteminde UseMvc önce görünen önemlidir.</span><span class="sxs-lookup"><span data-stu-id="db788-274">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="db788-275">Kimlik ConfigureServices içinde yapılandırırken AddDefaultTokenProviders çağrısı fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-275">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="db788-276">Bu web iletişimin güvenliğini sağlamak için kullanılabilir, ancak bunun yerine SMS veya e-posta için bunları sırayla kimliğini onaylamak için üzerinden kullanıcılara gönderilen istekleri oluşturmak sağlayıcıları başvuruyor belirteçleri ile ilgisi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="db788-276">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="db788-277">Hakkında daha fazla bilgiyi [iki faktörlü kimlik doğrulamasını yapılandırma](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) ve [dış oturum açma sağlayıcılarını etkinleştirme](https://docs.microsoft.com/aspnet/core/security/authentication/social/) resmi ASP.NET Core belgeleri gelen.</span><span class="sxs-lookup"><span data-stu-id="db788-277">You can learn more about [configuring two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) and [enabling external login providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="db788-278">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="db788-278">Authorization</span></span>

<span data-ttu-id="db788-279">Yetkilendirme en basit biçimi, anonim kullanıcılar için erişimi kısıtlamak içerir.</span><span class="sxs-lookup"><span data-stu-id="db788-279">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="db788-280">Bu basitçe uygulayarak sağlanabilir \[Authorize\] özniteliği belirli denetleyicileri veya eylemler.</span><span class="sxs-lookup"><span data-stu-id="db788-280">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="db788-281">Rolleri kullanılıyorsa gösterildiği gibi belirli rollere ait olan kullanıcılar için erişimi kısıtlamak için daha fazla öznitelik Genişletilebilir:</span><span class="sxs-lookup"><span data-stu-id="db788-281">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="db788-282">Bu durumda, kullanıcılar ya da HRManager veya finans rolleri (veya her ikisi de) ait SalaryController erişimi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db788-282">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="db788-283">Bir kullanıcı birden çok rol için (yalnızca biri birkaç) ait zorunlu kılmak için her zaman gerekli rol belirten birden çok kez öznitelik uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-283">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="db788-284">Birçok farklı denetleyicileri ve eylemleri dizelerde istenmeyen yineleme açabilir gibi belirli roller kümesi belirtme.</span><span class="sxs-lookup"><span data-stu-id="db788-284">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="db788-285">Yetkilendirme kuralları saklayan, yetkilendirme ilkelerini yapılandırın ve ardından ilkeyi bireysel rolleri yerine uygularken belirtin \[Authorize\] özniteliği:</span><span class="sxs-lookup"><span data-stu-id="db788-285">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="db788-286">İlkeleri bu şekilde kullanarak, belirli roller ya da uygulayan kuralları sınırlı kalmayarak Eylemler türlerini ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-286">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="db788-287">Belirli kaynaklara erişmesi gereken yeni bir rol oluşturursanız, daha sonra yalnızca üzerinde her rollerin listesini güncelleştirme yerine bir ilke güncelleştirebilirsiniz her \[Authorize\] özniteliği.</span><span class="sxs-lookup"><span data-stu-id="db788-287">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="db788-288">Talepleri</span><span class="sxs-lookup"><span data-stu-id="db788-288">Claims</span></span>

<span data-ttu-id="db788-289">Talep Kimliği doğrulanmış bir kullanıcı özelliklerini temsil eden adı değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="db788-289">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="db788-290">Örneğin, kullanıcıların çalışan numarası bir talep depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-290">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="db788-291">Talep Yetkilendirme İlkeleri bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-291">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="db788-292">"EmployeeOnly" adında bir ilke oluşturabilirsiniz Bu örnekte gösterildiği gibi "EmployeeNumber" adlı bir talep varlığını gerektirir:</span><span class="sxs-lookup"><span data-stu-id="db788-292">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

<span data-ttu-id="db788-293">Bu ilke ile sonra kullanılabilir \[Authorize\] herhangi bir denetleyici ve/veya eylem, yukarıda açıklandığı gibi korumak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="db788-293">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="db788-294">Web API güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="db788-294">Securing Web APIs</span></span>

<span data-ttu-id="db788-295">Çoğu web API'leri, bir belirteç tabanlı kimlik doğrulama sistemi uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db788-295">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="db788-296">Belirteç kimlik doğrulama, durum bilgisiz ve ölçeklenebilir olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="db788-296">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="db788-297">Bir belirteç tabanlı kimlik doğrulama sisteminde istemci ilk ile kimlik doğrulama sağlayıcısını kimliğini doğrulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db788-297">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="db788-298">Başarılı olursa, istemcinin sadece bir şifreleme açısından anlamlı karakter dizesidir bir belirteç verilir.</span><span class="sxs-lookup"><span data-stu-id="db788-298">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="db788-299">İstemci ardından bir API için bir istek yayınlamasını gerektiğinde bu belirteç isteği başlığındaki olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="db788-299">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="db788-300">Sunucu, ardından istek tamamlamadan önce istek üstbilgisinde bulunan belirteci doğrular.</span><span class="sxs-lookup"><span data-stu-id="db788-300">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="db788-301">Şekil 7-4, bu işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="db788-301">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="db788-303">**Şekil 7-4.**</span><span class="sxs-lookup"><span data-stu-id="db788-303">**Figure 7-4.**</span></span> <span data-ttu-id="db788-304">Belirteç tabanlı kimlik doğrulaması Web API'leri için.</span><span class="sxs-lookup"><span data-stu-id="db788-304">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="db788-305">Başvuruları – güvenlik</span><span class="sxs-lookup"><span data-stu-id="db788-305">References – Security</span></span>
> - <span data-ttu-id="db788-306">**Güvenlik belgeleri genel bakış**</span><span class="sxs-lookup"><span data-stu-id="db788-306">**Security Docs Overview**</span></span>  
> <span data-ttu-id="db788-307">https://docs.microsoft.com/ASPNET/Core/Security/</span><span class="sxs-lookup"><span data-stu-id="db788-307">https://docs.microsoft.com/aspnet/core/security/</span></span>
> - <span data-ttu-id="db788-308">**Bir ASP.NET Core uygulamasında SSL zorlama**</span><span class="sxs-lookup"><span data-stu-id="db788-308">**Enforcing SSL in an ASP.NET Core App**</span></span>  
> <span data-ttu-id="db788-309"><https://docs.microsoft.com/ASPNET/Core/Security/enforcing-SSL></span><span class="sxs-lookup"><span data-stu-id="db788-309"><https://docs.microsoft.com/aspnet/core/security/enforcing-ssl></span></span>
> - <span data-ttu-id="db788-310">**Kimlik giriş**</span><span class="sxs-lookup"><span data-stu-id="db788-310">**Introduction to Identity**</span></span>  
> <span data-ttu-id="db788-311"><https://docs.microsoft.com/ASPNET/Core/Security/Authentication/identity></span><span class="sxs-lookup"><span data-stu-id="db788-311"><https://docs.microsoft.com/aspnet/core/security/authentication/identity></span></span>
> - <span data-ttu-id="db788-312">**Yetkilendirme giriş**</span><span class="sxs-lookup"><span data-stu-id="db788-312">**Introduction to Authorization**</span></span>  
> <span data-ttu-id="db788-313"><https://docs.microsoft.com/ASPNET/Core/Security/Authorization/introduction></span><span class="sxs-lookup"><span data-stu-id="db788-313"><https://docs.microsoft.com/aspnet/core/security/authorization/introduction></span></span>
> - <span data-ttu-id="db788-314">**Kimlik doğrulama ve yetkilendirme Azure uygulama hizmetinde API uygulamaları için**</span><span class="sxs-lookup"><span data-stu-id="db788-314">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
> <span data-ttu-id="db788-315"><https://docs.microsoft.com/Azure/App-Service-api/App-Service-api-Authentication></span><span class="sxs-lookup"><span data-stu-id="db788-315"><https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication></span></span>

## <a name="client-communication"></a><span data-ttu-id="db788-316">İstemci iletişimi</span><span class="sxs-lookup"><span data-stu-id="db788-316">Client Communication</span></span>

<span data-ttu-id="db788-317">Sayfalarını sunmadan ve web API'leri aracılığıyla veri isteklerine yanıt ek olarak, ASP.NET Core uygulamaları doğrudan bağlı istemcileri ile iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-317">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="db788-318">Bu giden iletişim çeşitli aktarım teknolojiler, en yaygın olma WebSockets kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-318">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="db788-319">ASP.NET Core SignalR, uygulamalarınıza gerçek zamanlı sunucu istemci iletişimi işlevselliği türdeki basit sağlayan bir kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="db788-319">ASP.NET Core SignalR is a library that makes it simple to kind of real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="db788-320">SignalR WebSockets, aktarım teknolojilerini çeşitli destekler ve geliştirici uygulama ayrıntılarından, dışarıda çok soyutlar.</span><span class="sxs-lookup"><span data-stu-id="db788-320">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="db788-321">ASP.NET Core SignalR şu anda geliştirilmekte ve ASP.NET Core sonraki sürümde kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="db788-321">ASP.NET Core SignalR is currently under development, and will be available in the next release of ASP.NET Core.</span></span> <span data-ttu-id="db788-322">Ancak, diğer [kaynak WebSockets kitaplıkları açmak](https://github.com/radu-matei/websocket-manager) şu anda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-322">However, other [open source WebSockets libraries](https://github.com/radu-matei/websocket-manager) are currently available.</span></span>

<span data-ttu-id="db788-323">Gerçek zamanlı istemci iletişimi, doğrudan WebSockets veya başka teknikler kullanarak olup çeşitli uygulama senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-323">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="db788-324">Bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="db788-324">Some examples include:</span></span>

-   <span data-ttu-id="db788-325">Canlı sohbet odası uygulamaları</span><span class="sxs-lookup"><span data-stu-id="db788-325">Live chat room applications</span></span>

-   <span data-ttu-id="db788-326">Uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="db788-326">Monitoring applications</span></span>

-   <span data-ttu-id="db788-327">İş ilerleme güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="db788-327">Job progress updates</span></span>

-   <span data-ttu-id="db788-328">Bildirimler</span><span class="sxs-lookup"><span data-stu-id="db788-328">Notifications</span></span>

-   <span data-ttu-id="db788-329">Etkileşimli forms uygulamaları</span><span class="sxs-lookup"><span data-stu-id="db788-329">Interactive forms applications</span></span>

<span data-ttu-id="db788-330">İstemci iletişimi, uygulamalara oluştururken da genellikle iki bileşeni vardır:</span><span class="sxs-lookup"><span data-stu-id="db788-330">When building client communication into your applications, there are typically two components:</span></span>

-   <span data-ttu-id="db788-331">Sunucu tarafı Bağlantı Yöneticisi'ni (SignalR hub'ı, WebSocketManager WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="db788-331">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

-   <span data-ttu-id="db788-332">İstemci-tarafı kitaplığı</span><span class="sxs-lookup"><span data-stu-id="db788-332">Client-side library</span></span>

<span data-ttu-id="db788-333">İstemcileri tarayıcıları – mobil uygulamaları, konsol uygulamalar, sınırlı değildir ve diğer yerel uygulamalar ayrıca SignalR/WebSockets kullanarak iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-333">Clients are not limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="db788-334">Aşağıdaki basit programı WebSocketManager örnek bir uygulama bir parçası olarak konsola sohbet uygulamaya gönderilen tüm içeriği görüntülemektedir:</span><span class="sxs-lookup"><span data-stu-id="db788-334">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }
    
    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }
    
    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
```

<span data-ttu-id="db788-335">Uygulamalarınızı doğrudan istemci uygulamaları ile iletişim kurmak ve gerçek zamanlı iletişim uygulamanızın kullanıcı artırmak göz önünde bulundurun yolları deneyimi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="db788-335">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="db788-336">Başvuruları – istemci iletişimi</span><span class="sxs-lookup"><span data-stu-id="db788-336">References – Client Communication</span></span>
> - <span data-ttu-id="db788-337">**ASP.NET Core SignalR**</span><span class="sxs-lookup"><span data-stu-id="db788-337">**ASP.NET Core SignalR**</span></span>  
> <span data-ttu-id="db788-338"><https://github.com/ASPNET/SignalR></span><span class="sxs-lookup"><span data-stu-id="db788-338"><https://github.com/aspnet/SignalR></span></span>
> - <span data-ttu-id="db788-339">**WebSocket Yöneticisi**</span><span class="sxs-lookup"><span data-stu-id="db788-339">**WebSocket Manager**</span></span>  
> <span data-ttu-id="db788-340">https://github.com/radu-matei/websocket-Manager</span><span class="sxs-lookup"><span data-stu-id="db788-340">https://github.com/radu-matei/websocket-manager</span></span>

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="db788-341">Etki alanı tabanlı tasarım – bu uygulamalıdır?</span><span class="sxs-lookup"><span data-stu-id="db788-341">Domain-Driven Design – Should You Apply It?</span></span>

<span data-ttu-id="db788-342">Etki alanı tabanlı tasarım (DDD) olan üzerine odaklanan vurgular yazılım oluşturmaya Çevik bir yaklaşım *iş etki alanı*.</span><span class="sxs-lookup"><span data-stu-id="db788-342">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the *business domain*.</span></span> <span data-ttu-id="db788-343">Ağır indirimlere iletişim ve geliştiricileri için gerçek sisteminin nasıl çalıştığı ilişkilendirebilirsiniz iş etki alanı expert(s) etkileşim yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="db788-343">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="db788-344">Örneğin, stok ticaret anlaşması işleyen bir sistem oluşturuyorsanız, etki alanı Uzman deneyimli stok Aracısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-344">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="db788-345">DDD büyük ve karmaşık iş sorunlarını gidermek için tasarlanmıştır ve yatırım anlama ve etki alanı modelleme, olmadığından daha küçük, daha basit uygulamalar için uygun değil genellikle.</span><span class="sxs-lookup"><span data-stu-id="db788-345">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="db788-346">Ekibinizin (teknik olmayan paydaşlara ve katkıda bulunanlar dahil) DDD yaklaşımı izleyerek yazılım oluştururken geliştirmelisiniz bir *bulunabilen dil* sorun alanı için.</span><span class="sxs-lookup"><span data-stu-id="db788-346">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a *ubiquitous language* for the problem space.</span></span> <span data-ttu-id="db788-347">Diğer bir deyişle, aynı terminolojisi Modellenen gerçek kavram, yazılım eşdeğer ve (örneğin, veritabanı tabloları) kavram kalıcı hale getirmek için mevcut olabilecek tüm yapıları için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-347">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="db788-348">Bu nedenle, her yerden dilde açıklanan kavramları temelini, *etki alanı modeli*.</span><span class="sxs-lookup"><span data-stu-id="db788-348">Thus, the concepts described in the ubiquitous language should form the basis for your *domain model*.</span></span>

<span data-ttu-id="db788-349">Sistem davranışını temsil etmek için birbiriyle etkileşim nesnelerinin, etki alanı modeli oluşur.</span><span class="sxs-lookup"><span data-stu-id="db788-349">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="db788-350">Bu nesneler, aşağıdaki kategorilere ayrılır:</span><span class="sxs-lookup"><span data-stu-id="db788-350">These objects may fall into the following categories:</span></span>

-   <span data-ttu-id="db788-351">[Varlıkları](http://deviq.com/entity/), bir iş parçacığı kimliği nesneleriyle temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db788-351">[Entities](http://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="db788-352">Varlıklar, genellikle, bunlar daha sonra alınabilir bir anahtarla kalıcı depolanır.</span><span class="sxs-lookup"><span data-stu-id="db788-352">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

-   <span data-ttu-id="db788-353">[Toplamalar](http://deviq.com/aggregate-pattern/), bir birim olarak kalıcı nesne gruplarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db788-353">[Aggregates](http://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

-   <span data-ttu-id="db788-354">[Değer nesneleri](http://deviq.com/value-object/), özellik değerlerine toplamını temel alarak karşılaştırılabilir kavramları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db788-354">[Value objects](http://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="db788-355">Örneğin, bir başlangıç ve bitiş tarihi oluşan DateRange.</span><span class="sxs-lookup"><span data-stu-id="db788-355">For example, DateRange consisting of a start and end date.</span></span>

-   <span data-ttu-id="db788-356">[Etki alanı olayları](https://martinfowler.com/eaaDev/DomainEvent.html), sisteminin diğer bölümleriyle ilgi sistem içinde gerçekleştiği şeyler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db788-356">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="db788-357">DDD etki alanı modeli modelindeki karmaşık davranışı kapsülleyen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="db788-357">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="db788-358">Varlıklar, özellikle, yalnızca özelliklerinin koleksiyonlarından oluşan olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-358">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="db788-359">Etki alanı modeli davranışına sahip değil ve yalnızca sistem durumunu temsil eder, bu olarak kabul edilir bir [anemic modeli](http://deviq.com/anemic-model/), GGG istenmeyen olduğu.</span><span class="sxs-lookup"><span data-stu-id="db788-359">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](http://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="db788-360">Bu model türlerinin yanı sıra DDD genellikle desenleri çeşitli uygular:</span><span class="sxs-lookup"><span data-stu-id="db788-360">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

-   <span data-ttu-id="db788-361">[Depo](http://deviq.com/repository-pattern/), Kalıcılık ayrıntılarını özetleyen için.</span><span class="sxs-lookup"><span data-stu-id="db788-361">[Repository](http://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

-   <span data-ttu-id="db788-362">[Fabrika](https://en.wikipedia.org/wiki/Factory_method_pattern), karmaşık nesne oluşturma Kapsüllenen için.</span><span class="sxs-lookup"><span data-stu-id="db788-362">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

-   <span data-ttu-id="db788-363">Davranış tetikleme gelen bağımlı davranışı kesilmesi için etki alanı olaylar.</span><span class="sxs-lookup"><span data-stu-id="db788-363">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

-   <span data-ttu-id="db788-364">[Hizmetleri](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), kapsülleyerek karmaşık davranışı ve/veya altyapı uygulama ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="db788-364">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

-   <span data-ttu-id="db788-365">[Komut](https://en.wikipedia.org/wiki/Command_pattern), ayırma için verme komutları ve komut yürütme.</span><span class="sxs-lookup"><span data-stu-id="db788-365">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

-   <span data-ttu-id="db788-366">[Belirtimi](http://deviq.com/specification-pattern/), sorgu ayrıntıları Kapsüllenen için.</span><span class="sxs-lookup"><span data-stu-id="db788-366">[Specification](http://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="db788-367">DDD gevşek bağlantı, kapsülleme ve birim testleri kullanarak kolayca doğrulanabilir kodu için izin verme temiz daha önce ele alınan mimarisi kullanımını da önerir.</span><span class="sxs-lookup"><span data-stu-id="db788-367">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="db788-368">DDD uyguladığınızda</span><span class="sxs-lookup"><span data-stu-id="db788-368">When Should You Apply DDD</span></span>

<span data-ttu-id="db788-369">DDD (yalnızca teknik) önemli iş karmaşıklık ile büyük uygulamalar için çok uygundur.</span><span class="sxs-lookup"><span data-stu-id="db788-369">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="db788-370">Uygulama etki alanı uzmanlar bilgisi istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="db788-370">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="db788-371">İş kuralları ve yalnızca depolama ve veri depolarına çeşitli kayıtları geçerli durumu alma ötesinde etkileşimleri temsil eden etki alanı modeli kendisini önemli davranışı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db788-371">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="db788-372">DDD uyguladığınızda döndürmemelidir</span><span class="sxs-lookup"><span data-stu-id="db788-372">When Shouldn't You Apply DDD</span></span>

<span data-ttu-id="db788-373">DDD modelleme, mimari ve daha küçük uygulamalar veya temelde yalnızca CRUD (oluşturma/okuma/güncelleştirme/silme) olan uygulamalar için garanti değil iletişimi yatırım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="db788-373">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="db788-374">Uygulamanızı DDD aşağıdaki yaklaşımlardan, ancak etki alanınız yok davranışı anemic bir modelle olduğunu bulmak tercih ederseniz, yaklaşım zorlanıyor gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="db788-374">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="db788-375">Uygulamanızı DDD ihtiyacınız olmayabilir ya da etki alanı modeli yerine veritabanı ya da kullanıcı arabirimi iş mantığını saklamak için uygulamanızı yeniden düzenleme yardıma ihtiyacınız.</span><span class="sxs-lookup"><span data-stu-id="db788-375">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="db788-376">Karma bir yaklaşım, yalnızca GGG uygulamanın işlem ya da daha karmaşık alanlar için ancak daha basit CRUD veya uygulama salt okunur bölümlerini için kullanmak üzere olacaktır.</span><span class="sxs-lookup"><span data-stu-id="db788-376">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="db788-377">Örneğin, bir raporu görüntülemek için veya bir Pano için görselleştirmek için verileri sorgulama, bir toplama kısıtlama söz konusu gerekmez.</span><span class="sxs-lookup"><span data-stu-id="db788-377">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="db788-378">Bu tür gereksinimleri için daha basit, ayrı okuma modeline sahip edilebilir.</span><span class="sxs-lookup"><span data-stu-id="db788-378">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="db788-379">Başvuruları – etki alanı Odaklı Tasarım</span><span class="sxs-lookup"><span data-stu-id="db788-379">References – Domain-Driven Design</span></span>
> - <span data-ttu-id="db788-380">**Düz İngilizce (StackOverflow yanıt) DDD**</span><span class="sxs-lookup"><span data-stu-id="db788-380">**DDD in Plain English (StackOverflow Answer)**</span></span>  
> <span data-ttu-id="db788-381"><https://StackOverflow.com/Questions/1222392/CAN-someone-Explain-Domain-driven-Design-ddd-in-plain-English-Please/1222488#1222488></span><span class="sxs-lookup"><span data-stu-id="db788-381"><https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488></span></span>

## <a name="deployment"></a><span data-ttu-id="db788-382">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="db788-382">Deployment</span></span>

<span data-ttu-id="db788-383">Burada barındırılacak bağımsız olarak ASP.NET Core uygulamanızı dağıtma sürecinde ilgili birkaç adım vardır.</span><span class="sxs-lookup"><span data-stu-id="db788-383">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="db788-384">Yapılabilir uygulamayı yayımlamak için ilk adımdır dotnet kullanarak yayımlamak CLI komutu.</span><span class="sxs-lookup"><span data-stu-id="db788-384">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="db788-385">Bu uygulamayı derleyin ve atanmış bir klasöre uygulamayı çalıştırmak için gereken tüm dosyaların yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="db788-385">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="db788-386">Visual Studio'dan dağıttığınızda, bu adımı sizin için otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="db788-386">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="db788-387">Yayımlama klasörü .exe ve .dll dosyaları için uygulama ve onun bağımlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="db788-387">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="db788-388">Kendi başına bir uygulama .NET çalışma zamanı sürümünü de içerir.</span><span class="sxs-lookup"><span data-stu-id="db788-388">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="db788-389">ASP.NET Core uygulamaları da yapılandırma dosyalarını, statik istemciyi varlıklar ve MVC görünümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="db788-389">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="db788-390">ASP.NET Core uygulamaları sunucu önyüklenir ve uygulama (veya sunucu) çökerse yeniden başlatılması gerekir konsol uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="db788-390">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="db788-391">Bir işlem yöneticisi, bu işlemi otomatikleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db788-391">A process manager can be used to automate this process.</span></span> <span data-ttu-id="db788-392">ASP.NET Core en yaygın işlem yöneticilerinden Nginx ve Linux ve IIS üzerinde Apache ya da Windows'da Windows hizmeti ' dir.</span><span class="sxs-lookup"><span data-stu-id="db788-392">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="db788-393">İşlem Yöneticisi ek olarak, ASP.NET Core uygulamaları Kestrel web sunucusunda barındırılan bir ters proxy sunucusu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="db788-393">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="db788-394">Ters proxy sunucusu internet'ten HTTP isteklerini alır ve bunları Kestrel için bazı ön işleme sonra iletir.</span><span class="sxs-lookup"><span data-stu-id="db788-394">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="db788-395">Ters proxy sunucuları uygulama için bir güvenlik katmanı sağlamak ve (trafiğini Internet'ten gösterilen) kenar dağıtımlar için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="db788-395">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="db788-396">Kestrel görece olarak daha yeni ve henüz belirli saldırılarına karşı savunma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="db788-396">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="db788-397">Kestrel aynı zamanda barındırma üstbilgileri gibi teknikler kendisiyle aynı bağlantı noktasını ve IP adresini birden çok uygulamayı barındıran etkinleştirmek için kullanılamaz aynı bağlantı noktasında birden çok uygulamayı barındıran desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="db788-397">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![Internet'e kestrel](./media/image7-5.png)

<span data-ttu-id="db788-399">Şekil 7-5 ters proxy sunucunun arkasında Kestrel içinde barındırılan ASP.NET</span><span class="sxs-lookup"><span data-stu-id="db788-399">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="db788-400">Ters proxy yararlı olabilir başka bir SSL/HTTPS kullanarak birden çok uygulama güvenliğini sağlamak için bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="db788-400">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="db788-401">Bu durumda, yalnızca ters proxy SSL yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db788-401">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="db788-402">Ters proxy sunucusu ve Kestrel arasındaki iletişimi yer HTTP üzerinden Şekil 7-6'da gösterildiği gibi ele geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="db788-402">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="db788-403">Şekil 7-6 HTTPS güvenlikli ters proxy sunucunun arkasında barındırılan ASP.NET</span><span class="sxs-lookup"><span data-stu-id="db788-403">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="db788-404">Bir giderek popüler ASP.NET Core uygulamanızda ardından yerel olarak barındırılan veya bulut tabanlı barındırmak için Azure'da dağıtılan bir Docker kapsayıcısı barındırmak için bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="db788-404">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="db788-405">Docker kapsayıcısı Kestrel üzerinde çalışan uygulama kodunuz içerebilir ve bir ters proxy sunucunun arkasındaki yukarıda gösterildiği gibi dağıtılması.</span><span class="sxs-lookup"><span data-stu-id="db788-405">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="db788-406">Uygulamanızı Azure üzerinde koyduysanız birkaç hizmetleri sağlamak için ayrılmış bir sanal gereç olarak Microsoft Azure uygulama ağ geçidi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db788-406">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="db788-407">Tek tek uygulamalar için ters proxy görevi gören ek olarak, uygulama ağ geçidi aynı zamanda aşağıdaki özellikleri sunmaktadır:</span><span class="sxs-lookup"><span data-stu-id="db788-407">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

-   <span data-ttu-id="db788-408">HTTP Yük Dengeleme</span><span class="sxs-lookup"><span data-stu-id="db788-408">HTTP load balancing</span></span>

-   <span data-ttu-id="db788-409">SSL boşaltma (yalnızca Internet'e SSL)</span><span class="sxs-lookup"><span data-stu-id="db788-409">SSL offload (SSL only to Internet)</span></span>

-   <span data-ttu-id="db788-410">Uçtan uca SSL</span><span class="sxs-lookup"><span data-stu-id="db788-410">End to End SSL</span></span>

-   <span data-ttu-id="db788-411">Çok siteli yönlendirme (tek bir uygulama ağ geçidi en fazla 20 sitelerinde birleştirmek)</span><span class="sxs-lookup"><span data-stu-id="db788-411">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

-   <span data-ttu-id="db788-412">Web uygulaması güvenlik duvarı</span><span class="sxs-lookup"><span data-stu-id="db788-412">Web application firewall</span></span>

-   <span data-ttu-id="db788-413">Websocket desteği</span><span class="sxs-lookup"><span data-stu-id="db788-413">Websocket support</span></span>

-   <span data-ttu-id="db788-414">Gelişmiş tanılama</span><span class="sxs-lookup"><span data-stu-id="db788-414">Advanced diagnostics</span></span>

<span data-ttu-id="db788-415">*Bölüm 10'daki Azure dağıtım seçenekleri hakkında daha fazla bilgi edinin.*</span><span class="sxs-lookup"><span data-stu-id="db788-415">*Learn more about Azure deployment options in Chapter 10.*</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="db788-416">Başvuruları – dağıtım</span><span class="sxs-lookup"><span data-stu-id="db788-416">References – Deployment</span></span>
> - <span data-ttu-id="db788-417">**Barındırma ve dağıtımına genel bakış**</span><span class="sxs-lookup"><span data-stu-id="db788-417">**Hosting and Deployment Overview**</span></span>  
> <span data-ttu-id="db788-418"><https://docs.microsoft.com/ASPNET/Core/Publishing/></span><span class="sxs-lookup"><span data-stu-id="db788-418"><https://docs.microsoft.com/aspnet/core/publishing/></span></span>
> - <span data-ttu-id="db788-419">**Ters proxy ile Kestrel kullanma zamanı**</span><span class="sxs-lookup"><span data-stu-id="db788-419">**When to use Kestrel with a reverse proxy**</span></span>  
> <span data-ttu-id="db788-420"><https://docs.microsoft.com/ASPNET/Core/Fundamentals/Servers/kestrel#When-to-use-kestrel-with-a-reverse-proxy></span><span class="sxs-lookup"><span data-stu-id="db788-420"><https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy></span></span>
> - <span data-ttu-id="db788-421">**Docker ana ASP.NET Core uygulamaları**</span><span class="sxs-lookup"><span data-stu-id="db788-421">**Host ASP.NET Core apps in Docker**</span></span>  
> <span data-ttu-id="db788-422"><https://docs.microsoft.com/ASPNET/Core/Publishing/docker></span><span class="sxs-lookup"><span data-stu-id="db788-422"><https://docs.microsoft.com/aspnet/core/publishing/docker></span></span>
> - <span data-ttu-id="db788-423">**Azure uygulama ağ geçidi Tanıtımı**</span><span class="sxs-lookup"><span data-stu-id="db788-423">**Introducing Azure Application Gateway**</span></span>  
> <span data-ttu-id="db788-424"><https://docs.microsoft.com/Azure/Application-Gateway/Application-Gateway-introduction></span><span class="sxs-lookup"><span data-stu-id="db788-424"><https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="db788-425">[Önceki] (ortak-istemci-tarafı-web-technologies.md) [sonraki] (work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="db788-425">[Previous] (common-client-side-web-technologies.md) [Next] (work-with-data-in-asp-net-core-apps.md)</span></span>