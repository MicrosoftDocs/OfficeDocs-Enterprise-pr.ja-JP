---
title: Exchange オンラインで複数の地域の機能
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Exchange Online の機能を複数地域での複数の地理的な領域に、Office 365 のプレゼンスを展開します。
ms.openlocfilehash: 6acd2ffab1f35b74d06d6ab5f7bfcbf70f88f8b4
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200740"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Exchange オンラインで複数の地域の機能

Office 365 に複数の地域の機能は、複数の地域にまたがる 1 つのテナントを有効にします。複数地域を有効にすると、お客様は、ユーザーごとに Exchange Online のメールボックスの内容 (データ) の場所を選択できます。

(中央の場所と呼ばれる)、初期のテナントの場所は、住所に基づいて決まります。複数地域を有効にすると、によって、他のサテライト オフィスでのメールボックスを配置できます。

- サテライトの場所に直接新しいオンラインの Exchange メールボックスを作成しています。

- サテライトの場所に既存の Exchange Online メールボックスを移動します。

- サテライトの場所に直接、オンプレミスの Exchange 組織からメールボックスを契約時。

複数地域の構成で使用するため、以下の地域があります。

- アジア太平洋地域

- オーストラリア

- カナダ

- 欧州連合

- フランス

- インド

- 日本

- 韓国

- イギリス

- 米国

## <a name="prerequisite-configuration"></a>前提条件の構成
機能を使用して複数の地域では、Exchange オンラインを開始する前にマイクロソフトは複数地域のサポートのため、Exchange Online のテナントを構成する必要があります。Office 365 の複数の地域のライセンス表示して、テナント内の順序を後に、この 1 回限りの構成プロセスがトリガーされます。1 回のみ構成する必要があります通常かかる 30 日未満で完了します。Office 365 の複数の地域を注文するのには、マイクロソフトの担当者に問い合わせてください。詳細についてを参照してくださいhttps://aka.ms/Multi-Geo。

構成が完了したときは、 [Office 365 のメッセージ センター](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093)に通知が届きます。テナントに、複数地域のライセンスが表示されたら、構成が自動的にトリガーされます。

## <a name="mailbox-placement-and-moves"></a>メールボックスの配置と移動
マイクロソフトでは、前提条件の複数の地域の設定手順が完了すると、Exchange Online を優先、ユーザー オブジェクトの**PreferredDataLocation**属性が Azure AD にします。

Exchange Online は、オンラインの Exchange のディレクトリ サービス内の**MailboxRegion**プロパティに Azure AD から**PreferredDataLocation**のプロパティを同期します。**MailboxRegion**の値は、地域のユーザーのメールボックスと関連付けられているアーカイブ メールボックスの配置場所を決定します。ユーザーのプライマリ メールボックス、アーカイブ メールボックスを別の地域の場所に存在するを構成することはできません。ユーザー オブジェクトごと、地域の 1 つだけの場所を構成できます。

- **PreferredDataLocation**が既存のメールボックスを持つユーザーで構成されると、メールボックスの再配置のキューに入れ、地域を指定した場所に自動的に移動します。 

- **PreferredDataLocation**が構成すると、既存のメールボックスにユーザーのメールボックスが地域を指定した場所に準備されます。 

- ユーザーに**PreferredDataLocation**を指定しない場合は、中央の場所で、メールボックスが配置されます。

- **PreferredDataLocation**コードが正しくない場合 (たとえば、型名ではなく NAN の)、メールボックスは、中央の場所に配置されます。

**注**: 複数地域の機能と Skype を地域ごとにホストされているビジネス オンラインの会議のプロパティを使用して**PreferredDataLocation**ユーザー オブジェクトのサービスを検索します。地域ごとにホストされている会議のためのユーザー オブジェクトの**PreferredDataLocation**の値を構成する場合は、それらのユーザーのメールボックスに自動的に移動されます地域を指定した場所に複数地域を有効にした後 Office 365 テナントに。

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Exchange オンラインで複数の地域の機能の制限
1. ユーザーのメールボックス、リソース メールボックス (部屋・備品のメールボックス)、および共有メールボックスは、複数地域の機能をサポートします。パブリック フォルダーのメールボックスと Office 365 のグループは、中央の場所に残ります。
 
