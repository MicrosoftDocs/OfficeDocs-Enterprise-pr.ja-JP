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
description: '概要: Azure Active Directory での分離とアクセス制御のしくみについて説明します。'
ms.openlocfilehash: 0e6423c53bd0c2823708f59830d1ba628a0c71ca
ms.sourcegitcommit: 9eb68633728cc78e9906dab222edbf9977b17e21
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38035784"
---
# <a name="isolation-and-access-control-in-azure-active-directory"></a>Azure Active Directory Domain Services での分離とアクセス制御

Azure Active Directory は、論理的なデータの分離を通じて、高度に安全な方法で複数のテナントをホストするように設計されています。 Azure Active Directory へのアクセスは、承認層でゲートされます。 Azure Active Directory は、テナントコンテナーをセキュリティ境界として使用して顧客を分離し、ユーザーのコンテンツを保護します。これにより、共同テナントによるコンテンツへのアクセスや侵害を防ぐことができます。 Azure Active Directory の承認レイヤーによって、次の3つのチェックが実行されます。

- プリンシパルは Azure Active Directory テナントへのアクセスを有効にしていますか?
- プリンシパルはこのテナント内のデータへのアクセスを有効にしますか?
- 要求されたデータアクセスの種類に対して、このテナントのプリンシパルの役割は承認されていますか。

アプリケーション、ユーザー、サーバー、またはサービスは、適切な認証とトークンまたは証明書を使用せずに Azure Active Directory にアクセスできません。 適切な資格情報を伴わない場合、要求は拒否されます。

実際には、Azure Active Directory は、各テナントを独自の保護されたコンテナー内にホストします。これには、テナントで所有および管理されているコンテナーに対するポリシーとアクセス許可が含まれます。
 
![Azure コンテナー](media/office-365-isolation-azure-container.png)

テナントコンテナーの概念は、ポータルから永続的な記憶域まで、すべての層のディレクトリサービスで深く ingrained されています。 複数の Azure Active Directory テナントのメタデータが同じ物理ディスクに格納されている場合でも、ディレクトリサービスによって定義されているコンテナー以外のコンテナー間には、テナント管理者によって定義された関係はありません。 最初に承認層を経由せずに、要求しているアプリケーションまたはサービスから Azure Active Directory ストレージへの直接接続を行うことはできません。

次の例では、Contoso と Fabrikam の両方に個別の専用のコンテナーがありますが、それらのコンテナーはサーバーやストレージなどの同じ基礎インフラストラクチャの一部を共有している場合もあります。承認とアクセス制御のレイヤー。
 
![Azure 専用コンテナー](media/office-365-isolation-azure-dedicated-containers.png)

さらに、Azure Active Directory 内から実行できるアプリケーションコンポーネントはなく、1つのテナントが別のテナントの整合性を強制的に侵害したり、別のテナントの暗号化キーをアクセスしたり、サーバーから生データを読み取ったりすることはできません。

既定では、Azure Active Directory は、他のテナント内の id によって発行されたすべての操作を許可しません。 各テナントは、クレームベースのアクセス制御によって Azure Active Directory 内で論理的に分離されています。 ディレクトリデータの読み取りおよび書き込みはテナントコンテナーを対象としており、内部アブストラクションレイヤーおよび役割ベースのアクセス制御 (RBAC) 層でゲートされます。これにより、テナントがセキュリティ境界として適用されます。 すべてのディレクトリデータアクセス要求は、これらのレイヤーによって処理され、Office 365 のすべてのアクセス要求は上記のロジックによって許可されます。

Azure Active Directory には、北アメリカ、米国政府機関、欧州連合、ドイツ、およびワールドワイドパーティションがあります。 テナントは単一のパーティション内に存在し、パーティションに複数のテナントを含めることができます。 パーティション情報はユーザーから抽象化されています。 特定のパーティション (その中のすべてのテナントを含む) は、複数のデータセンターにレプリケートされます。 テナントのパーティションは、テナントのプロパティ (たとえば、国コード) に基づいて選択されます。 各パーティション内の機密情報は、専用キーを使用して暗号化されます。 キーは、新しいパーティションが作成されるときに自動的に生成されます。

Azure Active Directory システムの機能は、各ユーザーセッションに対する一意のインスタンスです。 さらに、Azure Active Directory は、暗号化テクノロジを使用して、共有されたシステムリソースをネットワークレベルで分離し、不正な情報の転送を防止します。
