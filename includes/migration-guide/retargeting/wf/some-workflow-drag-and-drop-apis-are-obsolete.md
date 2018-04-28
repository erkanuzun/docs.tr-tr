### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="8a71f-101">Bazı iş akışı sürükle ve bırak API artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="8a71f-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8a71f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8a71f-102">Details</span></span>|<span data-ttu-id="8a71f-103">Bu iş akışı sürükle ve bırak API artık kullanılmıyor ve uygulama karşı 4.5 yeniden oluşturulursa derleyici uyarıları neden olur.</span><span class="sxs-lookup"><span data-stu-id="8a71f-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>|
|<span data-ttu-id="8a71f-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="8a71f-104">Suggestion</span></span>|<span data-ttu-id="8a71f-105">Yeni <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> birden fazla nesne işlemleriyle destekler API'lerini bunun yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a71f-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="8a71f-106">Alternatif olarak, derleme uyarıları gizlenebilir veya eski bir derleyici kullanılarak önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="8a71f-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="8a71f-107">API'ler hala desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8a71f-107">The APIs are still supported.</span></span>|
|<span data-ttu-id="8a71f-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="8a71f-108">Scope</span></span>|<span data-ttu-id="8a71f-109">Küçük</span><span class="sxs-lookup"><span data-stu-id="8a71f-109">Minor</span></span>|
|<span data-ttu-id="8a71f-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="8a71f-110">Version</span></span>|<span data-ttu-id="8a71f-111">4,5</span><span class="sxs-lookup"><span data-stu-id="8a71f-111">4.5</span></span>|
|<span data-ttu-id="8a71f-112">Tür</span><span class="sxs-lookup"><span data-stu-id="8a71f-112">Type</span></span>|<span data-ttu-id="8a71f-113">Yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="8a71f-113">Retargeting</span></span>|
|<span data-ttu-id="8a71f-114">Etkilenen API'leri</span><span class="sxs-lookup"><span data-stu-id="8a71f-114">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|
