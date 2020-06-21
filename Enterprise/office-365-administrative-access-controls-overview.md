---
title: Microsoft 365 の管理アクセス制御
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- NOCSH
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: '概要: Microsoft 365 の管理アクセス制御とデータ分類の概要について説明します。'
ms.openlocfilehash: 93b62acbda2508d5b41578eb807293c34fdda4dd
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774972"
---
# <a name="administrative-access-controls-in-microsoft-365"></a>Microsoft 365 の管理アクセス制御 

Microsoft は、microsoft によってお客様のコンテンツへのアクセスを意図的に制限する一方で、Microsoft の365の大部分を自動化するシステムと管理に多大な投資を行っています。 人間がサービスを制御し、ソフトウェアがサービスを運用します。 これにより、Microsoft は Microsoft 365 をスケールで管理し、お客様のコンテンツに対する内部の脅威のリスクを管理することができます。

既定では、Microsoft のエンジニアは、Microsoft 365 ではゼロの管理者権限と、お客様のコンテンツへのアクセスがゼロになります。 Microsoft のエンジニアは、限られた期間、お客様のコンテンツへのアクセスを制限、監査、およびセキュリティで保護することができます。 アクセスは、サービス操作に必要な場合と、Microsoft シニアマネージメントのメンバーによって承認された場合にのみ使用できます。 お客様にライセンスを供与されたお客様のために、お客様は Microsoft 365 でホストされているコンテンツへのアクセスを承認します。

Microsoft では、複数の形式のクラウド配信を使用したオンラインサービスを提供しています。

- **パブリッククラウド:** Microsoft 365、Azure、および北アメリカ、南米、ヨーロッパ、アジア、オーストラリアなどでホストされているその他のサービスのマルチテナントバージョンが含まれています。
- **国立雲:** 米国外にあるすべての独立およびサードパーティ製の雲 (前述したものを除く) (中国で運用されている 365)、ドイツの microsoft 365 (ドイツのデータを使用している場合はドイツの場合がありますが、ドイツのテレの場合があります) により、顧客データおよびお客様のデータを含むシステムへのアクセス
- **行政機関向けクラウド:** 米国政府機関のお客様が利用できる Microsoft 365 および Azure サービスが含まれています。

この記事の目的として、Microsoft 365 サービスには次のものが含まれます。

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive for Business](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype for Business](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="microsoft-365-access-controls"></a>Microsoft 365 のアクセス制御

アクセス制御を目的として、microsoft は Microsoft 365 データを顧客データまたはその他の種類のデータとして分類しています。

### <a name="customer-data"></a>顧客データ

お客様のデータは、Microsoft 365 サービスを使用している場合に、お客様によって提供されるすべてのデータです。 これは、Microsoft 365 ユーザーによって直接作成またはアップロードされる、次のようなお客様向けコンテンツです。

- メール
- SharePoint Online のコンテンツ
- インスタントメッセージ
- 予定表アイテム
- ドキュメント
- Contacts
- エンドユーザー識別情報 (EUII) (ユーザーに固有のデータ、または個別のユーザーに linkable されていても、顧客コンテンツは含まれません)

### <a name="other-types-of-data"></a>その他の種類のデータ

その他の種類のデータは次のとおりです。

- **アカウントデータ:** 管理データ (管理者がサインアップまたはサービスを購入するときに提供される情報) と支払いデータ (クレジットカードの詳細などの支払い手段に関する情報) が含まれています。
- **組織的に識別できる情報:** テナントを識別するために使用されるデータ、使用状況データ、個々のユーザーに linkable していないこと、または顧客コンテンツに含まれているデータを含みます。
- **システムのメタデータ:** 構成設定、システム状態、Microsoft IP アドレス、およびサブスクリプションとテナントに関する技術情報を含むサービスログが含まれています。

Microsoft は、お客様のデータまたはアクセスコントロールのデータへのアクセスが許可されていないことを確認するためのアクセス制御メカニズムを確立しています。 Access control データは、お客様のコンテンツや EUII、Microsoft のパスワード、セキュリティ証明書、およびその他の認証関連データへのアクセスを含む、環境内の他の種類のデータまたは機能へのアクセスを管理します。 アクセス制御メカニズムは、Microsoft 365 運用環境への許可されていない物理、論理、またはリモートアクセスに対する保護も行います。

Microsoft が microsoft 365 を実行するために使用するアクセス制御には、次の3つのカテゴリがあります。

- 分離コントロール
- 人事管理
- テクノロジコントロール

これらのコントロールを組み合わせると、Microsoft 365 で悪意のあるアクションを防ぎ、検出することができます。 Microsoft によって使用される分離、人物、およびテクノロジの各コントロールに加えて、ユーザーによって実装されるコントロールには、次の4つのカテゴリがあります。

Microsoft 365 では、オンプレミス環境でのデータ管理と同じ方法でデータを管理できます。 Microsoft 365 の組織にサインアップするユーザーは、自動的にグローバル管理者になります。 グローバル管理者は、管理ポータルのすべての機能にアクセスでき、次のことができます。

- ユーザーを作成または編集する
- 他のユーザーに管理者ロールを割り当てる
- ユーザーのパスワードをリセットする
- ユーザーライセンスを管理する
- ドメインの管理
- 顧客のロックボックス要求を承認する

各組織で少なくとも2人の管理者アカウントを構成することをお勧めします。 大規模な企業組織の場合、さまざまな機能を提供する特別な管理者アカウントをお勧めします。

管理者の役割とアクセス許可の割り当ての詳細については、「[管理者の役割の割り当て](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)」および「[管理者の役割につい](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles)て」を参照

## <a name="related-links"></a>関連リンク

- [分離コントロール](office-365-isolation-controls.md)
- [人事管理](office-365-personnel-controls.md)
- [テクノロジコントロール](office-365-technology-controls.md)
- [アクセス制御の監視と監査](office-365-monitoring-and-auditing-access-controls.md)
- [Yammer Enterprise でのアクセス制御](office-365-yammer-enterprise-access-controls.md)