---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaec1b7d179810faaba016cfa0c5eb7e6c950ab6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="e5fa4-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e5fa4-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="e5fa4-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e5fa4-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5fa4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5fa4-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e5fa4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5fa4-105">Methods</span></span>  
 <span data-ttu-id="e5fa4-106">TcpConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e5fa4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5fa4-107">Properties</span></span>  
 <span data-ttu-id="e5fa4-108">TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e5fa4-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="e5fa4-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="e5fa4-109">GroupName</span></span>  
 <span data-ttu-id="e5fa4-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e5fa4-110">Data type: string</span></span>  
  
 <span data-ttu-id="e5fa4-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e5fa4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5fa4-112">Bağlama öğesi tarafından kullanılan bağlantı havuzu grup adı.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="e5fa4-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="e5fa4-113">IdleTimeout</span></span>  
 <span data-ttu-id="e5fa4-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e5fa4-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5fa4-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e5fa4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5fa4-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="e5fa4-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="e5fa4-117">LeaseTimeout</span></span>  
 <span data-ttu-id="e5fa4-118">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="e5fa4-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5fa4-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e5fa4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5fa4-120">Zaman aşımından önce tamamlamak kira işlemi için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="e5fa4-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="e5fa4-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="e5fa4-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e5fa4-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5fa4-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e5fa4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5fa4-124">Her uç nokta için en fazla giden bağlantı.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5fa4-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5fa4-125">Requirements</span></span>  
  
|<span data-ttu-id="e5fa4-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e5fa4-126">MOF</span></span>|<span data-ttu-id="e5fa4-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e5fa4-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e5fa4-128">Namespace</span></span>|<span data-ttu-id="e5fa4-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e5fa4-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5fa4-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5fa4-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>