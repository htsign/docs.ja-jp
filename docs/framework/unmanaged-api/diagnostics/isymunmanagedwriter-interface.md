---
title: "ISymUnmanagedWriter インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter
helpviewer_keywords: ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1e74e625c911f35bdb7c20451b1babd02cdb7658
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter インターフェイス
シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|シンボルをシンボル ストアにコミットせずシンボル ライターを閉じます。|  
|[Close メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|シンボルをシンボル ストアにコミットした後にシンボル ライターを閉じます。|  
|[CloseMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|現在のメソッドを閉じます。 メソッドが閉じられた後は、内部にシンボルを定義できます。|  
|[CloseNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|終了では、名前空間、最も最近開いたします。|  
|[CloseScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|現在の構文のスコープを閉じます。|  
|[DefineConstant メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|定数値の名前を定義します。|  
|[DefineDocument メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|ソース ドキュメントを定義します。|  
|[DefineField メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|メソッド内ではない 1 つの変数を定義します。|  
|[DefineGlobalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|単一のグローバル変数を定義します。|  
|[DefineLocalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|現在の構文のスコープの変数を 1 つ定義します。|  
|[DefineParameter メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|現在のメソッドの 1 つのパラメーターを定義します。|  
|[DefineSequencePoints メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|現在のメソッド内のシーケンス ポイントのグループを定義します。|  
|[GetDebugInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|ポータブル実行可能 (PE) ファイル ヘッダーのデバッグ ディレクトリ エントリを書き込むときにコンパイラに必要な情報を返します。|  
|[Initialize メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|このライターが関連付けられるメタデータ エミッタ インターフェイスを設定し、デバッグ シンボルが書き込まれる出力ファイル名を設定します。|  
|[Initialize2 メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|出力ファイル名のデバッグ シンボルが記述され、プログラム データベース (PDB) ファイルの最終的な場所に設定を設定、このライターが関連付けられるメタデータ エミッタ インターフェイスを設定します。|  
|[OpenMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|シンボル情報は生成先のメソッドを開きます。|  
|[OpenNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|新しい名前空間を開きます。|  
|[OpenScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|現在のメソッドの構文の新しいスコープを開きます。|  
|[RemapToken メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|メタデータの生成と、メタデータ トークンが再マップされたシンボル ライターを通知します。|  
|[SetMethodSourceRange メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|実際の先頭とソース ファイル内のメソッドの末尾を指定します。|  
|[SetScopeRange メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|指定した構文のスコープのオフセット範囲を定義します。|  
|[SetSymAttribute メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|その名前に基づくカスタム属性を定義します。|  
|[SetUserEntryPoint メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|このモジュールのエントリ ポイントは、ユーザー定義のメソッドを指定します。|  
|[UsingNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|現在開かれている構文スコープ内で指定した名前空間の完全修飾名を使用していることを指定します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [シンボル ストア診断インターフェイスします。](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [ISymUnmanagedWriter3 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
