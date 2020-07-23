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
description: '概要: Microsoft 365 の PowerShell を使用して、既存の顧客テナントに代替ドメイン名を追加します。'
ms.openlocfilehash: d5a6c7326684c74d3b05e7b4a1e88c2a37e99ca0
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229783"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="9ffb1-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell でクライアント テナンシーにドメインを追加する</span><span class="sxs-lookup"><span data-stu-id="9ffb1-103">Add a domain to a client tenancy with Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

<span data-ttu-id="9ffb1-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="9ffb1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="9ffb1-105">Microsoft 365 の PowerShell を使用して、Microsoft 365 管理センターより高速に、新しいドメインを作成して、顧客のテナントと関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-105">You can create and associate new domains with your customer's tenancy with PowerShell for Microsoft 365 faster than using the Microsoft 365 admin center.</span></span>
  
<span data-ttu-id="9ffb1-106">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="9ffb1-107">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="9ffb1-108">これらのサブスクリプションは、お客様に対して Microsoft 365 のサブスクリプションをサービス提供にバンドルしています。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="9ffb1-109">Microsoft 365 サブスクリプションを販売する際には、顧客のテナンシーに対して管理およびレポートできるように、顧客テナンシーへの (AOBO) アクセス許可が自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="9ffb1-110">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="9ffb1-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="9ffb1-111">このトピックの手順では、 [PowerShell を使用して Microsoft 365 に](connect-to-office-365-powershell.md)接続するために接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-111">The procedures in this topic require you to connect to [Connect to Microsoft 365 with PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="9ffb1-112">また、パートナーのテナント管理者の資格情報も必要です。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-112">You also need your partner tenant administrator credentials.</span></span>
  
<span data-ttu-id="9ffb1-113">また、以下の情報も必要になります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-113">You also need the following information:</span></span>
  
- <span data-ttu-id="9ffb1-114">顧客が望む完全修飾ドメイン名 (FQDN) が必要です。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-114">You need the fully qualified domain name (FQDN) that your customer wants.</span></span>
    
- <span data-ttu-id="9ffb1-115">顧客の **テナント ID** も必要です。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-115">You need the customer's **TenantId**.</span></span>
    
- <span data-ttu-id="9ffb1-p102">FQDN は、GoDaddy などのインターネット ドメイン名サービス (DNS) 登録業者に登録されている必要があります。公的にドメイン名を登録する方法について詳しくは、「[ドメイン名の購入方法](https://go.microsoft.com/fwlink/p/?LinkId=532541)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-p102">The FQDN must be registered with an Internet domain name service (DNS) registrar, such as GoDaddy. For more information on how to publically register a domain name, see [How to buy a domain name](https://go.microsoft.com/fwlink/p/?LinkId=532541).</span></span>
    
- <span data-ttu-id="9ffb1-118">DNS 登録業者の登録済み DNS ゾーンに TXT レコードを追加する方法を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-118">You need to know how to add a TXT record to the registered DNS zone for your DNS registrar.</span></span> <span data-ttu-id="9ffb1-119">TXT レコードを追加する方法の詳細については、「[ドメインを接続するための DNS レコードを追加](https://go.microsoft.com/fwlink/p/?LinkId=532542)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-119">For more information on how to add a TXT record, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="9ffb1-120">これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-120">If those procedures don't work for you, you will need to find the procedures for your DNS registrar.</span></span>
    
## <a name="create-domains"></a><span data-ttu-id="9ffb1-121">ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="9ffb1-121">Create domains</span></span>

 <span data-ttu-id="9ffb1-p104">顧客から、既定の<domain>.onmicrosoft.comドメインを世界に対して自企業を表す主ドメインにしたくないため、追加のドメインを作成して顧客のテナンシーに関連付けるよう依頼される可能性があります。この手順では、ドメインを新規作成して顧客のテナンシーに関連付ける方法を順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-p104">Your customers will likely ask you to create additional domains to associate with their tenancy because they don't want the default <domain>.onmicrosoft.com domain to be the primary one that represents their corporate identities to the world. This procedure walks you through creating a new domain associated with your customer's tenancy.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9ffb1-124">これらの操作の一部を実行するには、Microsoft 365 管理センターの管理者アカウントの詳細にある [サポートされている**企業への管理アクセス権を割り当てる**] の設定を [**完全管理**] に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-124">To perform some of these operations, the partner administrator account you sign in with must be set to **Full administration** for the **Assign administrative access to companies you support** setting found in the details of the admin account in the Microsoft 365 admin center.</span></span> <span data-ttu-id="9ffb1-125">パートナー管理者の役割の管理の詳細については、「[パートナー: 代理管理を提案](https://go.microsoft.com/fwlink/p/?LinkId=532435)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-125">For more information on managing partner administrator roles, see [Partners: Offer delegated administration](https://go.microsoft.com/fwlink/p/?LinkId=532435).</span></span> 
  
### <a name="create-the-domain-in-azure-active-directory"></a><span data-ttu-id="9ffb1-126">Azure Active Directory でドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="9ffb1-126">Create the domain in Azure Active Directory</span></span>

<span data-ttu-id="9ffb1-127">このコマンドは、Azure Active Directory にドメインを作成しますが、公的に登録されたドメインとは関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-127">This command creates the domain in Azure Active Directory but does not associate it with the publicly registered domain.</span></span> <span data-ttu-id="9ffb1-128">公開されているドメインを企業向け Microsoft Microsoft 365 に所有していることを証明すると、これが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-128">That comes when you prove that you own the publicly registered domain to Microsoft Microsoft 365 for enterprises.</span></span>
  
```
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

>[!Note]
><span data-ttu-id="9ffb1-129">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="9ffb1-130">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="get-the-data-for-the-dns-txt-verification-record"></a><span data-ttu-id="9ffb1-131">DNS の TXT 検証レコードのデータを取得する</span><span class="sxs-lookup"><span data-stu-id="9ffb1-131">Get the data for the DNS TXT verification record</span></span>

 <span data-ttu-id="9ffb1-132">Microsoft 365 は、DNS TXT 検証レコードに格納する必要がある特定のデータを生成します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-132">Microsoft 365 will generate the specific data that you need to place into the DNS TXT verification record.</span></span> <span data-ttu-id="9ffb1-133">データを取得するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-133">To get the data, run this command.</span></span>
  
```
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

<span data-ttu-id="9ffb1-134">これにより、次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-134">This will give you output like:</span></span>
  
 `Label: domainname.com`
  
 `Text: MS=ms########`
  
 `Ttl: 3600`
  
> [!NOTE]
> <span data-ttu-id="9ffb1-135">公的に登録された DNS ゾーンに TXT レコードを作成するには、このテキストが必要です。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-135">You will need this text to create the TXT record in the publicly registered DNS zone.</span></span> <span data-ttu-id="9ffb1-136">必ずコピーし、保存してください。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-136">Be sure to copy and save it.</span></span> 
  
### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a><span data-ttu-id="9ffb1-137">公的に登録された DNS ゾーンに TXT レコードを追加する</span><span class="sxs-lookup"><span data-stu-id="9ffb1-137">Add a TXT record to the publically registered DNS zone</span></span>

<span data-ttu-id="9ffb1-138">公開されているドメイン名宛てのトラフィックの受信を開始する前に、Microsoft 365 は、ドメインに対する管理者アクセス許可を所有していることを証明する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-138">Before Microsoft 365 will start accepting traffic that is directed to the publicly registered domain name, you must prove that you own and have administrator permissions to the domain.</span></span> <span data-ttu-id="9ffb1-139">ドメインを保有していることを証明するには、ドメインに TXT レコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-139">You prove you own the domain by creating a TXT record in the domain.</span></span> <span data-ttu-id="9ffb1-140">TXT レコードは、ドメインでは何も行わず、ドメインの所有権が確立した後に削除することができます。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-140">A TXT record doesn't do anything in your domain, and it can be deleted after your ownership of the domain is established.</span></span> <span data-ttu-id="9ffb1-141">TXT レコードを作成するには、「 [DNS レコードを追加する](https://go.microsoft.com/fwlink/p/?LinkId=532542)」の手順に従ってドメインを接続します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-141">To create the TXT records, follow the procedures at [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=532542).</span></span> <span data-ttu-id="9ffb1-142">これらの手順がうまくいかない場合は、使っている DNS 登録業者用の手順を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-142">If those procedures don't work for you , you need to find the procedures for your DNS registrar.</span></span>
  
<span data-ttu-id="9ffb1-p111">TXT レコードが正常に作成されたことを、nslookup 経由で確認します。次の構文に従います。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-p111">Confirm the successful creation of the TXT record via nslookup. Follow this syntax.</span></span>
  
```
nslookup -type=TXT <FQDN of registered domain>
```

<span data-ttu-id="9ffb1-145">これにより、次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-145">This will give you output like:</span></span>
  
 `Non-authoritative answer:`
  
 `FQDN of the registered domain`
  
 `text=MS=ms########`
  
### <a name="validate-domain-ownership-in-microsoft-365"></a><span data-ttu-id="9ffb1-146">Microsoft 365 でドメインの所有権を検証する</span><span class="sxs-lookup"><span data-stu-id="9ffb1-146">Validate domain ownership in Microsoft 365</span></span>

<span data-ttu-id="9ffb1-147">この最後の手順では、公的登録済みドメインを所有していることを Microsoft 365 に検証します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-147">In this last step, you validate to Microsoft 365 that you own the publically registered domain.</span></span> <span data-ttu-id="9ffb1-148">この手順の後、Microsoft 365 は新しいドメイン名にルーティングされたトラフィックの受け入れを開始します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-148">After this step, Microsoft 365 will begin accepting traffic routed to the new domain name.</span></span> <span data-ttu-id="9ffb1-149">ドメインの作成と登録のプロセスを完了するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-149">To complete the domain creation and registration process, run this command.</span></span> 
  
```
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="9ffb1-150">このコマンドは出力を返しません。そのため、機能したことを確認するために、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-150">This command won't return any output, so to confirm that this worked, run this command.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

<span data-ttu-id="9ffb1-151">コマンドを実行すると、次のようなものが返されます。</span><span class="sxs-lookup"><span data-stu-id="9ffb1-151">This will return something like this</span></span>
  
||||
|:-----|:-----|:-----|
| `Name` <br/> | `Status` <br/> | `Authentication` <br/> |
| `FQDN of new domain` <br/> | `Verified` <br/> | `Managed` <br/> |
   
## <a name="see-also"></a><span data-ttu-id="9ffb1-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ffb1-152">See also</span></span>

#### 

[<span data-ttu-id="9ffb1-153">パートナーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="9ffb1-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

