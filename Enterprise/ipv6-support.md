---
title: Office 365 サービスでの IPv6 サポート
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/10/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: '概要: Microsoft Office 365 コンポーネントおよび Office 365 government 製品の IPv6 サポートについて説明します。'
ms.openlocfilehash: 13fd1cfef26f5e69c87f650c46f71071b72f2d15
ms.sourcegitcommit: 3aa6c61242c5691e3180a474ad059bd84c86dc9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2020
ms.locfileid: "43206544"
---
# <a name="ipv6-support-in-office-365-services"></a><span data-ttu-id="30154-103">Office 365 サービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="30154-103">IPv6 support in Office 365 services</span></span>

<span data-ttu-id="30154-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="30154-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="30154-105">Office 365 は IPv6 と IPv4 の両方をサポートしています。ただし、すべての Office 365 機能が IPv6 で完全に有効になっているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="30154-105">Office 365 supports both IPv6 and IPv4; however, not all Office 365 features are fully enabled with IPv6.</span></span> <span data-ttu-id="30154-106">これは、Office 365 に接続するために IPv4 と IPv6 の両方を使用する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="30154-106">This means that you must use both IPv4 and IPv6 to connect to Office 365.</span></span> <span data-ttu-id="30154-107">Office 365 への送信トラフィックをフィルタリングする場合は、office 365 でサポートされる IPv6 アドレスの完全な一覧については、記事「 [office 365 url および IP アドレス範囲](urls-and-ip-address-ranges.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30154-107">If you are filtering your outbound traffic to Office 365, the full list of IPv6 addresses that are supported by Office 365 can be found in the article [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span> <span data-ttu-id="30154-108">ネットワークが構成され、適切な IPv6 アドレスが許可されたら、Microsoft ダウンロードセンターから[Office 365 IPv6 テスト計画](https://go.microsoft.com/fwlink/?LinkId=293447)をダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="30154-108">After your network is configured and the appropriate IPv6 addresses are allowed, you can download the [Office 365 IPv6 test plan](https://go.microsoft.com/fwlink/?LinkId=293447) from the Microsoft Download Center.</span></span>
  
## <a name="ipv6-support-in-office-365-subscription-service"></a><span data-ttu-id="30154-109">Office 365 サブスクリプションサービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="30154-109">IPv6 support in Office 365 subscription service</span></span>

### <a name="exchange-online-and-ipv6"></a><span data-ttu-id="30154-110">Exchange Online および IPv6</span><span class="sxs-lookup"><span data-stu-id="30154-110">Exchange Online and IPv6</span></span>

<span data-ttu-id="30154-111">Exchange Online への接続に使用するプログラムが IPv6 をサポートしている場合は、有線ネットワークとワイヤレスネットワークの両方で IPv6 を既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="30154-111">If the program that you use to connect to Exchange Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="30154-112">Exchange Online への通信を制御するには、Office 365 の IP アドレスの範囲[と ip アドレス範囲](urls-and-ip-address-ranges.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="30154-112">If you want to control communications to Exchange Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="sharepoint-online-and-ipv6"></a><span data-ttu-id="30154-113">SharePoint Online と IPv6</span><span class="sxs-lookup"><span data-stu-id="30154-113">SharePoint Online and IPv6</span></span>

 <span data-ttu-id="30154-114">**Office 365 Government G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、既定で IPv6 の使用を試みます。</span><span class="sxs-lookup"><span data-stu-id="30154-114">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
 <span data-ttu-id="30154-115">**パブリックマルチテナントクラウド**Microsoft は、お客様の要求で SharePoint Online の IPv6 を有効にします。</span><span class="sxs-lookup"><span data-stu-id="30154-115">**Public multi-tenant cloud** Microsoft enables SharePoint Online IPv6 at your request.</span></span> <span data-ttu-id="30154-116">組織の DNS インフラストラクチャには、CIDR で入力された IP アドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30154-116">You need to provide the CIDR notated IP addresses for your organization's DNS infrastructure.</span></span> <span data-ttu-id="30154-117">この DNS インフラストラクチャは、テナントに対して IPv6 を有効にするために他の組織と共有できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="30154-117">Keep in mind that this DNS infrastructure can't be shared by other organizations for IPv6 to be enabled for your tenant.</span></span> <span data-ttu-id="30154-118">IPv6 を有効にした後、SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、ipv6 が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="30154-118">After IPv6 is enabled, if the program that you use to connect to SharePoint Online supports IPv6, it uses IPv6 by default.</span></span>
  
<span data-ttu-id="30154-119">SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、有線ネットワークとワイヤレスネットワークの両方で IPv6 を既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="30154-119">If the program that you use to connect to SharePoint Online supports IPv6, it will use IPv6 by default on both wired and wireless networks.</span></span> <span data-ttu-id="30154-120">SharePoint Online との通信を制御する場合は、「Office 365 の IP アドレスの範囲」の[url と ip アドレスの範囲](urls-and-ip-address-ranges.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="30154-120">If you want to control communications to SharePoint Online, use the IP address ranges in [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
 <span data-ttu-id="30154-121">**Office 365 Government G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、既定で IPv6 の使用を試みます。</span><span class="sxs-lookup"><span data-stu-id="30154-121">**Office 365 Government G1/G3/G4/K1** If the program that you use to connect to SharePoint Online supports IPv6, it will attempt to use IPv6 by default.</span></span>
  
### <a name="skype-for-business-and-ipv6"></a><span data-ttu-id="30154-122">Skype for Business および IPv6</span><span class="sxs-lookup"><span data-stu-id="30154-122">Skype for Business and IPv6</span></span>

<span data-ttu-id="30154-123">Skype for Business では IPv6 がサポートされておらず、有効にできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="30154-123">Please be aware IPv6 is not supported in Skype for Business and can no longer be enabled.</span></span>
  
### <a name="exchange-online-protection-and-ipv6"></a><span data-ttu-id="30154-124">Exchange Online Protection および IPv6</span><span class="sxs-lookup"><span data-stu-id="30154-124">Exchange Online Protection and IPv6</span></span>

<span data-ttu-id="30154-125">Exchange Online Protection (EOP) は、転送がトランスポート層セキュリティプロトコルで行われている場合、IPv6 をサポートします。</span><span class="sxs-lookup"><span data-stu-id="30154-125">Exchange Online Protection (EOP) supports IPv6 if the transmission occurs over Transport Layer Security Protocol.</span></span> <span data-ttu-id="30154-126">EOP の範囲については、 [Office 365 の url と IP アドレスの範囲](urls-and-ip-address-ranges.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="30154-126">For the EOP range, use [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>
  
### <a name="ipv6-support-for-office-365-government-offerings"></a><span data-ttu-id="30154-127">Office 365 government 製品の IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="30154-127">IPv6 support for Office 365 government offerings</span></span>

<span data-ttu-id="30154-128">Office 365 の IPv6 サポートは、経営部門および省庁の最高情報責任者、およびインターネットプロトコルバージョン 6 (IPv6) Memorandum の連邦政府機関による管理と予算 (OMB) Memorandum のオフィスに準拠しています。</span><span class="sxs-lookup"><span data-stu-id="30154-128">Office 365 IPv6 support for government offerings conforms to the Office of Management and Budget (OMB) Memorandum for Chief Information Officers of Executive Departments and Agencies, as well as the Federal Government Adoption of Internet Protocol Version 6 (IPv6) memorandum.</span></span> <span data-ttu-id="30154-129">[Microsoft Office 365 For government](https://go.microsoft.com/fwlink/p/?LinkId=325414)は、政府機関のデータを分離されたコミュニティクラウドに保存するマルチテナントサービスです。</span><span class="sxs-lookup"><span data-stu-id="30154-129">[Microsoft Office 365 for Government](https://go.microsoft.com/fwlink/p/?LinkId=325414) is a multi-tenant service that stores US government data in a segregated community cloud.</span></span> <span data-ttu-id="30154-130">他の Office 365 製品と同様に、Exchange Online、Skype for Business、SharePoint Online、Office 365 ProPlus を含む、生産性とコラボレーションのサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="30154-130">Like other Office 365 offerings, it provides productivity and collaboration services, including Exchange Online, Skype for Business, SharePoint Online, and Office 365 ProPlus.</span></span> 

<span data-ttu-id="30154-131">Microsoft Office 365 government のサービスは2013以降にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="30154-131">The Microsoft Office 365 government offerings apply only for 2013 and later.</span></span> <span data-ttu-id="30154-132">Office 365 government 製品の詳細については、「米国政府機関[向け office 365 の発表: US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30154-132">For more information about the Office 365 government offerings, see [Announcing Office 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414).</span></span> <span data-ttu-id="30154-133">国際通話のトラフィック (ITAR) とは、米国の[Munitions リスト (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)での、防衛関連の記事およびサービスのエクスポートとインポートを制御する米国政府規制のセットです。</span><span class="sxs-lookup"><span data-stu-id="30154-133">International Traffic in Arms Regulations (ITAR) is a set of US government regulations that control the export and import of defense-related articles and services on the [United States Munitions List (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415).</span></span> 

<span data-ttu-id="30154-134">Microsoft Office 365 for enterprise では、米国連邦政府機関向けのセキュリティ、プライバシー、および規制コンプライアンスの要件をサポートする Microsoft の生産性向上ソリューション専用のホスティングサービスを提供しています。連邦情報セキュリティ管理 (FISMA) 証明書と商用エンティティが ITAR に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="30154-134">Microsoft Office 365 for Enterprises provides dedicated hosting services for Microsoft productivity solutions that support the security, privacy, and regulatory compliance requirements for US federal agencies requiring Federal Information Security Management (FISMA) certification and commercial entities subject to ITAR.</span></span>
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a><span data-ttu-id="30154-135">IPv6 および Office 365 を使用する場合の考慮事項</span><span class="sxs-lookup"><span data-stu-id="30154-135">Things to consider when using IPv6 and Office 365</span></span>

<span data-ttu-id="30154-136">IPv6 を無効にしないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="30154-136">We recommend that you do not disable IPv6.</span></span> <span data-ttu-id="30154-137">詳細については、この[ガイダンス記事](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30154-137">For more information, see this [guidance article](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users).</span></span> <span data-ttu-id="30154-138">ネットワークで使用されている IP バージョンを確認するには、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="30154-138">To determine what IP versions are being used on your network, consider the following:</span></span>
  
- <span data-ttu-id="30154-139">コマンドプロンプトでの**IPConfig**コマンドの表示に "ipv6 address" または "Temporary ipv6 address" という名前の行が含まれている場合は、環境内に ipv6 が存在します。</span><span class="sxs-lookup"><span data-stu-id="30154-139">If the display of the **IPConfig** command at the command prompt contains rows named "IPv6 Address" or "Temporary IPv6 Address," you have IPv6 in your environment.</span></span>

- <span data-ttu-id="30154-140">すべての IPv6 アドレスが "fe80" で始まり、"リンクローカル IPv6 アドレス" という名前の行に対応している場合は、環境内に IPv6 がありません。</span><span class="sxs-lookup"><span data-stu-id="30154-140">If all the IPv6 addresses begin with "fe80" and correspond to rows named "Link-Local IPv6 Address," you don't have IPv6 in your environment.</span></span>

<span data-ttu-id="30154-141">ネットワークには、次のような考慮事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="30154-141">These considerations might apply to your network:</span></span>
  
- <span data-ttu-id="30154-142">パブリックサブスクリプションサービスは、IPv6 経由のクレジットカードによる購入をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="30154-142">The public subscription service does not support purchase by credit card over IPv6.</span></span> <span data-ttu-id="30154-143">これは、自治体がエンタープライズアグリーメント (EA) ライセンスを所有しているため、Government Community Cloud (GCC) には適用されません。</span><span class="sxs-lookup"><span data-stu-id="30154-143">This does not apply to the Government Community Cloud (GCC) because governments have Enterprise Agreement (EA) licensing.</span></span>

- <span data-ttu-id="30154-144">IPv6 は、一部の Rights Management Services (RMS) シナリオをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="30154-144">IPv6 does not support some Rights Management Services (RMS) scenarios.</span></span>

- <span data-ttu-id="30154-145">BlackBerry は IPv6 をサポートしていないため、IPv6 は BlackBerry® Enterprise Server (BE) をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="30154-145">IPv6 does not support BlackBerry® Enterprise Server (BES) because BlackBerry doesn't support IPv6.</span></span>

- <span data-ttu-id="30154-146">Office 365 で Active Directory フェデレーションサービス (AD FS) を使用している場合は、IPv6 を使用して AD FS ネットワークエンドポイントを Office 365 にアドバタイズすることはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="30154-146">If you use Active Directory Federation Services (AD FS) with Office 365, advertising your AD FS network endpoint to Office 365 using IPv6 is not supported.</span></span> <span data-ttu-id="30154-147">Exchange Online を使用している場合は、AD FS DNS エントリに AAAA レコードを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="30154-147">You should not include AAAA records in the AD FS DNS entry when using Exchange Online.</span></span> 

<span data-ttu-id="30154-148">ここに戻る場合は、次のショート リンクをご利用ください: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span><span class="sxs-lookup"><span data-stu-id="30154-148">Here's a short link you can use to come back: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="30154-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="30154-149">See also</span></span>

<span data-ttu-id="30154-150">[IPv6 の学習ロードマップ](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span><span class="sxs-lookup"><span data-stu-id="30154-150">[IPv6 Learning Roadmap](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))</span></span>
  
[<span data-ttu-id="30154-151">IPv6 サバイバルガイド</span><span class="sxs-lookup"><span data-stu-id="30154-151">IPv6 Survival Guide</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
