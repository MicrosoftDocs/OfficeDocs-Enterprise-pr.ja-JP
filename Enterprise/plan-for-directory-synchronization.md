---
title: Office 365 のディレクトリ同期の計画
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Office 365、Active Directory のクリーンアップ、Azure Active Directory 接続ツールとディレクトリの同期について説明します。
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541670"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期の計画
によって、ビジネス ・ ニーズと技術的な要件では、ディレクトリ同期処理は、Office 365 に移行する企業のお客様の最も一般的なプロビジョニングの選択です。ディレクトリ同期により、オンプレミスの Active Directory で管理するユーザーとそのユーザーにすべての更新プログラムが Office 365 に同期されます。
  
いくつかのディレクトリの準備、および要件と Azure Active Directory の機能を含め、ディレクトリの同期の実装を計画する際に留意することがあります。ディレクトリの準備では、非常に多くの領域について説明します。属性の更新、監査、およびドメイン コント ローラー配置の計画が含まれます。要件と機能の計画には、multiforest/ディレクトリの場合、容量計画、および双方向同期を計画する必要なアクセス許可の決定が含まれます。
  
## <a name="office-365-identity-models"></a>Office 365 のユーザー モデル
Office 365 は、2 つの主な認証と id モデルを使用して: クラウドの認証と統合認証します。
  
### <a name="cloud-authentication"></a>クラウドの認証
[クラウドのアイデンティティ](about-office-365-identity.md)を作成し、Office 365 の管理センターでユーザーを管理、ユーザーを管理するために、Windows PowerShell、または Active Directory の Azure を使用することもできます。 
  
[シームレスなシングル サインオンとパスワードのハッシュが同期](about-office-365-identity.md)の Azure AD で設置ディレクトリ オブジェクトの認証を有効にする簡単な方法です。パスワード ハッシュ (PHS)、同期に、オンプレミスの Active Directory ユーザー アカウント オブジェクトを Office 365 と同期して、ユーザーの設置型の管理します。 
  
Azure AD の認証サービスと直接ユーザーを検証するためにソフトウェア エージェントは、1 つまたは複数のオンプレミスのサーバーで実行されているを使用して単純なパスワードの検証を提供する[シームレスなシングル サインオンでのパススルー認証](about-office-365-identity.md)が、Active Directory を設置します。 
  
### <a name="federated-authentication"></a>フェデレーション認証
[に Active Directory フェデレーション サービスの AD FS のフェデレーション id](about-office-365-identity.md)でより複雑な認証の要件を持つ大規模な組織に主に設置型のディレクトリ オブジェクトは、Office 365 と同期し、ユーザー アカウントは、マネージ設置します。 
  
[サード ・ パーティ製の認証と id プロバイダー](about-office-365-identity.md)の設置型のディレクトリ オブジェクトが Office 365 に同期させることがあり、クラウドのリソースへのアクセスは、主にサードパーティの id プロバイダー (IdP) によって管理されます。 
  
## <a name="active-directory-cleanup"></a>Active Directory のクリーンアップ
同期を使用して Office 365 へのシームレスな移行を確保するためには、強くお勧め、Office 365 のディレクトリ同期の展開を開始する前に、Active Directory フォレストを準備することです。
  
[ダウンロードして IdFix ツールを実行](install-and-run-idfix.md)するときの手順の 1 つは[Office 365 のディレクトリ同期を設定](set-up-directory-synchronization.md)すると、.[ディレクトリのクリーンアップ](prepare-directory-attributes-for-synch-with-idfix.md)を支援する IdFix ツールを使用することができます。
  
ディレクトリのクリーンアップは、次のタスクに集中する必要があります。

