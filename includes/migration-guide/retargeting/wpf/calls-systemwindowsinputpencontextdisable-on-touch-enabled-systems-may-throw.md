### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="38e31-101">Dokunmatik özellikli sistemlerde System.Windows.Input.PenContext.Disable çağrıları ArgumentException atabilir</span><span class="sxs-lookup"><span data-stu-id="38e31-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="38e31-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="38e31-102">Details</span></span>|<span data-ttu-id="38e31-103">Bazı durumlarda, iç ağa çağırır <strong>System.Windows.Intput.PenContext.Disable</strong> yöntemi Dokunmatik özellikli sistemlerde işlenmeyen bir throw <code>T:System.ArgumentException</code> yeniden giriş nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="38e31-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="38e31-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="38e31-104">Suggestion</span></span>|<span data-ttu-id="38e31-105">.NET Framework 4.7 bu sorun giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38e31-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="38e31-106">Özel durum önlemek için .NET Framework 4.7 ile başlayan .NET Framework sürümünü yükseltin.</span><span class="sxs-lookup"><span data-stu-id="38e31-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="38e31-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="38e31-107">Scope</span></span>|<span data-ttu-id="38e31-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="38e31-108">Edge</span></span>|
|<span data-ttu-id="38e31-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="38e31-109">Version</span></span>|<span data-ttu-id="38e31-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="38e31-110">4.6.1</span></span>|
|<span data-ttu-id="38e31-111">Tür</span><span class="sxs-lookup"><span data-stu-id="38e31-111">Type</span></span>|<span data-ttu-id="38e31-112">Yeniden hedefleme</span><span class="sxs-lookup"><span data-stu-id="38e31-112">Retargeting</span></span>|
