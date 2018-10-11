---
title: Office 365 サービスでの IPv6 サポート
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: '概要: は、Microsoft Office 365 コンポーネントと Office 365 の政府サービスの IPv6 のサポートについて説明します。'
ms.openlocfilehash: ed06f1eac3c6a3d631445db1d623bd25c62a309c
ms.sourcegitcommit: ae7f2087d51698d3c5ef371888278544a7046205
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2018
ms.locfileid: "25493832"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="2ebfa-103">Office 365 サービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="2ebfa-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="2ebfa-104">**概要**: Microsoft Office 365 コンポーネントと Office 365 の政府サービスの IPv6 のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="2ebfa-p101">Office 365 は、IPv6 と IPv4 の両方はサポートしています。ただし、すべての Office 365 の機能は完全に ipv6 が有効になります。つまり、Office 365 への接続に IPv4 と IPv6 の両方を使用する必要があります。Office 365 へ送信されたトラフィックをフィルターする場合、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の記事で Office 365 でサポートされている IPv6 アドレスの完全な一覧を参照しています。ネットワークを構成して、適切な IPv6 アドレスが許可されて後からダウンロードできます[Office 365 の IPv6 のテスト計画](https://go.microsoft.com/fwlink/?LinkId=293447)を Microsoft ダウンロード センター。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p101">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6. This means that you must use both IPv4 and IPv6 to connect to Office 365. If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744). After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="2ebfa-109">この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="2ebfa-110">Office 365 サブスクリプション サービスで IPv6 のサポート</span><span class="sxs-lookup"><span data-stu-id="2ebfa-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="2ebfa-111">Exchange Online と IPv6</span><span class="sxs-lookup"><span data-stu-id="2ebfa-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="2ebfa-p102">Exchange Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、IPv6 をワイヤード (有線) とワイヤレスの両方のネットワークでは、既定で使います。Exchange Online への通信を制御する場合は、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の IP アドレスの範囲を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p102">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="2ebfa-114">SharePoint Online と IPv6</span><span class="sxs-lookup"><span data-stu-id="2ebfa-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="2ebfa-115">**Office 365 の政府 G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、既定で IPv6 を使用するを試みます。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="2ebfa-p103">**マルチ テナント型のパブリック クラウド**マイクロソフトでは、ご要望により SharePoint のオンラインの IPv6 を有効にします。CIDR 表記の IP アドレスを組織の DNS インフラストラクチャを提供する必要があります。この DNS インフラストラクチャを ipv6 の場合、テナントを有効にするには、他の組織と共有できないことに留意してください。IPv6 を有効にする、SharePoint Online への接続に使用するプログラムは、IPv6 をサポートしている場合、既定で IPv6 を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p103">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request. You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure. Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant. After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="2ebfa-p104">SharePoint Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、ワイヤード (有線) とワイヤレスの両方のネットワークでは、既定で IPv6 が使用されます。SharePoint Online への通信を制御する場合は、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の IP アドレスの範囲を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p104">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks. If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
 <span data-ttu-id="2ebfa-122">**Office 365 の政府 G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、既定で IPv6 を使用するを試みます。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="2ebfa-123">ビジネスと IPv6 の Skype</span><span class="sxs-lookup"><span data-stu-id="2ebfa-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="2ebfa-p105">マイクロソフトはマルチ テナント型のパブリック クラウドと Office 365 政府 G1/G3/G4 と K1 のサブスクリプションでは、ご要望のビジネス用の Skype の IPv6 を有効になります。それを有効にする、ビジネスの Skype への接続に使用するプログラムは、IPv6 をサポートしている場合、既定で IPv6 を使用します。ビジネス用の Skype への通信を制御する場合は、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の IP アドレスの範囲を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p105">Microsoft will enable IPv6 for Skype for Business at your request in the public multi-tenant cloud and in Office 365 Government G1/G3/G4/K1 subscriptions. After it's enabled, if the program that you use to connect to Skype for Business supports IPv6, it will use IPv6 by default. If you want to control communications to Skype for Business, use the IP address ranges in [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
