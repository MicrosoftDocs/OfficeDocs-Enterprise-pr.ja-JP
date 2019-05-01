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
description: '概要: Microsoft office 365 コンポーネントおよび Office 365 government 製品の IPv6 サポートについて説明します。'
ms.openlocfilehash: 82af5c7659b3c16c8e92b45b65b6868a404eca23
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487754"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="e1684-103">Office 365 サービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="e1684-103">IPv6 support in Office 365 services</span></span>

 <span data-ttu-id="e1684-104">**概要**: Microsoft office 365 コンポーネントおよび Office 365 government 製品の IPv6 サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e1684-104">**Summary**: Describes IPv6 support in Microsoft Office 365 components and in Office 365 government offerings.</span></span>
  
<span data-ttu-id="e1684-105">Office 365 は IPv6 と IPv4 の両方をサポートしています。ただし、すべての Office 365 機能が IPv6 で完全に有効になっているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e1684-105">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6.</span></span> <span data-ttu-id="e1684-106">これは、Office 365 に接続するために IPv4 と IPv6 の両方を使用する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e1684-106">This means that you must use both IPv4 and IPv6 to connect to Office 365.</span></span> <span data-ttu-id="e1684-107">office 365 への送信トラフィックをフィルタリングする場合は、office 365 でサポートされる IPv6 アドレスの完全な一覧については、記事「 [office 365 url および IP アドレス範囲](urls-and-ip-address-ranges.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1684-107">If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span> <span data-ttu-id="e1684-108">ネットワークが構成され、適切な IPv6 アドレスが許可されたら、Microsoft ダウンロードセンターから[Office 365 IPv6 テスト計画](https://go.microsoft.com/fwlink/?LinkId=293447)をダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="e1684-108">After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
||
|:-----|
| <span data-ttu-id="e1684-109">この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1684-109">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="e1684-110">Office 365 サブスクリプションサービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="e1684-110">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="e1684-111">Exchange Online および IPv6</span><span class="sxs-lookup"><span data-stu-id="e1684-111">Exchange Online and IPv6</span></span>

<span data-ttu-id="e1684-112">Exchange Online への接続に使用するプログラムが ipv6 をサポートしている場合は、有線ネットワークとワイヤレスネットワークの両方で ipv6 を既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="e1684-112">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="e1684-113">Exchange Online への通信を制御するには、Office 365 の ip アドレスの範囲[と ip アドレス範囲](urls-and-ip-address-ranges.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1684-113">If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="e1684-114">SharePoint Online と IPv6</span><span class="sxs-lookup"><span data-stu-id="e1684-114">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="e1684-115">**Office 365 Government G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムが ipv6 をサポートしている場合は、既定で ipv6 の使用を試みます。</span><span class="sxs-lookup"><span data-stu-id="e1684-115">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="e1684-116">**パブリックマルチテナントクラウド**Microsoft は、お客様の要求で SharePoint Online の IPv6 を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e1684-116">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request.</span></span> <span data-ttu-id="e1684-117">組織の DNS インフラストラクチャには、CIDR で入力された IP アドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1684-117">You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure.</span></span> <span data-ttu-id="e1684-118">この DNS インフラストラクチャは、テナントに対して IPv6 を有効にするために他の組織と共有できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e1684-118">Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant.</span></span> <span data-ttu-id="e1684-119">ipv6 を有効にした後、SharePoint Online への接続に使用するプログラムが ipv6 をサポートしている場合は、ipv6 が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1684-119">After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="e1684-120">SharePoint Online への接続に使用するプログラムが ipv6 をサポートしている場合は、有線ネットワークとワイヤレスネットワークの両方で ipv6 を既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="e1684-120">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="e1684-121">SharePoint Online との通信を制御する場合は、「Office 365 の ip アドレスの範囲」の[url と ip アドレスの範囲](urls-and-ip-address-ranges.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1684-121">If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="e1684-122">**Office 365 Government G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムが ipv6 をサポートしている場合は、既定で ipv6 の使用を試みます。</span><span class="sxs-lookup"><span data-stu-id="e1684-122">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="e1684-123">Skype for business および IPv6</span><span class="sxs-lookup"><span data-stu-id="e1684-123">Skype for Business and IPv6</span></span>

<span data-ttu-id="e1684-124">Skype for business では IPv6 がサポートされておらず、有効にできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e1684-124">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="e1684-125">Exchange Online Protection および IPv6</span><span class="sxs-lookup"><span data-stu-id="e1684-125">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="e1684-126">Exchange Online Protection (EOP) は、転送がトランスポート層セキュリティプロトコルで行われている場合、IPv6 をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e1684-126">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol.</span></span> <span data-ttu-id="e1684-127">EOP の範囲については、 [Office 365 の url と IP アドレスの範囲](urls-and-ip-address-ranges.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1684-127">For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="e1684-128">Office 365 government 製品の IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="e1684-128">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="e1684-129">米国政府機関向けの office 365 IPv6 サポート (OMB) Memorandum は、経営部門および省庁の最高情報責任者、およびインターネットプロトコルバージョン 6 (IPv6) の連邦政府機関による採用に準拠しています。) memorandum。</span><span class="sxs-lookup"><span data-stu-id="e1684-129">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum.</span></span> <span data-ttu-id="e1684-130">[Microsoft Office 365 for government](https://go.microsoft.com/fwlink/p/?LinkId=325414)は、政府機関のデータを分離されたコミュニティクラウドに保存するマルチテナントサービスです。</span><span class="sxs-lookup"><span data-stu-id="e1684-130">[Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud.</span></span> <span data-ttu-id="e1684-131">他の Office 365 製品と同様に、Exchange Online、Skype for business、SharePoint Online、office Professional Plus など、生産性とコラボレーションのサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e1684-131">Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office Professional Plus.</span></span> 

<span data-ttu-id="e1684-132">Microsoft Office 365 government のサービスは2013以降にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="e1684-132">The Microsoft Office 365 government offerings apply only for 2013 and later.</span></span> <span data-ttu-id="e1684-133">office 365 government 製品の詳細については、「米国政府機関[向け office 365 の発表: US government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1684-133">For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414).</span></span> <span data-ttu-id="e1684-134">国際通話のトラフィック (ITAR) とは、米国の[munitions リスト (usml)](https://go.microsoft.com/fwlink/p/?LinkId=325415)での、防衛関連の記事およびサービスのエクスポートとインポートを制御する米国政府規制のセットです。</span><span class="sxs-lookup"><span data-stu-id="e1684-134">International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="e1684-135">microsoft Office 365 for enterprise では、連邦情報セキュリティを必要とする米国連邦機関のセキュリティ、プライバシー、および規制コンプライアンスの要件をサポートする microsoft の生産性向上ソリューションに専用のホスティングサービスを提供しています。ITAR の対象となる管理 (FISMA) 証明書と商用エンティティ。</span><span class="sxs-lookup"><span data-stu-id="e1684-135">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="e1684-136">IPv6 および Office 365 を使用する場合の考慮事項</span><span class="sxs-lookup"><span data-stu-id="e1684-136">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="e1684-137">IPv6 を無効にしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e1684-137">We recommend that you do not disable IPv6.</span></span> <span data-ttu-id="e1684-138">詳細については、この[ガイダンス記事](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1684-138">For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users).</span></span> <span data-ttu-id="e1684-139">ネットワークで使用されている IP バージョンを確認するには、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="e1684-139">To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="e1684-140">コマンドプロンプトでの**IPConfig**コマンドの表示に "ipv6 address" または "Temporary ipv6 address" という名前の行が含まれている場合は、環境内に ipv6 が存在します。</span><span class="sxs-lookup"><span data-stu-id="e1684-140">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="e1684-141">すべての ipv6 アドレスが "fe80" で始まり、"リンクローカル ipv6 アドレス" という名前の行に対応している場合は、環境内に ipv6 がありません。</span><span class="sxs-lookup"><span data-stu-id="e1684-141">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="e1684-142">ネットワークには、次のような考慮事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e1684-142">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="e1684-143">パブリックサブスクリプションサービスは、IPv6 経由のクレジットカードによる購入をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e1684-143">The public subscription service does not support purchase by credit card over IPv6.</span></span> <span data-ttu-id="e1684-144">これは、自治体がエンタープライズアグリーメント (EA) ライセンスを所有しているため、Government Community Cloud (GCC) には適用されません。</span><span class="sxs-lookup"><span data-stu-id="e1684-144">This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="e1684-145">IPv6 は、一部の Rights Management Services (RMS) シナリオをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e1684-145">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="e1684-146">blackberry は ipv6 をサポートしていないため、ipv6 は blackberry ® Enterprise Server (be) をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e1684-146">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="e1684-147">office 365 で Active Directory フェデレーションサービス (ad fs) を使用している場合は、IPv6 を使用して ad fs ネットワークエンドポイントを office 365 にアドバタイズすることはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e1684-147">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported.</span></span> <span data-ttu-id="e1684-148">Exchange Online を使用している場合は、AD FS DNS エントリに AAAA レコードを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="e1684-148">You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="e1684-149">ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="e1684-149">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1684-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1684-150">See also</span></span>

<span data-ttu-id="e1684-151">[IPv6 の学習ロードマップ](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="e1684-151">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="e1684-152">IPv6 サバイバルガイド</span><span class="sxs-lookup"><span data-stu-id="e1684-152">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
