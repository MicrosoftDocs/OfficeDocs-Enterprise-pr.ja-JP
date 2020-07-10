---
title: Microsoft 365 Multi-Geo の計画
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Microsoft 365 Multi-Geo 複数地域、複数地域のしくみ、およびデータ ストレージに使用できる地理的な場所について説明します。
ms.openlocfilehash: 8f06c43b9a622e06959ab12fa0e055c8653ca61c
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052460"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo の計画

このガイドは、データ所在地に関する要件を満たすように、Microsoft 365 Multi-Geo テナントを企業の所在地に応じて追加の地域に展開するための準備を整える多国籍企業 (MNC) の管理者を対象としています。

複数地域構成では、Microsoft 365 テナントは中央の場所と、1 つ以上のサテライトの場所から構成されます。 これは、複数の地域にまたがる単一のテナントです。 地理的な場所を含むテナント情報は、Azure Active Directory (Azure AD) 内で管理されます。

この構成の基本的な概念についての理解を助けるために、複数地域に関するいくつかの主要な用語を示します。

-   **テナント** - Microsoft 365 における組織の表現。通常、1 つ以上のドメインが関連付けられています (例: https://contoso.sharepoint.com))。 

-   **地理的な場所** – Microsoft 365 テナントのデータをホストできる地理的な場所。

-   **サテライトの場所** – Office 365 テナントのデータをホストするように構成した追加の地理的な場所。 複数地域テナントは、複数の地域の場所 (たとえば、北米とヨーロッパ) に展開します。

-   **優先するデータの場所 (PDL)** – 個別のユーザーの Exchange および OneDrive データが保存される地域の場所。 この場所は、テナントに対して構成されている地理的位置のいずれかに管理者が設定できます。 既に OneDrive サイトを所有しているユーザーの PDL を変更しても、そのユーザーの OneDrive データは新しい地域の場所に自動的には移動されない点に注意してください。 詳細については、「[別の地域の場所に OneDrive ライブラリを移動する](move-onedrive-between-geo-locations.md)」を参照してください。 Exchange メールボックスがある場合、メールボックスは自動的に新しい優先するデータの場所に移動されます。

複数地域の有効化に必要になる主な 4 つの手順は次のとおりです。

1.  アカウント チームと協力して、_Microsoft 365 の複数地域機能_をサービス プランに追加します。

2.  サテライトの場所を選択して、その場所をテナントに追加します。

3.  ユーザーの優先するデータの場所を適切なサテライトの場所に設定します。 ユーザーに新しい OneDrive サイトまたは Exchange メールボックスがプロビジョニングされると、そのサイトがユーザーの PDL にプロビジョニングされます。

4.  ユーザーの既存の OneDrive サイトを中央の場所から、そのユーザーの優先するデータの場所に移行します (必要な場合)。 (ユーザーの PDL を設定すると、Exchange メールボックスは自動的に移行されます。)

それぞれの手順の詳細については、「[Microsoft 365 Multi-Geo の構成](multi-geo-tenant-configuration.md)」を参照してください。

> [!IMPORTANT]
> Microsoft 365 Multi-Geo は、パフォーマンスの最適化を目的とした設計ではなく、データ所在地に関する要件を満たすように設計されていることにご注意ください。 Microsoft 365 のパフォーマンスを最適化する方法については、「[Microsoft 365 のネットワーク計画とパフォーマンス チューニング](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)」を参照するか、サポート グループにお問い合わせください。

次に示す場所は、OneDrive、SharePoint サイト、Exchange のメールボックスをホストできるサテライトの場所として構成できます。 Multi-Geo の計画をするときには、Microsoft 365 テナントに追加する場所のリストを作成します。 1 つまたは 2 つのサテライトの場所から初めて、必要に応じて段階的に別の地域の場所に拡張することをお勧めします。

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Microsoft 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.

## <a name="best-practices"></a>ベスト プラクティス

いくつかの初期テストのために、Microsoft 365 にテスト用ユーザーを作成することをお勧めします。 Microsoft 365 Multi-Geo に実稼働ユーザーをオンボードする前に、このテスト用ユーザーでいくつかのテストと検証の手順を実行します。

テスト用ユーザーでのテストが完了したら、新しい地域の場所で最初に OneDrive および Exchange を使用するパイロット グループを IT 部門 (など) から選択します。 この最初のグループには、OneDrive をまだ所有していないユーザーを選択します。 この初期グループのユーザーは 5 人未満にして、バッチ ロールアウトのアプローチに従って段階的に増員していきます。

Each user should have a *preferred data location* (PDL) set so that Microsoft 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.

Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.

ユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期される場合、同期されるユーザーの優先されるデータの場所を Active Directory 属性にして、Azure Active Directory Connect を使用して設定する必要があります。 同期されるユーザーの優先されるデータの場所は、Azure AD PowerShell を使用して直接構成することはできません。 Active Directory で PDL を設定して同期する手順については、「[Azure Active Directory Connect 同期: Microsoft 365 リソースの優先されるデータの場所を構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)」を参照してください。

The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.

複数地域環境でのエンド ユーザーのエクスペリエンスの詳細については、「[複数地域環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)」を参照してください。

Microsoft 365 の複数地域テナントにおける Teams エクスペリエンスの詳細については、「[Microsoft 365 OneDrive および SharePoint Online Multi-Geo 対応テナントでの Teams のエクスペリエンス](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)」を参照してください。

Microsoft 365 Multi-Geo 複数地域の構成を開始する場合は、「[Microsoft 365 Multi-Geo の構成](multi-geo-tenant-configuration.md)」を参照してください。

構成の完了後は、ユーザーが優先するデータの場所から作業するために必要になる、[ユーザーの OneDrive ライブラリの移行](move-onedrive-between-geo-locations.md)を必ず実行してください。
