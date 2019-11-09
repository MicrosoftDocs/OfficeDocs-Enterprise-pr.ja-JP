---
title: Office 365 Multi-Geo テナントの構成
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
ms.custom: ''
localization_priority: Priority
description: Office 365 Multi-Geo の構成方法の詳細。
ms.openlocfilehash: 8e845a7d1c3a8d83189a77c5fc7a6e8d3358a425
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076391"
---
# <a name="office-365-multi-geo-tenant-configuration"></a>Office 365 Multi-Geo テナントの構成

Office 365 Multi-Geo 用にテナントを構成する前に、必ず「[Office 365 Multi-Geo のプラン](plan-for-multi-geo.md)」を読んでください。 この記事の手順を実行するには、サテライトの場所として有効にする地理的位置のリストと、それらの場所用にプロビジョニングするテスト ユーザーが必要です。

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Office 365 プランの複数地域機能をテナントに追加する

Office 365 Multi-Geo を使用するには、_Office 365 の複数地域機能_ のプランが必要です。 アカウント チームと連携して、このプランをテナントに追加してください。 アカウント チームが適切なライセンス スペシャリストと連絡を取り、テナントを構成します。

_Office 365 の複数地域機能_プランは、ユーザー レベルのサービス プランである点に注意してください。サテライトの場所でホストするユーザーごとにライセンスが必要です。サテライトの場所にユーザーを追加するたびに、さらにライセンスを追加できます。

テナントが _Office 365 の複数地域機能_プランでプロビジョニングされると、OneDrive および SharePoint 管理センターで [**地理的位置**] タブが使用できるようになります。

## <a name="add-satellite-locations-to-your-tenant"></a>サテライトの場所をテナントに追加する

データを保存する地理的位置ごとにサテライトの場所を追加する必要があります。 以下の表に、使用可能な地理的位置を示します。

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![SharePoint 管理センターの [地域の場所] ページのスクリーン ショット](media/sharepoint-multi-geo-admin-center.png)

サテライトの場所を追加する方法

1. SharePoint 管理センターを開きます。

2. **[地理的位置]** タブを開きます。

3. **[場所を追加します]** をクリックします。

4. 追加する場所を選択して、**[次へ]** をクリックします。

5. 地域の場所で使用するドメインを入力して、**[追加]** をクリックします。

6. **[閉じる]** をクリックします。

テナントのサイズに応じて、プロビジョニングには最大 72 時間かかることがあります。サテライトの場所のプロビジョニングが完了すると、電子メールの確認通知が送信されます。OneDrive 管理センターの **[地理的位置]** タブにある地図上に、新しい地域の場所が青色で表示されているときには、その地域の場所にユーザーの優先されるデータの場所を設定する作業に進めます。 

> [!IMPORTANT]
> 新しいサテライトの場所は、既定の設定でセットアップされます。そのサテライトの場所は、この設定を使用して、ローカルのコンプライアンス ニーズに適合するように構成できます。

## <a name="setting-users-preferred-data-location"></a>ユーザーの優先されるデータの場所の設定
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

必要なサテライトの場所を使用可能にすると、適切な優先されるデータの場所を使用するように、ユーザー アカウントを更新できます。ユーザーが中央の場所から移動しない場合でも、すべてのユーザーに対して優先されるデータの場所を設定するようにしてください。

> [!IMPORTANT]
> ユーザーの優先されるデータの場所がサテライトの場所または中央の場所として構成されていない場所に設定されている場合、OneDrive および SharePoint サイトとグループ メールボックスをプロビジョニングするときに、システムは既定で中央の場所に設定します。

> [!TIP]
> 組織の広範囲に Multi-Geo をロール アウトする前に、テスト ユーザーまたは少数のユーザーのグループでのテストを開始するようにしてください。

Azure Active Directory には、クラウドのみのユーザーと同期ユーザーの 2 種類のユーザー オブジェクトがあります。 ユーザーの種類に適した指示に従ってください。

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a>Azure Active Directory Connect を使用してユーザーの優先されるデータの場所を同期する 

社内のユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期される場合は、そうしたユーザーの PreferredDataLocation は AD に移入する必要があり、AAD に同期される必要があります。「[Azure Active Directory Connect 同期: Office 365 リソースの優先されるデータの場所を構成する](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)」の手順に従って、オンプレミスの Active Directory から Azure Active Directory への優先されるデータの場所の同期を構成します。

標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。

> [!IMPORTANT]
> OneDrive がプロビジョニングされていない新規ユーザーの場合、ユーザーが OneDrive for Business にログインする前に、ユーザーの PDL が Azure Active Directory に同期されてから少なくとも 24 時間待ち、変更が反映されるようにします。 (ユーザーが OneDrive for Business をプロビジョニングするために、ログインする前に優先されるデータの場所を設定しておくと、ユーザーの新しい OneDrive が正しい場所にプロビジョニングされるようになります。)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>クラウド専用ユーザーの優先されるデータの場所を設定する 

