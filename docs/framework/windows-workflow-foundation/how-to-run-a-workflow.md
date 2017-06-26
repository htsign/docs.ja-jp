---
title: "ワークフローを実行する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
caps.latest.revision: 33
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 33
---
# ワークフローを実行する方法
このトピックでは、Windows Workflow Foundation チュートリアル入門の続きと、ワークフロー ホストを作成して、前の「[ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)」で定義したワークフローを実行する方法について説明します。  
  
> [!NOTE]
>  チュートリアル入門の各トピックは、前のトピックに応じて異なります。 このトピックを完了する前に、「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」および「[ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)」を完了する必要があります。  
  
> [!NOTE]
>  チュートリアルの完成版をダウンロードするには、「[Windows Workflow Foundation \(WF45\) \- Getting Started Tutorial \(Windows Workflow Foundation \(WF45\) \- チュートリアル入門\)](http://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。  
  
### ワークフロー ホスト プロジェクトを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] を使用して、前の「[アクティビティを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-an-activity.md)」トピックからソリューションを開きます。  
  
2.  **ソリューション エクスプローラー**で **WF45GettingStartedTutorial** ソリューションを右クリックし、**\[追加\]** をポイントして、**\[新しいプロジェクト\]** をクリックします。  
  
    > [!TIP]
    >  **ソリューション エクスプローラー** ウィンドウが表示されない場合は、**\[表示\]** メニューの **\[ソリューション エクスプローラー\]** をクリックします。  
  
3.  **\[インストール済み\]** ノードで、**\[Visual C\#\]**、**\[ワークフロー\]** \(または **\[Visual Basic\]**、**\[ワークフロー\]**\) の順に選択します。  
  
    > [!NOTE]
    >  Visual Studio で第一言語として設定されているプログラミング言語に応じて、**\[インストール済み\]** ノードの **\[他の言語\]** ノードの下に、**\[Visual C\#\]** ノードまたは **\[Visual Basic\]** ノードが表示されます。  
  
     .NET Framework バージョンのドロップダウン リストで **\[.NET Framework 4.5\]** が選択されていることを確認します。**\[ワークフロー\]** の一覧から **\[ワークフロー コンソール アプリケーション\]** を選択します。**\[名前\]** ボックスに「`NumberGuessWorkflowHost`」と入力し、**\[OK\]** をクリックします。 これで、基本的なワークフロー ホスティングをサポートする、基本ワークフロー アプリケーションが作成されます。 この基本的なホスティング コードを変更し、ワークフロー アプリケーションの実行に使用します。  
  
4.  **ソリューション エクスプローラー**で新しく追加した **NumberGuessWorkflowHost** プロジェクトを右クリックし、**\[参照の追加\]** をクリックします。**\[参照の追加\]** の一覧から **\[ソリューション\]** を選択し、**NumberGuessWorkflowActivities** の横にあるチェック ボックスをオンにして、**\[OK\]** をクリックします。  
  
5.  **ソリューション エクスプローラー**で **Workflow1.xaml** を右クリックし、**\[削除\]** をクリックします。**\[OK\]** をクリックして確定します。  
  
### ワークフロー ホスティング コードを変更するには  
  
1.  **ソリューション エクスプローラー**で、**Program.cs** または **Module1.vb** をダブルクリックしてコードを表示します。  
  
    > [!TIP]
    >  **ソリューション エクスプローラー** ウィンドウが表示されない場合は、**\[表示\]** メニューの **\[ソリューション エクスプローラー\]** をクリックします。  
  
     このプロジェクトは**ワークフロー コンソール アプリケーション** テンプレートを使用して作成されたため、**Program.cs** または **Module1.vb** には、次のようなワークフローの基本的なホスティング コードが含まれます。  
  
    ```vb  
    ' Create and cache the workflow definition  
    Activity workflow1 = new Workflow1()  
    WorkflowInvoker.Invoke(workflow1)  
    ```  
  
    ```csharp  
    // Create and cache the workflow definition  
    Activity workflow1 = new Workflow1();  
    WorkflowInvoker.Invoke(workflow1);  
    ```  
  
     この生成されたホスト コードでは <xref:System.Activities.WorkflowInvoker> を使用します。<xref:System.Activities.WorkflowInvoker> は、メソッド呼び出しのようにワークフローを呼び出す簡単な方法を提供し、永続化を使用しないワークフローのみに使用できます。<xref:System.Activities.WorkflowApplication> は、ライフ サイクル イベントの通知、実行制御、ブックマークの再開、および永続化を含むワークフローを実行するための豊富なモデルを提供します。 次の例ではブックマークを使用し、ワークフローのホスティングには <xref:System.Activities.WorkflowApplication> を使用します。**Program.cs** または **Module1.vb** の先頭にある既存の **using** ステートメントまたは **Imports** ステートメントの下に、次の `using` ステートメントまたは **Imports** ステートメントを追加します。  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     <xref:System.Activities.WorkflowInvoker> を使用するコード行を次の <xref:System.Activities.WorkflowApplication> の基本的なホスティング コードに置き換えます。 このサンプル ホスティング コードでは、ワークフローをホストして呼び出すための基本的な手順を示します。ただし、このトピックのワークフローを正しく実行するための機能はまだありません。 次の手順では、アプリケーションが完了するまでにこの基本的なコードを変更して機能を追加します。  
  
    > [!NOTE]
    >  前の「[ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)」の手順で完了したワークフローに応じて、これらの例の `Workflow1` を `FlowchartNumberGuessWorkflow`、`SequentialNumberGuessWorkflow`、または `StateMachineNumberGuessWorkflow` に置き換えます。`Workflow1` を置き換えないと、ワークフローをビルドまたは実行しようとするときにビルド エラーが発生します。  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     このコードでは <xref:System.Activities.WorkflowApplication> を作成し、3 つのワークフローのライフサイクル イベントに定期受信し、<xref:System.Activities.WorkflowApplication.Run%2A> を呼び出してワークフローを開始し、そのワークフローが完了するまで待機します。 ワークフローが完了すると <xref:System.Threading.AutoResetEvent> が設定され、ホスト アプリケーションが完了します。  
  
### ワークフローの入力引数を設定するには  
  
1.  **Program.cs** または **Module1.vb** の先頭にある既存の `using` ステートメントまたは `Imports` ステートメントの下に、次のステートメントを追加します。  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  新しい <xref:System.Activities.WorkflowApplication> を作成するコード行を、作成時にワークフローにパラメーターの辞書を作成して渡す次のコードに置き換えます。  
  
    > [!NOTE]
    >  前の「[ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)」の手順で完了したワークフローに応じて、これらの例の `Workflow1` を `FlowchartNumberGuessWorkflow`、`SequentialNumberGuessWorkflow`、または `StateMachineNumberGuessWorkflow` に置き換えます。`Workflow1` を置き換えないと、ワークフローをビルドまたは実行しようとするときにビルド エラーが発生します。  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     この辞書には、`MaxNumber` というキーを持つ 1 つの要素が含まれます。 入力辞書のキーは、ワークフローのルート アクティビティの入力引数に対応します。`MaxNumber` は、ランダムに生成される数値の上限を決定するためにワークフローによって使用されます。  
  
### ワークフローの出力引数を取得するには  
  
1.  <xref:System.Activities.WorkflowApplication.Completed%2A> ハンドラーを変更して、ワークフローが使用する順番の数を取得して表示します。  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### ブックマークを再開するには  
  
1.  `Main` メソッドの上部にある既存の <xref:System.Threading.AutoResetEvent> 宣言の直後に、次のコードを追加します。  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  <xref:System.Activities.WorkflowApplication.Idle%2A> にある既存の 3 つのワークフロー ライフサイクル ハンドラーの直後に、次の `Main` ハンドラーを追加します。  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     このハンドラーは、次の推定値を待機してワークフローがアイドル状態になるたびに呼び出され、`idleAction`<xref:System.Threading.AutoResetEvent> が設定されます。 次の手順のコードでは、`idleEvent` と `syncEvent` を使用して、ワークフローが次の推定値を待機しているのか、完了しているのかを判断します。  
  
    > [!NOTE]
    >  この例では、ホスト アプリケーションは <xref:System.Activities.WorkflowApplication.Completed%2A> および <xref:System.Activities.WorkflowApplication.Idle%2A> ハンドラーの自動リセット イベントを使用して、ホスト アプリケーションとワークフローの進行状況を同期させます。 ブックマークを再開する前にワークフローがアイドル状態になるのをブロックして待機する必要はありませんが、この例では同期イベントが必要であるため、ホストはワークフローが完了しているのか、さらにユーザーの入力を待っているのかを <xref:System.Activities.Bookmark> を使用して把握します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [ブックマーク](../../../docs/framework/windows-workflow-foundation//bookmarks.md)。  
  
3.  `WaitOne` への呼び出しを削除して、ユーザーからの入力を収集して <xref:System.Activities.Bookmark> を再開するためのコードに置き換えます。  
  
     次のコード行を削除します。  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     これを次の例に置き換えます。  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a> アプリケーションをビルドして実行するには  
  
1.  **ソリューション エクスプローラー**で **NumberGuessWorkflowHost** を右クリックして **\[スタートアップ プロジェクトに設定\]** を選択します。  
  
2.  Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。 できるだけ早い順番の数を推測します。  
  
     他のスタイルのワークフローのいずれかでアプリケーションを試すには、目的のワークフローのスタイルに応じて、`Workflow1` を作成するコード内の <xref:System.Activities.WorkflowApplication> を、`FlowchartNumberGuessWorkflow`、`SequentialNumberGuessWorkflow`、または `StateMachineNumberGuessWorkflow` に置き換えます。  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     ワークフロー アプリケーションに永続化を追加する方法については、次のトピック「[長時間にわたって実行されるワークフローを作成して実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-and-run-a-long-running-workflow.md)」を参照してください。  
  
## 使用例  
 次の例では、`Main` メソッドの完全なコードの一覧を示します。  
  
> [!NOTE]
>  前の「[ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)」の手順で完了したワークフローに応じて、これらの例の `Workflow1` を `FlowchartNumberGuessWorkflow`、`SequentialNumberGuessWorkflow`、または `StateMachineNumberGuessWorkflow` に置き換えます。`Workflow1` を置き換えないと、ワークフローをビルドまたは実行しようとするときにビルド エラーが発生します。  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## 参照  
 <xref:System.Activities.WorkflowApplication>   
 <xref:System.Activities.Bookmark>   
 [Windows Workflow Foundation プログラミングの新機能](../../../docs/framework/windows-workflow-foundation//programming.md)   
 [チュートリアル入門](../../../docs/framework/windows-workflow-foundation//getting-started-tutorial.md)   
 [ワークフローを作成する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-a-workflow.md)   
 [長時間にわたって実行されるワークフローを作成して実行する方法](../../../docs/framework/windows-workflow-foundation//how-to-create-and-run-a-long-running-workflow.md)   
 [ワークフロー内での入力の待機](../../../docs/framework/windows-workflow-foundation//waiting-for-input-in-a-workflow.md)   
 [ワークフローのホスティング](../../../docs/framework/windows-workflow-foundation//hosting-workflows.md)