### <a name="selector-selectionchanged-event-and-selectedvalue-property"></a><span data-ttu-id="d9ffd-101">Seçici SelectionChanged olayı ve SelectedValue özelliği</span><span class="sxs-lookup"><span data-stu-id="d9ffd-101">Selector SelectionChanged event and SelectedValue property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d9ffd-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d9ffd-102">Details</span></span>|<span data-ttu-id="d9ffd-103">.Net ile başlayan Framework 4.7.1, bir <xref:System.Windows.Controls.Primitives.Selector> değeri her zaman güncelleştirmeleri kendi <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> oluşturma işlemi önce özellik <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> kendi seçim değiştiğinde olay.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-103">Starting with the .Net Framework 4.7.1, a <xref:System.Windows.Controls.Primitives.Selector> always updates the value of its <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property before raising the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event, when its selection changes.</span></span> <span data-ttu-id="d9ffd-104">Bu SelectedValue özelliği diğer seçim özellikleri ile tutarlı hale getirir (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> ve <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), hangi olayı tetiklenmeden önce güncelleştirilir. .NET Framework 4.7 ve önceki sürümleri, çoğu durumda olayından önce SelectedValue güncelleştirmeye oldu, ancak seçimi değişiklik değiştirerek neden oldu, sonra olayın meydana geldiği <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-104">This makes the SelectedValue property consistent with the other selection properties (<xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A> and <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>), which are updated before raising the event.In the .NET Framework 4.7 and earlier versions, the update to SelectedValue happened before the event in most cases, but it happened after the event if the selection change was caused by changing the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property.</span></span>|
|<span data-ttu-id="d9ffd-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="d9ffd-105">Suggestion</span></span>|<span data-ttu-id="d9ffd-106">.NET Framework 4.7.1 hedefleyen veya daha sonra bu dışında seçebilirsiniz uygulamalar değiştirin ve aşağıdaki ekleyerek eski davranışı kullanmak <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasının:</span><span class="sxs-lookup"><span data-stu-id="d9ffd-106">Apps that target the .NET Framework 4.7.1 or later can opt out of this change and use legacy behavior by adding the following to the <code>&lt;runtime&gt;</code> section of the application configuration file:</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><span data-ttu-id="d9ffd-107">Daha sonra yeni davranışı aşağıdaki satırı ekleyerek etkinleştirebilirsiniz veya .NET Framework 4.7.1 çalıştırıyorsanız .NET Framework 4.7 veya önceki ancak hedef uygulamaları <code>&lt;runtime&gt;</code> uygulama .configuration dosyasının:</span><span class="sxs-lookup"><span data-stu-id="d9ffd-107">Apps that target the .NET Framework 4.7 or earlier but are running on the .NET Framework 4.7.1 or later can enable the new behavior by adding the following line to the <code>&lt;runtime&gt;</code> section of the application .configuration file:</span></span><pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="d9ffd-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d9ffd-108">Scope</span></span>|<span data-ttu-id="d9ffd-109">Küçük</span><span class="sxs-lookup"><span data-stu-id="d9ffd-109">Minor</span></span>|
|<span data-ttu-id="d9ffd-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d9ffd-110">Version</span></span>|<span data-ttu-id="d9ffd-111">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d9ffd-111">4.7.1</span></span>|
|<span data-ttu-id="d9ffd-112">Tür</span><span class="sxs-lookup"><span data-stu-id="d9ffd-112">Type</span></span>|<span data-ttu-id="d9ffd-113">Yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="d9ffd-113">Retargeting</span></span>|
|<span data-ttu-id="d9ffd-114">Etkilenen API'leri</span><span class="sxs-lookup"><span data-stu-id="d9ffd-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|
