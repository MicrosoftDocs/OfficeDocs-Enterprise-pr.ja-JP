---
title: Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: ディレクトリ同期し、このメソッドを使用する場合の長期的な利点を使用して、Office 365 にユーザーをプロビジョニングできるようにする方法について説明します。
ms.openlocfilehash: 78636fd3ec7aaaac8fa06ba8a0f2c37d76d1b045
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541778"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備

ディレクトリ同期によってユーザーをプロビジョニングするには、詳細の計画と準備をするだけで Office 365 に直接、職場、学校のアカウントを管理するよりもする必要があります。追加の計画と準備タスクは、Azure Active Directory に、オンプレミスの Active Directory が正しく同期することを確認する必要があります。組織に追加の利点は次のとおりです。
  
- 組織の管理プログラムの削減
- 必要に応じてシングル サインオンのシナリオを有効にします。
- Office 365 でのアカウントの変更の自動化
    
ディレクトリ同期を使用する利点の詳細については、[ディレクトリ同期のロードマップ]( https://go.microsoft.com/fwlink/p/?LinkId=525398)」および「 [Office 365 Id を理解すると Azure Active Directory](about-office-365-identity.md)を参照してください。
  
シナリオではを組織にとって最適なを確認するのには、[ディレクトリの統合ツールの比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)を確認します。
  
## <a name="directory-cleanup-tasks"></a>ディレクトリのクリーンアップ タスク

ディレクトリの同期を開始する前に、ディレクトリをクリーンアップする必要があります。
  
[Azure AD 接続で、Azure Active directory 属性を同期](https://go.microsoft.com/fwlink/p/?LinkId=746480)するも参照してください。
  
> [!IMPORTANT]
> 同期する前に、ディレクトリのクリーンアップを実行しない、する場合があります、展開プロセスに重大な悪影響を及ぼす。日かかる、エラー、および再同期を識別する、ディレクトリ同期のサイクルを通過して、数週間にわたって、可能性があります。 
  
設置ディレクトリには、次のクリーンアップ タスクを完了します。
  
1. Office 365 サービスが割り当てられる各ユーザーについて、**proxyAddresses** 属性のメール アドレスが有効かつ一意であることを確認します。 
    
2. **proxyAddresses** 属性に重複する値が存在する場合は削除します。 
    
3.  可能であれば、Office 365 サービスに割り当てられる各ユーザーがあるユーザーの**ユーザー**オブジェクトの**userPrincipalName**属性に対して有効で、一意の値を確認します。快適に同期、オンプレミスの Active ディレクトリ UPN がクラウドの UPN と一致していることを確認します。**UserPrincipalName**属性の値がなくても場合、**ユーザー**オブジェクトは**sAMAccountName**属性に対して有効で、一意の値を含める必要があります。**UserPrincipalName**属性内の重複する値を削除します。 
    
4. グローバル アドレス一覧 (GAL) を最適に利用できるように、以下の属性の情報が正しいことを確認してください。
    
  - givenName 
  - 姓
  - 表示名
  - 役職
  - 部署
  - 事業所
  - 事業所電話番号
  - 携帯電話
  - FAX 番号
  - 番地
  - 市区町村
  - 都道府県
  - 郵便番号
  - 国または地域
    
## <a name="directory-object-and-attribute-preparation"></a>ディレクトリ オブジェクトおよび属性の準備

設置ディレクトリと Office 365 のディレクトリ同期では、オンプレミスのディレクトリの属性が適切に準備されている必要があります。たとえば、特定の文字が Office 365 環境と同期している特定の属性で使用されていないことを確認する必要があります。予期しない文字は、ディレクトリ同期が失敗するが発生しないが、警告メッセージを返すことがあります。無効な文字には、ディレクトリ同期が失敗するが発生します。
  
ディレクトリ同期は、1 つまたは複数の重複する属性がある、Active Directory のユーザーの場合も失敗します。各ユーザー固有の属性が必要です。
  
準備する必要がある属性は次のとおりです。
  
 **注:** 非常に簡単にするのには[IdFix ツール](install-and-run-idfix.md)を使用することもできます。 
  
- **表示名**
    
  - この属性がユーザー オブジェクトに存在する場合は、Office 365 と同期されます。
  - この属性がユーザー オブジェクトに存在する場合、値を割り当てる必要があります。この属性を空白にすることはできません。
  - 最大文字数: 256
    
- **givenName **
    
  - ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。
  - 最大文字数: 64
    
- **mail**
    
  - この属性値は、ディレクトリ内で一意にする必要があります。
    
    > [!NOTE]
    > 重複する値がある場合は、値を持つ最初のユーザーが同期されます。Office 365 では、後続のユーザーは表示されません。、Office 365 で、いずれかの値を変更または、両方のユーザーを Office 365 に表示するために、オンプレミス ディレクトリ内の値の両方を変更する必要があります。 
  
- **mailNickname** (Exchange エイリアス) 
    
  - 属性の値は、ピリオド (.) で始めることはできません。
  - この属性値は、ディレクトリ内で一意にする必要があります。
    
- **proxyAddresses **
    
  - 複数値属性
  - 1 つの値に使用できる最大文字数:256
  - 属性の値は、スペースを含めないでください。
  - この属性値は、ディレクトリ内で一意にする必要があります。
  - 無効な文字: \< \> ();, [ ] "
    
    型の区切り記号に続く文字列に無効な文字を適用することに注意してくださいと":"SMTP:User@contso.com も可能ですが、SMTP:user:M@contoso.com ではありませんように、します。
    
    > [!IMPORTANT]
    > すべての簡易メール転送プロトコル (SMTP) アドレスは、標準のメッセージを電子メールで従う必要があります。重複や不要なアドレスが存在する場合は、 [Exchange では重複や不要なプロキシを削除する](https://go.microsoft.com/fwlink/?LinkId=293860)ヘルプ トピックを参照してください。 
  
- **sAMAccountName**
    
  - 最大文字数: 20
  - この属性値は、ディレクトリ内で一意にする必要があります。
  - 無効な文字: [\] |、/: \< \> + =;?\* ]
  - ユーザーの **sAMAccountName** 属性が無効で、**userPrincipalName** 属性が有効な場合、ユーザー アカウントは Office 365 に作成されます。 
  - **SAMAccountName**と**userPrincipalName**の両方が無効な場合、オンプレミスの Active Directory の**userPrincipalName**属性を更新する必要があります。 
    
- **sn** (姓) 
    
  - ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。
    
- **targetAddress**
    
    必要と Office 365 のグローバル アドレス一覧にユーザーの設定は、 **targetAddress**属性 (たとえば、SMTP:tom@contoso.com) があります。サード ・ パーティ製メッセージングの移行シナリオでは、この必要がある Office 365 のスキーマ拡張設置ディレクトリにあります。設置ディレクトリからディレクトリ同期ツールを使用して指定されている Office 365 のオブジェクトを管理するために役立つその他の属性、Office 365 のスキーマ拡張機能も追加します。たとえば、非表示のメールボックスまたは配布グループを管理するために**msExchHideFromAddressLists**属性が追加されます。 
   
  - 最大文字数: 256
  - 属性の値は、スペースを含めないでください。
  - この属性値は、ディレクトリ内で一意にする必要があります。
  - 無効な文字: \ \< \> ();, [ ] "
  - すべての SMTP (Simple Mail Transport Protocol) アドレスは、電子メール メッセージング標準に準拠する必要があります。
    
- **userPrincipalName**
    
  - **UserPrincipalName**属性は、インターネット スタイルのサインイン名の形式は、ユーザー名に続けてである必要があります、アット マーク (@) とドメイン名: user@contoso.com など。すべての簡易メール転送プロトコル (SMTP) アドレスは、標準のメッセージを電子メールで従う必要があります。
  - **userPrincipalName** 属性の最大文字数は 113 です。アットマーク (@) の前後の文字数の制限は、次のとおりです。 
  - アットマーク記号 (@) の前に来るユーザー名の最大文字数: 6464
  - アットマーク記号 (@) の後に続くドメイン名の最大文字数: 48
  - 無効な文字: \ % &amp; \* +/= でしょうか。{ } |\< \> ( ) ;: , [ ] "
  - ウムラウトが無効な文字もあります。
  - **UserPrincipalName**の各値に @ 文字が必要です。 
  - **userPrincipalName** 値の 1 文字目に @ 文字を使用することはできません。 
  - ユーザー名は、ピリオド (.)、アンパサンドで終わることはできません (&amp;)、スペース、またはアットマーク (@)。
  - ユーザー名にスペースを含めることはできません。
  - ルーティング可能なドメインを使用する必要があります。たとえば、ローカルまたは内部ドメインを使用できません。
  - ユニコードはアンダースコア文字に変換されます。
  - ディレクトリ内で **userPrincipalName** の値が重複しないようにします。 
    
## <a name="prepare-the-userprincipalname-attribute"></a>userPrincipalName 属性の準備

**SAMAccountName**または**userPrincipalName**を使用して、ディレクトリにサインインするのには、組織内のエンド ・ ユーザーを許可するのには、active Directory は設計されています。同様に、エンド ・ ユーザーは、自分の仕事のユーザー プリンシパル名 (UPN) を使用して Office 365 にサインインやアカウントの学校です。ディレクトリ同期は、オンプレミス ディレクトリ内にある同一の UPN を使用して、Azure Active Directory で新しいユーザーを作成しようとします。UPN は、電子メール アドレスのように書式設定されます。 

Office 365 では、UPN は、電子メール アドレスを生成するために使用される既定の属性です。**UserPrincipalName**を取得するは簡単 (設置型と Azure Active Directory) と**proxyAddresses**が異なる値に設定でプライマリ電子メール アドレスです。異なる値に設定されている場合があります管理者とエンド ・ ユーザー用の混乱します。 
  
混乱を減らすためにこれらの属性を配置することをお勧めします。Active Directory フェデレーション サービス (AD FS) とシングル サインオンの要件を満たすために 2.0 では、Azure Active Directory と、オンプレミスの Active Directory で Upn を確認する必要がありますと一致し、有効なドメインの名前空間を使用しています。
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>AD DS に代わりの UPN サフィックスを追加します。

Office 365 環境で企業のユーザーの資格情報を関連付けるには、代わりの UPN サフィックスを追加する必要があります。ユーザー プリンシパル名サフィックス、UPN の右側の部分では、@ 文字。Upn は、シングル サインオンに使用するには、文字、番号、期間、ダッシュ、およびアンダー スコアがない他の種類の文字を含めることができます。
  
代わりの UPN サフィックスを Active Directory に追加する方法の詳細については、[ディレクトリ同期の準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)を参照してください。
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Office 365 で、オンプレミスの UPN に一致する UPN

ディレクトリ同期処理をされている場合、Office 365 のユーザーの UPN が設置ディレクトリ サービスで定義されているユーザーの設置型の UPN が一致しません。これは、ドメインを確認する前に、ユーザーにライセンスが割り当てられていた場合に発生します。これを修正するには、Office 365 の UPN が企業内のユーザー名とドメインと一致することを確認するのには、ユーザーの UPN を更新するのには[重複する UPN を解決するのに PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396730)を使用します。設置ディレクトリ サービスの UPN を更新するし、Azure Active Directory ユーザーとの同期に、オンプレミスの変更を行う前に、Office 365 のユーザーのライセンスを削除する必要があります。 
  
[ディレクトリ同期の .local ドメイン) などのルーティング不可能なドメインを準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)を参照してください。
  
## <a name="directory-integration-tools"></a>ディレクトリ統合ツール

ディレクトリ同期は、ディレクトリ オブジェクト (ユーザー、グループ、および連絡先)、オンプレミスの Active Directory 環境から Office 365 のディレクトリ インフラストラクチャ、Azure Active Directory の同期です。使用できるツールとその機能の一覧については、[ディレクトリの統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)を参照してください。推奨されるツールは、 [Microsoft Azure Active Directory に接続](https://go.microsoft.com/fwlink/p/?LinkID=510956)します。Azure Active Directory の接続の詳細については、[オンプレミス ユーザー Azure Active Directory との統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)を参照してください。
  
マークされている場合、ユーザー アカウントは、最初に Office 365 のディレクトリと同期は、アクティブ化されていません。送信したり、電子メールを受信できないし、サブスクリプション ライセンスを消費しません。特定のユーザーに Office 365 のサブスクリプションを割り当てる準備ができたら、選択して、[ビジネス向けの Office 365 のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)ことによってそれらをアクティブ化する必要があります。
  
ライセンスを割り当てるには[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)を使用することもできます。自動化ソリューションは、 [Office 365 ユーザーにライセンスを自動的に割り当てるに PowerShell を使用する方法](https://go.microsoft.com/fwlink/p?LinkID=329805)を参照してください。