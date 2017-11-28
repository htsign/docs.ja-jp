---
title: "ICorDebugThread3::GetActiveInternalFrames メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.GetActiveInternalFrames Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9b94827ac49c69c5e72c2e300a80914774cc498
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="bb6c4-102">ICorDebugThread3::GetActiveInternalFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="bb6c4-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="bb6c4-103">内部フレームの配列を返します ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)オブジェクト)、スタックにします。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6c4-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb6c4-104">Syntax</span></span>  
  
```  
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb6c4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb6c4-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="bb6c4-106">[in]内部のフレーム数`ppInternalFrames`です。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="bb6c4-107">[out]ポインター、`ULONG32`内部スタック フレームの数を格納しています。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="bb6c4-108">[入力、出力].スタック上のフレームに内部の配列のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb6c4-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="bb6c4-109">Return Value</span></span>  
 <span data-ttu-id="bb6c4-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bb6c4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb6c4-111">HRESULT</span></span>|<span data-ttu-id="bb6c4-112">説明</span><span class="sxs-lookup"><span data-stu-id="bb6c4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb6c4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb6c4-113">S_OK</span></span>|<span data-ttu-id="bb6c4-114">[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)オブジェクトが正常に作成します。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="bb6c4-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bb6c4-115">E_INVALIDARG</span></span>|<span data-ttu-id="bb6c4-116">`cInternalFrames`0 でないと`ppInternalFrames`は`null`、または`pcInternalFrames`は`null`します。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="bb6c4-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="bb6c4-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="bb6c4-118">`ppInternalFrames`内部フレームの数未満です。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bb6c4-119">例外</span><span class="sxs-lookup"><span data-stu-id="bb6c4-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb6c4-120">コメント</span><span class="sxs-lookup"><span data-stu-id="bb6c4-120">Remarks</span></span>  
 <span data-ttu-id="bb6c4-121">内部フレームは、一時的なデータを格納する、ランタイムによってスタックにプッシュするデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="bb6c4-122">呼び出すと`GetActiveInternalFrames`、設定する必要があります、`cInternalFrames`パラメーターを 0 (ゼロ)、および`ppInternalFrames`パラメーターを null にします。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="bb6c4-123">ときに`GetActiveInternalFrames`最初を返します、`pcInternalFrames`スタックでは、内部のフレーム数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="bb6c4-124">`GetActiveInternalFrames`呼び出すことが 2 番目の時間。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="bb6c4-125">適切な数を渡す必要があります (`pcInternalFrames`) で、`cInternalFrames`パラメーターに適切なサイズの配列へのポインターを指定して`ppInternalFrames`です。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="bb6c4-126">使用して、 [icordebugstackwalk::getframe](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)スタック フレームの実績を返します。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6c4-127">要件</span><span class="sxs-lookup"><span data-stu-id="bb6c4-127">Requirements</span></span>  
 <span data-ttu-id="bb6c4-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb6c4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6c4-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb6c4-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb6c4-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb6c4-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb6c4-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6c4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6c4-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb6c4-132">See Also</span></span>  
 [<span data-ttu-id="bb6c4-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6c4-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bb6c4-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="bb6c4-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)