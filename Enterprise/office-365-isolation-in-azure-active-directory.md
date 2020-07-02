---
title: Azure Active Directory での Microsoft 365 の分離とアクセス制御
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: fe242acb5d14f5c90d6e646140b50f5f96c7a331
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998717"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a><span data-ttu-id="3bfce-103">Azure Active Directory での Microsoft 365 の分離とアクセス制御</span><span class="sxs-lookup"><span data-stu-id="3bfce-103">Microsoft 365 Isolation and Access Control in Azure Active Directory</span></span>

<span data-ttu-id="3bfce-104">Azure Active Directory (Azure AD) は、論理的なデータの分離を通じて、高度にセキュリティで保護された方法で複数のテナントをホストするように設計されています。</span><span class="sxs-lookup"><span data-stu-id="3bfce-104">Azure Active Directory (Azure AD) was designed to host multiple tenants in a highly secure way through logical data isolation.</span></span> <span data-ttu-id="3bfce-105">Azure AD へのアクセスは、承認層でゲートされます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-105">Access to Azure AD is gated by an authorization layer.</span></span> <span data-ttu-id="3bfce-106">Azure AD は、テナントコンテナーをセキュリティ境界として使用することにより、ユーザーのコンテンツを保護し、共同テナントがコンテンツにアクセスしたり侵害したりできないようにします。</span><span class="sxs-lookup"><span data-stu-id="3bfce-106">Azure AD isolates customers using tenant containers as security boundaries to safeguard a customer's content so that the content cannot be accessed or compromised by co-tenants.</span></span> <span data-ttu-id="3bfce-107">Azure AD の承認レイヤーによって、次の3つのチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-107">Three checks are performed by Azure AD's authorization layer:</span></span>

- <span data-ttu-id="3bfce-108">プリンシパルは Azure AD テナントへのアクセスを有効にしていますか?</span><span class="sxs-lookup"><span data-stu-id="3bfce-108">Is the principal enabled for access to Azure AD tenant?</span></span>
- <span data-ttu-id="3bfce-109">プリンシパルはこのテナント内のデータへのアクセスを有効にしますか?</span><span class="sxs-lookup"><span data-stu-id="3bfce-109">Is the principal enabled for access to data in this tenant?</span></span>
- <span data-ttu-id="3bfce-110">要求されたデータアクセスの種類に対して、このテナントのプリンシパルの役割は承認されていますか。</span><span class="sxs-lookup"><span data-stu-id="3bfce-110">Is the principal's role in this tenant authorized for the type of data access requested?</span></span>

<span data-ttu-id="3bfce-111">アプリケーション、ユーザー、サーバー、またはサービスは、適切な認証とトークンまたは証明書を使用せずに、Azure AD にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="3bfce-111">No application, user, server, or service can access Azure AD without the proper authentication and token or certificate.</span></span> <span data-ttu-id="3bfce-112">適切な資格情報を伴わない場合、要求は拒否されます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-112">Requests are rejected if they are not accompanied by proper credentials.</span></span>

<span data-ttu-id="3bfce-113">実際には、Azure AD は独自の保護されたコンテナー内の各テナントをホストし、テナントが所有し管理するだけのコンテナーに対するポリシーとアクセス許可を持っています。</span><span class="sxs-lookup"><span data-stu-id="3bfce-113">Effectively, Azure AD hosts each tenant in its own protected container, with policies and permissions to and within the container solely owned and managed by the tenant.</span></span>
 
![Azure コンテナー](media/office-365-isolation-azure-container.png)

<span data-ttu-id="3bfce-115">テナントコンテナーの概念は、ポータルから永続的な記憶域まで、すべての層のディレクトリサービスで深く ingrained されています。</span><span class="sxs-lookup"><span data-stu-id="3bfce-115">The concept of tenant containers is deeply ingrained in the directory service at all layers, from portals all the way to persistent storage.</span></span> <span data-ttu-id="3bfce-116">複数の Azure AD テナントメタデータが同じ物理ディスクに格納されている場合でも、ディレクトリサービスによって定義されたコンテナー以外のコンテナー間には、テナント管理者によって定義された関係はありません。</span><span class="sxs-lookup"><span data-stu-id="3bfce-116">Even when multiple Azure AD tenant metadata is stored on the same physical disk, there is no relationship between the containers other than what is defined by the directory service, which in turn is dictated by the tenant administrator.</span></span> <span data-ttu-id="3bfce-117">最初に承認層を経由せずに、要求しているアプリケーションまたはサービスから Azure AD ストレージへの直接接続を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="3bfce-117">There can be no direct connections to Azure AD storage from any requesting application or service without first going through the authorization layer.</span></span>

