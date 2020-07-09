---
title: Office 365 GCC High および DoD の追加のネットワークセキュリティ要件
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
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: '概要: Office 365 GCC High および DoD には、追加のネットワークセキュリティ要件があります。'
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371633"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Office 365 GCC High および DOD の追加のネットワークセキュリティ要件

*この記事は、Office 365 GCC High、Office 365 DOD、Microsoft 365 GCC 高、および Microsoft 365 DOD に適用されます。*

Office 365 GCC High および DOD は、米国政府機関とそのサプライヤーおよび請負業者のニーズを満たすために、セキュリティで保護されたクラウド環境です。  これらのクラウド環境には、サービスがアクセスを許可されている外部エンドポイントに対する、追加のネットワーク制限があります。

フェデレーション id またはハイブリッド共存を計画しているお客様は、既存のオンプレミス展開への受信または送信アクセスを許可するために Microsoft を必要とする場合があります。  これらのアクティビティの例を次に示します。

* フェデレーション id の使用 (Active Directory フェデレーションサービスまたは同様にサポートされている STS)
* オンプレミスの Exchange サーバーまたは Skype for Business 展開とのハイブリッド共存
* オンプレミスのシステムからの既存のユーザーコンテンツの移行

サービスがオンプレミスエンドポイントと通信できるようにするには、ネットワークの変更に備えて Office 365 エンジニアリングに電子メールを送信する**必要があり**ます。

> [!WARNING]
> すべての要求には**3 週間**の SLA があり、必要なセキュリティとコンプライアンスの制御と展開パイプラインがあるため、優先することはできません。  これには、サービスに移行した後の初期のネットワーク要求だけでなく、すべての変更が含まれます。  ネットワークチームがこのタイムラインを認識して、計画サイクルに含めるようにしてください。

次の情報を使用して、 [Office 365 Government ネットワークホワイトリスト](mailto:o365gwlt@microsoft.com)にメールを送信してください。

* **To**: [Office 365 Government ネットワークホワイトリスト](mailto:o365gwlt@microsoft.com)
* **From**: テナント管理者-送信メールはテナント内の全体管理者の連絡先と一致**する必要があります**
* **電子メールの件名**: OFFICE 365 GCC High Network Request-contoso.onmicrosoft.us (これをテナント名に置き換えます)

メッセージの本文には、次のデータを含める必要があります。

* Microsoft Online Services テナント名 (contoso.onmicrosoft.com、fabrikam.onmicrosoft.us)
* ネットワークの変更に関連した、または無効なサブネットのフォローアップのために Microsoft が通信する電子メール配布リスト
* オンプレミスの展開で Microsoft Teams ハイブリッド共存を使用することを計画しているかどうかを示します
* (たとえば、sts.contoso.com) 外部からアクセス可能な URL (たとえば、10.1.1.0/28) のフェデレーション id システム (たとえば、) および IP アドレス範囲
* CIDR 表記でのオンプレミスの PKI 証明書失効リストの URL と IP アドレス範囲
* CIDR 表記での Exchange Server オンプレミス展開の外部アクセス可能な URL と IP アドレス範囲
* CIDR 表記での、Skype for Business のオンプレミス展開の外部アクセス可能な URL と IP アドレス範囲

セキュリティおよびコンプライアンス上の理由から、要求に関する以下の制限事項に注意してください。

* テナントごとに4つのサブネット制限があります。
* サブネットは CIDR 表記 (例: 10.1.1.0/28) である必要があります。
* サブネット範囲を/24 より大きくすることはできません
* 商用のクラウドサービス (市販の Office 365、Google G-Suite、Amazon Web サービスなど) へのアクセスを許可する要求に対応する**ことはできません**。

要求が Microsoft によって受信され、承認されると、実装に3週間の SLA が発生し、優先度を設定することはできません。  要求を受信した後、最初の受信確認が送信されます。完了した後、最終的な受信確認を受信します。
