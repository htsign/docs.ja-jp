---
title: "構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86a6e12f-73b5-450e-8725-f4ca5fe0702c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3eee9f955ca75d799b9e5384e47df527934a595f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="configuration"></a>構成
ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 構成によって生成されるすべての例外を示します。  
  
## <a name="exception-list"></a>例外の一覧  
  
|リソース コード|リソースの文字列|  
|-------------------|---------------------|  
|ConfigBindingCannotBeConfigured|サービス エンドポイントのバインディングを構成できません。|  
|ConfigElementKeyNull|指定された構成要素キーを NULL にすることはできません。|  
|ConfigExtensionTypeNotRegisteredInCollection|指定された拡張の型は、指定された拡張のコレクションに登録されていません。|  
|ConfigIndexOutOfRange|指定された属性の値が範囲外です。|  
|ConfigInvalidBindingConfigurationName|指定された構成に指定された名前のバインディングが含まれていません。|  
|ConfigInvalidBindingName|指定された構成に指定された名前のバインディングが含まれていません。 これはこのバインディングに対して無効な値です。|  
|ConfigInvalidCommonEndpointBehaviorType|指定された動作拡張は指定された型を実装していないため、共通エンドポイント動作に追加できません。|  
|ConfigInvalidCommonServiceBehaviorType|指定された動作拡張は指定された型を実装していないため、共通サービス動作に追加できません。|  
|ConfigInvalidEndpointBehaviorType|基になる動作型が IServiceBehavior インターフェイスを実装していないため、指定された動作拡張を指定されたエンドポイント動作に追加できません。|  
|ConfigInvalidExtensionType|指定された型をコレクションで使用するには、指定された拡張から派生する必要があります。|  
|ConfigInvalidServiceBehaviorType|基になる動作型が IServiceBehavior インターフェイスを実装していないため、動作拡張を指定された名前のサービス動作に追加できません。|  
|ConfigMessageEncodingAlreadyInBinding|指定されたメッセージ エンコーディング要素を追加できません。 指定されたバインディングには、別のメッセージ エンコーディング要素が既に存在しています。 バインディングのメッセージ エンコーディング要素は各バインディングに 1 つしか指定できません。|  
|ConfigNoExtensionCollectionAssociatedWithType|指定された型の拡張に関連付けられた拡張のコレクションが見つかりません。|  
|ConfigSectionNotFound|指定された構成セクションを作成できません。 Machine.config ファイルに情報がありません。 構成セクションが適切に登録されていること、およびセクション名を正しく入力していることを確認してください。 Windows Communication Foundation セクションの場合は、ServiceModelReg.exe -i を実行してこのエラーを修正してください。|  
|ConfigTransportAlreadyInBinding|指定されたトランスポート要素を追加できません。 指定されたバインディングには、別のトランスポート要素が既に存在しています。 バインディングのメッセージ エンコーディング要素は各バインディングに 1 つしか指定できません。|
