---
title: "ICorDebugStepper::IsActive メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25e4b59c59ee4340c14da22143f49c645e1dcc7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive メソッド
この ICorDebugStepper が現在の手順を実行中かどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbActive`  
 [out]返します`true`ステッパは、ステップ; を現在実行中の場合、それを返します`false`です。  
  
## <a name="remarks"></a>コメント  
 デバッガーが受信するまで、ステップのアクションがアクティブなまま、 [icordebugmanagedcallback::stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)を呼び出すと、自動的に非アクティブ化するステッパです。 ステッパ可能性がありますも非アクティブ化処理の途中で呼び出すことによって[icordebugstepper::deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)状態に達すると、コールバックの前にします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
