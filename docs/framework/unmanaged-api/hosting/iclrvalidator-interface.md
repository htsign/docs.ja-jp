---
title: "ICLRValidator インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator
helpviewer_keywords: ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0057be1457ad369b84f311008180dc7c4a3c323d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrvalidator-interface"></a>ICLRValidator インターフェイス
ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告のメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FormatEventInfo メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|指定された検証エラーに関する詳細なメッセージを取得します。|  
|[Validate メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|ポータブル実行可能ファイルまたは Microsoft intermediate language (MSIL) で指定されたファイルを検証します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** IValidator.idl、IValidator.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRErrorReportingManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CLRRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
