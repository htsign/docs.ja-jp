---
title: ICorDebugThread2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2
helpviewer_keywords: ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3a554d075adb56294e4693b234ce22735fb982
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2-interface1"></a>ICorDebugThread2 Interface1
ICorDebugThread インターフェイスを論理的に拡張として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetActiveFunctions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|スレッドのフレームでアクティブな関数に関するデータを含む COR_ACTIVE_FUNCTION インスタンスの配列を取得します。|  
|[GetConnectionID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|この接続の識別子を取得`ICorDebugThread2`です。|  
|[GetTaskID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|このタスクの識別子を取得`ICorDebugThread2`です。|  
|[GetVolatileOSThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|このオペレーティング システムのスレッド識別子を取得`ICorDebugThread2`です。|  
|[InterceptCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|スレッドで現在の例外をインターセプトするデバッガーを使用します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