2. セキュリティとコンプライアンスの機能 (たとえば、監査および電子的証拠開示) は、Exchange 管理センター (EAC) で使用されるは、複数地域の組織では使用できません。代わりに、セキュリティとコンプライアンスの機能を構成するのには、 [Office 365 のセキュリティとコンプライアンスのセンター](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8)を使用する必要があります。

3. Mac ユーザーは、outlook は、地域の新しい場所に自分のメールボックスを移動するときに、そのオンライン ・ アーカイブのフォルダーへのアクセスの一時的な損失にすることがあります。この条件では、ユーザーのプライマリとアーカイブ メールボックスが別の地域の場所ではメールボックスの移動の間の地域は、さまざまな時点で完了可能性がありますのでに発生します。

4. ユーザーは、Outlook (Outlook Web App または OWA と呼ばれていました)、web 上の場所を地域全体で*メールボックス フォルダー*を共有できません。たとえば、欧州連合内のユーザーは、米国内にあるメールボックス内の共有フォルダーを開くに web 上で Outlook を使用できません。ただし、Web ユーザーに Outlook は、 [Outlook Web App で別のブラウザー ウィンドウ内の他のユーザーのメールボックスを開く](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362)で説明したように別のブラウザー ウィンドウを使用して、別の地域で*その他のメールボックス*を開くことができます。

    **注**: Windows 上の Outlook ではサポートされて間 geo メールボックス フォルダーを共有します。

## <a name="administration"></a>管理 
リモート PowerShell は、表示し、Office 365 環境内の複数の地域のプロパティを構成する必要があります。Office 365 の管理に使用される各種の PowerShell モジュールについては、 [Office 365 の管理、および Windows PowerShell で Exchange のオンライン](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)を参照してください。

- [Microsoft Azure Active Directory の PowerShell モジュール](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx)の v1.1.166.0 または後での v1.x ユーザー オブジェクトの**PreferredDataLocation**プロパティを表示する必要があります。AAD に AAD の接続経由で同期するユーザー オブジェクトには、AAD PowerShell を使用して直接変更を加える、 **PreferredDataLocation**の値を持つことはできません。AAD PowerShell を使用してクラウド専用のユーザー オブジェクトを変更できます。Azure AD PowerShell に接続するには、 [Office 365 の PowerShell への接続](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)を参照してください。 

- オンライン PowerShell を Exchange に接続するには、 [Exchange オンライン PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)を参照してください。 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Exchange オンライン PowerShell を使用して特定の地域に直接接続します。
通常、Exchange のオンライン PowerShell は、geo の既定の場所に接続されます。既定以外の地域の場所に直接接続することもできます。パフォーマンスの向上のためだけにその地域の場所のユーザーを管理するときに、既定以外の地域の場所への直接接続をお勧めします。

特定の地域に接続するには*ConnectionUri*パラメーターは通常の接続手順とは異なるです。コマンドと値の残りの部分は、同じです。手順は次のとおりです。

1. ローカル コンピューターに Windows PowerShell を開き次のコマンドを実行します。
    
    ```
    $UserCredential = Get-Credential
    ```
   **Windows PowerShell の資格情報の要求**] ダイアログ ボックスで、作業時間や学校のアカウントとパスワードを入力し、し、[ **OK**] をクリックします。
    
