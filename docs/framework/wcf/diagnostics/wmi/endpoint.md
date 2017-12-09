---
title: "Uç Noktası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed3c01f6943ec2958da56777ac0d6223fff66ab0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint"></a><span data-ttu-id="bdc39-102">Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="bdc39-102">Endpoint</span></span>
<span data-ttu-id="bdc39-103">Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="bdc39-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdc39-104">Syntax</span></span>  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bdc39-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bdc39-105">Methods</span></span>  
 <span data-ttu-id="bdc39-106">Uç nokta sınıfı aşağıdaki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bdc39-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="bdc39-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bdc39-107">Method</span></span>|<span data-ttu-id="bdc39-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdc39-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdc39-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="bdc39-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="bdc39-110">İşlemi performans sayacı örneği adını alır.</span><span class="sxs-lookup"><span data-stu-id="bdc39-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="bdc39-111">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bdc39-111">Properties</span></span>  
 <span data-ttu-id="bdc39-112">Uç nokta sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bdc39-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="bdc39-113">Adres</span><span class="sxs-lookup"><span data-stu-id="bdc39-113">Address</span></span>  
 <span data-ttu-id="bdc39-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bdc39-114">Data type: string</span></span>  
  
 <span data-ttu-id="bdc39-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-116">Uç nokta adresi içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="bdc39-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="bdc39-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="bdc39-117">AddressHeaders</span></span>  
 <span data-ttu-id="bdc39-118">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="bdc39-118">Data type: string array</span></span>  
  
 <span data-ttu-id="bdc39-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-120">Bu uç noktaya eklenen adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bdc39-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="bdc39-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="bdc39-121">AddressIdentity</span></span>  
 <span data-ttu-id="bdc39-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bdc39-122">Data type: string</span></span>  
  
 <span data-ttu-id="bdc39-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-124">Bitiş noktasının kimliğini.</span><span class="sxs-lookup"><span data-stu-id="bdc39-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="bdc39-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="bdc39-125">AppDomainId</span></span>  
 <span data-ttu-id="bdc39-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="bdc39-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="bdc39-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-128">Uç noktayı barındıran appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="bdc39-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="bdc39-129">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="bdc39-129">Behaviors</span></span>  
 <span data-ttu-id="bdc39-130">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="bdc39-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="bdc39-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-132">Bu bitiş noktası tarafından uygulanan davranış koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bdc39-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="bdc39-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="bdc39-133">Binding</span></span>  
 <span data-ttu-id="bdc39-134">Veri türü: bağlama</span><span class="sxs-lookup"><span data-stu-id="bdc39-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="bdc39-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-136">Bu bitiş noktası tarafından kullanılan bağlama.</span><span class="sxs-lookup"><span data-stu-id="bdc39-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="bdc39-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="bdc39-137">ContractName</span></span>  
 <span data-ttu-id="bdc39-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bdc39-138">Data type: string</span></span>  
  
 <span data-ttu-id="bdc39-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-140">Bu uç noktaya sunduğu sözleşmeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bdc39-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="bdc39-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="bdc39-141">CounterInstanceName</span></span>  
 <span data-ttu-id="bdc39-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bdc39-142">Data type: string</span></span>  
  
 <span data-ttu-id="bdc39-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-144">Uç noktanın performans sayaçları örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="bdc39-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="bdc39-145">listenUri</span><span class="sxs-lookup"><span data-stu-id="bdc39-145">ListenUri</span></span>  
 <span data-ttu-id="bdc39-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bdc39-146">Data type: string</span></span>  
  
 <span data-ttu-id="bdc39-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-148">Uç noktası URI dinler.</span><span class="sxs-lookup"><span data-stu-id="bdc39-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="bdc39-149">Ad</span><span class="sxs-lookup"><span data-stu-id="bdc39-149">Name</span></span>  
 <span data-ttu-id="bdc39-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="bdc39-150">Data type: string</span></span>  
  
 <span data-ttu-id="bdc39-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-152">Bu uç noktayı benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="bdc39-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="bdc39-153">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="bdc39-153">ProcessId</span></span>  
 <span data-ttu-id="bdc39-154">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="bdc39-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="bdc39-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-156">İşlemin işlem kimliği uç noktasını barındıran.</span><span class="sxs-lookup"><span data-stu-id="bdc39-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="bdc39-157">ref</span><span class="sxs-lookup"><span data-stu-id="bdc39-157">ref</span></span>  
 <span data-ttu-id="bdc39-158">Veri türü: Sözleşme</span><span class="sxs-lookup"><span data-stu-id="bdc39-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="bdc39-159">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bdc39-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bdc39-160">Bu bitiş noktasının sunduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="bdc39-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdc39-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdc39-161">Requirements</span></span>  
  
|<span data-ttu-id="bdc39-162">MOF</span><span class="sxs-lookup"><span data-stu-id="bdc39-162">MOF</span></span>|<span data-ttu-id="bdc39-163">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bdc39-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bdc39-164">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="bdc39-164">Namespace</span></span>|<span data-ttu-id="bdc39-165">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bdc39-165">Defined in root\ServiceModel</span></span>|