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
# <a name="ipv6-support-in-office-365-services"></a>Office 365 サービスでの IPv6 サポート

 **概要**: Microsoft Office 365 コンポーネントと Office 365 の政府サービスの IPv6 のサポートについて説明します。
  
Office 365 は、IPv6 と IPv4 の両方はサポートしています。ただし、すべての Office 365 の機能は完全に ipv6 が有効になります。つまり、Office 365 への接続に IPv4 と IPv6 の両方を使用する必要があります。Office 365 へ送信されたトラフィックをフィルターする場合、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の記事で Office 365 でサポートされている IPv6 アドレスの完全な一覧を参照しています。ネットワークを構成して、適切な IPv6 アドレスが許可されて後からダウンロードできます[Office 365 の IPv6 のテスト計画](https://go.microsoft.com/fwlink/?LinkId=293447)を Microsoft ダウンロード センター。
  
||
|:-----|
| この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。|

## <a name="ipv6-support-in-office-365-subscription-service"></a>Office 365 サブスクリプション サービスで IPv6 のサポート

### <a name="exchange-online-and-ipv6"></a>Exchange Online と IPv6

Exchange Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、IPv6 をワイヤード (有線) とワイヤレスの両方のネットワークでは、既定で使います。Exchange Online への通信を制御する場合は、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の IP アドレスの範囲を使用します。
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online と IPv6

 **Office 365 の政府 G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、既定で IPv6 を使用するを試みます。
  
 **マルチ テナント型のパブリック クラウド**マイクロソフトでは、ご要望により SharePoint のオンラインの IPv6 を有効にします。CIDR 表記の IP アドレスを組織の DNS インフラストラクチャを提供する必要があります。この DNS インフラストラクチャを ipv6 の場合、テナントを有効にするには、他の組織と共有できないことに留意してください。IPv6 を有効にする、SharePoint Online への接続に使用するプログラムは、IPv6 をサポートしている場合、既定で IPv6 を使用します。
  
SharePoint Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、ワイヤード (有線) とワイヤレスの両方のネットワークでは、既定で IPv6 が使用されます。SharePoint Online への通信を制御する場合は、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の IP アドレスの範囲を使用します。
  
 **Office 365 の政府 G1/G3/G4/K1**SharePoint Online への接続に使用するプログラムでは、IPv6 をサポートする場合は、既定で IPv6 を使用するを試みます。
  
### <a name="skype-for-business-and-ipv6"></a>ビジネスと IPv6 の Skype

マイクロソフトはマルチ テナント型のパブリック クラウドと Office 365 政府 G1/G3/G4 と K1 のサブスクリプションでは、ご要望のビジネス用の Skype の IPv6 を有効になります。それを有効にする、ビジネスの Skype への接続に使用するプログラムは、IPv6 をサポートしている場合、既定で IPv6 を使用します。ビジネス用の Skype への通信を制御する場合は、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)の IP アドレスの範囲を使用します。
  
IPv6 は、すべての地域では利用可能ではありませんし、マイクロソフトは、この時点で、テナントのアクティブ化できない場合があります注意してください。
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection と IPv6

Exchange オンライン保護 (EOP) は、トランスポート層セキュリティ プロトコル経由で転送が発生した場合、IPv6 をサポートしています。EOP を範囲のセルには、 [Office 365 の Url と IP アドレスの範囲](https://go.microsoft.com/fwlink/?LinkId=293744)を使用します。
  
### <a name="ipv6-support-for-office-365-government-offerings"></a>Office 365 Government 製品の IPv6 サポート

経営部門や機関などと同様の連邦政府機関採用のインターネット プロトコル バージョン 6 (IPv6 の最高情報責任者の Office の管理および予算 (OMB) のメモに、政府の製品の IPv6 サポートを office 365 に準拠しています。) メモします。[政府向けの Microsoft Office 365](https://go.microsoft.com/fwlink/p/?LinkId=325414)は、分離されたコミュニティ クラウドで米国政府のデータが格納されているマルチ テナント サービスです。他の Office 365 の製品と同じように Exchange Online、Skype のビジネス、SharePoint Online では、Office Professional Plus を含む、生産性とコラボレーションのサービスを提供します。2013 についてのみ、後で、Microsoft Office 365 の政府サービスが適用されます。Office 365 の政府サービスの詳細についてを参照してください[政府向けの Office 365 の発表: A 米国政府のコミュニティ クラウド](https://go.microsoft.com/fwlink/p/?LinkId=325414)。国際トラフィックのアームの規制 (ITAR) では、防御に関連する資料と[米国兵器リスト (USML)](https://go.microsoft.com/fwlink/p/?LinkId=325415)上のサービスのインポートとエクスポートを制御する米国政府の規制のセットです。企業向けの Microsoft Office 365 には、マイクロソフトの生産性をサポートするソリューション、セキュリティ、プライバシー、および規制へのコンプライアンス要件の連邦政府機関の連邦政府の情報セキュリティを必要とするための専用のホスティング サービスが用意されています。管理 (FISMA) 証明書および営利団体は、ITAR にさらされます。
  
## <a name="things-to-consider-when-using-ipv6-and-office-365"></a>IPv6 および Office 365 の使用に関する考慮事項

IPv6 を無効にしないことをお勧めします。詳細についてを参照してください[Microsoft Windows の IPv6: よく寄せられる質問](https://go.microsoft.com/fwlink/p/?LinkId=325418)。ネットワーク上にどのような IP のバージョンを使用されているを確認するのには、以下を考慮してください。
  
- コマンド プロンプトで IPConfig コマンドの表示に「IPv6 アドレス」または「一時的 IPv6 アドレス」という名前の行が含まれている場合、環境内で IPv6 がいます。

- すべての IPv6 アドレス"fe80"で、「リンク ローカル IPv6 アドレス」をという名前行に対応している場合は、環境内で IPv6 がありません。

以下の事項がネットワークに適用される場合があります。
  
- パブリック サブスクリプション サービスでは、IPv6 を介したクレジット カードでの購入はサポートされません。ただし、政府機関コミュニティ クラウド (GCC) の場合、政府機関には Enterprise Agreement (EA) ライセンスがあるため、これは適用されません。

- IPv6 では、Rights Management サービス (RMS) の一部のシナリオはサポートされません。

- IPv6 では、BlackBerry は、IPv6 をサポートしていませんので BlackBerry® エンタープライズ サーバー (BE) をサポートしていません。

- を Office 365 を Active Directory フェデレーション サービス (AD FS) を使用する場合は、Office 365 AD FS ネットワーク エンドポイントを提供する IPv6 を使用してサポートされていません。、Exchange Online を使用する場合、AAAA レコードを AD FS の DNS エントリに含める必要があります。 

ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)
  
## <a name="see-also"></a>関連項目

[マイクロソフトのテクノロジ ポジション ペーパー](https://go.microsoft.com/fwlink/p/?linkid=525743)
  
[TCP/IP v4 と v6](https://go.microsoft.com/fwlink/p/?LinkID=211898)
  
[IPv6 のサバイバル ガイド](https://go.microsoft.com/fwlink/p/?LinkID=237480)