2. 交換`<emailaddress>`のターゲット地域の場所と実行次のコマンドでメールボックス**の**電子メール アドレスがあります。メールボックスとの関連性のステップ 1 で資格情報のアクセス許可は、ファクターではありません。電子メール アドレスだけで位置を通知 Exchange オンライン接続します。
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   などの olga@contoso.onmicrosoft.com に接続する地域で有効なメールボックスの電子メール アドレスがある場合は、次のコマンドを実行します。

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. 次のコマンドを実行します。
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Azure AD 接続バージョン要件
AAD の接続のバージョン 1.1.524.0 または後でのみサポートされているメソッド、オンプレミスの Active Directory から同期されるユーザー オブジェクトの**PreferredDataLocation**プロパティを設定するためです。AAD に AAD の接続経由で同期するユーザー オブジェクトには、AAD PowerShell を使用して直接変更を加える、 **PreferredDataLocation**の値を持つことはできません。AAD PowerShell を使用してクラウド専用のユーザー オブジェクトを変更できます。詳細についてを参照してください[Azure Active Directory 接続の同期: Office 365 のリソースの優先データのパスを構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。

### <a name="geo-codes"></a>地域コード
**PreferredDataLocation**プロパティで、地域を指定するのにには、3 文字のコードを使用します。次の表は、使用可能な地域のコードを一覧します。

|geo |コード |
|---------|---------|
|アジア/太平洋地域 |APC |
|オーストラリア |AUS |
|カナダ |CAN |
|欧州連合 |EUR |
|フランス |FRA|
|インド |IND |
|日本 |JPN |
|韓国 |KOR |
|イギリス |GBR |
|米国 |NAM |

**注**: **PreferredDataLocation**および**MailboxRegion**プロパティは、エラーのチェックなしで文字列です。無効な値 (たとえば、NAN) を入力する場合は、既定の地域で、メールボックスが配置されます。

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>オンラインの Exchange 組織で構成されている使用可能な地域を表示します。
オンラインの Exchange 組織で構成されている地域の一覧を表示するには、次のコマンドを実行 Exchange オンライン PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

コマンドの出力は次のようになります。

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Geo オンラインの Exchange 組織の既定の設定を表示します。
オンラインの Exchange 組織の既定の地域を表示するには、次のコマンドを実行 Exchange オンライン PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

コマンドの出力は次のようになります。

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>メールボックスの地域の場所を検索します。
メールボックスのプロパティを Exchange オンライン PowerShell 表示次の複数の地域で**取得メールボックス**コマンドレットに関連します。

- **データベース**: データベース名の最初の 3 つの文字が、メールボックスが置かれている場所を表示する地域コードに対応します。オンライン アーカイブ メールボックスの**ArchiveDatabase**プロパティを使用してください。

- **MailboxRegion**: (Azure AD では、 **PreferredDataLocation**の同期) の管理者によって設定された地域場所コードを指定します。

- **MailboxRegionLastUpdateTime**: MailboxRegion が最終更新日時 (自動または手動のいずれか) を示します。

メールボックスのこれらのプロパティを表示するには、次の構文を使用します。

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

などのメールボックスの chris@contoso.onmicrosoft.com の地域情報を表示するには、次のコマンドを実行します。

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

コマンドの出力は次のようになります。

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **注:** 地域場所コード、データベース名には、 **MailboxRegion**の値と一致しない、メールボックスの再配置のキューに自動的にするなり、 **MailboxRegion**の値で指定された地域の場所に移動 (Exchange のオンライン検索は一致しないこれらのプロパティ値の間)。

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>既存クラウド専用のメールボックスを特定の地域に移動します。
クラウド専用のユーザーは、AAD の接続を使用してテナントのときではないユーザーです。Azure AD で直接、このユーザーが作成されました。Windows PowerShell の Azure AD モジュールで**Get MsolUser**と**セット MsolUser**コマンドレットを使用して、表示またはクラウドのみユーザーのメールボックスを格納する地域を指定します。

ユーザーの**PreferredDataLocation**の値を表示するには、Azure AD PowerShell でこの構文を使用します。

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

たとえば、ユーザーの michelle@contoso.onmicrosoft.com の**PreferredDataLocation**の値を表示するには、次のコマンドを実行します。

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

コマンドの出力は次のようになります。

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

クラウド専用のユーザー オブジェクトの**PreferredDataLocation**の値を変更するには、Azure AD PowerShell で次の構文を使用します。

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

たとえば、ユーザー michelle@contoso.onmicrosoft.com の欧州連合 (EUR) の地域には、 **PreferredDataLocation**値を設定するには、次のコマンドを実行します。

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**注**:

- 説明したように以前は使用できませんこの手順、オンプレミスの Active Directory から同期されたユーザー オブジェクトの。AAD の接続を使用して**PreferredDataLocation**の値を変更する必要があります。詳細についてを参照してください[Azure Active Directory 接続の同期: Office 365 のリソースの優先データのパスを構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。 

- かかる目的の地域の別の場所に、現在の地域は、いくつかの要因によって異なります、mailboxfrom を再配置します。
 
  - サイズとメールボックスの種類。
 
  - 移動中のメールボックスの数です。
 
  - リソースの可用性の移動します。

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>移動には、証拠保全上にあるメールボックスが無効になっています。
電子証拠開示の目的が無効になっている状態で、 **PreferredDataLocation**の値を変更することで移動できないのは、証拠保全上のメールボックスを無効にします。保留中の訴訟で無効になっているメールボックスを移動するのには

1. 一時的にメールボックスにライセンスを割り当てます。

2. **PreferredDataLocation**を変更します。

3. 無効の状態に戻すことを選択した地域の場所に、移動した後、メールボックスからライセンスを削除します。

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>特定の地域で新しいクラウドのメールボックスを作成します。 
地域の特定の場所に新しいメールボックスを作成するには次の手順のいずれかを実行する必要があります。

- 前のセクション*の前に*メールボックスの作成は、オンライン Exchange で説明したように、 **PreferredDataLocation**の値を構成します。ユーザーにライセンスを割り当てる前に、たとえば、 **PreferredDataLocation**の値を構成します。 

- **PreferredDataLocation**値を設定すると同時にライセンスを割り当てます。

特定の地域で、新しいクラウド専用ライセンスを受けたユーザー (AAD 接続の同期) を作成するには、Azure AD PowerShell で次の構文を使用します。

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
次の使用例は、次の値を持つエリザベス Brunner の新しいユーザー アカウントを作成します。

- ユーザー プリンシパル名: ebrunner@contoso.onmicrosoft.com

- 名: エリザベス

- 姓、名: Brunner

- エリザベス Brunner の名前を表示します。

- パスワード: は、ランダムに生成され、(*パスワード*パラメーターは使用しない) ために、コマンドの結果に示すように

- ライセンス: contoso:ENTERPRISEPREMIUM (E5)

- 場所: オーストラリア (オーストラリア)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

新しいユーザー アカウントを作成して、Azure AD PowerShell で LicenseAssignment の値を検索する方法の詳細については、 [Office 365 の PowerShell でユーザー アカウントを作成](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)し、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell)を参照してください。

> **注:** メールボックスを有効にし、 **PreferredDataLocation**で指定されている地域で直接作成するメールボックスが必要な Exchange のオンライン PowerShell を使用する場合は、**有効にするメールボックス**や新規メールボックスの**などのオンラインの Exchange のコマンドレットを使用する必要があります。** クラウド サービスを直接します。**有効にする RemoteMailbox**オンプレミスの Exchange コマンドレットを使用する場合は、既定の地域で、メールボックスが作成されます。

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>既存のオンボード設置特定地域内のメールボックス
など[、EAC での移行のダッシュ ボード](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)の[新規 MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch)コマンドレットでは、Exchange オンライン Exchange オンライン、オンプレミスの Exchange 組織からメールボックスを移行するのには、契約時の標準的なツールとプロセスを使用することができます。PowerShell。

最初のステップでは、onboarded では、Azure AD では、適切な**PreferredDataLocation**値を設定することを確認するには、各メールボックスのユーザー オブジェクトが存在することを確認します。契約時のツールは、 **PreferredDataLocation**の値が反映され、指定の地域に直接メールボックスが移行されます。

または、Exchange オンライン PowerShell の[新規 MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest)コマンドレットを使用して特定の地域の場所に直接オンボードのメールボックスに次の手順を使用することができます。

1. Onboarded と**PreferredDataLocation**は、Azure AD で目的の値に設定されている各メールボックスのユーザー オブジェクトが存在することを確認します。**PreferredDataLocation**の値が同期されます、対応するメール ユーザー オブジェクトの**MailboxRegion**属性に Exchange オンライン。

2. 特定の衛星からの接続方法を使用して、このトピックで前述した地域に直接接続します。

3. Exchange オンラインの PowerShell で次のコマンドを実行して、変数にメールボックスの移行を実行するために使用される設置管理者の資格情報を格納します。

    ```
    $RC = Get-Credential
    ```

4. Exchange オンラインの PowerShell で次の例のような新しい**新しい MoveRequest**を作成します。 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. メールボックスが現在接続しているサテライトの場所に、オンプレミスの Exchange から移行する必要がありますごとに手順 4 を繰り返します。

6. さまざまなサテライトの場所に追加のメールボックスを移行する場合は、特定の衛星場所ごとに手順 2 ~ 4 を繰り返します。

### <a name="multi-geo-reporting"></a>複数地域のレポート
Office 365 管理センターの**利用状況レポートの複数の地域**では、地域の場所でユーザー数が表示されます。レポートでは、当月のユーザーの分散を表示し、過去 6 か月の履歴データを提供します。
