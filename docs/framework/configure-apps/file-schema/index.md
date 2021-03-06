---
title: ".NET Framework の構成ファイル スキーマ"
ms.custom: 
ms.date: 05/01/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7f2dec0d71c1a0822bf39ae420d4e56bdaf99e0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework の構成ファイル スキーマ

構成ファイルは、設定を変更し、アプリのポリシーを設定するために使用できる標準 XML ファイルです。 .NET Framework の構成スキーマは、アプリの動作を制御するために構成ファイルで使用できる要素で構成されます。 このセクションの目次は、スキーマ、起動時の階層、ランタイム、ネットワーク、およびその他の種類の構成設定を反映しています。

構成ファイルの種類、形式、および場所については、「[アプリの構成](~/docs/framework/configure-apps/index.md)」の記事を参照してください。 構成ファイルを直接編集する場合は、XML に関する知識が必要です。

> [!IMPORTANT]
> 構成ファイルの XML タグおよび属性では、大文字と小文字が区別されます。

## <a name="in-this-section"></a>このセクションの内容

[**\<configuration>** 要素](~/docs/framework/configure-apps/file-schema/configuration-element.md) すべての構成ファイルの最上位要素である `<configuration>` 要素について説明します。

[**\<assemblyBinding>** 要素](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) 構成レベルでのアセンブリ バインディング ポリシーを指定します。

[**\<linkedConfiguration>** 要素](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) インクルードする構成ファイルを指定します。

[スタートアップ設定スキーマ](~/docs/framework/configure-apps/file-schema/startup/index.md) 使用する共通言語ランタイムのバージョンを指定する要素について説明します。

[ランタイム設定スキーマ](~/docs/framework/configure-apps/file-schema/runtime/index.md) アセンブリのバインディングとランタイムの動作を構成する要素について説明します。

[ネットワーク設定スキーマ](~/docs/framework/configure-apps/file-schema/network/index.md) .NET Framework がインターネットに接続する方法を指定する要素について説明します。

[暗号設定スキーマ](~/docs/framework/configure-apps/file-schema/cryptography/index.md) アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。

[構成セクション スキーマ](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) カスタム設定の構成セクションを作成し、使用するための要素について説明します。

[トレースおよびデバッグ設定のスキーマ](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) トレース スイッチとリスナーを指定する要素について説明します。

[コンパイラおよび言語プロバイダー設定のスキーマ](~/docs/framework/configure-apps/file-schema/compiler/index.md) 使用できる言語プロバイダーのコンパイラの構成を指定する要素について説明します。

[アプリケーション設定のスキーマ](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Windows フォームや ASP.NET アプリケーションで、アプリケーション スコープおよびユーザー スコープの設定の格納と取得を可能にする要素について説明します。

[アプリ設定スキーマ](~/docs/framework/configure-apps/file-schema/appsettings/index.md) ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。

[Web 設定スキーマ](~/docs/framework/configure-apps/file-schema/web/index.md) IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。 *Aspnet.config* ファイルで使用します。

[Windows フォーム構成スキーマ](winforms/index.md) マルチ モニターや高 DPI サポートなどのカスタマイズを含む、Windows フォーム アプリケーションの構成セクションのすべての要素。

[WCF 構成スキーマ](~/docs/framework/configure-apps/file-schema/wcf/index.md) WCF サービスとクライアント アプリケーションを構成できるすべての要素。

[WCF ディレクティブ構文](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) .svc コンパイラによって使用されるページ固有の属性を定義する、`@ServiceHost` ディレクティブについて説明します。

[WIF 構成スキーマ](windows-identity-foundation/index.md) Windows Identity Foundation (WIF) 構成スキーマのすべての要素。

## <a name="related-sections"></a>関連項目

[リモート処理設定スキーマ](http://msdn.microsoft.com/en-us/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) リモート処理を実装するクライアント アプリケーションとサーバー アプリケーションを構成する要素について説明します。

[ASP.NET の設定スキーマ](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) ASP.NET Web アプリケーションの動作を制御する要素について説明します。

[Web サービス設定スキーマ](http://msdn.microsoft.com/en-us/f84d6d55-1add-4eb7-ae46-33df5833ea2e) ASP.NET Web サービス、およびそれらのクライアントの動作を制御する要素について説明します。

[.NET Framework アプリの構成](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) セキュリティ、アセンブリのバインディング、および .NET Framework のリモート処理を構成する方法について説明します。
