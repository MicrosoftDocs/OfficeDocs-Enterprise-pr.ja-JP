---
title: Office 365 DoD の DNS レコード
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: '概要: Office 365 DoD の DNS レコード'
hideEdit: true
ms.openlocfilehash: d1f8c82224934f11eddbfa10c5dea7d15cc9e9a2
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "44339814"
---
# <a name="dns-records-for-office-365-dod"></a>Office 365 DoD の DNS レコード

*この記事は、Office 365 DoD および Microsoft 365 DoD に適用されます。*

Office 365 DoD へのオンボードの一部として、SMTP および SIP ドメインをオンラインサービステナントに追加する必要があります。  これを行うには、Azure AD PowerShell で Get-msoldomain コマンドレットを使用するか、 [Azure Government ポータル](https://portal.azure.us)を使用してドメインを追加し、所有権を証明するプロセスを開始します。

ドメインをテナントに追加して検証したら、次のガイダンスを使用して、以下のサービスに適切な DNS レコードを追加します。  次の表は、組織のニーズに合わせて変更する必要があります。これには、受信 MX レコードおよびその場で既存の Exchange 自動検出レコードに関する要件があります。  このような DNS レコードをメッセージングチームと調整して、電子メールの停止や不適切な配信を回避することを強くお勧めします。

## <a name="exchange-online"></a>Exchange Online

| Type | Priority | ホスト名 | ポイント (アドレスまたは値) | TTL |
| --- | --- | --- | --- | --- |
| MX | .0 | @ | *tenant*mail.protection.office365.us (詳細については、以下を参照してください) | 1 Hour |
| TXT | - | @ | v = spf1 には、以下が含まれます。 | 1 Hour |
| CNAME | - | autodiscover | autodiscover-dod.office365.us | 1 Hour |

### <a name="exchange-autodiscover-record"></a>Exchange 自動検出レコード

オンプレミスの Exchange Server を使用している場合は、Exchange Online に移行するときに既存のレコードをそのままにしておき、移行の完了後にそのレコードを更新することをお勧めします。

### <a name="exchange-online-mx-record"></a>Exchange Online MX レコード

承認済みドメインの MX レコード値は、前述したように、mail.protection.office365.us を使用して既定のテナント名の最初の部分に*テナント*を置き換えて、標準形式に*従います。*

たとえば、テナント名が contoso.onmicrosoft.us の場合は、MX レコードの値として**contoso.mail.protection.office365.us**を使用します。

## <a name="skype-for-business-online"></a>Skype for Business Online

### <a name="cname-records"></a>CNAME レコード

| 種類 | ホスト名 | ポイント (アドレスまたは値) | TTL |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.dod.skypeforbusiness.us | 1 Hour |
| CNAME | lyncdiscover | webdir.online.dod.skypeforbusiness.us | 1 Hour | 

### <a name="srv-records"></a>SRV レコード

| 種類 | サービス | プロトコル | ポート | 太さ | 優先度 | 氏名 | Target | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1  | 100 | @ | sipdir.online.dod.skypeforbusiness.us | 1 Hour |
| SRV | \_sipfederationtls | \_プロトコル | 5061 | 1  | 100 | @ | sipfed.online.dod.skypeforbusiness.us | 1 Hour |

## <a name="additional-dns-records"></a>追加の DNS レコード

> [!IMPORTANT]
> DNS ゾーンに既存の*msoid* CNAME レコードがある場合は、この時点でそのレコードを dns から**削除**する必要があります。  Msoid レコードは Microsoft 365 Enterprise Apps *(旧称 Office 365 ProPlus)* と互換性がありません。また、ライセンス認証が成功することはありません。
