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
# <a name="ipv6-support-in-office-365-services"></a>Office 365 サービスでの IPv6 サポート

*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*

Office 365 は IPv6 と IPv4 の両方をサポートしています。ただし、すべての Office 365 機能が IPv6 で完全に有効になっているわけではありません。 これは、Office 365 に接続するために IPv4 と IPv6 の両方を使用する必要があることを意味します。 Office 365 への送信トラフィックをフィルタリングする場合は、office 365 でサポートされる IPv6 アドレスの完全な一覧については、記事「 [office 365 url および IP アドレス範囲](urls-and-ip-address-ranges.md)」を参照してください。 ネットワークが構成され、適切な IPv6 アドレスが許可されたら、Microsoft ダウンロードセンターから[Office 365 IPv6 テスト計画](https://go.microsoft.com/fwlink/?LinkId=293447)をダウンロードすることができます。
  
## <a name="ipv6-support-in-office-365-subscription-service"></a>Office 365 サブスクリプションサービスでの IPv6 サポート

### <a name="exchange-online-and-ipv6"></a>Exchange Online および IPv6

Exchange Online への接続に使用するプログラムが IPv6 をサポートしている場合は、有線ネットワークとワイヤレスネットワークの両方で IPv6 を既定で使用します。 Exchange Online への通信を制御するには、Office 365 の IP アドレスの範囲[と ip アドレス範囲](urls-and-ip-address-ranges.md)を使用します。
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online と IPv6

 **Office 365 Government G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、既定で IPv6 の使用を試みます。
  
 **パブリックマルチテナントクラウド**Microsoft は、お客様の要求で SharePoint Online の IPv6 を有効にします。 組織の DNS インフラストラクチャには、CIDR で入力された IP アドレスを指定する必要があります。 この DNS インフラストラクチャは、テナントに対して IPv6 を有効にするために他の組織と共有できないことに注意してください。 IPv6 を有効にした後、SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、ipv6 が既定で使用されます。
  
SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、有線ネットワークとワイヤレスネットワークの両方で IPv6 を既定で使用します。 SharePoint Online との通信を制御する場合は、「Office 365 の IP アドレスの範囲」の[url と ip アドレスの範囲](urls-and-ip-address-ranges.md)を使用します。
  
 **Office 365 Government G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムが IPv6 をサポートしている場合は、既定で IPv6 の使用を試みます。
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business および IPv6

Skype for Business では IPv6 がサポートされておらず、有効にできないことに注意してください。
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection および IPv6

Exchange Online Protection (EOP) は、転送がトランスポート層セキュリティプロトコルで行われている場合、IPv6 をサポートします。 EOP の範囲については、 [Office 365 の url と IP アドレスの範囲](urls-and-ip-address-ranges.md)を使用します。
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Office 365 government 製品の IPv6 サポート

Office 365 の IPv6 サポートは、経営部門および省庁の最高情報責任者、およびインターネットプロトコルバージョン 6 (IPv6) Memorandum の連邦政府機関による管理と予算 (OMB) Memorandum のオフィスに準拠しています。 [Microsoft Office 365 For government](https://go.microsoft.com/fwlink/p/?LinkId=325414)は、政府機関のデータを分離されたコミュニティクラウドに保存するマルチテナントサービスです。 他の Office 365 製品と同様に、Exchange Online、Skype for Business、SharePoint Online、Office 365 ProPlus を含む、生産性とコラボレーションのサービスを提供します。 

Microsoft Office 365 government のサービスは2013以降にのみ適用されます。 Office 365 government 製品の詳細については、「米国政府機関[向け office 365 の発表: US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414)」を参照してください。 国際通話のトラフィック (ITAR) とは、米国の[Munitions リスト (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)での、防衛関連の記事およびサービスのエクスポートとインポートを制御する米国政府規制のセットです。 

Microsoft Office 365 for enterprise では、米国連邦政府機関向けのセキュリティ、プライバシー、および規制コンプライアンスの要件をサポートする Microsoft の生産性向上ソリューション専用のホスティングサービスを提供しています。連邦情報セキュリティ管理 (FISMA) 証明書と商用エンティティが ITAR に準拠している必要があります。
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>IPv6 および Office 365 を使用する場合の考慮事項

IPv6 を無効にしないことをお勧めします。 詳細については、この[ガイダンス記事](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)を参照してください。 ネットワークで使用されている IP バージョンを確認するには、次の点を考慮してください。
  
- コマンドプロンプトでの**IPConfig**コマンドの表示に "ipv6 address" または "Temporary ipv6 address" という名前の行が含まれている場合は、環境内に ipv6 が存在します。

- すべての IPv6 アドレスが "fe80" で始まり、"リンクローカル IPv6 アドレス" という名前の行に対応している場合は、環境内に IPv6 がありません。

ネットワークには、次のような考慮事項が適用されます。
  
- パブリックサブスクリプションサービスは、IPv6 経由のクレジットカードによる購入をサポートしていません。 これは、自治体がエンタープライズアグリーメント (EA) ライセンスを所有しているため、Government Community Cloud (GCC) には適用されません。

- IPv6 は、一部の Rights Management Services (RMS) シナリオをサポートしていません。

- BlackBerry は IPv6 をサポートしていないため、IPv6 は BlackBerry® Enterprise Server (BE) をサポートしていません。

- Office 365 で Active Directory フェデレーションサービス (AD FS) を使用している場合は、IPv6 を使用して AD FS ネットワークエンドポイントを Office 365 にアドバタイズすることはサポートされていません。 Exchange Online を使用している場合は、AD FS DNS エントリに AAAA レコードを含めないでください。 

ここに戻る場合は、次のショート リンクをご利用ください: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>関連項目

[IPv6 の学習ロードマップ](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 サバイバルガイド](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
