---
title: "IMetaDataAssemblyImport::GetExportedTypeProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e142d0c77493ac1e9ab2bf485d8e111af4fb3ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="cf94a-102">IMetaDataAssemblyImport::GetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="cf94a-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="cf94a-103">指定したメタデータ シグネチャを持つエクスポートされた型のプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="cf94a-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf94a-104">構文</span><span class="sxs-lookup"><span data-stu-id="cf94a-104">Syntax</span></span>  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf94a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cf94a-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="cf94a-106">[in]`mdExportedType`エクスポートされた型を表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="cf94a-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="cf94a-107">[out]エクスポートされた型の名前。</span><span class="sxs-lookup"><span data-stu-id="cf94a-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cf94a-108">[in]ワイド文字単位のサイズの`szName`します。</span><span class="sxs-lookup"><span data-stu-id="cf94a-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="cf94a-109">[out]実際に返されるワイド文字の数`szName`</span><span class="sxs-lookup"><span data-stu-id="cf94a-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="cf94a-110">[out]`mdFile`、 `mdAssemblyRef`、または`mdExportedType`含まれているか、エクスポートされた型のプロパティにアクセスできるようにするメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="cf94a-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="cf94a-111">[out]ポインター、`mdTypeDef`ファイル内の型を表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="cf94a-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="cf94a-112">[out]エクスポートされた型に適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cf94a-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="cf94a-113">1 つまたは複数フラグ値を指定できます[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)値。</span><span class="sxs-lookup"><span data-stu-id="cf94a-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf94a-114">要件</span><span class="sxs-lookup"><span data-stu-id="cf94a-114">Requirements</span></span>  
 <span data-ttu-id="cf94a-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf94a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf94a-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf94a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf94a-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="cf94a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf94a-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf94a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf94a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf94a-119">See Also</span></span>  
 [<span data-ttu-id="cf94a-120">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf94a-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)