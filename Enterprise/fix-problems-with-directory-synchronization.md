---
title: Microsoft 365 のディレクトリ同期に関する問題の解決
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
ms.openlocfilehash: cb2ec57331d227f0965095ee0782f13af935d569
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711910"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Microsoft 365 のディレクトリ同期に関する問題の解決

ディレクトリ同期を使用すると、ユーザーとグループを社内で管理し続け、追加、削除、および変更をクラウドに同期できます。 しかし、セットアップは少し複雑で、問題の原因を特定するのが困難な場合があります。 潜在的な問題を特定して修正するのに役立つリソースが用意されています。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>問題があるかどうかを確認する方法

最初に間違ったことが示されている場合は、Microsoft 365 管理センターの [DirSync Status] タイルに問題があることを示しています。
  
また、テナントでディレクトリ同期エラーが検出されたことを示すメール (連絡用メールと管理者向けメール) も Microsoft 365 から受け取ります。 詳細については、「 [Microsoft 365 でのディレクトリ同期エラーの識別](identify-directory-synchronization-errors.md)」を参照してください。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory Connect ツールを入手するにはどうすればよいですか?

[Microsoft 365 管理センター](https://admin.microsoft.com)で、[**ユーザー** ] [ \> **アクティブなユーザー**] に移動します。 [**その他**] メニュー (3 つのドット) をクリックし、[**ディレクトリ同期**] を選択します。 
  
ウィザードの[指示](set-up-directory-synchronization.md)に従って、Azure AD Connect をダウンロードします。 
  
まだ Azure Active Directory 同期 (DirSync) を使用している場合は、「 [Microsoft 365 での Azure Active Directory 同期ツールのインストールと構成ウィザードのエラーメッセージ](https://go.microsoft.com/fwlink/p/?LinkId=396717)」を参照してください。 dirsync をインストールするためのシステム要件、必要なアクセス許可、および一般的なエラーのトラブルシューティング方法について説明します。 
  
Azure Active Directory 同期から Azure AD Connect に更新するには、[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Microsoft 365 でのディレクトリ同期に関する問題の一般的な原因の解決

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同期されたオブジェクトは、オンラインで表示または更新されません。または、サービスから同期エラーレポートを取得しています。**

- [ID 同期と重複属性の回復性](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**管理センターに通知があります。または、最近の同期イベントが発生していない自動メールを受信しています。**
- [Azure AD Connect での接続に関する問題のトラブルシューティング](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect: アカウントとアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect 同期: Azure AD サービス アカウントを管理する方法](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory 同期ツールによる同期処理が停止する、または同期が 24 時間以上実行されていないという内容のメッセージを受け取る](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**パスワードハッシュが同期されていない、または管理センターに最近のパスワードハッシュ同期がないことを示すアラートが表示されている**
- [Azure AD Connect Sync を使用してパスワード ハッシュの同期を実装する](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**オブジェクトクォータを超えたという警告が表示されています**
- サービスを保護するために、組み込みのオブジェクトクォータが用意されています。 Microsoft 365 に同期する必要があるディレクトリ内のオブジェクトが多すぎる場合は、予算を増やすために、[ビジネス製品のサポートに連絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)する必要があります。

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

[Idfix ツール](prepare-directory-attributes-for-synch-with-idfix.md)は、Microsoft 365 への移行の準備として、オンプレミスの Active Directory 環境での id オブジェクトとその属性の検出と修復を実行するために使用されます。 IDFix は、Microsoft 365 サービスとのディレクトリ同期を担当する Active Directory 管理者を対象としています。 

[IDFix ツール](https://go.microsoft.com/fwlink/p/?LinkId=396718)を Microsoft ダウンロードセンターからダウンロードします。