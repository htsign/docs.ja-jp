---
title: "方法 : パネルの子を装飾する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d30e9e5ac15f48dabf983123ba007674a14626d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>方法 : パネルの子を装飾する
この例では、指定した子に装飾をプログラムでバインド<xref:System.Windows.Controls.Panel>です。  
  
## <a name="example"></a>例  
 子に装飾をバインドする、 <xref:System.Windows.Controls.Panel>、これらの手順に従います。  
  
1.  新しい宣言<xref:System.Windows.Documents.AdornerLayer>オブジェクトと呼び出し、 `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>メソッドが子によって実装されている要素の装飾層が見つかりません。  
  
2.  親要素と呼び出しの子を列挙、<xref:System.Windows.Documents.AdornerLayer.Add%2A>装飾を各子要素にバインドするメソッド。  
  
 次の例では、子に (上記) SimpleCircleAdorner、<xref:System.Windows.Controls.StackPanel>という*myStackPanel*です。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、装飾を別の要素にバインドする方法は、現在サポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)
