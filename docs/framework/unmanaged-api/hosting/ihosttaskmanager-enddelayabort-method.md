---
title: "IHostTaskManager::EndDelayAbort メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EndDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45148c506e2f6073dc175abe4397fad2172b355e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="caeef-102">IHostTaskManager::EndDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="caeef-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="caeef-103">マネージ コードをホストが終了するに通知を現在のタスクを中断できない、期間、事前に呼び出した[ihosttaskmanager::begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="caeef-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caeef-104">構文</span><span class="sxs-lookup"><span data-stu-id="caeef-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="caeef-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="caeef-105">Return Value</span></span>  
  
|<span data-ttu-id="caeef-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="caeef-106">HRESULT</span></span>|<span data-ttu-id="caeef-107">説明</span><span class="sxs-lookup"><span data-stu-id="caeef-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="caeef-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="caeef-108">S_OK</span></span>|<span data-ttu-id="caeef-109">`EndDelayAbort`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="caeef-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="caeef-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="caeef-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="caeef-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="caeef-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="caeef-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="caeef-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="caeef-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="caeef-113">The call timed out.</span></span>|  
|<span data-ttu-id="caeef-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="caeef-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="caeef-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="caeef-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="caeef-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="caeef-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="caeef-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="caeef-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="caeef-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="caeef-118">E_FAIL</span></span>|<span data-ttu-id="caeef-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="caeef-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="caeef-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="caeef-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="caeef-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="caeef-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="caeef-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="caeef-122">E_UNEXPECTED</span></span>|<span data-ttu-id="caeef-123">`EndDelayAbort`対応する呼び出しなしで呼び出されました`BeginDelayAbort`です。</span><span class="sxs-lookup"><span data-stu-id="caeef-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caeef-124">コメント</span><span class="sxs-lookup"><span data-stu-id="caeef-124">Remarks</span></span>  
 <span data-ttu-id="caeef-125">CLR は、対応する呼び出し`BeginDelayAbort`呼び出す前に現在のタスクで`EndDelayAbort`です。</span><span class="sxs-lookup"><span data-stu-id="caeef-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="caeef-126">このような対応する呼び出しがない場合のホストの実装[IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)から E_UNEXPECTED が返されます`EndDelayAbort`は操作を行わないとします。</span><span class="sxs-lookup"><span data-stu-id="caeef-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caeef-127">要件</span><span class="sxs-lookup"><span data-stu-id="caeef-127">Requirements</span></span>  
 <span data-ttu-id="caeef-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="caeef-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caeef-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="caeef-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="caeef-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="caeef-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caeef-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caeef-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caeef-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="caeef-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="caeef-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caeef-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="caeef-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caeef-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="caeef-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caeef-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="caeef-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caeef-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)