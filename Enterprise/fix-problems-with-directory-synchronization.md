---
title: Office 365 のディレクトリ同期の問題を解決する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365 のディレクトリ同期に関する問題の一般的な原因について説明し、トラブルシューティングと解決に役立ついくつかの方法について説明します。
ms.openlocfilehash: cc0fe15d0d49542489ac1e586efbe99d0846b3ab
ms.sourcegitcommit: fbd2f3fb297c508212baed3ee9d1ce51765cc8bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2019
ms.locfileid: "39254526"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期の問題を解決する

ディレクトリ同期を使用すると、ユーザーとグループを社内で管理し続け、追加、削除、および変更をクラウドに同期できます。 しかし、セットアップは少し複雑で、問題の原因を特定するのが困難な場合があります。 潜在的な問題を特定して修正するのに役立つリソースが用意されています。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>問題があるかどうかを確認する方法

最初に間違ったことが示されている場合は、Microsoft 365 管理センターの [DirSync Status] タイルに問題があることを示しています。
  
また、テナントがディレクトリ同期エラーを検出したことを示す、Office 365 からのメール (連絡メールと管理者の電子メールへ) を受信することになります。 詳細については、「 [Office 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory Connect ツールを入手するにはどうすればよいですか?

[Microsoft 365 管理センター](https://admin.microsoft.com)で、[**ユーザー** \> ] [**アクティブなユーザー**] に移動します。 [**その他**] メニュー (3 つのドット) をクリックし、[**ディレクトリ同期**] を選択します。 
  
ウィザードの[指示](set-up-directory-synchronization.md)に従って、Azure AD Connect をダウンロードします。 
  
まだ Azure Active Directory 同期 (DirSync) を使用している場合は、「 [365 Office system の Azure Active Directory 同期ツールのインストールと構成ウィザードのエラーメッセージ」](https://go.microsoft.com/fwlink/p/?LinkId=396717)を参照してください。これには、dirsync をインストールするためのシステム要件、必要なアクセス許可、および一般的なエラーのトラブルシューティング方法に関する情報が含まれます。 
  
Azure Active Directory 同期から Azure AD Connect に更新するには、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Office 365 でのディレクトリ同期に関する問題の一般的な原因の解決

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同期されたオブジェクトは、オンラインで表示または更新されません。または、サービスから同期エラーレポートを取得しています。**

- [Id 同期と重複属性の復元](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**管理センターに通知があります。または、最近の同期イベントが発生していない自動メールを受信しています。**
- [Azure AD Connect による接続の問題のトラブルシューティング](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect のアカウントとアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect sync: Azure AD サービスアカウントを管理する方法](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory とのディレクトリ同期が停止するか、同期が1日以上登録されていないことを示す警告が表示される](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**パスワードハッシュが同期されていない、または管理センターに最近のパスワードハッシュ同期がないことを示すアラートが表示されている**
- [Azure AD Connect 同期を使用したパスワードハッシュ同期の実装](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**オブジェクトクォータを超えたという警告が表示されています**
- サービスを保護するために、組み込みのオブジェクトクォータが用意されています。 Office 365 と同期する必要があるディレクトリ内のオブジェクトが多すぎる場合は、[ビジネス製品のサポートに連絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)してクォータを増やす必要があります。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**どの属性が同期されているかを知る必要がある**
- オンプレミスとクラウドの間で同期されているすべての属性の一覧については、[こちら](https://go.microsoft.com/fwlink/p/?LinkId=396719)を参照してください。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**クラウドに同期されたオブジェクトを管理または削除できません**
- クラウド内のオブジェクトのみを管理する準備はできていますか。 または、オンプレミスで削除されたオブジェクトは存在しますか。クラウドに保持されていますか? これらの問題を解決する方法については、「同期とサポート」の[記事に記載](https://go.microsoft.com/fwlink/p/?LinkId=396720)されている[トラブルシューティングエラー](https://go.microsoft.com/fwlink/p/?linkid=842044)を参照してください。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**会社が同期できるオブジェクトの数を超えたというエラーメッセージが表示されました**
- この問題の詳細については、[こちら](https://go.microsoft.com/fwlink/p/?LinkId=396721)を参照してください。
   
## <a name="other-resources"></a>その他のリソース

- [ユーザー プリンシパル名の重複を修正するためのスクリプト](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [ディレクトリ同期にルーティング可能ではないドメイン (たとえば、ローカルドメイン) を準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [同期されたオブジェクトの合計数をカウントするためのスクリプト](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [AD FS 2.0 のトラブルシューティング](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [PowerShell を使用して、メールが有効なグループの空の DisplayName 属性を修正する](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [PowerShell を使用して重複した UPN を修正する](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [PowerShell を使用して重複した電子メールアドレスを修正する](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>診断ツール

[Idfix ツール](prepare-directory-attributes-for-synch-with-idfix.md)は、Office 365 への移行の準備として、オンプレミスの Active Directory 環境での id オブジェクトとその属性の検出と修復を実行するために使用されます。 IDFix は、Office 365 サービスとのディレクトリ同期を担当する Active Directory 管理者を対象としています。 

[IDFix ツール](https://go.microsoft.com/fwlink/p/?LinkId=396718)を Microsoft ダウンロードセンターからダウンロードします。