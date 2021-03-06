---
title: "CompareAssemblyIdentity 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: CompareAssemblyIdentity
helpviewer_keywords: CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d9d7b4934d4295ee799fb13d3d749e6b977e644
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity 関数
それらが等しいかどうかを決定する 2 つのアセンブリ id を比較します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwzAssemblyIdentity1`  
 [in]比較では、最初のアセンブリのテキスト形式の id。  
  
 `fUnified1`  
 [in]ユーザー指定の統一を示すブール型のフラグ`pwzAssemblyIdentity1`です。  
  
 `pwzAssemblyIdentity2`  
 [in]比較では、2 番目のアセンブリのテキスト形式の id。  
  
 `fUnified2`  
 [in]ユーザー指定の統一を示すブール型のフラグ`pwzAssemblyIdentity2`です。  
  
 `pfEquivalent`  
 [out]2 つのアセンブリが等価かどうかを示すブール型のフラグ。  
  
 `pResult`  
 [out][AssemblyComparisonResult](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)比較に関する詳細情報を含む列挙です。  
  
## <a name="return-value"></a>戻り値  
 `pfEquivalent`2 つのアセンブリが等価かどうかを示すブール値を返します。 `pResult`いずれかを返します、`AssemblyComparisonResult`の値の詳細な理由を指定する値、`pfEquivalent`です。  
  
## <a name="remarks"></a>コメント  
 `CompareAssemblyIdentity`チェックするかどうか`pwzAssemblyIdentity1`と`pwzAssemblyIdentity2`は同等です。 `pfEquivalent`設定されている`true`次の条件の下にある 1 つ以上。  
  
-   2 つのアセンブリ id は等価です。 厳密な名前付きアセンブリの場合、等価性は、アセンブリ名、バージョン、公開キー トークン、およびカルチャと同じである必要があります。 単に名前付きアセンブリは、等価であるアセンブリ名、およびカルチャに一致する必要があります。  
  
-   両方のアセンブリ id は、.NET Framework で実行されるアセンブリを参照してください。 この条件の戻り値`true`アセンブリ バージョン番号が一致しない場合でもです。  
  
-   2 つのアセンブリは、マネージ アセンブリではありませんが、`fUnified1`または`fUnified2`に設定された`true`です。  
  
 `fUnified`フラグは、厳密な名前付きアセンブリのバージョン番号までのすべてのバージョン番号同等と見なされる厳密な名前付きのアセンブリにことを示します。 たとえば場合の値`pwzAssemblyIndentity1`は"MyAssembly, バージョン 3.0.0.0]、[カルチャを = = neutral, publicKeyToken =..."の値と`fUnified1`は`true`、これは、すべてのバージョンから version 3.0.0.0 に 0.0.0.0 MyAssembly の必要があることを示します。それと同等として扱われます。 このような場合は場合、`pwzAssemblyIndentity2`と同じアセンブリを指す`pwzAssemblyIndentity1`、下位のバージョン番号があることを除いて、`pfEquivalent`に設定されている`true`です。 場合`pwzAssemblyIdentity2`上位のバージョン番号を指す`pfEquivalent`に設定されている`true`場合にのみの値`fUnified2`は`true`します。  
  
 `pResult`パラメーターには、理由、2 つのアセンブリは同等または同等ではないと見なされますに関する特定の情報が含まれています。 詳細については、次を参照してください。 [AssemblyComparisonResult 列挙型](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [AssemblyComparisonResult 列挙型](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)
