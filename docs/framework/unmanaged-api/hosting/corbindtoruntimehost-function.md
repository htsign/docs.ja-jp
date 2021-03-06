---
title: "CorBindToRuntimeHost 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeHost
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeHost
helpviewer_keywords: CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eff6fdf0294e3b1cc9830e58bc8103a64102d5b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost 関数
ホストが、指定したバージョンの共通言語ランタイム (CLR: Common Language Runtime) をプロセスに読み込むことができるようにします。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwszVersion`  
 [入力] 読み込む CLR のバージョンを示す文字列。  
  
 .NET Framework のバージョン番号はピリオドで区切られた 4 つの部分で構成されています: *major.minor.build.revision*です。 `pwszVersion` として渡される文字列は、文字 "v" で始まり、バージョン番号の最初の 3 つの部分がその後に続く必要があります (たとえば "v1.0.1529")。  
  
 いくつかのバージョンの CLR は、以前のバージョンの CLR との互換性を指定するポリシー ステートメントと共にインストールされています。 既定では、スタートアップ shim により、ポリシー ステートメントに対して `pwszVersion` が評価され、要求されたバージョンと互換性がある最新バージョンのランタイムが読み込まれます。 ホストは shim に対し、`pwszVersion` パラメーターで値 STARTUP_LOADER_SAFEMODE を渡すことにより、ポリシー評価を省略し、`startupFlags` で指定されたバージョンとまったく同じバージョンを読み込ませることができます。  
  
 `pwszVersion` が `null,` の場合、メソッドはどのバージョンの CLR も読み込みません。 代わりに、ランタイムの読み込みに失敗したことを示す CLR_E_SHIM_RUNTIMELOAD が返されます。  
  
 `pwszBuildFlavor`  
 [入力] CLR のサーバー ビルドまたはワークステーション ビルドのどちらを読み込むかを指定する文字列。 有効値は `svr` または `wks` です。 ワークステーション ビルドはシングルプロセッサ コンピューターでクライアント アプリケーションを実行するために最適化され、サーバー ビルドはガベージ コレクションでマルチ プロセッサを利用するために最適化されています。  
  
 場合`pwszBuildFlavor`に設定されている null の場合、ワークステーション ビルドが読み込まれます。 シングル プロセッサ コンピューターで実行されている、ときにワークステーション ビルド常に読み込まれると、場合でも`pwszBuildFlavor`に設定されている`svr`です。 ただし場合、`pwszBuildFlavor`に設定されている`svr`同時実行ガベージ コレクションを指定し、(の説明を参照して、`startupFlags`パラメーター)、サーバー ビルドが読み込まれます。  
  
> [!NOTE]
>  同時実行ガベージ コレクションは、Intel Itanium アーキテクチャ (以前の IA-64) を実装する 64 ビット システム上で WOW64 x86 エミュレーターを実行しているアプリケーションではサポートされません。 64 ビットの Windows システムで WOW64 の使用に関する詳細については、次を参照してください。[を実行している 32 ビット アプリケーション](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx)です。  
  
 `pwszHostConfigFile`  
 [入力] 読み込む CLR のバージョンを指定するホスト構成ファイルの名前。 ファイル名に絶対パスが含まれていない場合、ファイルは呼び出しを行った実行可能ファイルと同じディレクトリにあるものと見なされます。  
  
 `pReserved`  
 [入力] 将来の機能拡張に備えて予約されています。  
  
 `startupFlags`  
 [入力] 同時実行ガベージ コレクション、ドメインに中立なコード、および `pwszVersion` パラメーターの動作を制御するフラグのセット。 どのフラグも設定されていない場合は、既定はシングル ドメインになります。 サポートされている値の一覧は、次を参照してください。、 [STARTUP_FLAGS 列挙型](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)です。  
  
 `rclsid`  
 [in]`CLSID`を実装するいずれかのコクラスの[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)または[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)インターフェイスです。 サポートされている値は CLSID_CorRuntimeHost と CLSID_CLRRuntimeHost です。  
  
 `riid`  
 [入力] 要求するインターフェイスの `IID`。 サポートされている値は IID_ICorRuntimeHost と IID_ICLRRuntimeHost です。  
  
 `ppv`  
 [出力] 読み込まれたランタイムのバージョンへのインターフェイス ポインター。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [CorBindToCurrentRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx 関数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [推奨されなくなった CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
