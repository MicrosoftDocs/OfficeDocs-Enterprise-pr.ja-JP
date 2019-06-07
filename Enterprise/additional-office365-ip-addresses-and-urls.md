---
title: Office 365 IP アドレスと URL Web サービスに含まれないその他のエンドポイント
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/05/2019
audience: Admin
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
ms.openlocfilehash: 05bb48efef57785b75d302fd12294b7fb7062862
ms.sourcegitcommit: 6eb8a32c6899a884cb1c760cbfc134f427c8b6c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "34726243"
---
# <a name="additional-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Office 365 IP アドレスと URL Web サービスに含まれないその他のエンドポイント

一部のネットワーク エンドポイントは以前に公開されているため、[Office 365 IP アドレスと URL Web サービス](office-365-ip-web-service.md)には含まれていません。Web サービスの範囲に含まれるのは、組織の境界ネットワーク上の Office 365 のユーザーの接続に必要なネットワーク エンドポイントです。現在、以下のものが含まれません。

1. Microsoft データ センターからお客様のネットワーク (ハイブリッド サーバーの着信ネットワーク トラフィック) への必要なネットワーク接続。
2. 組織のネットワーク境界上 (送信サーバーのネットワーク トラフィック) のお客様のネットワーク上のサーバーからのネットワーク接続。
3. ユーザーが設定する、ネットワーク接続要件に関する特殊なシナリオ。
4. DNS 解決の接続要件 (下記の一覧には含まれていません)。
5. Internet Explorer または Microsoft Edge の信頼済みサイト。

DNS に関するものを除き、記載された特定のシナリオを必要としない場合は、大多数のお客様にとりこれらはすべて省略可能です。

