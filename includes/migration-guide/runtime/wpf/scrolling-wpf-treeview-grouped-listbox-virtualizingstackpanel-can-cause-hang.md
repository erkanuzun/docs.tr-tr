### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="8ec01-101">Bir WPF TreeView veya gruplandırılmış liste kutusunda bir VirtualizingStackPanel kaydırma bir yanıt vermemesine neden olabilir</span><span class="sxs-lookup"><span data-stu-id="8ec01-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8ec01-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8ec01-102">Details</span></span>|<span data-ttu-id="8ec01-103">.NET Framework v4.5 içinde bir WPF kaydırma <xref:System.Windows.Controls.TreeView?displayProperty=name> görünüm penceresinin içinde kenar boşlukları varsa sanallaştırılmış yığında paneli askıda neden olabilir (öğeler arasında <xref:System.Windows.Controls.TreeView?displayProperty=name>, örneğin veya bir ItemsPresenter öğede).</span><span class="sxs-lookup"><span data-stu-id="8ec01-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=name> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=name>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="8ec01-104">Kenar boşlukları olsa bile ek olarak, bazı durumlarda, görünümdeki farklı boyutlarda öğeleri tutarsızlığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ec01-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>|
|<span data-ttu-id="8ec01-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="8ec01-105">Suggestion</span></span>|<span data-ttu-id="8ec01-106">Bu hata, .NET Framework 4.5.1 yükselterek önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="8ec01-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="8ec01-107">Alternatif olarak, kenar boşlukları görünüm koleksiyonlarından kaldırılabilir (gibi <xref:System.Windows.Controls.TreeView?displayProperty=name>s) sanallaştırılmış yığın içindeki tüm öğeler içeriyorsa paneller aynı boyuttadır.</span><span class="sxs-lookup"><span data-stu-id="8ec01-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=name>s) within virtualized stack panels if all contained items are the same size.</span></span>|
|<span data-ttu-id="8ec01-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8ec01-108">Scope</span></span>|<span data-ttu-id="8ec01-109">Ana</span><span class="sxs-lookup"><span data-stu-id="8ec01-109">Major</span></span>|
|<span data-ttu-id="8ec01-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8ec01-110">Version</span></span>|<span data-ttu-id="8ec01-111">4,5</span><span class="sxs-lookup"><span data-stu-id="8ec01-111">4.5</span></span>|
|<span data-ttu-id="8ec01-112">Tür</span><span class="sxs-lookup"><span data-stu-id="8ec01-112">Type</span></span>|<span data-ttu-id="8ec01-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8ec01-113">Runtime</span></span>|
|<span data-ttu-id="8ec01-114">Etkilenen API'leri</span><span class="sxs-lookup"><span data-stu-id="8ec01-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
