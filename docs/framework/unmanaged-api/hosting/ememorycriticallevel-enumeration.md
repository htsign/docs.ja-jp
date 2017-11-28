---
title: "EMemoryCriticalLevel 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="428c2-102">EMemoryCriticalLevel 列挙型</span><span class="sxs-lookup"><span data-stu-id="428c2-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="428c2-103">特定のメモリ割り当てが要求されましたが満足することはできません、エラーの影響を示す値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="428c2-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="428c2-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="428c2-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="428c2-105">Members</span></span>  
  
|<span data-ttu-id="428c2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="428c2-106">Member</span></span>|<span data-ttu-id="428c2-107">説明</span><span class="sxs-lookup"><span data-stu-id="428c2-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="428c2-108">割り当てが、割り当てが要求したドメイン内のマネージ コードを実行するために重要なことを示します。</span><span class="sxs-lookup"><span data-stu-id="428c2-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="428c2-109">メモリを割り当てることができない場合、CLR はドメインが引き続き使用できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="428c2-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="428c2-110">ホストは、満たすことができない、割り当て時に実行するアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="428c2-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="428c2-111">中止する CLR に指示することができますが、`AppDomain`自動的に、メソッドを呼び出すことによっても引き続き実行することを許可または[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="428c2-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="428c2-112">割り当てが、プロセスのマネージ コードの実行に不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="428c2-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="428c2-113">この値は使用の起動中に、ファイナライザーを実行するときにします。</span><span class="sxs-lookup"><span data-stu-id="428c2-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="428c2-114">メモリを割り当てることができない場合、CLR は、プロセスで動作できません。</span><span class="sxs-lookup"><span data-stu-id="428c2-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="428c2-115">割り当てに失敗した場合、CLR は無効になります。</span><span class="sxs-lookup"><span data-stu-id="428c2-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="428c2-116">CLR のすべての後続の呼び出しは、HOST_E_CLRNOTAVAILABLE で失敗します。</span><span class="sxs-lookup"><span data-stu-id="428c2-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="428c2-117">割り当てが、割り当てが要求したタスクの実行に不可欠であることを示します。</span><span class="sxs-lookup"><span data-stu-id="428c2-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="428c2-118">メモリを割り当てることができない場合、CLR がタスクを実行できることを保証することはできません。</span><span class="sxs-lookup"><span data-stu-id="428c2-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="428c2-119">CLR を発生させる障害が発生した場合、<xref:System.Threading.ThreadAbortException>物理的な運用システムのスレッドでします。</span><span class="sxs-lookup"><span data-stu-id="428c2-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="428c2-120">コメント</span><span class="sxs-lookup"><span data-stu-id="428c2-120">Remarks</span></span>  
 <span data-ttu-id="428c2-121">定義されているメモリの割り当て方法、 [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)と[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)インターフェイスは、この型のパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="428c2-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="428c2-122">エラーの重大度に応じて、ホスト決定できますは割り当て要求はすぐに失敗するか、満たすことができるまで待機するか。</span><span class="sxs-lookup"><span data-stu-id="428c2-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="428c2-123">要件</span><span class="sxs-lookup"><span data-stu-id="428c2-123">Requirements</span></span>  
 <span data-ttu-id="428c2-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="428c2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="428c2-125">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="428c2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="428c2-126">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="428c2-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="428c2-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="428c2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="428c2-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="428c2-128">See Also</span></span>  
 [<span data-ttu-id="428c2-129">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="428c2-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="428c2-130">ホスティングの列挙体</span><span class="sxs-lookup"><span data-stu-id="428c2-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)