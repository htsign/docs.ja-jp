---
title: "ISymUnmanagedReader インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56e0012ae1412c0fb5b434d3b4c0221831296c60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="199e6-102">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="199e6-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="199e6-103">ドキュメント、メソッド、およびシンボル ストア内の変数へのアクセスを提供するシンボル リーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="199e6-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="199e6-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-104">Methods</span></span>  
  
|<span data-ttu-id="199e6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-105">Method</span></span>|<span data-ttu-id="199e6-106">説明</span><span class="sxs-lookup"><span data-stu-id="199e6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="199e6-107">GetDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="199e6-108">ドキュメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="199e6-108">Finds a document.</span></span>|  
|[<span data-ttu-id="199e6-109">GetDocuments メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="199e6-110">シンボル ストアで定義されているすべてのドキュメントの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="199e6-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="199e6-111">GetDocumentVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="199e6-112">指定されたドキュメントの指定されたバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="199e6-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="199e6-113">GetGlobalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="199e6-114">すべてのグローバル変数を返します。</span><span class="sxs-lookup"><span data-stu-id="199e6-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="199e6-115">GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="199e6-116">メソッドのトークンを指定、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="199e6-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="199e6-117">GetMethodByVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="199e6-118">メソッドのトークンと編集、コピーのバージョン番号を指定、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="199e6-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="199e6-119">GetMethodFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="199e6-120">ドキュメント内の指定位置にブレークポイントを含むメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="199e6-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="199e6-121">GetMethodsFromDocumentPosition メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="199e6-122">メソッドのドキュメントで指定された位置にブレークポイントを含むそれぞれの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="199e6-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="199e6-123">GetMethodVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="199e6-124">メソッドのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="199e6-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="199e6-125">GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="199e6-126">このシンボル ストア内のグローバル スコープで定義された名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="199e6-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="199e6-127">GetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="199e6-128">その名前に基づくカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="199e6-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="199e6-129">GetSymbolStoreFileName メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="199e6-130">シンボル ストアのディスク上のファイル名を提供します。</span><span class="sxs-lookup"><span data-stu-id="199e6-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="199e6-131">GetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="199e6-132">存在する場合は、モジュールのユーザー エントリ ポイントとして指定されたメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="199e6-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="199e6-133">GetVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="199e6-134">親と名前を指定された非ローカル変数を返します。</span><span class="sxs-lookup"><span data-stu-id="199e6-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="199e6-135">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="199e6-136">このリーダーは、モジュールのファイル名と共に、関連付けられるメタデータ インポーターのインターフェイスで、シンボル リーダーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="199e6-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="199e6-137">ReplaceSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="199e6-138">既存のシンボル ストアをデルタ シンボル ストアで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="199e6-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="199e6-139">UpdateSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="199e6-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="199e6-140">既存のシンボル ストアをデルタ シンボル ストアで更新します。</span><span class="sxs-lookup"><span data-stu-id="199e6-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="199e6-141">要件</span><span class="sxs-lookup"><span data-stu-id="199e6-141">Requirements</span></span>  
 <span data-ttu-id="199e6-142">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="199e6-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="199e6-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="199e6-143">See Also</span></span>  
 [<span data-ttu-id="199e6-144">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="199e6-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="199e6-145">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="199e6-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)