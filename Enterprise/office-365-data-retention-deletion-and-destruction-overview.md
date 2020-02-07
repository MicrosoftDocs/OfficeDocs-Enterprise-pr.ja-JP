---
title: Office 365 でのデータの保持、削除、および破棄
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: データの保持、削除、および破壊に関する Office 365 の Microsoft ポリシーの概要。
ms.openlocfilehash: a1f799be5582a112808d8efed65f1a3d420546c5
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844508"
---
# <a name="data-retention-deletion-and-destruction-in-office-365"></a>Office 365 でのデータの保持、削除、および破棄

Microsoft では、ユーザーが削除した後に顧客データを保持する期間を指定する、Office 365 のデータ処理の標準ポリシーを使用しています。 一般的に、顧客データが削除されるシナリオは2つあります。

- **アクティブな削除**: テナントにはアクティブなサブスクリプションがあり、ユーザーまたは管理者がデータを削除するか、管理者がユーザーを削除します。
- **パッシブ削除**: テナントサブスクリプションが終了します。

## <a name="data-retention"></a>データ保持

これらの削除シナリオのそれぞれについて、次の表に、データの最大保持期間、データカテゴリ、および分類を示します。

| データカテゴリ | データ分類 | 説明 | 例 | 保持期間 |
|-----------------|-----------------|-----------------|----------------------------------|-------------------------------|
| 顧客データ | 顧客コンテンツ| 管理者とユーザーによって直接提供/作成されたコンテンツ <br><br> Office 365 でサービスを使用している場合に、Microsoft データセンターにすべてのテキスト、サウンド、ビデオ、画像ファイル、およびソフトウェアが作成され保存されるようにします。 | Word、Excel、PowerPoint、Outlook、OneNote など、ユーザーがデータを作成できる、最も一般的に使用される Office 365 アプリケーションの例 <br><br> お客様のコンテンツには、お客様が所有/提供する機密情報 (パスワード、証明書、暗号化キー、ストレージキー) も含まれています。 | **アクティブな削除のシナリオ:** 最大で30日 <br><br> **パッシブ削除のシナリオ:** 最大180日 |
| 顧客データ | エンドユーザーを特定できる情報 (EUII) | Microsoft サービスのユーザーを識別または特定するために使用されるデータ。 EUII にお客様のコンテンツは含まれていません | ユーザー名または表示名 (DOMAIN\UserName) <br><br> ユーザープリンシパル名 (name@domain) <br><br>  ユーザー固有の IP アドレス | **アクティブな削除のシナリオ:** 最大180日 (テナント管理者のアクションのみ) <br><br> **パッシブ削除のシナリオ:** 最大180日 |
| 個人データ <br> (顧客データに含まれていないデータ) | エンドユーザー仮名識別子 (EUPI) | Microsoft サービスのユーザーに関連付けられた id。 マッピングテーブルなど、他の情報と組み合わせて使用する場合、EUPI はエンドユーザーを識別します。 <br><br> EUPI お客様がアップロードまたは作成した情報は含まれません。 | ユーザー Guid、PUIDs、または Sid <br><br> セッション Id | **アクティブな削除のシナリオ:** 最大で30日 <br><br> **パッシブ削除のシナリオ:** 最大180日 |

## <a name="subscription-retention"></a>サブスクリプションの保持期間

アクティブなサブスクリプションの場合、サブスクライバーは Office 365 に格納されている顧客データにアクセス、抽出、または削除することができます。 有料サブスクリプションが終了または終了した場合、Microsoft は Office 365 に格納されている顧客データを90日間保持して、サブスクライバーがデータを抽出できるようにします。 90日の保持期間が終了すると、Microsoft はアカウントを無効にし、顧客データを削除します。 Office 365 へのサブスクリプションの有効期限または終了後に、180日を超えていない場合、Microsoft はアカウントを無効にし、アカウントからすべての顧客データを削除します。 いずれかのデータの最大保持期間が経過すると、データは商業的に復旧できないように表示されます。

無料試用版の場合、アカウントは、ほとんどの国や地域で30日の猶予状態に移行します。 この猶予期間中に、Office 365 を購入することができます。 Office 365 を購入しない場合は、試用をキャンセルするか、猶予期間を過ぎて、試用版のアカウント情報とデータを削除することができます。

## <a name="expedited-deletion"></a>優先削除

サブスクリプションの場合、サブスクライバーは Microsoft サポートに連絡して、サブスクリプションの優先プロビジョニング解除を要求できます。 このプロセスでは、管理者が Microsoft によって提供されたロックアウトコードを入力した3日後に、すべてのユーザーデータが削除されます。 これには、SharePoint Online および Exchange Online のデータが保持されるか、非アクティブなメールボックスに格納されます。

優先除外の詳細については、「 [Office 365 の取り消し](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/cancel-your-subscription)」を参照してください。

## <a name="related-links"></a>関連リンク

- [データの破棄](office-365-data-destruction.md)
- [Office 365 での不変性](office-365-data-immutability.md)
- [Exchange Online でのデータ削除](office-365-exchange-online-data-deletion.md)
- [SharePoint Online でのデータ削除](office-365-sharepoint-online-data-deletion.md)
- [Skype for Business でのデータ削除](office-365-skype-data-deletion.md)