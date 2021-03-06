---
title: "Web サービス ジェネリック シリアル化の技術サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0ec4f05fd68c523bcffcb9173de7e66d0dcc9a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="web-services-generics-serialization-technology-sample"></a>Web サービス ジェネリック シリアル化の技術サンプル
[サンプルのダウンロード](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 このサンプルでは、ASP.NET Web サービスで、ジェネリックのシリアル化を使用および制御する方法について説明します。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio を使用してサンプルをビルドするには  
  
1.  Visual Studio を起動し、**[ファイル]** メニューの **[新しい Web サイト]** をクリックします。  
  
2.  **[新しい Web サイト]** ダイアログ ボックスの左ペインで、目的のプログラミング言語を選択し、右ペインの **[ASP.NET Web サービス]** をクリックします。  
  
3.  **[参照]** をクリックし、\CS\GenericsService サブディレクトリに移動します。  
  
4.  Service.asmx を選択して、このファイルを Visual Studio で開きます。  
  
5.  **[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。  
  
> [!NOTE]
>  この一覧の最初の 5 つの手順は省略可能です。 サービスが最初に要求されたときに、.NET Framework ランタイムによって Web サービスが自動的に生成されます。  
  
> [!NOTE]
>  サンプルをビルドするには、次の手順が必要です。  
  
1.  [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、\CS サブディレクトリに移動します。  
  
2.  GenericsService サブディレクトリのアイコンを右クリックし、**[共有とセキュリティ]** をクリックします。  
  
3.  **[Web 共有]** タブの **[このフォルダーを共有する]** をオンにします。  
  
> [!IMPORTANT]
>  **[別名]** ウィンドウに表示される仮想ディレクトリ名をメモします。このディレクトリ名は、サンプルを実行するために必要になります。  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>インターネット インフォメーション サービス (IIS: Internet Information Services) を使用してサンプルをビルドするには  
  
1.  **[インターネット インフォメーション サービス]** 管理スナップインを開き、**[Web サイト]** を展開します。  
  
2.  **[既定の Web サイト]** を左クリックして **[新規作成]**、**[仮想ディレクトリ]** の順にクリックし、**仮想ディレクトリの作成ウィザード**を作成します。  
  
3.  **[次へ]** をクリックし、仮想ディレクトリのパブリック別名を入力し、**[次へ]** をクリックします。  
  
4.  サンプルを保存したディレクトリへのパス (通常は \CS\GenericsService サブディレクトリ) を入力し、**[次へ]** をクリックします。 **[次へ]** をクリックして、ウィザードを終了します。  
  
> [!IMPORTANT]
>  **[別名]** ペインに表示される仮想ディレクトリ名をメモします。このディレクトリ名は、サンプルを実行するために必要になります。  
  
### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  Web ブラウザー ウィンドウを開き、アドレス バーをクリックします。  
  
2.  **http://localhost/[virtual directory]/Service.asmx** と入力します。[virtual directory] は、サンプルのビルド時に作成した仮想ディレクトリを表します。  
  
## <a name="remarks"></a>コメント  
 サンプルでは、Web サービスの定義へのリンクを含む既定の ASP.NET ページが表示されます。 Web サービスのソース コードの変更に加えて、表示のカスタマイズも可能です。 詳細については、「[XML Web サービス クライアントの作成](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [シリアル化](../../../docs/standard/serialization/index.md)  
 [ASP.NET と XML Web サービス クライアントを使用して作成した XML Web サービス](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)