- **メタベース**および**userPrincipalName**属性の重複を削除します。
- 空白および無効な **userPrincipalName** 属性を有効な **userPrincipalName** 属性で更新します。
- **GivenName**姓 ( **sn** )、 **sAMAccountName**、**表示名**、**メール**、 **proxyAddresses**、 **mailNickname**、 **userPrincipalName**で信用できない無効な文字を削除します。属性。属性を準備する方法の詳細は、 [Azure Active Directory 同期ツールで同期する、属性の一覧](https://go.microsoft.com/fwlink/p/?LinkId=396719)を参照してください。
    
    > [!NOTE]
    > これらは、Azure AD 接続を同期するのと同じ属性です。 
  
## <a name="multiforest-deployment-considerations"></a>マルチフォレスト展開について考慮事項
複数のフォレストと SSO オプションでは、 [Azure のインストールをユーザー設定の AD 接続](https://go.microsoft.com/fwlink/p/?LinkId=698430)を使用します。
  
組織に認証 (ログオン フォレスト) に複数のフォレストがある場合は、強くお勧め以下。
  
- **、フォレストの統合を評価します**。一般に、複数のフォレストを維持するために必要な多くのオーバーヘッドがあります。組織に別々 のフォレストが必要になるセキュリティ上の制約がある場合を除き、オンプレミス環境の簡素化を検討してください。
- **プライマリ ログオン フォレスト内でのみ使用します**。Office 365 の初期ロールアウトは、優先的にログオンするフォレストでのみ Office 365 の展開を検討してください。 
    
複数フォレストの Active Directory の展開を統合することはできませんか id を管理するその他のディレクトリ サービスを使用している場合は、マイクロソフトまたはパートナーの支援によりこれらを同期することができます。
  
詳細については、[シングル サインオンのシナリオでディレクトリ同期を複数のフォレスト](https://go.microsoft.com/fwlink/p/?LinkId=525321)を参照してください。
  
## <a name="directory-integration-tools"></a>ディレクトリ統合ツール
ディレクトリが同期ディレクトリのオブジェクト (ユーザー、グループ、および連絡先) の同期、オンプレミスの Active Directory 環境から Office 365 のディレクトリ インフラストラクチャにします。[ディレクトリの統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)を使用できるツールとその機能の一覧についてを参照してください。使用することをお勧めのツールでは、 [Azure Active Directory の接続です](https://go.microsoft.com/fwlink/?LinkId=525323)。
  
ユーザー アカウントは、最初に Office 365 のディレクトリと同期は、ときに、非アクティブとしてマークされています。送信したり、電子メールを受信できないし、サブスクリプション ライセンスを消費しません。特定のユーザーに Office 365 のサブスクリプションを割り当てる準備ができたら、選択して、有効なライセンスを割り当てることによってそれらをアクティブ化する必要があります。
  
ディレクトリ同期は、次の機能と機能の必要です。
  
- SSO
    
- Lync の共存
    
- Exchange ハイブリッド展開を含みます。
    
  - 完全に、オンプレミスの Exchange 環境と Office 365 の間でグローバル アドレス一覧 (GAL) を共有します。
  - 他のメール システムの GAL 情報の同期。
  - ユーザーを追加し、Office 365 サービスからユーザーを削除する機能。次必要があります。
  - ディレクトリ同期のセットアップ中に、双方向同期を構成しなければなりません。既定では、ディレクトリ同期ツールは、クラウドへの移行のみディレクトリ情報を記述します。双方向同期を構成するとき、オブジェクトの属性の数に制限が、クラウドからコピーし、書きして、ローカルの Active Directory に戻すように、書き戻し機能が有効にします。書き戻しは、Exchange ハイブリッド モードとも呼ばれます。 
  - オンプレミス Exchange ハイブリッド展開
  - 他のユーザーのメールボックスの設置型を維持しながら Office 365 によってユーザーのメールボックスを移動する機能。
  - 差出人セーフ リストと受信拒否リストの設置型は、Office 365 に複製されます。
  - 基本的な委任と代理送信メールの機能。
  - オンプレミスで統合されたスマート カードまたは多要素認証ソリューションがあります。
    
- 写真、サムネイル、会議室、およびセキュリティ グループの同期