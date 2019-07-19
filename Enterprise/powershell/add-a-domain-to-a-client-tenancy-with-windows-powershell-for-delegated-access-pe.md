---
title: 委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: ''
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: 概要:Office 365 の Windows PowerShell を使用して、既存の顧客テナントに代替ドメイン名を追加します。
ms.openlocfilehash: 1a1c1c06a2912f6624e6eb860ea6794f9474c09e
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "35781847"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="f37b0-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する</span><span class="sxs-lookup"><span data-stu-id="f37b0-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="f37b0-104">**概要:** Office 365 の Windows PowerShell を使用して、既存の顧客テナントに代替ドメイン名を追加します。</span><span class="sxs-lookup"><span data-stu-id="f37b0-104">**Summary:** Use Windows PowerShell for Office 365 to add an alternate domain name to an existing customer tenant.</span></span>
  
<span data-ttu-id="f37b0-105">Microsoft 365 管理センターよりも、Office 365用 Windows PowerShellを使用して、新しいドメインを作成して顧客のテナントに関連付けたほうが迅速に作業が行えます。</span><span class="sxs-lookup"><span data-stu-id="f37b0-105">You can create and associate new domains with your customer's tenancy with Windows PowerShell for Office 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="f37b0-106">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="f37b0-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="f37b0-107">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="f37b0-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="f37b0-108">それらの企業は、顧客に提供するサービスに Office 365 サブスクリプションをバンドルします。</span><span class="sxs-lookup"><span data-stu-id="f37b0-108">They bundle Office 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="f37b0-109">Office 365のサブスクリプションを販売する際に、顧客テナンシーに対する「代理で管理」(AOBO) 権限が自動的に付与されるため、顧客テナンシーを管理し、顧客テナンシーに関するレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f37b0-109">When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="f37b0-110">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="f37b0-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="f37b0-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span><span class="sxs-lookup"><span data-stu-id="f37b0-111">UNRESOLVED_TOKEN_VAL(GENL_O365_PowerShell_BeforeYouBegin)</span></span>
  
<span data-ttu-id="f37b0-112">また、以下の情報も必要になります。</span><span class="sxs-lookup"><span data-stu-id="f37b0-112">You also need the following information:</span></span>
  
- <span data-ttu-id="f37b0-113">顧客が望む完全修飾ドメイン名 (FQDN) が必要です。</span><span class="sxs-lookup"><span data-stu-id="f37b0-113">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="f37b0-114">顧客の **テナント ID** も必要です。</span><span class="sxs-lookup"><span data-stu-id="f37b0-114">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="f37b0-p102">FQDN は、GoDaddy などのインターネット ドメイン名サービス (DNS) 登録業者に登録されている必要があります。公的にドメイン名を登録する方法について詳しくは、「[ドメイン名の購入方法](https://go.microsoft.com/fwlink/p/?LinkId=532541)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="f37b0-p103">DNS 登録業者の登録済み DNS ゾーンに TXT レコードを追加する方法を理解する必要があります。TXT レコードを追加する方法について詳しくは、「[任意の DNS ホスティング プロバイダーで DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=532542)」をご覧ください。これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p103">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar. For more information on how to add a TXT record, see [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542). If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="f37b0-120">ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="f37b0-120">Create domains</span></span>

 <span data-ttu-id="f37b0-p104">顧客から、既定の<domain>.onmicrosoft.comドメインを世界に対して自企業を表す主ドメインにしたくないため、追加のドメインを作成して顧客のテナンシーに関連付けるよう依頼される可能性があります。この手順では、ドメインを新規作成して顧客のテナンシーに関連付ける方法を順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f37b0-123">これらの操作の一部を実行するには、でサインインするパートナー管理者アカウントが\*\*\*\* 、管理者アカウントの詳細にある「サポートしている**企業への管理アクセスを割り当てる**」の設定になっている必要があります。Microsoft 365 管理センター。</span><span class="sxs-lookup"><span data-stu-id="f37b0-123">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="f37b0-124">パートナー管理者の役割の管理について詳しくは、「[パートナー: 代理管理を提供する](https://go.microsoft.com/fwlink/p/?LinkId=532435)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f37b0-124">For more information on managing partner administrator roles, see[Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="f37b0-125">Azure Active Directory でドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="f37b0-125">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="f37b0-126">このコマンドは、Azure Active Directory にドメインを作成しますが、公的に登録されたドメインとは関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="f37b0-126">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="f37b0-127">関連付けのためには、企業向けのMicrosoft Office 365に対し、公に登録されたドメインを所有していることを証明していただく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37b0-127">That comes when you prove that you own the publicly registered domain to Microsoft Office 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="f37b0-128">DNS の TXT 検証レコードのデータを取得する</span><span class="sxs-lookup"><span data-stu-id="f37b0-128">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="f37b0-p107">Office 365 は、DNS の TXT 検証レコードに配置する必要がある特定のデータを形成します。データを取得するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p107">Office 365 will generate the specific data that you need to place into the DNS TXT verification record. To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="f37b0-131">これにより、次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="f37b0-131">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="f37b0-132">公的に登録された DNS ゾーンに TXT レコードを作成するには、このテキストが必要です。</span><span class="sxs-lookup"><span data-stu-id="f37b0-132">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="f37b0-133">必ずコピーし、保存してください。</span><span class="sxs-lookup"><span data-stu-id="f37b0-133">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="f37b0-134">公的に登録された DNS ゾーンに TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="f37b0-134">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="f37b0-135">Office 365 が公的に登録されたドメイン名に向けられたトラフィックの受け入れを開始する前に、そのドメインの所有者であることと、ドメインに対する管理者のアクセス許可を保有していることを証明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37b0-135">Before Office 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="f37b0-136">ドメインを保有していることを証明するには、ドメインに TXT レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="f37b0-136">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="f37b0-137">TXT レコードは、ドメインでは何も行わず、ドメインの所有権が確立した後に削除することができます。</span><span class="sxs-lookup"><span data-stu-id="f37b0-137">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="f37b0-138">TXT レコードを作成するには、「[任意の DNS ホスティング プロバイダーで DNS レコードを作成する](https://go.microsoft.com/fwlink/p/?LinkId=532542)」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="f37b0-138">To create the TXT records, follow the procedures at [Create DNS records at any DNS hosting provider for Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="f37b0-139">これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f37b0-139">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="f37b0-p110">TXT レコードが正常に作成されたことを、nslookup 経由で確認します。次の構文に従います。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p110">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="f37b0-142">これにより、次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="f37b0-142">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-office-365"></a><span data-ttu-id="f37b0-143">Office 365 でドメインの所有権を検証する</span><span class="sxs-lookup"><span data-stu-id="f37b0-143">Validate domain ownership in Office 365</span></span>

<span data-ttu-id="f37b0-p111">この最後の手順では、公的に登録されたドメインを保有していることを Office 365 に検証します。この手順の完了後、Office 365 は新しいドメイン名にルーティングされるトラフィックの受け入れを開始します。ドメインの作成と登録のプロセスを完了するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f37b0-p111">In this last step, you validate to Office 365 that you own the publically registered domain. After this step, Office 365 will begin accepting traffic routed to the new domain name. To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="f37b0-147">このコマンドは出力を返しません。そのため、機能したことを確認するために、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f37b0-147">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="f37b0-148">コマンドを実行すると、次のようなものが返されます。</span><span class="sxs-lookup"><span data-stu-id="f37b0-148">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="f37b0-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="f37b0-149">See also</span></span>

#### 

[<span data-ttu-id="f37b0-150">パートナーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="f37b0-150">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

