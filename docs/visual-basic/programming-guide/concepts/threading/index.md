---
title: "スレッド処理 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: acf9e15aa03b177533f87417278842735c1d6318
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="threading-visual-basic"></a>スレッド処理 (Visual Basic)
スレッド処理により、Visual Basic プログラムが同時処理を実行できるようになり、一度に複数の操作を行うことが可能になります。 たとえば、スレッド処理を使用してユーザーの入力を監視したり、バックグラウンド タスクを実行したり、入力の同時ストリームを処理したりできます。  
  
 スレッドには次のようなプロパティがあります。  
  
-   スレッドにより、プログラムの同時処理の実行が可能になります。  
  
-   .NET Framework の <xref:System.Threading> 名前空間により、スレッドの使用が簡単になります。  
  
-   スレッドは、アプリケーションのリソースを共有します。 詳細については、「[Using Threads and Threading](../../../../../docs/standard/threading/using-threads-and-threading.md)」(スレッドの使用とスレッド処理) を参照してください。  
  
 既定では、Visual Basic プログラムにはスレッドが 1 つあります。 ただし、補助スレッドを作成し、プライマリ スレッドと並行してコードを実行するために使用することができます。 このようなスレッドは、よく*ワーカー スレッド*と呼ばれます。  
  
 ワーカー スレッドを使用すると、プライマリ スレッドに拘束されることなく、時間がかかるタスクやタイム クリティカルなタスクを実行することができます。 たとえば、ワーカー スレッドは、前の要求が完了するのを待たずに受信する要求を処理するために、サーバー アプリケーションで多く使用されます。 ワーカー スレッドは、デスクトップ アプリケーションで "バックグラウンド" タスクを実行するためにも使用されます。これにより、ユーザー インターフェイス要素を動かすメイン スレッドは引き続きユーザー操作に応答できます。  
  
 スレッド処理はスループットと応答速度の問題を解決しますが、その一方で、デッドロックや競合状態のようなリソース共有の問題を発生させます。 複数のスレッドは、ファイル ハンドルやネットワーク接続など、さまざまなリソースを必要とするタスクに最適です。 複数のスレッドを 1 つのリソースに割り当てると、同期の問題が発生しやすくなり、他のスレッドの待機中に頻繁にブロックされるスレッドがあると、複数のスレッドを使用する目的が果たされなくなります。  
  
 一般的な方法としては、ワーカー スレッドを使用して、他のスレッドで使用されるリソースをあまり必要としない、時間がかかるタスクやタイム クリティカルなタスクを実行します。 当然ながら、プログラムの一部のリソースは、複数のスレッドによってアクセスされます。 このような場合に、<xref:System.Threading> 名前空間によってスレッドを同期するためのクラスが提供されます。 これらのクラスには、<xref:System.Threading.Mutex>、<xref:System.Threading.Monitor>、<xref:System.Threading.Interlocked>、<xref:System.Threading.AutoResetEvent>、および <xref:System.Threading.ManualResetEvent> があります。  
  
 これらのクラスの一部またはすべてを使用して、複数のスレッドのアクティビティを同期できますが、スレッド処理一部のサポートは Visual Basic 言語によりサポートされています。 たとえば、[SyncLock ステートメント](../../../../visual-basic/language-reference/statements/synclock-statement.md)は、<xref:System.Threading.Monitor> を暗黙的に使用することで同期機能を提供します。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)] 以降では、<xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> クラスおよび <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラス、[Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688)、<xref:System.Collections.Concurrent?displayProperty=nameWithType> 名前空間の新しい同時実行コレクション クラス、スレッドではなくタスクの概念をベースにした新しいプログラミング モデルにより、マルチスレッド プログラミングが大幅に簡略化されています。 詳細については、[並列プログラミング](../../../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[マルチスレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)|スレッドの作成方法および使用方法について説明します。|  
|[マルチスレッド プロシージャのパラメーターと戻り値 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|マルチ スレッド アプリケーションでパラメーターを受け渡す方法について説明します。|  
|[チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|簡単なマルチスレッド アプリケーションを作成する方法を示します。|  
|[スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)|スレッドの相互作用を制御する方法について説明します。|  
|[スレッド タイマー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)|一定の間隔で個別のスレッド上でプロシージャを実行する方法について説明します。|  
|[スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)|システムで管理されるワーカー スレッドのプールを使用する方法について説明します。|  
|[方法: スレッド プールを使用する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|スレッド プール内の複数スレッドの同期された使用方法を示します。|  
|[スレッド化](../../../../../docs/standard/threading/index.md)|.NET Framework でのスレッドの実装方法について説明します。|
