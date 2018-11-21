---
title: OneDrive for Business 複数地域テナントの構成
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: OneDrive for Business 複数地域の構成方法について説明します。
ms.openlocfilehash: 5049904b1419935ed1d55eb73b74d2cd12edb3c0
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547169"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive for Business 複数地域テナントの構成

OneDrive for Business Multi-Geo のテナントを構成する前に、「[OneDrive for Business Multi-Geo の計画](plan-for-multi-geo.md)」を参照してください。この記事の手順を実行するには、サテライトの場所として有効にする地理的場所と、その場所にプロビジョニングするテスト ユーザーのリストが必要になります。

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Office 365 プランの複数地域機能をテナントに追加する

OneDrive for Business 複数地域を使用するには、_Office 365 の複数地域機能_プランが必要になります。アカウント チームと協力して、このプランをテナントに追加してください。アカウント チームは、適切なライセンス スペシャリストを紹介してテナントを構成します。

_Office 365 の複数地域機能_プランは、ユーザー レベルのサービス プランである点に注意してください。サテライトの場所でホストするユーザーごとにライセンスが必要です。サテライトの場所にユーザーを追加するたびに、さらにライセンスを追加できます。

テナントが _Office 365 の複数地域機能_プランでプロビジョニングされると、[OneDrive 管理センター](https://admin.onedrive.com)で **[地理的位置]** タブが使用できるようになります。

## <a name="add-satellite-locations-to-your-tenant"></a>サテライトの場所をテナントに追加する

OneDrive for Business を使用する地理的位置ごとに、サテライトの場所を追加する必要があります。次の表に、利用可能な地理的位置を示します。

<table>
<thead>
<tr class="header">
<th align="left"><strong>場所</strong></th>
<th align="left"><strong>コード</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">アジア太平洋</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">オーストラリア</td>
<td align="left">AUS</td>
</tr>
<tr class="even">
<td align="left">カナダ</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">ヨーロッパ/中東/アフリカ</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
<td align="left">フランス</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">韓国</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">北アメリカ</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">イギリス</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

サテライトの場所を追加する

1. [OneDrive 管理センター](https://admin.onedrive.com)を開きます。

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

> [!TIP]
> 組織の広範囲に Multi-Geo をロール アウトする前に、テスト ユーザーまたは少数のユーザーのグループでのテストを開始するようにしてください。

AAD には、クラウド専用ユーザーと同期ユーザーの 2 種類のユーザー オブジェクトがあります。目的のユーザーの種類に該当する指示に従ってください。

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>AD Connect を使用してユーザーの優先されるデータの場所を同期する 

社内のユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期される場合は、そうしたユーザーの PreferredDataLocation は AD に移入する必要があり、AAD に同期される必要があります。「[Azure Active Directory Connect 同期: Office 365 リソースの優先されるデータの場所を構成する](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation)」の手順に従って、オンプレミスの Active Directory から Azure Active Directory への優先されるデータの場所の同期を構成します。

標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。

> [!IMPORTANT]
> OneDrive がプロビジョニングされていない新しいユーザーの場合は、変更内容の反映のためにユーザーの PDL が Azure Active Directory に同期されてから少なくとも 24 時間待機して、OneDrive for Business にログインします (OneDrive for Business をプロビジョニングするためにユーザーがログインする前に優先されるデータの場所を設定することで、ユーザーの新しい OneDrive が正しい場所にプロビジョニングされるようになります)。

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>クラウド専用ユーザーの優先されるデータの場所を設定する 

社内のユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期されていない場合、つまり、ユーザーが Office 365 または Azure Active Directory で作成されている場合は、Azure Active Directory PowerShell を使用して PDL を設定する必要があります。

ここに示す手順には、[Windows PowerShell 用 Microsoft Azure Active Directory モジュール](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)が必要です。Azure Active Directory PowerShell のインストールが済んでいる場合は、最新バージョンに更新してください。

1.  Windows PowerShell 用 Microsoft Azure Active Directory モジュールを開きます。

2.  `Connect-MsolService` を実行して、テナントの全体管理者の資格情報を入力します。

3.  [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) コマンドレットを使用して、ユーザーごとに優先されるデータの場所を設定します。次に、例を示します。

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Get-MsolUser コマンドレットを使用すると、優先されるデータの場所が適切に更新されたことを確認できます。

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

標準のユーザー作成フローの一部として、ユーザーの優先されるデータの場所の設定を含めることをお勧めします。

> [!IMPORTANT]
> OneDrive がプロビジョニングされていない新しいユーザーの場合は、変更内容の反映のためにユーザーの PDL が設定されてから少なくとも 24 時間待機して、OneDrives にログインします (OneDrive for Business をプロビジョニングするためにユーザーがログインする前に優先されるデータの場所を設定することで、ユーザーの新しい OneDrive が正しい場所にプロビジョニングされるようになります)。

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive のプロビジョニングと PDL の効果

既にユーザーがテナントで作成された OneDrive サイトを持っている場合は、そのユーザーの PDL を設定しても既存の OneDrive が自動的に移動されることはありません。ユーザーの OneDrive を移動する場合は、「[OneDrive for Business の地域の移動](move-onedrive-between-geo-locations.md)」を参照して、地域の場所間での OneDrive の移動についての手順に従ってください。

ユーザーがテナント内に OneDrive サイトを持っていないユーザーの場合、ユーザーの PDL が会社のサテライトの場所のいずれかと一致すれば、ユーザーの OneDrive は PDL 値に応じてプロビジョニングされます。

## <a name="configuring-multi-geo-search"></a>複数地域検索の構成

複数地域テナントには、検索クエリでテナント内のあらゆる場所からの結果が得られるようになる、集約検索機能が備わります。

既定では、それらのエントリ ポイントからの検索は、それぞれの検索インデックスが関連する地域の場所に配置されていたとしても、集約された結果を返します。

- OneDrive for Business

- Delve

- SharePoint Home

- 検索センター

さらに、Multi-Geo 検索機能は、SharePoint 検索 API を使用するカスタムの検索アプリケーション用に構成することもできます。

手順と制限事項や相違点などについては、「[OneDrive for Business 複数地域の検索の構成](configure-search-for-multi-geo.md)」を参照してください。

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>OneDrive for Business 複数地域の構成の検証

次に示す、いくつかのユース ケースは、OneDrive for Business 複数地域を会社に広範囲にロール アウトする前の検証計画に含めるようにします。これらのテストと会社に関連する追加のユース ケースを完了してから、最初のパイロット グループにユーザーを追加するようにしてください。

**OneDrive for Business**

Office 365 アプリ起動ツールから OneDrive を選択し、ユーザーの PDL に基づいて、そのユーザーにとって自動的に適切な地域の場所に自動的に移動されることを確認します。その場所で OneDrive for Business のプロビジョニングが開始されます。プロビジョニングが完了したら、ドキュメントのアップロードとダウンロードを試してください。

**OneDrive モバイル アプリ**

OneDrive モバイル アプリにテスト用アカウントの資格情報でログインします。OneDrive for Business のファイルを表示できることと、それらのファイルをモバイル デバイスから操作できることを確認します。

**OneDrive 同期クライアント**

ログイン時に、OneDrive 同期クライアントが OneDrive for Business 地域の場所を自動的に検出することを確認します。同期クライアントのダウンロードが必要な場合は、OneDrive ライブラリで **[同期]** をクリックしてください。

**Office アプリケーション**

Word などの Office アプリケーションからのログインで OneDrive for Business にアクセスできることを確認します。Office アプリケーションを開いて、[OneDrive – <TenantName>] を選択します。Office によって、OneDrive の場所が検出され、開くことができるファイルが表示されます。

**共有**

OneDrive ファイルを共有してみます。地域の場所に関係なく、ユーザー選択にすべての SharePoint Online ユーザーが表示されていることを確認します。
