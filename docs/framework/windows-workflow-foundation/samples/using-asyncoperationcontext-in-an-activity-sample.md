---
title: "アクティビティ サンプルでの AsyncOperationContext の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5fce0160f98b5af5476b5e647763d79e94fb4e3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a>アクティビティ サンプルでの AsyncOperationContext の使用
このサンプルでは、<xref:System.Activities.CodeActivity> を使用してワークフロー外で非同期に作業を実行するカスタムの <xref:System.Activities.AsyncCodeActivityContext> を開発する方法を示します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 サンプルのアクティビティでは、<xref:System.IO.FileStream.BeginWrite%2A> クラスの <xref:System.IO.FileStream.EndWrite%2A> メソッドおよび <xref:System.IO.FileStream> メソッドを使用して、非同期にデータをファイルに書き込みます。 ここで示すパターンは、他の非同期メソッドでの使用に合わせて変更できます。 非同期操作の実行中、ワークフローの他のアクティビティを実行できますが、ワークフローを永続化することはできません。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で Async.sln サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`