|||||
|:-----|:-----|:-----|:-----|
| **行** | **用途** | **宛先** | **型** |
| 1  | PST やファイル取り込みのための[インポート サービス](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) | その他の要件については、「[インポート サービス](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6)」をご覧ください。 | 特殊な送信シナリオ |
| 2  | [Microsoft Office 365 サポート/回復アシスタント](https://diagnostics.office.com/#/) -シングル サインオン ユーザーの資格情報を検証します。ソース: <br> ```o365diagnosticsbasic-eus.cloudapp.net (104.211.54.99)``` <br> ```o365diagnosticworker-eus.cloudapp.net (104.211.54.134)```  | オンプレミス セキュリティ トークン サービス | 受信サーバー トラフィック |
| 3  | Azure AD Connect (SSO オプション使用) – WinRM およびリモート PowerShell | 顧客の STS 環境 (AD FS サーバーおよび AD FS プロキシ) \| TCP ポート 80 と 443 | 受信サーバー トラフィック |
| 4  | AD FS プロキシ サーバー (フェデレーション対象顧客専用) などの STS | 顧客の STS (AD FS プロキシなど)\|ポート TCP 443 または TCP 49443 (ClientTLS使用) | 受信サーバー トラフィック |
| 5  | [Exchange Online ユニファイド メッセージング/SBC 統合](https://technet.microsoft.com/library/jj673565.aspx) | オンプレミス セッション ボーダー コント ローラーと *. um.outlook.com 間で双方向 | 送信サーバー トラフィック |
| 6  | メールボックスの移行。オンプレミスの [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant) から Office 365 へのメールボックスの移行が開始されると、Office 365 は Exchange Web サービス (EWS)/Mailbox Replication サービス (MRS) サーバーに接続されます。Exchange Online サーバーが使用する NAT IP アドレスを特定の送信元 IP の範囲からの受信接続に限定する場合は、「 [Office 365 の URL と IP アドレスの範囲](urls-and-ip-address-ranges.md) 」の「Exchange Online」サービス領域の欄に一覧が掲載されています。TCP 443 接続を特定の送信元 IP 範囲に制限する前に、MRS プロキシが別の FQDN とパブリック IP アドレスに解決するようにして、OWA などの公開済みの EWS エンドポイントへのアクセスが制限されないように注意する必要があります。 | 顧客のオンプレミス EWS/MRS プロキシ<br> TCP ポート 443 | 受信サーバー トラフィック |
| 7  | [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant) 空き時間情報の共有などの共存機能。 | 顧客のオンプレミス Exchange サーバーのバージョン | 受信サーバー トラフィック |
| 8  | [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant) プロキシ認証 | 顧客のオンプレミス STS | 受信サーバー トラフィック |
| 9  | [Exchange ハイブリッド構成ウィザード](https://docs.microsoft.com/exchange/hybrid-configuration-wizard)を使用して [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant)を構成する場合に使用します。 <br> 注: これらのエンドポイントは、Exchange ハイブリッドの構成にのみ必要です。  | TCP ポート 80 と 443 の domains.live.com は、Exchange 2010 SP3 ハイブリッド構成ウィザードでのみ必要です<BR> <BR> GCC High、DoD IP アドレス: 40.118.209.192/32、168.62.190.41/32 <BR> <BR> 世界中の商用および GCC: *.store.core.windows.net、asl.configure.office.com、mshrcstorageprod.blob.core.windows.net、tds.configure.office.com、mshybridservice.trafficmanager.net <BR>  | 送信サーバー トラフィック |
| 10  | AutoDetect サービスは、[iOS および Android 用の Outlook でハイブリッド先進認証](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth)を行う [Exchange ハイブリッド](https://docs.microsoft.com/exchange/exchange-deployment-assistant) シナリオで使用します。 <BR> <BR> ```*.acompli.net``` <BR> <BR> ```*.outlookmobile.com``` <BR> <BR> ```*.outlookmobile.us``` <BR> <BR> ```52.125.128.0/20``` <BR> ```52.127.96.0/23``` <BR> | 顧客の TCP 443 のオンプレミス Exchange サーバー | 受信サーバー トラフィック |
| 11  | Office 2016 の Skype for Business には、UDP ポートを使用するビデオ ベースの画面共有が含まれています。Office 2013 以前の Skype for Business クライアントでは、TCP ポート 443 経由で RDP を使用していました。 | TCP ポート 443 を 52.112.0.0/14 に開く | Office 2013 以前の Skype for Business の古いクライアント バージョン |
| 12  | Skype for Business ハイブリッド オンプレミス サーバーから Skype for Business Online への接続性 | 13.107.64.0/18、52.112.0.0/14 UDP ポート 50,000-59,999 <BR>  TCP ポート 50,000-59,999 | Skype for Business オンプレミス サーバーの送信接続性 |
| 13  | オンプレミスのハイブリッド接続を使用するクラウド PSTN では、オンプレミスのホストへのネットワーク接続を開く必要があります。Skype for Business Online のハイブリッド構成の詳細については、  | 「[Skype for Business Server と Office 365 間のハイブリッド接続を計画する](https://docs.microsoft.com/skypeforbusiness/hybrid/plan-hybrid-connectivity)」を参照してください。 | Skype for Business オンプレミス ハイブリッド受信 |
| 14  | **認証と ID FQDN** <br> FQDN (```secure.aadcdn.microsoftonline-p.com```) を機能させるには、クライアントの Internet Explorer (IE) またはエッジの信頼済みサイト ゾーンに含める必要があります。 |  | 信頼済みサイト |
| 15  |  **Microsoft Teams FQDN** <br> Internet Explorer または Microsoft Edge を使用している場合は、最初にサード パーティの cookie を有効にし、信頼済みサイトに (スイート製品全体の FQDN、CDN、および 14 行目に記載されているテレメトリに加え) Teams の FQDN を追加する必要があります。詳細については、「[Microsoft Teams の既知の問題](https://docs.microsoft.com/microsoftteams/known-issues)」を参照してください。 |  | 信頼済みサイト |
| 16  |  **Sharepoint Online と OneDrive for Business FQDN** <br> “\<tenant>” が入ったすべての FQDN (“.sharepoint.com”) を機能させるには、クライアントの IE またはエッジの信頼済みサイト ゾーンに含める必要があります。スイート製品全体の FQDN、CDN、および 14 行目に記載されているテレメトリに加えて、これらのエンドポイントも追加する必要があります。 |  | 信頼済みサイト |
| 17  | **Yammer**  <br> Yammer はブラウザーでのみ利用でき、認証されたユーザーはプロキシを経由する必要があります。Yammer のすべての FQDN をさせるには、クライアントの IE またはエッジの信頼済みサイト ゾーンに含める必要があります。 |  | 信頼済みサイト |
| 18  | [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/)を使用して、オンプレミスのユーザー アカウントを Azure AD に同期します。 | 詳細については、「[ハイブリッド ID で必要なポートとプロトコル](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-ports)」、「[Azure AD の接続のトラブルシューティング](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity) 」および「[Azure AD Connect Health エージェントのインストール](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints)」を参照してください。 | 送信サーバーのみのトラフィック |

## <a name="related-topics"></a>関連項目

[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)
  
[Office 365 の接続に関するトラブルシューティング](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[クライアント接続](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[コンテンツ配信ネットワーク](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure データ センターの IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Microsoft パブリック IP スペース](https://www.microsoft.com/download/details.aspx?id=53602)