社内のユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期されていない場合、つまり、ユーザーが Office 365 または Azure Active Directory で作成されている場合は、Azure Active Directory PowerShell を使用して PDL を設定する必要があります。

ここに示す手順には、[Windows PowerShell 用 Microsoft Azure Active Directory モジュール](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)が必要です。Azure Active Directory PowerShell のインストールが済んでいる場合は、最新バージョンに更新してください。

1.  Windows PowerShell 用 Microsoft Azure Active Directory モジュールを開きます。

2.  `Connect-MsolService` を実行して、テナントの全体管理者の資格情報を入力します。

3.  [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) コマンドレットを使用して、ユーザーごとに優先されるデータの場所を設定します。次に、例を示します。

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Get-MsolUser コマンドレットを使用すると、優先されるデータの場所が適切に更新されたことを確認できます。

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![set-msoluser を示す PowerShell ウィンドウのスクリーン ショット](media/multi-geo-tenant-configuration-image3.png)

標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。

> [!IMPORTANT]
> OneDrive がプロビジョニングされていない新規ユーザーの場合、ユーザーが OneDrive にログインする前に、ユーザーの PDL が 設定されてから少なくとも 24 時間待ち、変更が反映されるようにします。 (ユーザーが OneDrive for Business をプロビジョニングするために、ログインする前に優先されるデータの場所を設定すると、新しい OneDrive が正しい場所にプロビジョニングされるようになります。)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive のプロビジョニングと PDL の効果

テナントに ユーザーの OneDrive サイトが既に作成されている場合は、そのユーザーの PDL を設定しても既存の OneDrive は自動的に移動されません。 ユーザーの OneDrive を移動するには、「[OneDrive for Business の地域移動](move-onedrive-between-geo-locations.md)」を参照し、地域間での OneDrive の移動手順に従ってください。 (ユーザーの PDL を設定すると、Exchange メールボックスは自動的に移動します。)

テナント内に OneDrive サイトを持っていないユーザーの場合、ユーザーの PDL が会社のサテライトの場所のいずれかと一致すれば、ユーザーの OneDrive は PDL 値に基づいてプロビジョニングされます。

## <a name="configuring-multi-geo-search"></a>複数地域検索の構成

複数地域テナントには、検索クエリでテナント内のあらゆる場所からの結果が得られるようになる、集約検索機能が備わります。

既定では、それらのエントリ ポイントからの検索は、それぞれの検索インデックスが関連する地域の場所に配置されていたとしても、集約された結果を返します。

- OneDrive for Business

- Delve

- SharePoint Home

- 検索センター

さらに、Multi-Geo 検索機能は、SharePoint 検索 API を使用するカスタムの検索アプリケーション用に構成することもできます。

手順と制限事項や相違点などについては、「[OneDrive for Business 複数地域の検索の構成](configure-search-for-multi-geo.md)」を参照してください。

## <a name="validating-the-office-365-multi-geo-configuration"></a>Office 365 Multi-Geo の構成を検証する

以下は、Office 365 Multi-Geo を会社で広く展開する前に、検証のプランに含めることができる基本的なユース ケースです。 これらのテストと会社に関連するその他のユース ケースを完了すると、最初のパイロット グループへのユーザーの追加を開始できます。

**OneDrive for Business**

Office 365 アプリ起動ツールから OneDrive を選択し、ユーザーの PDLに基づいて、適切な地理的位置に自動的に誘導されることを確認します。 OneDrive for Business により、その場所でプロビジョニングが開始されるはずです。 プロビジョニングが完了したら、ドキュメントのアップロードやダウンロードを試してください。

**OneDrive モバイル アプリ**

OneDrive モバイル アプリにテスト用アカウントの資格情報でログインします。OneDrive for Business のファイルを表示できることと、それらのファイルをモバイル デバイスから操作できることを確認します。

**OneDrive 同期クライアント**

ログイン時に、OneDrive 同期クライアントが OneDrive for Business 地域の場所を自動的に検出することを確認します。同期クライアントのダウンロードが必要な場合は、OneDrive ライブラリで **[同期]** をクリックしてください。

**Office アプリケーション**

Word などの Office アプリケーションからのログインで OneDrive for Business にアクセスできることを確認します。Office アプリケーションを開いて、[OneDrive – <TenantName>] を選択します。Office によって、OneDrive の場所が検出され、開くことができるファイルが表示されます。

**共有**

OneDrive ファイルを共有してみます。地域の場所に関係なく、ユーザー選択にすべての SharePoint Online ユーザーが表示されていることを確認します。
