---
title: "ISymUnmanagedReader::GetMethodByVersion メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodByVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba4c3ae5b1883c3113d205eab44375cbd1034c29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="b1d73-102">ISymUnmanagedReader::GetMethodByVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="b1d73-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="b1d73-103">メソッドのトークンと編集、コピーのバージョン番号を指定、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="b1d73-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="b1d73-104">バージョン番号は 1 から開始し、編集、コピー操作の結果として、メソッドが変更されるたびにインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="b1d73-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d73-105">構文</span><span class="sxs-lookup"><span data-stu-id="b1d73-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1d73-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1d73-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="b1d73-107">[in]メソッド トークンです。</span><span class="sxs-lookup"><span data-stu-id="b1d73-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="b1d73-108">[in]メソッドのバージョン。</span><span class="sxs-lookup"><span data-stu-id="b1d73-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b1d73-109">[out]返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b1d73-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1d73-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="b1d73-110">Return Value</span></span>  
 <span data-ttu-id="b1d73-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="b1d73-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d73-112">要件</span><span class="sxs-lookup"><span data-stu-id="b1d73-112">Requirements</span></span>  
 <span data-ttu-id="b1d73-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b1d73-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d73-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1d73-114">See Also</span></span>  
 [<span data-ttu-id="b1d73-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1d73-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)