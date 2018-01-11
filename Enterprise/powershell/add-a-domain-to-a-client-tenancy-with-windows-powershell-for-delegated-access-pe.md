---
title: "委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: 
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "概要:Office 365 の Windows PowerShell を使用して、既存の顧客テナントに代替ドメイン名を追加します。"
ms.openlocfilehash: f99039ffa9f921b33829767a08f33db500a5d2ed
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する

 **概要:** Office 365 の Windows PowerShell を使用して、既存の顧客テナントに代替ドメイン名を追加します。
  
Office 365 管理センター を使うより短時間で、Office 365 の Windows PowerShell でドメインを新規作成して顧客のテナンシーと関連付けることができます。
  
委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。それらの企業は、顧客に提供するサービスに Office 365 サブスクリプションをバンドルします。 Office 365 サブスクリプションを販売する際に、顧客テナンシー に対する「代理で管理」(AOBO) 権限が自動的に付与されるため、顧客テナンシーを管理し、顧客テナンシーに関するレポートを作成できます。
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)
  
また、以下の情報も必要になります。
  
- 顧客が望む完全修飾ドメイン名 (FQDN) が必要です。
    
- 顧客の **テナント ID** も必要です。
    
- FQDN は、GoDaddy などのインターネット ドメイン名サービス (DNS) 登録業者に登録されている必要があります。公的にドメイン名を登録する方法について詳しくは、「[ドメイン名の購入方法](https://go.microsoft.com/fwlink/p/?LinkId=532541)」をご覧ください。
    
- DNS 登録業者の登録済み DNS ゾーンに TXT レコードを追加する方法を理解する必要があります。TXT レコードを追加する方法について詳しくは、「[任意の DNS ホスティング プロバイダーで DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=532542)」をご覧ください。これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。
    
## <a name="create-domains"></a>ドメインを作成する

 顧客から、既定の<domain>.onmicrosoft.comドメインを世界に対して自企業を表す主ドメインにしたくないため、追加のドメインを作成して顧客のテナンシーに関連付けるよう依頼される可能性があります。この手順では、ドメインを新規作成して顧客のテナンシーに関連付ける方法を順を追って説明します。
  
> [!NOTE]
> これらの操作の一部を実行するには、サインインに使うパートナー管理者アカウントについて、Office 365 管理センター の [管理者アカウントの詳細] にある **[管理のアクセス権をサポートする会社に割り当てる]** を **[完全管理]** に設定する必要があります。パートナー管理者の役割の管理について詳しくは、「[パートナー: 代理管理を提供する](https://go.microsoft.com/fwlink/p/?LinkId=532435)」をご覧ください。 
  
### <a name="create-the-domain-in-azure-active-directory"></a>Azure Active Directory でドメインを作成する

このコマンドは、Azure Active Directory にドメインを作成しますが、公的に登録されたドメインとは関連付けられません。Microsoft Office 365 for enterprises で公的に登録されたドメインを保有していることが証明されている場合に関連付けられます。
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>DNS の TXT 検証レコードのデータを取得する

 Office 365 は、DNS の TXT 検証レコードに配置する必要がある特定のデータを形成します。データを取得するには、次のコマンドを実行します。
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

これにより、次のような出力が得られます。
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> 公的に登録された DNS ゾーンに TXT レコードを作成するには、このテキストが必要です。必ずコピーし、それを保存してください。 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>公的に登録された DNS ゾーンに TXT レコードを追加する

Office 365 が公的に登録されたドメイン名に向けられたトラフィックの受け入れを開始する前に、そのドメインに対する管理者のアクセス許可を保有していることを証明する必要があります。ドメインを保有していることを証明するには、ドメインに TXT レコードを作成します。TXT レコードは、ドメインでは何も行わず、ドメインの所有権が確立した後に削除することができます。TXT レコードを作成するには、「[任意の DNS ホスティング プロバイダーで DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=532542)」の手順に従ってください。これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。
  
TXT レコードが正常に作成されたことを、nslookup 経由で確認します。次の構文に従います。
  
```
nslookup -type=TXT <FQDN of registered domain>
```

これにより、次のような出力が得られます。
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a>Office 365 でドメインの所有権を検証する

この最後の手順では、公的に登録されたドメインを保有していることを Office 365 に検証します。この手順の完了後、Office 365 は新しいドメイン名にルーティングされるトラフィックの受け入れを開始します。ドメインの作成と登録のプロセスを完了するには、次のコマンドを実行します。 
  
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

