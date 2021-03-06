---
title: "CLR_DEBUGGING_PROCESS_FLAGS 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_PROCESS_FLAGS
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords: CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5040b1e1eb7ec4bd814329de156fcdfeb9c383c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS 列挙体
によって使用されている値を提供、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|このランタイムには、送信する非 catch アップ マネージ デバッガー イベントがあります。 キャッチアップおよび非 catch アップ イベントを区別する「解説」セクションを参照してください。|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|保留中であるマネージ イベントは、<xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>要求します。|  
  
## <a name="remarks"></a>コメント  
 キャッチアップ イベントには、プロセス、アプリケーション ドメイン、アセンブリ、モジュール、および現在の状態には、プロセスにアタッチした後、デバッガーになるスレッドの作成の通知が含まれます。 示される非 catch アップ イベント、`CLR_DEBUGGING_MANAGED_EVENT_PENDING`すべて他のデバッガー イベント、例外などが含まれて、マネージ デバッグ アシスタント (MDA) 通知フラグを設定します。  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`フラグ終了例外とキャンセル可能なマネージ デバッガーをアタッチ要求を区別するためにランタイムを有効にします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Metahost.idl、Metahost.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙体のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
