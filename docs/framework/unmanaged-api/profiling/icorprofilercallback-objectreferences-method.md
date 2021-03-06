---
title: "ICorProfilerCallback::ObjectReferences メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5cdebc1984f86d3801759f8f987df8fb89d82e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences メソッド
指定したオブジェクトによって参照されているメモリ内のオブジェクトをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `objectId`  
 [in]オブジェクトを参照しているオブジェクトの ID。  
  
 `classId`  
 [in]クラスのインスタンスでは、指定したオブジェクトの ID。  
  
 `cObjectRefs`  
 [in]指定したオブジェクトによって参照されるオブジェクトの数 (つまり、内の要素の数、`objectRefIds`配列)。  
  
 `objectRefIds`  
 [in]によって参照されているオブジェクトの Id の配列`objectId`です。  
  
## <a name="remarks"></a>コメント  
 `ObjectReferences`ガベージ コレクションが完了した後に、ヒープの残りの各オブジェクトのメソッドが呼び出されます。 プロファイラーでは、このコールバックからエラーが返された場合をプロファイリング サービスは次のガベージ コレクションまでこのコールバックの呼び出しを中止します。  
  
 `ObjectReferences`コールバックを組み合わせて使用することができます、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)ランタイムの完全なオブジェクト参照グラフを作成するコールバック。 共通言語ランタイム (CLR) により、それぞれのオブジェクト参照をによって一度だけ報告、`ObjectReferences`メソッドです。  
  
 によって返されるオブジェクト Id`ObjectReferences`自体には、コールバック中に無効なため、オブジェクトを移動中にガベージ コレクションがある可能性があります。 そのため、プロファイラーは、中にオブジェクトを検査する試みる必要がありますいない、`ObjectReferences`呼び出します。 ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、ガベージ コレクションが完了し、検査を安全に行うことができます。  
  
 Null`ClassId`ことを示します`objectId`型がアンロード中が含まれています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
