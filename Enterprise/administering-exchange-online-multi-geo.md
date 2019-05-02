---
title: 複数地域環境での Exchange Online メールボックスの管理
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: Microsoft PowerShell を使用した Exchange Online 複数地域設定の管理方法を説明します。
ms.openlocfilehash: cc8adecda26073f588b63af12c13209720f9bc98
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490883"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>複数地域環境での Exchange Online メールボックスの管理

Office 365 環境で複数地域プロパティを表示および構成するには、リモート PowerShell が必要です。 Exchange Online PowerShell へ接続するには、「[Exchange Online PowerShell に接続する](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)」を参照してください。

ユーザー オブジェクトの **PreferredDataLocation** プロパティを参照するには、v1.x に [Microsoft Azure Active Directory PowerShell モジュール](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 以降が必要です。 AAD Connect 経由で AAD に同期されたユーザー オブジェクトでは、**PreferredDataLocation** 値を AAD PowerShell 経由で直接変更することはできません。 クラウド専用ユーザー オブジェクトは、AAD PowerShell 経由で変更できます。 Azure AD PowerShell に接続するには、「[Office 365 PowerShell への接続](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)」を参照してください。

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Exchange Online PowerShell を使用して、地域の場所に直接接続する

通常、Exchange Online PowerShellは地理上の中央位置に接続します。 しかし、衛星の地理的位置に直接接続することもできます。 パフォーマンスが向上するため、その場所にいるユーザーのみを管理している場合は、衛星地域に直接接続することをお勧めします。

特定の地域の場所に接続する場合、*ConnectionUri* パラメーターは、通常の接続手順とは異なります。 残りのコマンドと値は同じです。 手順は次のとおりです。

1. ローカル コンピューターで、Windows PowerShell を開き、次のコマンドを実行します。

   ```powershell
   $UserCredential = Get-Credential
   ```

   **[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、職場または学校のアカウントとパスワードを入力してから **[OK]** をクリックします。

2. `<emailaddress>` をターゲットの地域の場所にある**任意の**メールボックスの電子メールアドレスに置き換えます。 メールボックスのアクセス許可、および手順 1 の認証情報との関係は重要ではありません。電子メールアドレスによって、接続先が Exchange Online に通知されるだけです。
  
   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   たとえば、olga@contoso.onmicrosoft.com が、接続したい地理的位置で有効なメール ボックスのメール アドレスである場合、次のコマンドを実行します。

   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

3. 次のコマンドを実行します。

    ```powershell
    Import-PSSession $Session
    ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Exchange Online 組織で構成されている使用可能な地域の場所を表示する

Office 365 Multi-Geo の構成された地域の場所のリストを参照するには、Exchange Online PowerShell で次のコマンドを実行します。

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Exchange Online組織の地理上中央位置を表示する

テナントの地理上中央位置を表示するには、Exchange Online PowerShellで次のコマンドを実行します。

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>メールボックスの地域の場所を検索する

Exchange Online PowerShell の **Get-Mailbox** コマンドレットでは、メールボックスの複数地域に関連した以下のプロパティが表示されます。

- **Database**: データベース名の最初の 3 つの文字は、メールボックスが置かれていることを通知する地域コードに対応します。 オンライン アーカイブ メールボックスには、**ArchiveDatabase** が使用される必要があります。

- **MailboxRegion**: 管理者によって設定された地域の場所コード (Azure AD の **PreferredDataLocation** から同期された) を指定します。

- **MailboxRegionLastUpdateTime**: MailboxRegion が (自動または手動で) 最終更新された日時を示します。

メールボックスのこれらのプロパティを表示するには、次の構文を使用します。

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

たとえば、メール ボックスの chris@contoso.onmicrosoft.com の地理的位置の情報を表示するには、次のコマンドを実行します。

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

コマンドの出力は次のようになります。

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> **注:** データベース名の地域の場所コードが **MailboxRegion** 値と一致しない場合、メールボックスは自動的に再配置キューに入れられ、**MailboxRegion** 値で指定された地域の場所に移動されます (Exchange Online ではこれらのプロパティ値の間の不一致が検索されます)。

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>既存のクラウド専用メールボックスを特定の地域の場所に移動する

クラウド専用ユーザーとは、AAD Connectを介してテナントと同期していないユーザーです。 このユーザーは、Azure AD で直接作成されました。 クラウド専用ユーザーのメールボックスが格納される地理的な場所を表示または指定するには、Windows PowerShell用Azure ADモジュールの** Get-MsolUser **および** Set-MsolUser **コマンドレットを使用します。

ユーザーの **PreferredDataLocation** 値を表示するには、Azure AD PowerShell で次の構文を使用します。

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

たとえば、ユーザー michelle@contoso.onmicrosoft.com の **PreferredDataLocation** 値を表示するには、次のコマンドを実行します。

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

クラウド専用ユーザー オブジェクトの **PreferredDataLocation** 値を変更するには、Azure AD PowerShell で次の構文を使用します。

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

たとえば、**PreferredDataLocation** 値をユーザー michelle@contoso.onmicrosoft.com の欧州連合 (EUR) 地域に設定するには、次のコマンドを実行します。

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**注**:

- 前述したように、オンプレミスの Active Directory から同期されたユーザー オブジェクトにはこの手順は使用できません。 Active Directory で **PreferredDataLocation** 値を変更し、それを AAD Connect を使用して同期させる必要があります。 詳細については、「[Azure Active Directory Connect 同期: Office 365 リソースの優先されるデータの場所を構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)」を参照してください。

- メールボックスを新しい地域の場所に再配置するための所要時間は次のいくつかの要素によって決まります。

  - メールボックスのサイズと種類。

  - 移行されるメールボックスの数。

  - リソース移動の可用性。

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>訴訟ホールド中の無効のメールボックスを移動する

電子情報開示目的で保持されている訴訟ホールド中の無効なメールボックスは、無効状態の **PreferredDataLocation** 値を変更しても移動できません。 訴訟ホールド中の無効なメールボックスを移動するには:

1. 一時的にライセンスをメールボックスに割り当てます。

2. **PreferredDataLocation** を変更します。

3. 選択した地域の場所に移動した後に、メールボックスからライセンスを削除して、無効状態に戻します。

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>特定の地域の場所に新しいクラウド メールボックスを作成する

特定の地域の場所に新しいメールボックスを作成するには、以下の手順のいずれかを実行する必要があります。

- メールボックスが Exchange Online で作成される*前に*、前のセクションで説明されたように **PreferredDataLocation** を構成します。 たとえば、ライセンスを割り当てる前に、ユーザーに **PreferredDataLocation** 値を構成します。

- **PreferredDataLocation** 値の設定と同時にライセンスを割り当てます。

特定の地域にクラウド専用のライセンスユーザー（AAD Connectと同期していないユーザー）を作成するには、Azure AD PowerShellで次の構文を使用します：

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

この例では、次の値を使用して Elizabeth Brunner 用に新しいユーザー アカウントを作成します。

- ユーザー プリンシパル名: ebrunner@contoso.onmicrosoft.com

- 名: Elizabeth

- 姓: Brunner

- 表示名：Elizabeth Brunner

- パスワード: ランダムに生成され、コマンドの結果に表示される (*パスワード* パラメーターを使用していないため)

- ライセンス：`contoso:ENTERPRISEPREMIUM`（E5）

- 場所: オーストラリア (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Azure AD PowerShell での新しいユーザー アカウントの作成および LicenseAssignment 値の検索の詳細については、「[Office 365 PowerShell のユーザー アカウントを作成する](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)」および「[Office 365 PowerShell でライセンスとサービスを確認する](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)」を参照してください。

> [!NOTE]
> Exchange Online PowerShellを使用してメールボックスを有効にし、メールボックスを** PreferredDataLocation **で指定した地理上の場所に直接作成する必要がある場合は、クラウドサービスに対して** Enable-Mailbox**や**New-Mailbox**などのExchange Onlineコマンドレットを直接使用する必要があります。 オンプレミスのExchange PowerShellで** Enable-RemoteMailbox **コマンドレットを使用すると、メールボックスは地理上の中央位置に作成されます。

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>既存のオンプレミスのメールボックスを特定の地域の場所にオンボードする

標準のオンボーディング ツールとプロセスを使用して、オンプレミスの Exchange 組織から Exchange Online にメールボックスを移行できます ([EAC の移行ダッシュボード](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)、および Exchange Online PowerShell の [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) コマンドレットを含む)。

最初の手順は、オンボードされる各メールボックスにユーザー オブジェクトが存在することを確認し、正しい **PreferredDataLocation** 値が Azure AD で構成されていることを確認することです。 オンボーディングツールは** PreferredDataLocation **値に従い、メールボックスを指定された地理的位置に直接移行します。

または、Exchange Online PowerShell の [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) コマンドレットを使用してメールボックスを特定の地域に直接オンボードするために次の手順を使用できます。

1. オンボードされる各メールボックスにユーザー オブジェクトが存在し、Azure AD で **PreferredDataLocation** が適切な値に設定されていることを確認します。 **PreferredDataLocation** の値は、Exchange Online の対応するメール ユーザー オブジェクトの **MailboxRegion** 属性に同期されます。

2. このトピックの前半の接続手順を使用して、特定の衛星地域に直接接続してください。

3. Exchange Online PowerShell で、次のコマンドを実行して、メールボックスの移行を変数で実行するために使用されるオンプレミスの管理者認証情報を保存します。

   ```powershell
   $RC = Get-Credential
   ```

4. Exchange Online PowerShell で、次の例に類似した新しい **New-MoveRequest** を作成します。

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. オンプレミスのExchangeから現在接続している衛星地域に移行する必要があるメールボックスごとに、手順4を繰り返します。

6. If you need to migrate additional mailboxes to different satellite geo locations, repeat steps 2 through 4 for each specific location.

## <a name="multi-geo-reporting"></a>複数地域レポート

Microsoft 365 管理センターの**複数地域利用状況レポート**では、地域の場所ごとのユーザー数が表示されます。 レポートには、当月のユーザー分布が表示され、過去 6 か月間の履歴データが提供されます。

## <a name="see-also"></a>関連項目

[Windows PowerShell で Office 365 と Exchange Online を管理する](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
