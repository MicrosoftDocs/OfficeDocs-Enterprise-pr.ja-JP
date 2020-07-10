---
title: Microsoft 365 Multi-Geo テナントの構成
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Microsoft 365 Multi-Geo の構成方法について説明します。
ms.openlocfilehash: 928033dcbec0ad0b52f24bd0bec4dd6b9f9331bc
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052570"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 Multi-Geo テナントの構成

Microsoft 365 Multi-Geo 用にテナントを構成する前に、必ず「[Microsoft 365 Multi-Geo のプラン](plan-for-multi-geo.md)」をお読みください。 この記事の手順を実行するには、サテライトの場所として有効にする地理的位置のリストと、それらの場所用にプロビジョニングするテスト ユーザーが必要です。

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Microsoft 365 プランの複数地域機能をテナントに追加する

Microsoft 365 Multi-Geo を使用するには、_Microsoft 365 の複数地域機能_プランが必要です。 アカウント チームと連携して、このプランをテナントに追加してください。 アカウント チームが適切なライセンス スペシャリストと連絡を取り、テナントを構成します。

Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.

テナントが _Office 365 の複数地域機能_プランでプロビジョニングされると、OneDrive と SharePoint 管理センターで [**地理的位置**] タブが使用できるようになります。

## <a name="add-satellite-locations-to-your-tenant"></a>サテライトの場所をテナントに追加する

データを保存する地理的位置ごとにサテライトの場所を追加する必要があります。 以下の表に、使用可能な地理的位置を示します。

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![SharePoint 管理センターの [地域の場所] ページのスクリーン ショット](media/sharepoint-multi-geo-admin-center.png)

サテライトの場所を追加する方法

1. SharePoint 管理センターを開きます。

2. **[地理的位置]** タブを開きます。

3. **[場所を追加します]** をクリックします。

4. 追加する場所を選択して、**[次へ]** をクリックします。

5. 地域の場所で使用するドメインを入力して、**[追加]** をクリックします。

6. **[閉じる]** をクリックします。

Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location. 

> [!IMPORTANT]
> Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.

## <a name="setting-users-preferred-data-location"></a>ユーザーの優先されるデータの場所の設定
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.

> [!IMPORTANT]
> ユーザーの優先されるデータの場所がサテライトの場所または中央の場所として構成されていない場所に設定されている場合、OneDrive および SharePoint サイトとグループ メールボックスをプロビジョニングするときに、システムは既定で中央の場所に設定します。

> [!TIP]
> 組織の広範囲に Multi-Geo をロール アウトする前に、テスト ユーザーまたは少数のユーザーのグループでのテストを開始するようにしてください。

Azure Active Directory (Azure AD) には、クラウドのみのユーザーと同期ユーザーの 2 種類のユーザー オブジェクトがあります。 ユーザーの種類に適した指示に従ってください。

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Azure AD Connect を使用してユーザーの優先されるデータの場所を同期する 

会社のユーザーがオンプレミスの Active Directory システムから Azure AD に同期されている場合、それらの PreferredDataLocation を AD に入力し、Azure AD に同期する必要があります。

「[Azure Active Directory Connect 同期: Microsoft 365 リソースの優先されるデータの場所を構成する](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)」のプロセスに従って、オンプレミス Active Directory ドメイン サービス (AD DS) から Azure AD への優先されるデータの場所の同期を構成します。

標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。

> [!IMPORTANT]
> OneDrive がプロビジョニングされていない新規ユーザーの場合、ユーザーが OneDrive for Business にログインする前に、ユーザーの PDL が Azure AD に同期されてから少なくとも 24 時間待ち、変更が反映されるようにします。 (ユーザーが OneDrive for Business をプロビジョニングするために、ログインする前に優先されるデータの場所を設定しておくと、ユーザーの新しい OneDrive が正しい場所にプロビジョニングされるようになります。)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>クラウド専用ユーザーの優先されるデータの場所を設定する 

社内のユーザーがオンプレミスの Active Directory システムから Azure AD に同期されていない場合、つまり、ユーザーが Microsoft 365 または Azure AD で作成されている場合は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用して PDL を設定する必要があります。

このセクションの手順では、[Windows PowerShell モジュール用 Microsoft Azure Active Directory モジュール](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)が必要です。 このモジュールをすでにインストールしている場合は、必ず最新バージョンに更新してください。

1.  テナントの一連のグローバル管理者の資格情報を使用して、[接続してサインイン](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

2.  Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:

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

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Microsoft 365 Multi-Geo の構成を検証する

以下は、Microsoft 365 Multi-Geo を会社で広く展開する前に、検証のプランに含めることができる基本的なユース ケースです。 これらのテストと会社に関連するその他のユース ケースを完了すると、最初のパイロット グループへのユーザーの追加を開始できます。

**OneDrive for Business**

Microsoft 365 アプリ起動ツールから OneDrive を選択し、ユーザーの PDL に基づいて、ユーザーの適切な地理的位置に自動的に誘導されることを確認します。 OneDrive for Business により、その場所でプロビジョニングが開始されるはずです。 プロビジョニングが完了したら、ドキュメントのアップロードやダウンロードを試してください。

**OneDrive モバイル アプリ**

OneDrive モバイル アプリにテスト用アカウントの資格情報でログインします。 OneDrive for Business のファイルを表示できることと、それらのファイルをモバイル デバイスから操作できることを確認します。

**OneDrive 同期クライアント**

Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.

**Office アプリケーション**

Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.

**共有**

Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.
