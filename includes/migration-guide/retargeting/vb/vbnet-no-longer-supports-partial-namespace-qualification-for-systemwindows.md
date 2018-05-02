### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="1e1ee-101">VB.NET kısmi ad niteliği System.Windows API'leri için artık desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="1e1ee-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1e1ee-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1e1ee-102">Details</span></span>|<span data-ttu-id="1e1ee-103">VB.NET projelerinde .NET 4.5.2 başlayarak, kısmen nitelenmiş ad alanları ile System.Windows API'leri belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e1ee-103">Beginning in .NET 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="1e1ee-104">Örneğin, başvurma <code>Windows.Forms.DialogResult</code> başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1e1ee-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="1e1ee-105">Bunun yerine, kod için tam adı başvurması gerekir (<xref:System.Windows.Forms.DialogResult>) veya belirli bir ad alanı almak ve yalnızca çok başvurun <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="1e1ee-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="1e1ee-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="1e1ee-106">Suggestion</span></span>|<span data-ttu-id="1e1ee-107">Kod başvurmak için güncelleştirilmesi gerektiğini <code>System.Windows</code> API'leri basit adları (ve ilgili ad alanı içe aktarma) veya tam olarak nitelenmiş adlar ile.</span><span class="sxs-lookup"><span data-stu-id="1e1ee-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="1e1ee-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1e1ee-108">Scope</span></span>|<span data-ttu-id="1e1ee-109">Küçük</span><span class="sxs-lookup"><span data-stu-id="1e1ee-109">Minor</span></span>|
|<span data-ttu-id="1e1ee-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1e1ee-110">Version</span></span>|<span data-ttu-id="1e1ee-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1e1ee-111">4.5.2</span></span>|
|<span data-ttu-id="1e1ee-112">Tür</span><span class="sxs-lookup"><span data-stu-id="1e1ee-112">Type</span></span>|<span data-ttu-id="1e1ee-113">Yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="1e1ee-113">Retargeting</span></span>|
