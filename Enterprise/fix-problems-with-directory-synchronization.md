---
title: Microsoft 365 のディレクトリ同期に関する問題の修正
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
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
description: Office 365 のディレクトリ同期の問題の一般的な原因を示し、問題のトラブルシューティングと解決に役立ついくつかの方法を紹介します。
ms.openlocfilehash: faf0f061b8f2798054e63f3338b8076c0ec88f73
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "46570970"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Microsoft 365 のディレクトリ同期に関する問題の修正

ディレクトリ同期を使用することにより、社内のユーザーおよびグループを継続的に管理して、クラウドへの追加、削除、変更を同期することができます。 ただし、セットアップは少し複雑であり、問題の原因を特定することが困難な場合があります。 潜在的な問題を特定してそれを修正するのに役立つリソースがあります。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>問題がある場合に確認する方法

問題がある場合に最初の通知として、Microsoft 365 管理センターにある同期ツールの状態タイルに次のように問題があると示されます。
  
Microsoft 365 からディレクトリの同期エラーが発生したテナントを示すメール (連絡用メール アドレスと管理者メール宛) も受信します。 詳細については、「[Microsoft 365 でディレクトリ同期エラーを特定する](identify-directory-synchronization-errors.md)」を参照してください。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory Connect ツールを入手する方法

[Microsoft 365 管理センター](https://admin.microsoft.com) では、**[ユーザー]** \> **[アクティブ ユーザー]** の順に移動します。 **[その他]** メニュー (3つの点) をクリックして、**[ディレクトリ同期]** を選択します。 
  
[ウィザードの指示](set-up-directory-synchronization.md) に従って、Azure AD Connect をダウンロードします。 
  
まだ Azure Active Directory (Azure AD) Sync (DirSync) を使用している場合、dirsync をインストールするためのシステム要件、必要なアクセス許可、一般的なエラーのトラブルシューティング方法については、[「Azure Active Directory 同期ツールのインストールと Microsoft 365 の構成ウィザードのエラー メッセージをトラブルシューティングする方法」](https://go.microsoft.com/fwlink/p/?LinkId=396717) を参照してください。 
  
Azure AD Sync から Azure AD Connect に更新するには、「[アップグレード手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)」 を参照してください。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Microsoft 365 でのディレクトリ同期の問題の一般的な原因

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>同期対象オブジェクトがオンラインで表示または更新されない場合、サービスから同期エラー レポートを受け取ります。

- [ID 同期と重複属性の回復性](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>管理センターで警告を受け取ったか、または最近、同期イベントがないという自動メールを受け取ります。
- [Azure AD Connect での接続に関する問題のトラブルシューティング](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect: アカウントとアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD Connect 同期: Azure AD サービス アカウントを管理する方法](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory 同期ツールによる同期処理が停止する、または同期が 24 時間以上実行されていないという内容のメッセージを受け取る](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>パスワードが同期されていないか、またはパスワード ハッシュの同期がないという警告が最近管理センターに表示される
- [Azure AD Connect Sync を使用してパスワード ハッシュの同期を実装する](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>オブジェクト クォータの超過通知が表示される
- サービスを保護するのに役立つ、組み込みのオブジェクト クォータがあります。 Microsoft 365 に同期する必要があるオブジェクトの数が多すぎる場合、クォータを増やすために [一般法人向け製品のサポートに連絡](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) する必要があります。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>どの属性が同期されているか知る必要があります。
- オンプレミス環境とクラウドとの間で同期されるすべての属性の一覧については、[このページ](https://go.microsoft.com/fwlink/p/?LinkId=396719) を参照してください。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>クラウドに同期されたオブジェクトを管理または削除できない
- クラウドのみでオブジェクトを管理する準備ができていますか。 あるいは、社内で削除されたものの、クラウドでスタックしているオブジェクトがありますか。 このような問題を解決する方法については、[「同期中に発生したエラーのトラブルシューティング」](https://go.microsoft.com/fwlink/p/?linkid=842044) と [サポート記事](https://go.microsoft.com/fwlink/p/?LinkId=396720) を参照してください。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>会社で同期可能なオブジェクトの数を超えたというエラー メッセージが表示されました。
- この問題の詳細については、[このページ](https://go.microsoft.com/fwlink/p/?LinkId=396721) を参照してください。
   
## <a name="other-resources"></a>その他のリソース

- [ユーザー プリンシパル名の重複を修正するためのスクリプト](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [ディレクトリ同期用に (.local ドメインなどの) 非ルーティング ドメインを準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [同期されたオブジェクトの総数を取得するためのスクリプト](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [AD FS 2.0 のトラブルシューティング](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [PowerShell を使ってメールが有効なグループの空の DisplayName 属性を修正する](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [PowerShell を使ってユーザー プリンシパル名の重複を修正する](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [PowerShell を使ってメール アドレスの重複を修正する](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
