---
title: ビジネスの複数の地域のテナント構成の OneDrive
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: OneDrive に複数の地域のビジネスを構成する方法について説明します。
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>ビジネスの複数の地域のテナント構成の OneDrive

OneDrive は、テナントの複数の地域のビジネスを構成する前に、 [OneDrive 複数の地域のビジネスの計画](plan-for-multi-geo.md)を読んだことを確認します。この資料の手順を実行するを有効にする場所、およびそれらの場所を提供するテスト ユーザーの一覧を必要があります。

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Office 365 のプランで、テナントに複数地域の機能を追加します。

複数の地域のビジネスの OneDrive を使用して、 _Office 365 の機能を複数の地域_の計画が必要です。この計画をテナントに追加するのには、アカウント ・ チームと協力します。アカウント ・ チームは適切なライセンスのスペシャ リストに接続して、構成、テナントを取得します。

_Office 365 の機能を複数の地域_計画がユーザー レベルのサービス プランであることに注意します。Setellite の場所でホストするユーザーごとにライセンスが必要です。サテライト オフィスのユーザーを追加すると、時間の経過と共にライセンスを追加することができます。

テナントは、 _Office 365 の機能を複数の地域_の計画と準備されていると[OneDrive の管理センター](https://admin.onedrive.com)で利用可能な**地域の場所**] タブになります。

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>許可されるデータの場所 (ADL) をテナントに設定します。

必要がありますを設定する許可されるデータの場所、SharePoint の各地理的な場所のビジネスの OneDrive を使用します。利用可能な地域の場所は、次の表のとおりです。

<table>
<thead>
<tr class="header">
<th align="left"><strong>場所</strong></th>
<th align="left"><strong>コード</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">北アメリカ</td>
<td align="left">名</td>
</tr>
<tr class="even">
<td align="left">ヨーロッパ東中央//アフリカ</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">アジア太平洋</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">オーストラリア</td>
<td align="left">オーストラリア</td>
</tr>
<tr class="odd">
<td align="left">日本</td>
<td align="left">日本語版</td>
</tr>
<tr class="even">
<td align="left">カナダ</td>
<td align="left">できます。</td>
</tr>
<tr class="odd">
<td align="left">英国</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">韓国</td>
<td align="left">KOR</td>
</tr>
</tbody>
</table>

サテライト地域の場所を追加するには

1. [OneDrive 管理センター](https://admin.onedrive.com)を開きます。

2. **Geo [場所**] タブに移動します。

3. [**場所の追加**] をクリックします。

4. を追加する場所を選択し、[**次へ**] をクリックします。

5. Geo の場所で使用するドメインを入力し、[**追加**] をクリックします。

6. [ **閉じる**] をクリックします。

サテライトの場所の準備が完了すると、確認の電子メールが表示されます。OneDrive 管理センターの**地域の場所**] タブ上のマップの青い地域の別の場所が表示されたら、ユーザーの希望するデータの場所をその地理的な場所に設定することができます。 

> [!IMPORTANT]
> 新しいサテライト地域地域は、既定の設定で設定されます。これは、オプションを選択する、コンプライアンスのニーズに応じてその地域の場所を構成することができます。

## <a name="setting-users-preferred-data-location"></a>ユーザーの希望するデータの場所を設定します。
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

必要なデータの場所を有効にすると、適切なデータの場所を使用するユーザー アカウントを更新できます。場合でも、既定のデータの場所でそのユーザーが常にすべてのユーザーに対して推奨されるデータの場所を設定することをお勧めします。

> [!TIP]
> 広範な組織に複数の地域の機能を展開する前にテストのユーザーまたはユーザーの小さなグループでの検証を開始することをお勧めします。

AAD ではユーザー オブジェクトの 2 つの種類があります: クラウド ユーザーと同期されたユーザーのみです。ユーザーの種類に適切な手順に従ってください。

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>ユーザーの優先データを使用して場所 AD の接続を同期します。 

ユーザーの会社の同期している場合、オンプレミスの Active Directory (AD) システムから Azure Active Directory (AAD) に、PreferredDataLocation を AD に設定され、AAD に同期する必要があります。次の処理では、 [Azure AD 接続の同期: 既定の構成に変更を加える](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration)優先を構成するのにはデータの場所の同期のオンプレミス AD AAD にします。

ユーザーの優先データの場所を設定、標準のユーザー作成のワークフローの一部として含めることをお勧めします。

> [!IMPORTANT]
> 準備なしの OneDrive を持つ新しいユーザーは、ユーザーの PDL は、ユーザーがビジネスのための OneDrive にログインする前に反映する変更の AAD を同期した後、少なくとも 24 時間待機します。(優先データを設定する場所がビジネスのための OneDrive を提供する、ユーザーがログインする前に確実にユーザーの新しい OneDrive が正しい位置に準備すること。)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>クラウドの優先データの場所を設定するユーザーのみ 

会社のユーザーが同期していない場合、オンプレミスの Active Directory (AD) システムから Azure Active Directory (AAD) に、Office 365 または AAD で作成されることを意味し、PDL 設定してください AAD PowerShell を使用します。

このセクションの手順では、 [Microsoft Azure Active ディレクトリの Windows PowerShell モジュール](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0)が必要です。既に AAD PowerShell をインストールする場合は、最新バージョンに更新するようにしてください。

1.  Windows PowerShell は、Microsoft Azure Active Directory のモジュールを開きます。

2.  実行`Connect-MsolService`し、テナントのグローバル管理者の資格情報を入力します。

3.  [セット MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser)コマンドレットを使用すると、個々 のユーザーの希望するデータの場所を設定できます。例えば：

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Get MsolUser コマンドレットを使用して希望するデータの場所が正しく更新されたことを確認するのにはチェックすることができます。例えば：

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

ユーザーの優先データの場所を設定、標準のユーザー作成のワークフローの一部として含めることをお勧めします。

> [!IMPORTANT]
> 準備なしの OneDrive を持つ新しいユーザーは、ユーザーの PDL は、ユーザーが SharePoint の OneDrive にログインする前に反映する変更の設定後 24 時間以上待ちます。(優先データを設定する場所がビジネスのための OneDrive を提供する、ユーザーがログインする前に確実にユーザーの新しい OneDrive が正しい位置に準備すること。)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive のプロビジョニングと PDL の効果

ユーザーは、テナントで作成した OneDrive サイトを既に持っている場合、PDL の設定は自動的に移動されません、既存の OneDrive。ユーザーの OneDrive を移動するには、geo の場所の間で OneDrive の移動の指示に従ってください[OneDrive](move-onedrive-between-geo-locations.md)を参照してください。

ユーザーは、テナント内の OneDrive サイトを持っていない場合 OneDrive が準備されますに、PDL の値に従って、ユーザーは PDL では、会社のデータが許可されている場所 (ADLs) のいずれかと一致すると仮定した場合します。

## <a name="configuring-multi-geo-search"></a>マルチ地域検索の構成

複数地域のテナントが任意の場所から結果を返す検索クエリを許可する集計の検索機能は、テナント内です。

既定では、これらのエントリ ポイントからの検索は各検索のインデックスは、関連する地域場所内にある場合でもに、集計結果を返します。

- ビジネスの OneDrive

- Delve

- SharePoint ホーム

- 検索センター

さらに、SharePoint 検索 API を使用するカスタムの検索アプリケーションの複数の地域の検索機能を構成できます。

手順については、制限や相違点を含む、 [OneDrive 複数の地域のビジネスを検索する構成](configure-search-for-multi-geo.md)を確認してください。

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>ビジネスの複数の地域の構成の OneDrive を検証しています。

ロールバックする前に広く OneDrive を複数の地域のビジネス、会社に、検証の計画に含めることができます基本的な使用例を次に示します。これらのテストとは、会社に関連するすべての他の使用ケースを完了すると、初期のパイロットのグループにユーザーを追加するのに移動することができます。

**ビジネスの OneDrive**

Office 365 アプリケーション起動プログラムから OneDrive を選択し、ユーザーの PDL に基づいて、ユーザーの適切な地理的な場所に自動的に送信されることを確認します。ビジネスの OneDrive の場所にプロビジョニングを開始する必要があります。アップロードといくつかのドキュメントをダウンロード、一度準備されたが、不正解です。

**OneDrive モバイル アプリケーション**

テスト アカウントの資格情報を使用して OneDrive のモバイル アプリケーションにログインします。ビジネス ファイルを OneDrive を参照してくださいことができ、モバイル デバイスから、それらと対話できることを確認します。

**同期クライアントの OneDrive**

OneDrive 同期クライアントがログインしたときにビジネスの地理的な場所に、OneDrive を自動的に検出することを確認します。同期クライアントをダウンロードする場合は、OneDrive ライブラリの**同期**をクリックできます。

**Office アプリケーション**

Word などの Office アプリケーションからログインすることによりビジネスの OneDrive にアクセスできることを確認します。開くには、Office アプリケーションで ["OneDrive- <TenantName>」です。Office は、OneDrive の場所を検出し、開くことができるファイルを表示します。

**Sharing**

OneDrive ファイルを共有してみてください。ユーザー選択ウィンドウを表示するすべての SharePoint のオンライン ユーザーの地理的な場所に関係なくことを確認します。
