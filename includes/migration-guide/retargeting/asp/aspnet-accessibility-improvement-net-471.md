### <a name="aspnet-accessibility-improvement-in-net-471"></a><span data-ttu-id="d863e-101">.NET 4.7.1 ASP.NET erişilebilirlik geliştirme</span><span class="sxs-lookup"><span data-stu-id="d863e-101">ASP.NET Accessibility Improvement in .NET 4.7.1</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d863e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d863e-102">Details</span></span>|<span data-ttu-id="d863e-103">ASP.NET, ASP.NET Web denetimleri daha iyi destek ASP.NET müşterilere Erişilebilirlik teknolojisi Visual Studio ile nasıl çalıştığıyla artırma.</span><span class="sxs-lookup"><span data-stu-id="d863e-103">ASP.NET is improving how ASP.NET Web Controls work with accessibility technology in Visual Studio to better support ASP.NET customers.</span></span>  <span data-ttu-id="d863e-104">Bunlar aşağıdaki değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d863e-104">These include the following changes:</span></span><ul><li><span data-ttu-id="d863e-105">Ayrıntılar Görünümü Sihirbazı'nda alan Ekle iletişim kutusu gibi denetimlerinde eksik UI erişilebilirlik desenlerini uygulama şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="d863e-105">Changes to implement missing UI accessibility patterns in controls, like the Add Field dialog in the Details View wizard.</span></span></li><li><span data-ttu-id="d863e-106">Yüksek karşıtlık modunda gibi veri çağrı cihazı alanları Düzenleyicisi görüntü iyileştirmeye yönelik değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="d863e-106">Changes to improve the display in High Contrast mode, like the Data Pager Fields Editor.</span></span></li><li><span data-ttu-id="d863e-107">Klavye gezinti iyileştirmeye yönelik değişiklikler karşılaştığında yapılandırma nesnesi bağlam penceresi veya veri kaynağı yapılandırma penceresi gibi denetimleri için.</span><span class="sxs-lookup"><span data-stu-id="d863e-107">Changes to improve the keyboard navigation experiences for controls, like the Configure Object Context Window or the Configure Data Source Window.</span></span></li></ul>|
|<span data-ttu-id="d863e-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="d863e-108">Suggestion</span></span>|<span data-ttu-id="d863e-109">**İçinde veya dışında bu değişiklikleri kabul etmek nasıl** sırada bu değişikliklerden yararlanmak Visual Studio tasarımcısı için .NET Framework 4.7.1 çalıştırmanız gerekir ya da daha sonra.</span><span class="sxs-lookup"><span data-stu-id="d863e-109">**How to opt in or out of these changes** In order for the Visual Studio Designer to benefit from these changes, it must run on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="d863e-110">Web uygulama aşağıdaki yollardan biriyle bu değişiklikleri yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="d863e-110">The web application can benefit from these changes in either of the following ways:</span></span><ul><li><span data-ttu-id="d863e-111">Visual Studio 2017 15.3 yükleyin veya daha sonra aşağıdaki AppContext anahtarıyla yeni erişilebilirlik özellikleri varsayılan olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="d863e-111">Install Visual Studio 2017 15.3 or later, which supports the new accessibility features with the following AppContext Switch by default.</span></span></li><li><span data-ttu-id="d863e-112">Eski erişilebilirlik davranışları dışında ekleyerek opt **Switch.UseLegacyAccessibility** AppContext anahtara `<runtime>` bölümünde devenv.exe.config dosyasında ve ayarlamak `false`, aşağıdaki örnek olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="d863e-112">Opt out of the legacy accessibility behaviors by adding the **Switch.UseLegacyAccessibility** AppContext Switch to the `<runtime>` section in the devenv.exe.config file and setting it to `false`, as the following example shows.</span></span></li></ul><pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;<br />&lt;configuration&gt;<br />&lt;runtime&gt;<br />...</code></pre>|
|<span data-ttu-id="d863e-113">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d863e-113">Scope</span></span>|<span data-ttu-id="d863e-114">Küçük</span><span class="sxs-lookup"><span data-stu-id="d863e-114">Minor</span></span>|
|<span data-ttu-id="d863e-115">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d863e-115">Version</span></span>|<span data-ttu-id="d863e-116">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d863e-116">4.7.1</span></span>|
|<span data-ttu-id="d863e-117">Tür</span><span class="sxs-lookup"><span data-stu-id="d863e-117">Type</span></span>|<span data-ttu-id="d863e-118">Yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="d863e-118">Retargeting</span></span>|