<span data-ttu-id="3bfce-118">次の例では、Contoso と Fabrikam の両方に独立した専用のコンテナーがありますが、それらのコンテナーはサーバーやストレージなどの同じ基礎インフラストラクチャの一部を共有していますが、それらは互いに分離され、相互に分離されており、承認とアクセス制御のレイヤーで区切られています。</span><span class="sxs-lookup"><span data-stu-id="3bfce-118">In the example below, Contoso and Fabrikam both have separate, dedicated containers, and even though those containers may share some of the same underlying infrastructure, such as servers and storage, they remain separate and isolated from each other, and gated by layers of authorization and access control.</span></span>
 
![Azure 専用コンテナー](media/office-365-isolation-azure-dedicated-containers.png)

<span data-ttu-id="3bfce-120">さらに、Azure AD 内から実行できるアプリケーションコンポーネントはなく、1つのテナントが別のテナントの整合性を強制的に侵害したり、別のテナントの暗号化キーをアクセスしたり、サーバーから生データを読み取ったりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3bfce-120">In addition, there are no application components that can execute from within Azure AD, and it is not possible for one tenant to forcibly breach the integrity of another tenant, access encryption keys of another tenant, or read raw data from the server.</span></span>

<span data-ttu-id="3bfce-121">既定では、Azure AD は他のテナント内の id によって発行されたすべての操作を許可しません。</span><span class="sxs-lookup"><span data-stu-id="3bfce-121">By default, Azure AD disallows all operations issued by identities in other tenants.</span></span> <span data-ttu-id="3bfce-122">各テナントは、クレームベースのアクセス制御によって Azure AD 内で論理的に分離されています。</span><span class="sxs-lookup"><span data-stu-id="3bfce-122">Each tenant is logically isolated within Azure AD through claims-based access controls.</span></span> <span data-ttu-id="3bfce-123">ディレクトリデータの読み取りおよび書き込みはテナントコンテナーを対象としており、内部アブストラクションレイヤーおよび役割ベースのアクセス制御 (RBAC) 層でゲートされます。これにより、テナントがセキュリティ境界として適用されます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-123">Reads and writes of directory data are scoped to tenant containers, and gated by an internal abstraction layer and a role-based access control (RBAC) layer, which together enforce the tenant as the security boundary.</span></span> <span data-ttu-id="3bfce-124">すべてのディレクトリデータアクセス要求は、これらのレイヤーによって処理され、Microsoft 365 のすべてのアクセス要求は上記のロジックによって許可されます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-124">Every directory data access request is processed by these layers and every access request in Microsoft 365 is policed by the logic above.</span></span>

<span data-ttu-id="3bfce-125">Azure AD には、北アメリカ、米国政府機関、欧州連合、ドイツ、およびワールドワイドパーティションがあります。</span><span class="sxs-lookup"><span data-stu-id="3bfce-125">Azure AD has North America, U.S. Government, European Union, Germany, and World Wide partitions.</span></span> <span data-ttu-id="3bfce-126">テナントは単一のパーティション内に存在し、パーティションに複数のテナントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-126">A tenant exists in a single partition, and partitions can contain multiple tenants.</span></span> <span data-ttu-id="3bfce-127">パーティション情報はユーザーから抽象化されています。</span><span class="sxs-lookup"><span data-stu-id="3bfce-127">Partition information is abstracted away from users.</span></span> <span data-ttu-id="3bfce-128">特定のパーティション (その中のすべてのテナントを含む) は、複数のデータセンターにレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-128">A given partition (including all the tenants within it) is replicated to multiple datacenters.</span></span> <span data-ttu-id="3bfce-129">テナントのパーティションは、テナントのプロパティ (たとえば、国コード) に基づいて選択されます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-129">The partition for a tenant is chosen based on properties of the tenant (e.g., the country code).</span></span> <span data-ttu-id="3bfce-130">各パーティション内の機密情報は、専用キーを使用して暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-130">Secrets and other sensitive information in each partition is encrypted with a dedicated key.</span></span> <span data-ttu-id="3bfce-131">キーは、新しいパーティションが作成されるときに自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="3bfce-131">The keys are generated automatically when a new partition is created.</span></span>

<span data-ttu-id="3bfce-132">Azure AD システムの機能は、各ユーザーセッションに対する一意のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3bfce-132">Azure AD system functionalities are a unique instance to each user session.</span></span> <span data-ttu-id="3bfce-133">さらに、Azure AD では、暗号化テクノロジを使用して、共有されたシステムリソースをネットワークレベルで分離し、不正な情報の転送を防止します。</span><span class="sxs-lookup"><span data-stu-id="3bfce-133">In addition, Azure AD uses encryption technologies to provide isolation of shared system resources at the network level to prevent unauthorized and unintended transfer of information.</span></span>
