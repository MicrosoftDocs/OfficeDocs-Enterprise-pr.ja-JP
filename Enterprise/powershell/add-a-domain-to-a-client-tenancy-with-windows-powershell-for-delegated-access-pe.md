---
title: 委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: '概要: Microsoft 365 で Windows PowerShell を使用して、既存の顧客テナントに代替ドメイン名を追加します。'
ms.openlocfilehash: 6ba706c1fc0b2e2b43687ac582a40f36a2a3387c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997363"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する

Microsoft 365 管理センターを使用するよりも、Microsoft 365 用の Windows PowerShell を使用して、新しいドメインを作成して、お客様のテナントと関連付けることができます。
  
委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。 他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。 これらのサブスクリプションは、お客様に対して Microsoft 365 のサブスクリプションをサービス提供にバンドルしています。 Microsoft 365 サブスクリプションを販売する際には、顧客のテナンシーに対して管理およびレポートできるように、顧客テナンシーへの (AOBO) アクセス許可が自動的に付与されます。
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
また、パートナーのテナント管理者の資格情報も必要です。
  
また、以下の情報も必要になります。
  
- 顧客が望む完全修飾ドメイン名 (FQDN) が必要です。
    
- 顧客の **テナント ID** も必要です。
    
- The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).
    
- DNS 登録業者の登録済み DNS ゾーンに TXT レコードを追加する方法を理解する必要があります。 TXT レコードを追加する方法の詳細については、「[ドメインを接続するための DNS レコードを追加](https://go.microsoft.com/fwlink/p/?LinkId=532542)する」を参照してください。 これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。
    
## <a name="create-domains"></a>ドメインを作成する

 Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.
  
> [!NOTE]
> これらの操作の一部を実行するには、Microsoft 365 管理センターの管理者アカウントの詳細にある [サポートされている**企業への管理アクセス権を割り当てる**] の設定を [**完全管理**] に設定する必要があります。 パートナー管理者の役割の管理の詳細については、「[パートナー: 代理管理を提案](https://go.microsoft.com/fwlink/p/?LinkId=532435)する」を参照してください。 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Azure Active Directory でドメインを作成する

このコマンドは、Azure Active Directory にドメインを作成しますが、公的に登録されたドメインとは関連付けられません。 公開されているドメインを企業向け Microsoft Microsoft 365 に所有していることを証明すると、これが提供されます。
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>DNS の TXT 検証レコードのデータを取得する

 Microsoft 365 は、DNS TXT 検証レコードに格納する必要がある特定のデータを生成します。 データを取得するには、次のコマンドを実行します。
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

これにより、次のような出力が得られます。
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> 公的に登録された DNS ゾーンに TXT レコードを作成するには、このテキストが必要です。 必ずコピーし、保存してください。 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>公的に登録された DNS ゾーンに TXT レコードを追加する

公開されているドメイン名宛てのトラフィックの受信を開始する前に、Microsoft 365 は、ドメインに対する管理者アクセス許可を所有していることを証明する必要があります。 ドメインを保有していることを証明するには、ドメインに TXT レコードを作成します。 TXT レコードは、ドメインでは何も行わず、ドメインの所有権が確立した後に削除することができます。 TXT レコードを作成するには、「 [DNS レコードを追加する](https://go.microsoft.com/fwlink/p/?LinkId=532542)」の手順に従ってドメインを接続します。 これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。
  
Confirm the successful creation of the TXT record via nslookup. Follow this syntax.
  
```
nslookup -type=TXT <FQDN of registered domain>
```

これにより、次のような出力が得られます。
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a>Microsoft 365 でドメインの所有権を検証する

この最後の手順では、公的登録済みドメインを所有していることを Microsoft 365 に検証します。 この手順の後、Microsoft 365 は新しいドメイン名にルーティングされたトラフィックの受け入れを開始します。 ドメインの作成と登録のプロセスを完了するには、次のコマンドを実行します。 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

このコマンドは出力を返しません。そのため、機能したことを確認するために、次のコマンドを実行します。
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

コマンドを実行すると、次のようなものが返されます。
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a>関連項目

#### 

[パートナーのヘルプ](https://go.microsoft.com/fwlink/p/?LinkID=533477)

