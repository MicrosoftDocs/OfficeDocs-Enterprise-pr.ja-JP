---
title: Azure Active Directory での Office 365 の分離とアクセス制御
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: '概要: Azure Active Directory での分離とアクセス制御のしくみについて説明します。'
ms.openlocfilehash: ac8ea9cf0550517f4d4d8c6eac10812700bb668b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844468"
---
# <a name="isolation-and-access-control-in-azure-active-directory"></a><span data-ttu-id="71e8a-103">Azure Active Directory Domain Services での分離とアクセス制御</span><span class="sxs-lookup"><span data-stu-id="71e8a-103">Isolation and Access Control in Azure Active Directory</span></span>

<span data-ttu-id="71e8a-104">Azure Active Directory は、論理的なデータの分離を通じて、高度に安全な方法で複数のテナントをホストするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="71e8a-104">Azure Active Directory was designed to host multiple tenants in a highly secure way through logical data isolation.</span></span> <span data-ttu-id="71e8a-105">Azure Active Directory へのアクセスは、承認層でゲートされます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-105">Access to Azure Active Directory is gated by an authorization layer.</span></span> <span data-ttu-id="71e8a-106">Azure Active Directory は、テナントコンテナーをセキュリティ境界として使用して顧客を分離し、ユーザーのコンテンツを保護します。これにより、共同テナントによるコンテンツへのアクセスや侵害を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-106">Azure Active Directory isolates customers using tenant containers as security boundaries to safeguard a customer's content so that the content cannot be accessed or compromised by co-tenants.</span></span> <span data-ttu-id="71e8a-107">Azure Active Directory の承認レイヤーによって、次の3つのチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-107">Three checks are performed by Azure Active Directory's authorization layer:</span></span>

- <span data-ttu-id="71e8a-108">プリンシパルは Azure Active Directory テナントへのアクセスを有効にしていますか?</span><span class="sxs-lookup"><span data-stu-id="71e8a-108">Is the principal enabled for access to Azure Active Directory tenant?</span></span>
- <span data-ttu-id="71e8a-109">プリンシパルはこのテナント内のデータへのアクセスを有効にしますか?</span><span class="sxs-lookup"><span data-stu-id="71e8a-109">Is the principal enabled for access to data in this tenant?</span></span>
- <span data-ttu-id="71e8a-110">要求されたデータアクセスの種類に対して、このテナントのプリンシパルの役割は承認されていますか。</span><span class="sxs-lookup"><span data-stu-id="71e8a-110">Is the principal's role in this tenant authorized for the type of data access requested?</span></span>

<span data-ttu-id="71e8a-111">アプリケーション、ユーザー、サーバー、またはサービスは、適切な認証とトークンまたは証明書を使用せずに Azure Active Directory にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="71e8a-111">No application, user, server, or service can access Azure Active Directory without the proper authentication and token or certificate.</span></span> <span data-ttu-id="71e8a-112">適切な資格情報を伴わない場合、要求は拒否されます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-112">Requests are rejected if they are not accompanied by proper credentials.</span></span>

<span data-ttu-id="71e8a-113">実際には、Azure Active Directory は、各テナントを独自の保護されたコンテナー内にホストします。これには、テナントで所有および管理されているコンテナーに対するポリシーとアクセス許可が含まれます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-113">Effectively, Azure Active Directory hosts each tenant in its own protected container, with policies and permissions to and within the container solely owned and managed by the tenant.</span></span>
 
![Azure コンテナー](media/office-365-isolation-azure-container.png)

<span data-ttu-id="71e8a-115">テナントコンテナーの概念は、ポータルから永続的な記憶域まで、すべての層のディレクトリサービスで深く ingrained されています。</span><span class="sxs-lookup"><span data-stu-id="71e8a-115">The concept of tenant containers is deeply ingrained in the directory service at all layers, from portals all the way to persistent storage.</span></span> <span data-ttu-id="71e8a-116">複数の Azure Active Directory テナントのメタデータが同じ物理ディスクに格納されている場合でも、ディレクトリサービスによって定義されているコンテナー以外のコンテナー間には、テナント管理者によって定義された関係はありません。</span><span class="sxs-lookup"><span data-stu-id="71e8a-116">Even when multiple Azure Active Directory tenant metadata is stored on the same physical disk, there is no relationship between the containers other than what is defined by the directory service, which in turn is dictated by the tenant administrator.</span></span> <span data-ttu-id="71e8a-117">最初に承認層を経由せずに、要求しているアプリケーションまたはサービスから Azure Active Directory ストレージへの直接接続を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="71e8a-117">There can be no direct connections to Azure Active Directory storage from any requesting application or service without first going through the authorization layer.</span></span>

