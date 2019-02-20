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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: ディレクトリ同期を使用して Office 365 にユーザーをプロビジョニングするための準備方法と、この方法を使用する長期的な利点について説明します。
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085106"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Office 365 へのディレクトリ同期を通してユーザーをプロビジョニングするための準備

ディレクトリ同期を使用するユーザーのプロビジョニングには、Office 365 で職場または学校のアカウントを直接管理するよりも多くの計画と準備が必要です。オンプレミスの active directory が Azure active directory に適切に同期されるようにするには、追加の計画と準備のタスクが必要です。組織には、次のような利点が追加されています。
  
- 組織の管理プログラムの削減
- オプションでシングルサインオンのシナリオを有効にする
- Office 365 でのアカウントの変更の自動化
    
ディレクトリ同期を使用する利点の詳細については、「[ディレクトリ同期のロードマップ]( https://go.microsoft.com/fwlink/p/?LinkId=525398)」および「 [Office 365 id と Azure Active directory につい](about-office-365-identity.md)て」を参照してください。
  
組織に最適なシナリオを特定するには、[ディレクトリ統合ツールの比較](https://go.microsoft.com/fwlink/p/?LinkId=525320)を参照してください。
  
## <a name="directory-cleanup-tasks"></a>ディレクトリのクリーンアップタスク

ディレクトリの同期を開始する前に、ディレクトリをクリーンアップする必要があります。
  
azure [AD Connect によって azure Active Directory に同期](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)された属性も確認します。
  
> [!IMPORTANT]
> 同期の前にディレクトリのクリーンアップを実行しないと、展開プロセスに重大な悪影響が発生する可能性があります。ディレクトリ同期のサイクルを経て、エラーを特定し、再同期を実行するまでに、数日または数週間かかる場合があります。 
  
オンプレミスディレクトリで、次のクリーンアップタスクを実行します。
  
1. Office 365 サービスが割り当てられる各ユーザーについて、**proxyAddresses** 属性のメール アドレスが有効かつ一意であることを確認します。 
    
2. **proxyAddresses** 属性に重複する値が存在する場合は削除します。 
    
3.  可能な場合は、Office 365 サービスオファーリングを割り当てる各ユーザーに、ユーザーの**ユーザー**オブジェクトの**userPrincipalName**属性に有効な一意の値を指定します。最適な同期処理を行うには、オンプレミスの Active Directory upn がクラウド UPN に一致していることを確認してください。ユーザーが**userPrincipalName**属性の値を持っていない場合は、**ユーザー**オブジェクトに**sAMAccountName**属性の有効な一意の値が含まれている必要があります。**userPrincipalName**属性の重複する値を削除します。 
    
4. グローバル アドレス一覧 (GAL) を最適に利用できるように、以下の属性の情報が正しいことを確認してください。
    
  - givenName 
  - 姓
  - displayName
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

オンプレミスディレクトリと Office 365 との間のディレクトリ同期を正常に行うには、オンプレミスのディレクトリ属性が適切に準備されている必要があります。たとえば、Office 365 環境と同期されている特定の属性に特定の文字が使用されないようにする必要があります。予期しない文字によってディレクトリ同期が失敗することはありませんが、警告が返されることがあります。無効な文字は、ディレクトリ同期が失敗する原因となります。
  
Active directory ユーザーの一部に1つ以上の重複した属性がある場合も、ディレクトリ同期は失敗します。各ユーザーは固有の属性を持つ必要があります。
  
準備する必要がある属性を以下に示します。
  
 **注:**[idfix ツール](install-and-run-idfix.md)を使用して、このプロセスを非常に簡単にすることもできます。 
  
- **displayName**
    
  - この属性がユーザー オブジェクトに存在する場合は、Office 365 と同期されます。
  - この属性がユーザー オブジェクトに存在する場合、値を割り当てる必要があります。この属性を空白にすることはできません。
  - 最大文字数: 256
    
- **givenName **
    
  - ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。
  - 最大文字数: 64
    
- **mail**
    
  - この属性値は、ディレクトリ内で一意にする必要があります。
    
    > [!NOTE]
    > 重複する値がある場合、値を持つ最初のユーザーが同期されます。以降のユーザーは、Office 365 に表示されません。両方のユーザーが office 365 に表示されるようにするには、office 365 の値を変更するか、オンプレミスのディレクトリの両方の値を変更する必要があります。 
  
- **mailNickname** (Exchange エイリアス) 
    
  - 属性値はピリオド (.) で始めることはできません。
  - この属性値は、ディレクトリ内で一意にする必要があります。
    
- **proxyAddresses **
    
  - 複数値の属性
  - 1 つの値に使用できる最大文字数:256
  - 属性の値にスペースを含めることはできません。
  - この属性値は、ディレクトリ内で一意にする必要があります。
  - 無効な文字\< \> : ();, [ ] "
    
    無効な文字は、SMTP:User@contso.com が許可されていても、SMTP:user:M@contoso.com は許可されていませんが、型区切り記号の後の文字と ":" に適用されることに注意してください。
    
    > [!IMPORTANT]
    > すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。重複しているまたは不要なアドレスが存在する場合は、ヘルプトピックの「 [Exchange での重複および不要なプロキシアドレスの削除](https://go.microsoft.com/fwlink/?LinkId=293860)」を参照してください。 
  
- **sAMAccountName**
    
  - 最大文字数: 20
  - この属性値は、ディレクトリ内で一意にする必要があります。
  - 無効な文字: [\ "|,/ \< \> : + =;?\* ]
  - ユーザーの **sAMAccountName** 属性が無効で、**userPrincipalName** 属性が有効な場合、ユーザー アカウントは Office 365 に作成されます。 
  - **sAMAccountName**と**userPrincipalName**の両方が無効な場合は、オンプレミスの Active Directory **userprincipalname**属性を更新する必要があります。 
    
- **sn** (姓) 
    
  - ユーザー オブジェクトに存在する場合、この属性は Office 365 と同期されますが、Office 365 ではこの属性を必要とせず、使用されません。
    
- **targetAddress**
    
    ユーザーに対して設定されている**targetAddress**属性 (たとえば、SMTP:tom@contoso.com) を Office 365 GAL に表示する必要があります。サードパーティ製のメッセージング移行シナリオでは、オンプレミスのディレクトリに Office 365 スキーマ拡張が必要になります。office 365 スキーマ拡張機能は、オンプレミスディレクトリからのディレクトリ同期ツールを使用して設定された office 365 オブジェクトを管理するための便利な属性も追加します。たとえば、非表示のメールボックスまたは配布グループを管理する**msExchHideFromAddressLists**属性が追加されます。 
   
  - 最大文字数: 256
  - 属性の値にスペースを含めることはできません。
  - この属性値は、ディレクトリ内で一意にする必要があります。
  - 無効な文字: \< \> \ ();, [ ] "
  - すべての SMTP (Simple Mail Transport Protocol) アドレスは、電子メール メッセージング標準に準拠する必要があります。
    
- **userPrincipalName**
    
  - **userPrincipalName**属性は、ユーザー名の後にアットマーク記号 (@) とドメイン名が続く、インターネットスタイルのサインイン形式にする必要があります。たとえば、user@contoso.com のようにします。すべての簡易メール転送プロトコル (SMTP) アドレスは、電子メールメッセージング標準に準拠している必要があります。
  - **userPrincipalName** 属性の最大文字数は 113 です。アットマーク (@) の前後の文字数の制限は、次のとおりです。 
  - アットマーク記号 (@) の前に来るユーザー名の最大文字数: 6464
  - アットマーク記号 (@) の後に続くドメイン名の最大文字数: 48
  - 無効な文字: \ &amp; \* % +/=?{ } |\< \> ( ) ;: , [ ] "
  - ウムラウトは、無効な文字でもあります。
  - 各**userPrincipalName**値には @ 文字が必要です。 
  - **userPrincipalName** 値の 1 文字目に @ 文字を使用することはできません。 
  - ユーザー名の最後の文字には、ピリオド (.)、アンパサンド&amp;()、スペース、またはアットマーク (@) を使用することはできません。
  - ユーザー名にスペースを含めることはできません。
  - ルーティング可能なドメインを使用する必要があります。たとえば、ローカルまたは内部のドメインを使用することはできません。
  - ユニコードはアンダースコア文字に変換されます。
  - ディレクトリ内で **userPrincipalName** の値が重複しないようにします。 
    
## <a name="prepare-the-userprincipalname-attribute"></a>userPrincipalName 属性の準備

Active Directory は、組織内のエンドユーザーが**sAMAccountName**または**userPrincipalName**のいずれかを使用してディレクトリにサインインできるように設計されています。同様に、エンドユーザーは職場または学校アカウントのユーザープリンシパル名 (UPN) を使用して Office 365 にサインインできます。ディレクトリ同期では、オンプレミスディレクトリにある同じ UPN を使用して、Azure Active directory に新しいユーザーを作成しようとしています。UPN は、電子メールアドレスのように書式設定されます。 

Office 365 では、UPN は電子メールアドレスの生成に使用される既定の属性です。**userPrincipalName** (オンプレミスと Azure Active Directory) は簡単に取得でき、 **proxyAddresses**のプライマリ電子メールアドレスは異なる値に設定されます。複数の値が設定されている場合、管理者とエンドユーザーに混乱が生じることがあります。 
  
これらの属性を調整して混乱を軽減することをお勧めします。Active directory フェデレーションサービス (AD FS) 2.0 を使用したシングルサインオンの要件を満たすには、Azure active directory の upn とオンプレミスの active directory が一致し、有効なドメイン名前空間を使用していることを確認する必要があります。
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>AD DS に代替 UPN サフィックスを追加する

ユーザーの会社の資格情報を Office 365 環境に関連付けるには、代替 UPN サフィックスを追加する必要がある場合があります。upn サフィックスは、@ 記号の右側にある upn の一部です。シングルサインオンに使用される upn には、文字、数字、ピリオド、ダッシュ、およびアンダースコアを含めることができますが、その他の種類の文字は使用できません。
  
Active directory に代替 UPN サフィックスを追加する方法の詳細については、「[ディレクトリ同期の準備]( https://go.microsoft.com/fwlink/p/?LinkId=525430)」を参照してください。
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>オンプレミスの upn と Office 365 upn を照合する

ディレクトリ同期が既にセットアップされている場合、ユーザーの UPN for Office 365 は、オンプレミスのディレクトリサービスに定義されているユーザーのオンプレミス upn と一致しない場合があります。これは、ドメインが確認される前にユーザーにライセンスが割り当てられた場合に発生する可能性があります。この問題を解決するには、PowerShell を使用して重複した[upn を修正](https://go.microsoft.com/fwlink/p/?LinkId=396730)し、Office 365 upn が企業ユーザー名とドメインと一致するようにします。オンプレミスのディレクトリサービスで UPN を更新していて、Azure Active directory id と同期する必要がある場合は、オンプレミスで変更を行う前に、Office 365 でユーザーのライセンスを削除する必要があります。 
  
[ディレクトリ同期のためのルーティングできないドメイン (たとえば、ローカルドメイン) を準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)も参照してください。
  
## <a name="directory-integration-tools"></a>ディレクトリ統合ツール

ディレクトリ同期とは、オンプレミスの active directory 環境から Azure active directory へのディレクトリオブジェクト (ユーザー、グループ、および連絡先) の同期です。使用可能なツールとその機能の一覧については、「[ディレクトリ統合ツール](https://go.microsoft.com/fwlink/p/?LinkID=510956)」を参照してください。推奨されるツールは、 [Microsoft Azure Active Directory 接続](https://go.microsoft.com/fwlink/p/?LinkID=510956)です。azure active directory Connect の詳細については、「[オンプレミス id と azure active directory の統合](https://go.microsoft.com/fwlink/p/?LinkId=527969)」を参照してください。
  
ユーザーアカウントが初めて Office 365 ディレクトリと同期されると、それらはアクティブでないとマークされます。電子メールを送受信することはできません。サブスクリプションのライセンスは使用されません。office 365 サブスクリプションを特定のユーザーに割り当てる準備ができたら、 [office 365 for business のユーザーにライセンスを割り当てる](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc)ことによって、それらを選択してアクティブ化する必要があります。
  
[PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097)を使用してライセンスを割り当てることもできます。自動化されたソリューションの[Office 365 ユーザーにライセンスを自動的に割り当てる](https://go.microsoft.com/fwlink/p?LinkID=329805)には、「PowerShell を使用する方法」を参照してください。