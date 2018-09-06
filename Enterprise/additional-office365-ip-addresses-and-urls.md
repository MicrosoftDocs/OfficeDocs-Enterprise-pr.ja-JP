---
title: Web サービスに含まれないその他の Office 365 IP アドレスとURL
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 8/22/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: '概要: 新しいエンドポイントの Web サービスでは、特定のシナリオ用の一部のエンドポイントは含まれません。'
hideEdit: true
ms.openlocfilehash: b40fb1a40d2a815bfc6e02fa11204d10dde2af73
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22600511"
---
# <a name="additional-office-365-ip-addresses-and-urls-not-included-in-the-web-services"></a>Web サービスに含まれないその他の Office 365 IP アドレスとURL

一部のネットワーク エンドポイントは以前に公開されているため、Web サービスには含まれていません。Web サービスの範囲に含まれるのは、組織の境界ネットワーク上の Office 365 のエンドユーザーの接続に必要なネットワーク エンドポイントです。現在、以下のものが含まれません。

1. Microsoft データ センターからお客様のネットワーク (ハイブリッド サーバー の着信ネットワーク トラフィック) への必要なネットワーク接続
2. 組織のネットワーク境界上 (送信サーバーのネットワーク トラフィック) のお客様のネットワーク上のサーバーからのネットワーク接続
3. ユーザーが設定する、ネットワーク接続要件に関する特殊なシナリオ
4. DNS 解決の接続要件 (下記の一覧には含まれていません)
5. Internet Explorer または Microsoft Edge の信頼済みサイト

DNS に関するものを除き、記載された特定のシナリオを必要としない場合は、大多数のお客様にとりこれらはすべて省略可能です。

|||||
|:-----|:-----|:-----|:-----|
| **行** | **用途** | **宛先** | **型** |
| 1  | PST やファイル取り込みのための[インポート サービス](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) | その他の要件については、「[インポート サービス](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)」をご覧ください。 | 特殊な送信シナリオ |
| 2  | [Microsoft Office 365 サポート/回復アシスタント](https://diagnostics.office.com/#/) -シングル サインオン ユーザーの資格情報を検証します。ソース: <br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | オンプレミス セキュリティ トークン サービス | 受信サーバー トラフィック |
| 3  | Azure AD Connect (SSO オプション使用) – WinRM およびリモート PowerShell | 顧客の STS 環境 (AD FS サーバーおよび AD FS プロキシ) \| TCP ポート 80 と 443 | 受信サーバー トラフィック |
| 4  | AD FS プロキシ サーバー (フェデレーション対象顧客専用) などの STS | 顧客の STS (AD FS プロキシなど)\|ポート TCP 443 または TCP 49443 (ClientTLS使用) | 受信サーバー トラフィック |
| 5  | [Exchange Online ユニファイド メッセージング/SBC 統合](https://technet.microsoft.com/library/jj673565.aspx) | オンプレミス セッション ボーダー コント ローラーと *. um.outlook.com 間で双方向 | 送信サーバー トラフィック |
| 6  | [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant) 空き時間情報の共有などの共存機能。 | 顧客のオンプレミス Exchange サーバーのバージョン | 受信サーバー トラフィック |
| 7  | [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant) プロキシ認証 | 顧客のオンプレミス STS | 受信サーバー トラフィック |
| 8  | Exchange ハイブリッド構成ウィザードを使用して [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant)を構成する場合に使用します。 <br> 注: これらのエンドポイントは、Exchange ハイブリッドの構成にのみ必要です。  | TCP ポート 80 と 443 の ```domains.live.com``` は、Exchange 2010 SP3 ハイブリッド構成ウィザードでのみ必要です。 | 送信サーバー トラフィック |
| 9  | **認証と ID FQDN** <br> FQDN (```secure.aadcdn.microsoftonline-p.com```) を機能させるには、クライアントの Internet Explorer (IE) またはエッジの信頼済みサイト ゾーンに含める必要があります。 |  | 信頼済みサイト |
| 10  |  **Microsoft Teams FQDN** <br> Internet Explorer または Microsoft Edge を使用している場合は、最初にサード パーティの cookie を有効にし、信頼済みサイトに (スイート製品全体の FQDN、CDN、および上記のテレメトリに加え) Teams の FQDN を追加する必要があります。詳細については、「[Microsoft Teams の既知の問題](https://docs.microsoft.com/microsoftteams/known-issues)」を参照してください。 |  | 信頼済みサイト |
| 11  |  **Sharepoint Online と OneDrive for Business FQDN** <br> “\<tenant>” が入ったすべての FQDN (“.sharepoint.com”) を機能させるには、クライアントの IE またはエッジの信頼済みサイト ゾーンに含める必要があります。スイート製品全体の FQDN、CDN、および上記のテレメトリに加えて、これらのエンドポイントも追加する必要があります。 |  | 信頼済みサイト |
| 12  | **Yammer**  <br> Yammer はブラウザーでのみ利用でき、認証されたユーザーはプロキシを経由する必要があります。Yammer のすべての FQDN をさせるには、クライアントの IE またはエッジの信頼済みサイト ゾーンに含める必要があります。 |  | 信頼済みサイト |

## <a name="related-topics"></a>関連項目

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)
  
[Office 365 の接続に関するトラブルシューティング](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[クライアント接続](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[コンテンツ配信ネットワーク](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure データ センターの IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft パブリック IP スペース](https://www.microsoft.com/download/details.aspx?id=53602)

