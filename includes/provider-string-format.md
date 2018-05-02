 
<span data-ttu-id="bb847-101">Ancak, çağrılırken **String.Format** yöntemi, bunu gerekli olmadığı aramak istediğiniz belirli aşırı odaklanmak.</span><span class="sxs-lookup"><span data-stu-id="bb847-101">However, when calling the **String.Format** method, it is not necessary to focus on the particular overload that you want to call.</span></span> <span data-ttu-id="bb847-102">Bunun yerine, kültüre duyarlı veya özel biçimlendirme sağlayan bir nesne ile yöntemini çağırabilir ve bir [bileşik biçim dizesi](~/docs/standard/base-types/composite-formatting.md) bir veya daha fazla biçimi öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bb847-102">Instead, you can call the method with an object that provides culture-sensitive or custom formatting and a [composite format string](~/docs/standard/base-types/composite-formatting.md) that includes one or more format items.</span></span> <span data-ttu-id="bb847-103">Her biçim öğesi sayısal bir dizindir atamak; ilk dizin 0'da başlar.</span><span class="sxs-lookup"><span data-stu-id="bb847-103">You assign each format item a numeric index; the first index starts at 0.</span></span> <span data-ttu-id="bb847-104">Başlangıç dizesi yanı sıra, yöntem çağrısı dizin değerlere sahip kadar ek bağımsız değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb847-104">In addition to the initial string, your method call should have as many additional arguments as it has index values.</span></span> <span data-ttu-id="bb847-105">Örneğin, 0 ve 1 dizinlerini biçimi öğelerinin sahip bir dize 2 bağımsız olması gerekir; bir dizin 0 ile 5 ile 6 bağımsız olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb847-105">For example, a string whose format items have indexes of 0 and 1 should have 2 arguments; one with indexes 0 through 5 should have 6 arguments.</span></span> <span data-ttu-id="bb847-106">Dil derleyici ardından, belirli bir aşırı yüklemesini yöntemi çağrısına çözümleyecek **String.Format** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bb847-106">Your language compiler will then resolve your method call to a particular overload of the **String.Format** method.</span></span>   

<span data-ttu-id="bb847-107">Belgeleri kullanma hakkında daha ayrıntılı için **String.Format** yöntemi, bkz: [String.Format yöntemi ile çalışmaya başlama](#Starting) ve [hangi yöntemi ı çağırma?](#FTaskList).</span><span class="sxs-lookup"><span data-stu-id="bb847-107">For more detailed documentation on using the **String.Format** method, see [Getting started with the String.Format method](#Starting) and [Which method do I call?](#FTaskList).</span></span>   