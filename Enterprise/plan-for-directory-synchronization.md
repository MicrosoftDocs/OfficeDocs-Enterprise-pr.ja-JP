---
title: Office 用のディレクトリ同期の計画365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365、Active Directory クリーンアップ、および Azure Active Directory Connect ツールとのディレクトリ同期について説明します。
ms.openlocfilehash: b1d48696195c572de3a87bc5acb0646fc4bd0f41
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069363"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Office 用のディレクトリ同期の計画365

ビジネスニーズと技術上の要件に応じて、Office 365 に移行するエンタープライズお客様にとって最も一般的なプロビジョニングの選択として、ディレクトリ同期があります。 ディレクトリ同期を使用すると、オンプレミスの Active Directory で id を管理でき、その id に対するすべての更新が Office 365 に同期されます。
  
ディレクトリの準備を含むディレクトリ同期の実装を計画するときには、Azure Active Directory の要件と機能について、いくつかの点に注意する必要があります。 ディレクトリの準備には、多くの領域が含まれています。 これには、属性の更新、監査、およびドメインコントローラーの配置計画が含まれます。 要件と機能の計画には、必要なアクセス許可の決定、複数フォレスト/ディレクトリシナリオの計画、処理能力の計画、双方向同期などが含まれます。
  
## <a name="office-365-identity-models"></a>Office 365 の id モデル

Office 365 では、2つの主要な認証と id モデルを使用しています。クラウド認証とフェデレーション認証です。
  
### <a name="cloud-authentication"></a>クラウド認証