<span data-ttu-id="71e8a-118">次の例では、Contoso と Fabrikam の両方に個別の専用のコンテナーがありますが、それらのコンテナーはサーバーやストレージなどの同じ基礎インフラストラクチャの一部を共有している場合もあります。承認とアクセス制御のレイヤー。</span><span class="sxs-lookup"><span data-stu-id="71e8a-118">In the example below, Contoso and Fabrikam both have separate, dedicated containers, and even though those containers may share some of the same underlying infrastructure, such as servers and storage, they remain separate and isolated from each other, and gated by layers of authorization and access control.</span></span>
 
![Azure 専用コンテナー](media/office-365-isolation-azure-dedicated-containers.png)

<span data-ttu-id="71e8a-120">さらに、Azure Active Directory 内から実行できるアプリケーションコンポーネントはなく、1つのテナントが別のテナントの整合性を強制的に侵害したり、別のテナントの暗号化キーをアクセスしたり、サーバーから生データを読み取ったりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="71e8a-120">In addition, there are no application components that can execute from within Azure Active Directory, and it is not possible for one tenant to forcibly breach the integrity of another tenant, access encryption keys of another tenant, or read raw data from the server.</span></span>

<span data-ttu-id="71e8a-121">既定では、Azure Active Directory は、他のテナント内の id によって発行されたすべての操作を許可しません。</span><span class="sxs-lookup"><span data-stu-id="71e8a-121">By default, Azure Active Directory disallows all operations issued by identities in other tenants.</span></span> <span data-ttu-id="71e8a-122">各テナントは、クレームベースのアクセス制御によって Azure Active Directory 内で論理的に分離されています。</span><span class="sxs-lookup"><span data-stu-id="71e8a-122">Each tenant is logically isolated within Azure Active Directory through claims-based access controls.</span></span> <span data-ttu-id="71e8a-123">ディレクトリデータの読み取りおよび書き込みはテナントコンテナーを対象としており、内部アブストラクションレイヤーおよび役割ベースのアクセス制御 (RBAC) 層でゲートされます。これにより、テナントがセキュリティ境界として適用されます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-123">Reads and writes of directory data are scoped to tenant containers, and gated by an internal abstraction layer and a role-based access control (RBAC) layer, which together enforce the tenant as the security boundary.</span></span> <span data-ttu-id="71e8a-124">すべてのディレクトリデータアクセス要求は、これらのレイヤーによって処理され、Office 365 のすべてのアクセス要求は上記のロジックによって許可されます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-124">Every directory data access request is processed by these layers and every access request in Office 365 is policed by the logic above.</span></span>

<span data-ttu-id="71e8a-125">Azure Active Directory には、北アメリカ、米国政府機関、欧州連合、ドイツ、およびワールドワイドパーティションがあります。</span><span class="sxs-lookup"><span data-stu-id="71e8a-125">Azure Active Directory has North America, U.S. Government, European Union, Germany, and World Wide partitions.</span></span> <span data-ttu-id="71e8a-126">テナントは単一のパーティション内に存在し、パーティションに複数のテナントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-126">A tenant exists in a single partition, and partitions can contain multiple tenants.</span></span> <span data-ttu-id="71e8a-127">パーティション情報はユーザーから抽象化されています。</span><span class="sxs-lookup"><span data-stu-id="71e8a-127">Partition information is abstracted away from users.</span></span> <span data-ttu-id="71e8a-128">特定のパーティション (その中のすべてのテナントを含む) は、複数のデータセンターにレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-128">A given partition (including all the tenants within it) is replicated to multiple datacenters.</span></span> <span data-ttu-id="71e8a-129">テナントのパーティションは、テナントのプロパティ (たとえば、国コード) に基づいて選択されます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-129">The partition for a tenant is chosen based on properties of the tenant (e.g., the country code).</span></span> <span data-ttu-id="71e8a-130">各パーティション内の機密情報は、専用キーを使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-130">Secrets and other sensitive information in each partition is encrypted with a dedicated key.</span></span> <span data-ttu-id="71e8a-131">キーは、新しいパーティションが作成されるときに自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="71e8a-131">The keys are generated automatically when a new partition is created.</span></span>

<span data-ttu-id="71e8a-132">Azure Active Directory システムの機能は、各ユーザーセッションに対する一意のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="71e8a-132">Azure Active Directory system functionalities are a unique instance to each user session.</span></span> <span data-ttu-id="71e8a-133">さらに、Azure Active Directory は、暗号化テクノロジを使用して、共有されたシステムリソースをネットワークレベルで分離し、不正な情報の転送を防止します。</span><span class="sxs-lookup"><span data-stu-id="71e8a-133">In addition, Azure Active Directory uses encryption technologies to provide isolation of shared system resources at the network level to prevent unauthorized and unintended transfer of information.</span></span>
