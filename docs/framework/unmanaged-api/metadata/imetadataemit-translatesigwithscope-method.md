---
title: "IMetaDataEmit::TranslateSigWithScope メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.TranslateSigWithScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5127defc97423283b52b7b5bd8c6b7a31104fbc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a>IMetaDataEmit::TranslateSigWithScope メソッド
現在のスコープにアセンブリをインポートし、マージされたスコープの新しいメタデータ シグネチャを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAssemImport`  
 [in](署名が定義されている) インポート アセンブリのインターフェイスです。  
  
 `pbHashValue`  
 [in]アセンブリのハッシュ blob です。  
  
 `cbHashValue`  
 [in]内のバイト数`pbHashValue`です。  
  
 `import`  
 [in]インポートのメタデータ スコープのインターフェイスです。  
  
 `pbSigBlob`  
 [in]インポートする署名します。  
  
 `cbSigBlob`  
 [in]サイズをバイト単位での`pbSigBlob`します。  
  
 `pAssemEmit`  
 [in]エクスポートのアセンブリのインターフェイスです。  
  
 `emit`  
 [in]エクスポートのメタデータ スコープのインターフェイスです。  
  
 `pvTranslatedSig`  
 [out]翻訳されたシグネチャ blob を保持するバッファー。  
  
 `cbTranslatedSigMax`  
 [in](バイト単位) の容量の`pvTranslatedSig`します。  
  
 `pcbTranslatedSig`  
 [out]翻訳済みの署名の実際のバイト数。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