[クラウド id](about-office-365-identity.md) -ユーザーの作成と管理[Microsoft 365 管理センター](https://admin.microsoft.com)では、Windows PowerShell または Azure Active Directory を使用してユーザーを管理することもできます。
  
[シームレスなシングルサインオンを使用したパスワードハッシュ同期](about-office-365-identity.md)Azure AD でオンプレミスのディレクトリオブジェクトの認証を有効にする最も簡単な方法です。 パスワードハッシュ同期 (PHS) を使用して、オンプレミスの Active Directory ユーザーアカウントオブジェクトを Office 365 と同期し、オンプレミスでユーザーを管理します。
  
[シームレスなシングルサインオンを使用したパススルー認証](about-office-365-identity.md)-1 つまたは複数のオンプレミスサーバーで実行されているソフトウェアエージェントを使用して Azure AD 認証サービスのパスワード検証を行い、ユーザーの直接の確認をオンプレミスの Active Directory。
  
### <a name="federated-authentication"></a>フェデレーション認証

[Active Directory フェデレーションサービス AD FS を使用したフェデレーション id](about-office-365-identity.md) -主に、より複雑な認証要件を持つ大規模な企業組織では、オンプレミスのディレクトリオブジェクトは Office 365 と同期され、ユーザーアカウントはオンプレミスで管理されます。
  
[サードパーティの認証および id プロバイダー](about-office-365-identity.md) -オンプレミスのディレクトリオブジェクトは、Office 365 に同期される場合があります。また、クラウドリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。
  
## <a name="active-directory-cleanup"></a>Active Directory のクリーンアップ

同期を使用して Office 365 にシームレスに移行できるようにするには、Office 365 ディレクトリ同期の展開を開始する前に、Active Directory フォレストを準備することを強くお勧めします。
  
[Office 365 でディレクトリ同期](set-up-directory-synchronization.md)をセットアップする場合の手順の1つとして、 [idfix ツールをダウンロードして実行](install-and-run-idfix.md)する方法があります。 IdFix ツールを使用して、[ディレクトリのクリーンアップ](prepare-directory-attributes-for-synch-with-idfix.md)に役立てることができます。
  
ディレクトリのクリーンアップでは、次のタスクに焦点を当てる必要があります。

- 重複している**proxyAddress**属性と**UserPrincipalName**属性を削除します。
- 空白および無効な**userprincipalname**属性を有効な**Userprincipalname**属性で更新します。
- **GivenName**、姓 ( **Sn** )、 **sAMAccountName**、 **displayName**、 **mail**、 **proxyAddresses**、 **mailNickname**、および**userPrincipalName**の無効な文字と疑わしい文字を削除するattributes. 属性の準備の詳細については、「 [Azure Active Directory 同期ツールによって同期される属性の一覧](https://go.microsoft.com/fwlink/p/?LinkId=396719)」を参照してください。

    > [!NOTE]
    > Azure AD Connect が同期するのと同じ属性です。 
  
## <a name="multi-forest-deployment-considerations"></a>複数フォレストの展開に関する考慮事項

複数のフォレストおよび SSO オプションでは、 [AZURE AD Connect のカスタムインストール](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。
  
組織に認証用に複数のフォレストがある場合 (ログオンフォレスト)、次のことを強くお勧めします。
  
- **フォレストの統合を評価します。** 一般に、複数のフォレストを維持するには、より多くのオーバーヘッドが必要になります。 個別のフォレストの必要性を判断するセキュリティ上の制約が組織にない限り、オンプレミスの環境を簡素化することを検討してください。
- **プライマリのログオンフォレストでのみ使用します。** Office 365 を最初に展開する場合は、プライマリのログオンフォレストにのみ Office 365 を展開することを検討してください。 

複数フォレストの Active Directory 展開を統合できない場合や、他のディレクトリサービスを使用して id を管理している場合は、Microsoft またはパートナーのヘルプと同期することができます。
  
詳細については、「[マルチフォレストディレクトリ同期とシングルサインオンシナリオ](https://go.microsoft.com/fwlink/p/?LinkId=525321)」を参照してください。
  
## <a name="directory-integration-tools"></a>ディレクトリ統合ツール

ディレクトリ同期とは、オンプレミスの Active Directory 環境から Office 365 ディレクトリインフラストラクチャへのディレクトリオブジェクト (ユーザー、グループ、および連絡先) の同期です。 使用可能なツールとその機能の一覧については、「[ディレクトリ統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)」を参照してください。 使用する推奨ツールは、 [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323)です。
  
ユーザーアカウントが初めて Office 365 ディレクトリと同期されると、それらは非アクティブとしてマークされます。 電子メールを送受信することはできません。サブスクリプションのライセンスは使用されません。 Office 365 サブスクリプションを特定のユーザーに割り当てる準備ができたら、有効なライセンスを割り当てることによって、それらを選択してアクティブ化する必要があります。
  
次の機能には、ディレクトリ同期が必要です。
  
- SSO
- Skype の共存
- Exchange ハイブリッド展開 (次のものが含まれる)
  - オンプレミスの Exchange 環境と Office 365 間の完全に共有されたグローバルアドレス一覧 (GAL)。
  - 別のメールシステムから GAL 情報を同期します。
  - Office 365 サービスオファーリングにユーザーを追加したり、ユーザーを削除したりする機能。 これには、次のものが必要です。
  - ディレクトリ同期のセットアップ中に、双ウェイの同期を構成する必要があります。 既定では、ディレクトリ同期ツールは、ディレクトリ情報をクラウドにのみ書き込みます。 双ウェイの同期を構成する場合は、制限された数のオブジェクト属性がクラウドからコピーされるように書き戻し機能を有効にしてから、ローカルの Active Directory に書き戻します。 書き戻しは、Exchange ハイブリッドモードとも呼ばれます。 
  - オンプレミスの Exchange ハイブリッド展開
  - 他のユーザーのメールボックスをオンプレミスに保持したまま、一部のユーザーメールボックスを Office 365 に移動する機能。
  - 社内の信頼できる差出人と受信拒否リストは、Office 365 に複製されます。
  - 基本的な委任および代理送信電子メール機能。
  - オンプレミスのスマートカードまたは多要素認証ソリューションが統合されている。
- 写真、サムネイル、会議室、セキュリティグループの同期