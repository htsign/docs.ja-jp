---
title: "IHostAssemblyStore インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="27462-102">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27462-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="27462-103">アセンブリおよび共通言語ランタイム (CLR) とは無関係にモジュールの読み込みにホストできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="27462-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27462-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="27462-104">Methods</span></span>  
  
|<span data-ttu-id="27462-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="27462-105">Method</span></span>|<span data-ttu-id="27462-106">説明</span><span class="sxs-lookup"><span data-stu-id="27462-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27462-107">ProvideAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="27462-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="27462-108">によって参照されているアセンブリへの参照を取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)への呼び出しから返された[ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="27462-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="27462-109">ProvideModule メソッド</span><span class="sxs-lookup"><span data-stu-id="27462-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="27462-110">アセンブリまたはリンク (組み込まれていない) のリソース ファイル内のモジュールを解決します。</span><span class="sxs-lookup"><span data-stu-id="27462-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27462-111">コメント</span><span class="sxs-lookup"><span data-stu-id="27462-111">Remarks</span></span>  
 <span data-ttu-id="27462-112">`IHostAssemblyStore`アセンブリ id に基づく効率的にアセンブリを読み込むホスト方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="27462-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="27462-113">ホストを返すことによってアセンブリを読み込んで`IStream`バイトを直接ポイントするインスタンス。</span><span class="sxs-lookup"><span data-stu-id="27462-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="27462-114">CLR では、ホストが実装されているかどうかを判断`IHostAssemblyStore`を呼び出して`IHostAssemblyManager::GetNonHostAssemblyStores`初期化時にします。</span><span class="sxs-lookup"><span data-stu-id="27462-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="27462-115">これにより、ホスト、たとえば、.NET Framework アセンブリへのバインドをランタイムに依存するが、ユーザー アセンブリへのバインドを制御します。</span><span class="sxs-lookup"><span data-stu-id="27462-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27462-116">実装を提供する`IHostAssemblyStore`、ホストによって参照されていないすべてのアセンブリを解決するのにはその目的を指定する、`ICLRAssemblyReferenceList`から返された`IHostAssemblyManager::GetNonHostStoreAssemblies`です。</span><span class="sxs-lookup"><span data-stu-id="27462-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27462-117">によって提供されるように、.NET Framework version 2.0 が、アセンブリのネイティブ イメージの読み込みにホストの方法を提供しません、[ネイティブ イメージ ジェネレーター (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)ユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="27462-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27462-118">要件</span><span class="sxs-lookup"><span data-stu-id="27462-118">Requirements</span></span>  
 <span data-ttu-id="27462-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="27462-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27462-120">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="27462-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27462-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="27462-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27462-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27462-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27462-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="27462-123">See Also</span></span>  
 [<span data-ttu-id="27462-124">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27462-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="27462-125">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27462-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="27462-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27462-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)