<span data-ttu-id="2ebfa-127">IPv6 は、すべての地域では利用可能ではありませんし、マイクロソフトは、この時点で、テナントのアクティブ化できない場合があります注意してください。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-127">Please be aware IPv6 is not available in all regions and Microsoft may not be able to activate it for your Tenant at this time.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="2ebfa-128">Exchange Online Protection と IPv6</span><span class="sxs-lookup"><span data-stu-id="2ebfa-128">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="2ebfa-p106">Exchange オンライン保護 (EOP) は、トランスポート層セキュリティ プロトコル経由で転送が発生した場合、IPv6 をサポートしています。EOP を範囲のセルには、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p106">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol. For the EOP range, use [Office 365 URLs and IP address ranges](https://go.microsoft.com/fwlink/?LinkId=293744).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="2ebfa-131">Office 365 Government 製品の IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="2ebfa-131">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="2ebfa-p107">経営部門や機関などと同様の連邦政府機関採用のインターネット プロトコル バージョン 6 (IPv6 の最高情報責任者の Office の管理および予算 (OMB) のメモに、政府の製品の IPv6 サポートを office 365 に準拠しています。) メモします。[政府向けの Microsoft Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414)は、分離されたコミュニティ クラウドで米国政府のデータが格納されているマルチ テナント サービスです。他の Office 365 の製品と同じように Exchange Online、Skype のビジネス、SharePoint Online では、Office Professional Plus を含む、生産性とコラボレーションのサービスを提供します。2013 についてのみ、後で、Microsoft Office 365 の政府サービスが適用されます。Office 365 の政府サービスの詳細についてを参照してください[政府向けの Office 365 の発表: A 米国政府のコミュニティ クラウド](https://go.microsoft.com/fwlink/p/?LinkId=325414)。国際トラフィックのアームの規制 (ITAR) では、防御に関連する資料と[米国兵器リスト (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)上のサービスのインポートとエクスポートを制御する米国政府の規制のセットです。企業向けの Microsoft Office 365 には、マイクロソフトの生産性をサポートするソリューション、セキュリティ、プライバシー、および規制へのコンプライアンス要件の連邦政府機関の連邦政府の情報セキュリティを必要とするための専用のホスティング サービスが用意されています。管理 (FISMA) 証明書および営利団体は、ITAR にさらされます。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p107">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum. [Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud. Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus. The Microsoft Office 365 government offerings apply only for 2013 and later. For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415). Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="2ebfa-139">IPv6 および Office 365 の使用に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="2ebfa-139">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="2ebfa-p108">IPv6 を無効にしないことをお勧めします。詳細についてを参照してください[Microsoft Windows の IPv6: よく寄せられる質問](https://go.microsoft.com/fwlink/p/?LinkId=325418)。ネットワーク上にどのような IP のバージョンを使用されているを確認するのには、以下を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p108">We recommend that you do not disable IPv6. For more information, see [IPv6 for Microsoft Windows: Frequently Asked Questions](https://go.microsoft.com/fwlink/p/?LinkId=325418). To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="2ebfa-143">コマンド プロンプトで IPConfig コマンドの表示に「IPv6 アドレス」または「一時的 IPv6 アドレス」という名前の行が含まれている場合、環境内で IPv6 がいます。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-143">If the display of the IPConfig command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="2ebfa-144">すべての IPv6 アドレス"fe80"で、「リンク ローカル IPv6 アドレス」をという名前行に対応している場合は、環境内で IPv6 がありません。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-144">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="2ebfa-145">以下の事項がネットワークに適用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-145">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="2ebfa-p109">パブリック サブスクリプション サービスでは、IPv6 を介したクレジット カードでの購入はサポートされません。ただし、政府機関コミュニティ クラウド (GCC) の場合、政府機関には Enterprise Agreement (EA) ライセンスがあるため、これは適用されません。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p109">The public subscription service does not support purchase by credit card over IPv6. This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="2ebfa-148">IPv6 では、Rights Management サービス (RMS) の一部のシナリオはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-148">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="2ebfa-149">IPv6 では、BlackBerry は、IPv6 をサポートしていませんので BlackBerry® エンタープライズ サーバー (BE) をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-149">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="2ebfa-p110">を Office 365 を Active Directory フェデレーション サービス (AD FS) を使用する場合は、Office 365 AD FS ネットワーク エンドポイントを提供する IPv6 を使用してサポートされていません。、Exchange Online を使用する場合、AAAA レコードを AD FS の DNS エントリに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ebfa-p110">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported. You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="2ebfa-152">ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="2ebfa-152">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2ebfa-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ebfa-153">See also</span></span>

[<span data-ttu-id="2ebfa-154">マイクロソフトのテクノロジ ポジション ペーパー</span><span class="sxs-lookup"><span data-stu-id="2ebfa-154">Microsoft Technology Position Paper</span></span>](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[<span data-ttu-id="2ebfa-155">TCP/IP v4 と v6</span><span class="sxs-lookup"><span data-stu-id="2ebfa-155">TCP/IP v4 and v6</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[<span data-ttu-id="2ebfa-156">IPv6 のサバイバル ガイド</span><span class="sxs-lookup"><span data-stu-id="2ebfa-156">IPv6 Survival Guide</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=237480)
