### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="710b0-101">ArgumentOutOfRangeException DataGridCellsPanel.BringIndexIntoView oluşturur</span><span class="sxs-lookup"><span data-stu-id="710b0-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="710b0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="710b0-102">Details</span></span>|<span data-ttu-id="710b0-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> zaman uyumsuz olarak sütun sanallaştırma etkinleştirildi, ancak sütun genişliklerini henüz karar verilmemiştir olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="710b0-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="710b0-104">Zaman uyumsuz iş gerçekleşmeden önce sütunları kaldırdıysanız bir <xref:System.ArgumentOutOfRangeException?displayProperty=name> oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="710b0-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=name> can occur.</span></span>|
|<span data-ttu-id="710b0-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="710b0-105">Suggestion</span></span>|<span data-ttu-id="710b0-106">Aşağıdakilerden herhangi biri:</span><span class="sxs-lookup"><span data-stu-id="710b0-106">Any one of the following:</span></span><ol><li><span data-ttu-id="710b0-107">.NET 4.7'ye yükseltin.</span><span class="sxs-lookup"><span data-stu-id="710b0-107">Upgrade to .NET 4.7.</span></span></li><li><span data-ttu-id="710b0-108">Son bakım düzeltme eki için .NET 4.6.2 yükleyin.</span><span class="sxs-lookup"><span data-stu-id="710b0-108">Install the latest servicing patch for .NET 4.6.2.</span></span></li><li><span data-ttu-id="710b0-109">Zaman uyumsuz yanıtı kadar sütunları kaldırma kaçının <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="710b0-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>|
|<span data-ttu-id="710b0-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="710b0-110">Scope</span></span>|<span data-ttu-id="710b0-111">Kenar</span><span class="sxs-lookup"><span data-stu-id="710b0-111">Edge</span></span>|
|<span data-ttu-id="710b0-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="710b0-112">Version</span></span>|<span data-ttu-id="710b0-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="710b0-113">4.6.2</span></span>|
|<span data-ttu-id="710b0-114">Tür</span><span class="sxs-lookup"><span data-stu-id="710b0-114">Type</span></span>|<span data-ttu-id="710b0-115">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="710b0-115">Runtime</span></span>|
|<span data-ttu-id="710b0-116">Etkilenen API'leri</span><span class="sxs-lookup"><span data-stu-id="710b0-116">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
