---
title: "System.Object メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6998c2b00a2b8e83bc79ae7ba1dd01ea549cf5df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="systemobject-methods"></a>System.Object メソッド
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]次のサポート<xref:System.Object>メソッドです。  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の <xref:System.Object> メソッドをサポートしていません。  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>、`BINARY`、`VARBINARY`、`IMAGE` などのバイナリ型の `TIMESTAMP`||  
  
## <a name="differences-from-net"></a>.NET との相違  
 出力<xref:System.Object.ToString?displayProperty=nameWithType>倍を使用する SQL `CONVERT`(nvarchar (30), @x, 2) SQL にします。 このとき、SQL は常に 16 桁と指数表記を使用します (たとえば、0 に対して "0.000000000000000e+000" を使用)。 そのため、<xref:System.Object.ToString?displayProperty=nameWithType> 変換では、.NET Framework 内の <xref:System.Convert.ToString%2A?displayProperty=nameWithType>  と同じ文字列は作成されません。  
  
## <a name="see-also"></a>関連項目  
 [データ型および関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
