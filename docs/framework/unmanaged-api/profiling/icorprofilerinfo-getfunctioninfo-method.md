---
title: "ICorProfilerInfo::GetFunctionInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 859887d25e33b4780920ed688684c22031eac16c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>ICorProfilerInfo::GetFunctionInfo メソッド
指定した関数の親クラスとメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]親クラスとメタデータ トークンを取得する対象の関数の ID。  
  
 `pClassId`  
 [out] 関数の親クラスへのポインター。  
  
 `pModuleId`  
 [out] 関数の親クラスが定義されているモジュールへのポインター。  
  
 `pToken`  
 [out] 関数のメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>コメント  
 プロファイラー コードを呼び出すことができます[icorprofilerinfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)指定したモジュールのメタデータ インターフェイスを取得します。 `pToken` が参照している場所に返されるメタデータ トークンを使用すると、関数のメタデータにアクセスできます。  
  
 `ClassID`ジェネリック クラスの関数のできない可能性があります、関数の使用に関する詳細なコンテキスト情報取得できません。 この場合、`pClassId`は 0 になります。 プロファイラーのコードを使用する必要があります[icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)詳細なコンテキストを提供する COR_PRF_FRAME_INFO 値を使用します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
