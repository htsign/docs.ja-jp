---
title: "ICorDebugProcess::WriteMemory メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.WriteMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 053c6bf5f451377308f4defbeb6eff9525c4332e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory メソッド
このプロセスでメモリの領域にデータを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [in]A`CORDB_ADDRESS`のどのデータをメモリ領域のベース アドレスは、値が書き込まれます。 データ転送が発生すると、前に、システムは、ベース アドレスで始まる、指定したサイズのメモリ領域に書き込みアクセスできることを確認します。 アクセスできない場合、メソッドが失敗します。  
  
 `size`  
 [in]メモリ領域に書き込まれるバイト数。  
  
 `buffer`  
 [in]書き込むデータを格納するバッファー。  
  
 `written`  
 [out]このプロセスのメモリ領域に書き込まれたバイト数を受け取る変数へのポインター。 場合`written`が NULL の場合、このパラメーターは無視されます。  
  
## <a name="remarks"></a>コメント  
 データは、ブレークポイントの背後に自動的に書き込まれます。 .NET Framework version 2.0 でネイティブ デバッガーは、命令ストリームにブレークポイントを挿入するのにこのメソッドを使用する必要があります。 使用して[icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)代わりにします。  
  
 `WriteMemory`メソッドは、マネージ コード外にのみ使用する必要があります。 このメソッドを誤って使用するとランタイムが破損していることができます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
