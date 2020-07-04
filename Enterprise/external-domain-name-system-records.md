---
title: Office 365 の外部ドメイン ネーム システムのレコード
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/21/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: '概要: Office 365 の展開を計画するときに使用する DNS レコードのリファレンス リスト。'
ms.openlocfilehash: d0804cec4ce2c15345a9c4ddc83525d1961f8db4
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44996541"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Office 365 の外部ドメイン ネーム システムのレコード

|||
|:-----|:-----|
|![ドメイン](media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)|**Want to see a customized list of DNS records for your Office 365 organization?** You can [find the info you need to create Office 365 DNS records](https://support.office.microsoft.com/article/Gather-the-information-you-need-to-create-Office-365-DNS-records-77f90d4a-dc7f-4f09-8972-c1b03ea85a67) for your domain in Office 365.  <br/> **Need step-by-step help to add these records at your domain's DNS host, such as GoDaddy or eNom?** [Find links to step-by-step instructions for many popular DNS hosts](https://go.microsoft.com/fwlink/?LinkId=286745). <br/>  **Sticking around to use the reference list for your own custom deployment?** The below list should be used as a reference for your custom Office 365 deployment. You will need to select which records apply to your organization and fill in the appropriate values. <br/> 「[Office 365 のネットワーク計画とパフォーマンス チューニング](https://aka.ms/tune)」**に戻ります**。  <br/> |

Often the SPF and MX records are the hardest to figure out. We've updated our SPF records guidance at the end of this article. The important thing to remember is that _you can only have a single SPF record for your domain_. You can have multiple MX records; however, that can cause problems for mail delivery. Having a single MX record that directs email to one mail system removes many potential problems.
  
The sections below are organized by service in Office 365. To see a customized list of the Office 365 DNS records for your domain, sign in to Office 365 and [Gather the information you need to create Office 365 DNS records](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Office 365 に必要な外部の DNS レコード (コア サービス)
<a name="BKMK_ReqdCore"> </a>

Every Office 365 customer needs to add two records to their external DNS. The first CNAME record ensures that Office 365 can direct workstations to authenticate with the appropriate identity platform. The second required record is to prove you own your domain name.
  
||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**CNAME** <br/> **(スイート)** <br/> |Used by Office 365 to direct authentication to the correct identity platform. [More information](https://go.microsoft.com/fwlink/p/?LinkId=322005) <br/> **注:** この CNAME は、21Vianet が運営する Office 365 にのみ適用されます。   |**エイリアス:** msoid  <br/> **対象:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(ドメインの確認)** <br/> |Used by Office 365 to verify only that you own your domain. It doesn't affect anything else.  <br/> |**ホスト:** @ (または、一部の DNS ホスティング プロバイダーでは自分のドメイン名)  <br/> **TXT 値:** Office 365 "_から提供されるテキスト文字列_"  <br/> このレコードを作成するために使用する値は、Office 365 の **ドメイン セットアップ ウィザード** で指定されます。  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Office 365 でのメールに必要な外部 DNS レコード (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Email in Office 365 requires several different records. The three primary records that all customers should use are the Autodiscover, MX, and SPF records.
  
- **自動検出レコード**では、クライアント コンピューターは自動的に Exchange を検索し、クライアントを正しく構成することができます。

- **The MX record** tells other mail systems where to send email for your domain. **Note:** When you change your email to Office 365, by updating your domain's MX record, ALL email sent to that domain will start coming to Office 365.  
一部のメール アドレスのみを Office 365 に切り替える場合 [カスタム ドメインの少数のメール アドレスで Office 365 を試験運用する](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7) ことができます。

- **SPF の TXT レコード** は、ユーザーのメールを送信するサーバーが承認されていることを検証するために受信者のメール システムで使用されます。 これにより、メールのスプーフィングやフィッシングを防ぎます。 レコードに含める内容については、この記事の [SPF に必要な外部 DNS レコード](external-domain-name-system-records.md#BKMK_SPFrecords) を確認してください。

Exchange フェデレーションを使用しているメールのお客様は、表の一番下に一覧表示されている追加の CNAME および TXT レコードも必要です。
  
||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**CNAME** <br/> **(Exchange Online)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for users.  <br/> |**エイリアス:** Autodiscover  <br/> **リンク先:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |ドメインへの受信メールを Office 365 の Exchange Online サービスへ送信します。  <br/> [!NOTE] 電子メールが Exchange Online に流れたら、古いシステムを指定している MX レコードを削除する必要があります。   |**ドメイン:** 例: contoso.com  <br/> **対象の電子メールサーバー:** \<MX token\> 。mail.protection.outlook.com  <br/> **優先度:** その他すべての MX レコードより下 (これにより、メールが Exchange Online に確実に配信されます) - 例: 1 または "low"  <br/>  次の \<MX token\> 手順を実行して、を検索します。  <br/>  Office 365 にサインインし、[Office 365 管理] \> [ドメイン] に移動します。  <br/>  ドメインの [アクション] 列で [問題の修正] を選択します。  <br/>  [MX レコード] セクションで、[何を修正しますか?] を選択します。  <br/>  MX レコードを更新するには、このページに表示される指示に従います。  <br/> [MX 優先度とは何ですか。](https://go.microsoft.com/fwlink/p/?LinkId=396471) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Helps to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.  <br/> |[SPF に必要な外部 DNS レコード](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange フェデレーション)** <br/> |ハイブリッド展開のために Exchange フェデレーションに使用します。  <br/> |**TXT レコード 1:** たとえば、contoso.com および関連するカスタム生成されたもの、ドメイン証明ハッシュ テキスト (たとえば、Y96nu89138789315669824)  <br/> **TXT レコード 2:** たとえば、exchangedelegation.contoso.com および関連するカスタム生成されたもの、ドメイン証明ハッシュ テキスト (たとえば、Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange フェデレーション)** <br/> |Helps Outlook clients to easily connect to the Exchange Online service by using the Autodiscover service when your company is using Exchange federation. Autodiscover automatically finds the correct Exchange Server host and configures Outlook for your users.  <br/> |**エイリアス:** 例: Autodiscover.service.contoso.com  <br/> **リンク先:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Skype for Business Online に必要な外部 DNS レコード
<a name="BKMK_ReqdCore"> </a>

「[Office 365 の URL と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)」を使用して、ネットワークが正しく構成されていることを確認する場合、特定の手順を実行する必要があります。

> [!NOTE]
> これらの DNS レコードは、特に特定のフェデレーションの問題が発生する可能性のあるハイブリッド Teams と Skype for Business Online シナリオの Teams にも適用されます。
  
||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Allows your Office 365 domain to share instant messaging (IM) features with external clients by enabling SIP federation. Read more about [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**サービス:** sipfederationtls  <br/> **プロトコル:** TCP  <br/> **優先度:** 100  <br/> **重み:** 1  <br/> **ポート:** 5061  <br/> **リンク先:** sipfed.online.lync.com  <br/> **注:** ファイアウォールまたはプロキシ サーバーが外部 DNS の SRV ルックアップをブロックする場合、内部 DNS レコードにこのレコードを追加する必要があります。   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Lync クライアント間の情報の流れを調整するために Skype for Business で使用します。  <br/> |**サービス:** sip  <br/> **プロトコル:** TLS  <br/> **優先度:** 100  <br/> **重み:** 1  <br/> **ポート:** 443  <br/> **リンク先:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Skype for Business Online サービスを見つけてサインインするのを支援するために Lync クライアントで使用します。  <br/> |**エイリアス:** sip  <br/> **リンク先:** sipdir.online.lync.com  <br/> 詳しくは、「[Office 365 URL および IP アドレス範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO)」を参照してください。  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Skype for Business Online サービスを見つけてサインインするのを支援するために Lync モバイル クライアントで使用します。  <br/> |**エイリアス:** lyncdiscover  <br/> **リンク先:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Office 365 シングル サインオンに必要な外部 DNS レコード
<a name="BKMK_ReqdCore"> </a>

||||
|:-----|:-----|:-----|
|**DNS レコード** <br/> |**用途** <br/> |**使用する値** <br/> |
|**ホスト (A)** <br/> |Used for single sign-on (SSO). It provides the endpoint for your off-premises users (and on-premises users, if you like) to connect to your Active Directory Federation Services (AD FS) federation server proxies or load-balanced virtual IP (VIP).  <br/> |**対象:** 例: sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>SPF に必要な外部 DNS レコード
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF is designed to help prevent spoofing, but there are spoofing techniques that SPF cannot protect against. In order to protect against these, once you have set up SPF, you should also configure DKIM and DMARC for Office 365. To get started, see [Use DKIM to validate outbound email sent from your domain in Office 365](https://technet.microsoft.com/library/mt695945%28v=exchg.150%29.aspx). Next, see [Use DMARC to validate email in Office 365](https://technet.microsoft.com/library/mt734386%28v=exchg.150%29.aspx).
  
SPF records are TXT records that help to prevent other people from using your domain to send spam or other malicious email. Sender policy framework (SPF) records work by identifying the servers that are authorized to send email from your domain.
  
You can only have one SPF record (that is, a TXT record that defines SPF) for your domain. That single record can have a few different inclusions but the total DNS lookups that result can't be more than 10 (this helps prevent denial of service attacks). See the table and other examples below to help you create or update the right SPF record values for your environment.
  
### <a name="structure-of-an-spf-record"></a>SPF レコードの構造

All SPF records contain three parts: the declaration that it is an SPF record, the domains, and IP addresses that should be sending email, and an enforcement rule. You need all three in a valid SPF record. Here's an example of a common SPF record for Office 365 when you use only Exchange Online email:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

ドメインからメールを受信するメール システムは、この SPF レコードを確認し、メッセージを送信したメール サーバーが Office 365 サーバーの場合はメッセージが承認されます。 メッセージを送信したサーバーが古いメールシステムか、インターネット上の悪意のあるシステムだった場合、SPF チェックが失敗し、メッセージが配信されないことがあります。 これにより、スプーフィングやフィッシング メッセージを防ぐことができます。
  
### <a name="choose-the-spf-record-structure-you-need"></a>必要な SPF レコードの構造を選択する

Office 365 に対して Exchange Online メールだけを使用するのではないシナリオの場合は (たとえば、SharePoint Online から送信されたメールも使用する場合)、次の表を使用して、レコードの値に含めるものを決定します。
  
> [!NOTE]
> If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656). You can also learn much more about how SPF works with Office 365 by reading [How Office 365 uses Sender Policy Framework (SPF) to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787065).
  
|||||
|:-----|:-----|:-----|:-----|
||使用対象  <br/> |用途  <br/> |以下を追加します。  <br/> |
|1   <br/> |すべてのメール システム (必須)  <br/> |この値で始まるすべての SPF レコード  <br/> |v=spf1  <br/> |
|2   <br/> |Exchange Online (一般的)  <br/> |Exchange Online だけで使用します  <br/> |include:spf.protection.outlook.com  <br/> |
|3   <br/> |サード パーティのメール システム (あまり一般的でない)  <br/> ||\<email system like mail.contoso.com\> の内容を含めます。  <br/> |
|4   <br/> |オンプレミスのメール システム (あまり一般的でない)  <br/> |Exchange Online Protection または Exchange Online と別のメール システムを使用している場合に使用します  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> \<mail.contoso.com\> の内容を含めます。  <br/> 山かっこ (\<\>) 内の値は、自分のドメインにメールを送信する他のメール システムにする必要があります。  <br/> |
|5   <br/> |すべてのメール システム (必須)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>例: 既存の SPF レコードへの追加
<a name="bkmk_addtospf"> </a>

If you already have an SPF record, you'll need to add or update values for Office 365. For example, say your existing SPF record for contoso.com is this:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

これで、Office 365 用の SPF レコードを更新しています。 必要な値を含む SPF レコードがあるように、現在のレコードを編集します。 Office 365 の場合は、"spf.protection.outlook.com"。
  
正しい:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

正しくない:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>一般的な SPF 値の他の例
<a name="bkmk_addtospf"> </a>

Office 365 スイート全体を使用していて、ユーザーの代わりに MailChimp を使用してマーケティング電子メールを送信する場合、contoso.com の SPF レコードは次のようになります。これは、上記の表の行1、3、5を使用します。 行1と5が必要であることに注意してください。
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

代わりに、電子メールが Office 365 およびオンプレミスのメール システムの両方から送信される Exchange のハイブリッド構成がある場合、contoso.com の SPF レコードは次のようになることがあります。
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

These are some common examples that can help you adapt your existing SPF record when you add your domain to Office 365 for email. If you have a complicated scenario that includes, for example, edge email servers for managing email traffic across your firewall, you'll have a more detailed SPF record to set up. Learn how: [Set up SPF records in Office 365 to help prevent spoofing](https://go.microsoft.com/fwlink/?LinkId=787656).
  
ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365edns](https://aka.ms/o365edns)
