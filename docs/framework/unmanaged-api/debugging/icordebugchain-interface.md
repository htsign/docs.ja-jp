---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain
helpviewer_keywords: ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f964b5390e601b518acad44dd6fd170399ff0af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchain-interface1"></a>ICorDebugChain Interface1
物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateFrames メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|最新のフレームを使用して開始する、チェーン内のすべてのマネージ スタック フレームを含む列挙子を取得します。|  
|[GetActiveFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|アクティブなを取得 (つまり、最新) のフレーム チェーンをします。|  
|[GetCallee メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|このチェーンによって呼び出されたチェーンを取得します。|  
|[GetCaller メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|このチェーンと呼ばれる、チェーンを取得します。|  
|[GetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|実装されていません。|  
|[GetNext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|スレッドの次のフレーム チェーンを取得します。|  
|[GetPrevious メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|スレッドの前のフレーム チェーンを取得します。|  
|[GetReason メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|この呼び出しチェーンの生成の理由を取得します。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|このチェーンのアクティブな部分のレジスタ セットを取得します。|  
|[GetStackRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|このチェーンのスタック セグメントのアドレス範囲を取得します。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|この呼び出しチェーンが物理スレッドの一部を取得します。|  
|[IsManaged メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|このチェーンがマネージ コードを実行しているかどうかを示す値を取得します。|  
  
## <a name="remarks"></a>コメント  
 チェーン内のスタック フレームは、連続したスタック領域を占有し、同じスレッドとコンテキストを共有します。 チェーンには、いずれかのマネージまたはアンマネージ コードのチェーンを表すことがあります。 空`ICorDebugChain`インスタンスは、アンマネージ コードのチェーンを表します。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
