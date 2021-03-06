---
title: "トランザクション処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a6dcd11d34f0b81d6d3982ef1c6ab211d94818b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-processing"></a>トランザクション処理
オンライン書店で書籍を購入する場合、書籍と代金 (クレジット形式) を交換します。 クレジットに問題がなければ、一連の処理によって顧客は書籍を入手し、書店には代金が入金されます。 ただし、一連の取引処理の 1 つでも失敗すると取引全体が失敗し、 顧客は書籍を入手できず、書店は代金を受け取れません。  
  
 取引のバランスを取り、予測可能なものにするための技術をトランザクション処理と呼びます。 トランザクションは、トランザクション単位内のすべての処理が正常に完了しない限り、データ指向のリソースが永続的に更新されないことを保証します。 完全に成功するか、または完全に失敗する 1 つの単位に一連の関連する処理を結合することにより、エラーの回復を単純化し、アプリケーションの信頼性を高めることができます。  
  
 トランザクション処理システムは、ビジネスに必要なルーチン トランザクションを実行するためのトランザクション指向アプリケーションをホストする、コンピューター ハードウェアとソフトウェアから構成されます。 例としては、発注エントリ、航空券の予約、給与支払い、従業員レコード、製造、出荷などの管理システムが挙げられます。  
  
 ここでは、トランザクション処理に関する一般的な情報と、Microsoft .NET Framework を使用したトランザクション アプリケーションおよびリソース マネージャーの具体的な作成方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [トランザクションの基礎](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 トランザクション処理の基本的な用語と概念について紹介します。  
  
 [System.Transactions により提供される機能](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 System.Transactions の機能を使用して、独自のトランザクション アプリケーションを作成する方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Transactions>  
 コードのトランザクションへの参加を許可するクラスを提供します。 このクラスは、複数の分散参加要素、複数のフェーズ通知、および永続参加リストを使用するトランザクションをサポートします。
