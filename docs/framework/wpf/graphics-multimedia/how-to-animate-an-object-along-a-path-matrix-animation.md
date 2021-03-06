---
title: "方法 : パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)"
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
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70426e3341f78a22c8367daefc07d071c7add3ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>方法 : パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)
この例を使用する方法を示しています、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>によって定義されているパスに沿ってオブジェクトをアニメーション化するクラス、<xref:System.Windows.Media.PathGeometry>です。  
  
## <a name="example"></a>例  
 次の例では、以下の処理を実行し、パスに沿ってオブジェクトをアニメーション化します。  
  
-   適用される、<xref:System.Windows.Media.MatrixTransform>を移動するためにオブジェクトにします。  
  
-   使用してパスを定義、<xref:System.Windows.Media.PathGeometry>です。  
  
-   作成、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>アニメーション化を使用して、<xref:System.Windows.Media.Matrix>のプロパティ、<xref:System.Windows.Media.MatrixTransform>です。 <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>受け取り、<xref:System.Windows.Media.PathGeometry>しを使用して生成<xref:System.Windows.Media.Matrix>値。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 サンプル全体については、次を参照してください。[パス アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=160028)です。 幾何学模様のパスの詳細については、次を参照してください。、[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [パス アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
