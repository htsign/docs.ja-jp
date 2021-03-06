---
title: "相互運用 ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="interop-etw-events"></a>相互運用 ETW イベント
<a name="top"></a> 相互運用イベントは、Microsoft intermediate language (MSIL) のスタブ生成とキャッシュに関する情報をキャプチャします。  
  
 このカテゴリは、次のイベントで構成されます。  
  
-   [ILStubGenerated イベント](#ilstubgenerated_event)  
  
-   [ILStubCacheHit イベント](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>ILStubGenerated イベント  
 次の表に、キーワードとレベルを示します。 (詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。  
  
|イベントを発生させるキーワード|レベル|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|情報通知 (4)|  
  
 次の表に、イベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|MSIL スタブが生成された。|  
  
 次の表に、イベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|モジュールの識別子。|  
|StubMethodID|win:UInt64|スタブのメソッド識別子。|  
|StubFlags|win:UInt64|スタブのフラグ:<br /><br /> 0x1 - 逆方向の相互運用。<br /><br /> 0x2 - COM 相互運用。<br /><br /> 0x4 - NGen.exe で生成されたスタブ。<br /><br /> 0x8 - デリゲート。<br /><br /> 0x10 - 可変個引数。<br /><br /> 0x20 - アンマネージ呼び出し先。|  
|ManagedInteropMethodToken|win:UInt32|マネージ相互運用メソッドのトークンです。|  
|ManagedInteropMethodNameSpace|win:UnicodeString|マネージ相互運用メソッドの名前空間。|  
|ManagedInteropMethodName|win:UnicodeString|マネージ相互運用メソッドの名前。|  
|ManagedInteropMethodSignature|win:UnicodeString|マネージ相互運用メソッドのシグネチャ。|  
|NativeMethodSignature|win:UnicodeString|ネイティブ メソッド シグネチャ。|  
|StubMethodSignature|win:UnicodeString|スタブ メソッド シグネチャ。|  
|StubMethodILCode|win:UnicodeString|スタブ メソッドの MSIL コード。|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
 [ページのトップへ](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>ILStubCacheHit イベント  
 次の表に、キーワードとレベルを示します。  
  
|イベントを発生させるキーワード|レベル|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|情報通知 (4)|  
  
 次の表に、イベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|MSIL のキャッシュにアクセスがあった。|  
  
 次の表に、イベント データを示します。  
  
|フィールド名|データ型|説明|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|モジュールの識別子。|  
|StubMethodID|win:UInt64|スタブのメソッド識別子。|  
|ManagedInteropMethodToken|win:UInt32|マネージ相互運用メソッドのトークンです。|  
|ManagedInteropMethodNameSpace|win:UnicodeString|マネージ相互運用メソッドの名前空間。|  
|ManagedInteropMethodName|win:UnicodeString|マネージ相互運用メソッドの名前。|  
|ManagedInteropMethodSignature|win:UnicodeString|マネージ相互運用メソッドのシグネチャ。|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
 [ページのトップへ](#top)  
  
## <a name="see-also"></a>関連項目  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)
