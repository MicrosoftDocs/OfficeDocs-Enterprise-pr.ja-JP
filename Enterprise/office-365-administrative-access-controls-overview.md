---
title: Office 365 での管理アクセス制御
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
description: '概要: Office 365 の管理アクセス制御とデータ分類の概要について説明します。'
ms.openlocfilehash: e8cc470c617deea7435841f276b772b0a8ef17a3
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067634"
---
# <a name="administrative-access-controls-in-office-365"></a>Office 365 での管理アクセス制御 

Microsoft は、Microsoft によってお客様のコンテンツへのアクセスを意図的に制限する一方で、ほとんどの Office 365 操作を自動化するシステムと管理に多大な投資を行ってきました。 人間がサービスを制御し、ソフトウェアがサービスを運用します。 これにより、Microsoft は Office 365 をスケールで管理し、お客様のコンテンツに対する内部の脅威のリスクを管理することができます。

既定では、Microsoft のエンジニアには継続的な管理者権限も、Office 365 の顧客コンテンツへのアクセス権もありません。 Microsoft のエンジニアは、限られた期間、お客様のコンテンツへのアクセスを制限、監査、およびセキュリティで保護することができます。 アクセスは、サービス操作に必要な場合と、Microsoft シニアマネージメントのメンバーによって承認された場合にのみ使用できます。 お客様がライセンスを供与されたお客様の場合、お客様は Office 365 でホストされているコンテンツへのアクセスを承認します。

Microsoft では、複数の形式のクラウド配信を使用したオンラインサービスを提供しています。

- **パブリッククラウド:** Office 365、Azure、および北アメリカ、南米、ヨーロッパ、アジア、オーストラリアなどでホストされているその他のサービスのマルチテナントバージョンが含まれています。
- **国立雲:**(中国で運用されている) Office 365、ドイツの Office 365 (Microsoft が運用しているが、ドイツ語のデータトラスティを含むモデル) など、米国外のすべての独立およびサードパーティ製のクラウドを含みます (前述のものを除く)。ドイツの受付 Kom は、顧客データを含む Microsoft の顧客データやシステムへのアクセスを制御し、監視します。
- **行政機関向けクラウド:** 米国政府機関のお客様が利用できる Office 365 および Azure サービスが含まれています。

この記事の目的として、Office 365 サービスには次のものがあります。

- [Exchange Online](https://docs.microsoft.com/Exchange/exchange-online)
- [Exchange Online Protection](https://docs.microsoft.com/Office365/SecurityCompliance/eop/exchange-online-protection-overview)
- [SharePoint Online](https://docs.microsoft.com/sharepoint/sharepoint-online)
- [OneDrive for Business](https://docs.microsoft.com/OneDrive/onedrive)
- [Skype for Business](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-online)
- [Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/Teams-overview)
- [Yammer](https://docs.microsoft.com/yammer/yammer-landing-page)

## <a name="office-365-access-controls"></a>Office 365 のアクセス制御

アクセス制御を目的として、Microsoft では Office 365 データを顧客データまたはその他の種類のデータとして分類しています。

### <a name="customer-data"></a>顧客データ

顧客データとは、Office 365 サービスを使用している場合に、お客様によって提供される、または代理となるデータのことです。 これは、次のような Office 365 ユーザーによって直接作成またはアップロードされるお客様向けコンテンツです。

- メール
- SharePoint Online のコンテンツ
- インスタントメッセージ
- 予定表アイテム
- Documents
- 連絡先
- エンドユーザー識別情報 (EUII) (ユーザーに固有のデータ、または個別のユーザーに linkable されていても、顧客コンテンツは含まれません)。

### <a name="other-types-of-data"></a>その他の種類のデータ

その他の種類のデータは次のとおりです。

- **アカウントデータ:** 管理データ (管理者がサインアップまたはサービスを購入するときに提供される情報) と支払いデータ (クレジットカードの詳細などの支払い手段に関する情報) が含まれています。
- **組織的に識別できる情報:** テナントを識別するために使用されるデータ、使用状況データ、個々のユーザーに linkable していないこと、または顧客コンテンツに含まれているデータを含みます。
- **システムのメタデータ:** 構成設定、システム状態、Microsoft IP アドレス、およびサブスクリプションとテナントに関する技術情報を含むサービスログが含まれています。

Microsoft は、お客様のデータまたはアクセスコントロールのデータへのアクセスが許可されていないことを確認するためのアクセス制御メカニズムを確立しています。 Access control データは、お客様のコンテンツや EUII、Microsoft のパスワード、セキュリティ証明書、およびその他の認証関連データへのアクセスを含む、環境内の他の種類のデータまたは機能へのアクセスを管理します。 アクセス制御メカニズムは、Office 365 運用環境への許可されていない物理、論理、またはリモートアクセスに対する保護も行います。

Microsoft では、次の3つのカテゴリのアクセス制御を Office 365 用に使用しています。

- 分離コントロール
- 人事管理
- テクノロジコントロール

これらのコントロールを組み合わせると、Office 365 の悪意のあるアクションを防ぎ、検出することができます。 Microsoft によって使用される分離、人物、およびテクノロジの各コントロールに加えて、ユーザーによって実装されるコントロールには、次の4つのカテゴリがあります。

Office 365 では、オンプレミス環境でのデータ管理と同じ方法でデータを管理できます。 Office 365 の組織をサインアップするユーザーは、自動的にグローバル管理者になります。 グローバル管理者は、管理ポータルのすべての機能にアクセスでき、次のことができます。

- ユーザーを作成または編集する
- 他のユーザーに管理者ロールを割り当てる
- ユーザーのパスワードをリセットする
- ユーザーライセンスを管理する
- ドメインの管理
- 顧客のロックボックス要求を承認する

各組織で少なくとも2人の管理者アカウントを構成することをお勧めします。 大規模な企業組織の場合、さまざまな機能を提供する特別な管理者アカウントをお勧めします。

管理者の役割とアクセス許可の割り当てについては、「 [office 365 での管理者ロールの割り当て](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)」および「 [office 365 管理者ロールについ](https://support.office.com/article/Permissions-in-Office-365-DA585EEA-F576-4F55-A1E0-87090B6AAA9D)て」を参照してください。

## <a name="related-links"></a>関連リンク

- [分離コントロール](office-365-isolation-controls.md)
- [人事管理](office-365-personnel-controls.md)
- [テクノロジコントロール](office-365-technology-controls.md)
- [アクセス制御の監視と監査](office-365-monitoring-and-auditing-access-controls.md)
- [Yammer Enterprise でのアクセス制御](office-365-yammer-enterprise-access-controls.md)