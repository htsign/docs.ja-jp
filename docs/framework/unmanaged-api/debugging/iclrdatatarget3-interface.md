---
title: "ICLRDataTarget3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget3
api_location: mscordbi.dll
api_type: COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16e2d2aa1a2626f4124e1b43ff85abcdd17f6990
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 インターフェイス
サブクラス[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)例外情報へのアクセスを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetExceptionRecord メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。|  
|[GetExceptionContextRecord メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|ターゲット プロセスに関連付けられているコンテキスト レコードを取得するために、CLR データ アクセス サービスによって呼び出されます。|  
|[GetExceptionThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|例外をスローしたスレッドの ID を取得するために、CLR データ アクセス サービスによって呼び出されます。|  
  
## <a name="remarks"></a>コメント  
 API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。 たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。 ターゲットは、メモリ領域の変更をサポートしない可能性があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
