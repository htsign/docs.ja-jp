---
title: "方法 : 同時実行の競合を検査するメンバーを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c13c5d6578f27155b87744ed8730f5fae2e1e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>方法 : 同時実行の競合を検査するメンバーを指定する
次の 3 つの列挙型のいずれかを適用、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>プロパティを<xref:System.Data.Linq.Mapping.ColumnAttribute>オプティミスティック同時実行の競合を検出する更新プログラムに含まれるメンバーを指定する属性を確認します。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ (デザイン時に設定) は、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の実行時の同時実行機能と一緒に使用されます。 詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。  
  
> [!NOTE]
>  `IsVersion=true` として指定されているメンバーがない限り、元のメンバーの各値は、データベースの現在の状態と比較されます。 詳細については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>」を参照してください。  
  
 コード例については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>」を参照してください。  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>競合の検出でこのメンバーを常に使用するには  
  
1.  <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2.  <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `Always` に設定します。  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>競合の検出でこのメンバーを使用しないようにするには  
  
1.  <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2.  <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `Never` に設定します。  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>アプリケーションでメンバーの値が変更された場合にのみ、競合の検出でこのメンバーを使用するには  
  
1.  <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
2.  <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> プロパティ値を `WhenChanged` に設定します。  
  
## <a name="example"></a>例  
 次の例では、更新チェックで `HomePage` オブジェクトが検査されないように指定しています。 詳細については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>」を参照してください。  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [方法: 変更の競合の管理](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [作成方法とデータの変更の送信](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
