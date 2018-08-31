---
title: Office 365 のディレクトリ同期に関する問題の修正
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365 のディレクトリ同期の問題の一般的な原因を説明し、トラブルシューティングし、解決に役立ついくつかのメソッドを提供します。
ms.openlocfilehash: ad3b6e27439354a2ede9b1a4b100e0f9e06148d3
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541584"
---
# <a name="fixing-problems-with-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期に関する問題の修正

ディレクトリ同期によって、ユーザーとグループの設置を管理し、追加、削除、およびクラウドへの変更の同期を続行できます。セットアップは少し複雑な問題の原因を特定することは困難があります。潜在的な問題を識別し、それらを修正するためのリソースがあります。
  
## <a name="how-do-i-know-if-something-is-wrong"></a>何かが間違った方法を教えてください。

何かが間違っていることを示す最初の兆候は、Office 365 の管理センターのディレクトリ同期の状態のタイルでは、問題が示されている場合です。
  
![管理センターのプレビュー] で、ディレクトリ同期の状態を並べて表示します。](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
Office 365 のテナントには、ディレクトリ同期のエラーが発生したためであることを示すからメールを別の電子メールなど、管理者の電子メールにも表示されます。詳細については、 [Office 365 のディレクトリ同期エラーを識別する](identify-directory-synchronization-errors.md)を参照してください。
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory 接続ツールを取得する方法は?

Office 365 管理センターで、[に移動 * * ユーザー * * \> **アクティブなユーザー**です。[**詳細**] メニューのをクリックし、**ディレクトリ同期**を選択します。 
  
![[詳細] メニューの [ディレクトリ同期を選択します](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
古い Office 365 管理センターでは、**ユーザー**に移動\>**アクティブなユーザー**、および選択**の設定****作業中のディレクトリ同期**の横にあります。 
  
![Active Directory の同期の横のセットを選択します。](media/bd95492b-d65e-4072-a6ee-e562f5f566c3.png)
  
Azure AD 接続をダウンロードするのには[、ウィザードの指示](set-up-directory-synchronization.md)に従います。 
  
まだ Azure Active ディレクトリ同期 (ディレクトリ同期) を使用している場合を見て[Azure Active Directory 同期ツールのインストールと Office 365 の構成ウィザードのエラー メッセージをトラブルシューティングする方法](https://go.microsoft.com/fwlink/p/?LinkId=396717)をインストールするシステムの要件についてディレクトリ同期、必要なアクセス許可および一般的なエラーのトラブルシューティングを行う方法です。 
  
Azure Active Directory 同期から Azure AD 接続を更新するには、[アップグレードの手順](https://go.microsoft.com/fwlink/p/?LinkId=733240)を参照してください。
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-office-365"></a>Office 365 のディレクトリ同期の問題の原因は一般的な解決

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**同期されたオブジェクトは表示されないようにしたり、オンラインで更新またはサービスから同期エラーのレポートを取得します。**

- [アイデンティティの同期化と重複している属性の弾力性](https://go.microsoft.com/fwlink/p/?LinkID=798300)

### <a name="i-have-an-alert-in-the-office-365-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Office 365 管理センターで、アラートがあるか、または最新の同期イベントが発生されていない自動の電子メールを受信しています。**
- [Azure AD 接続と接続の問題のトラブルシューティングを行う](https://go.microsoft.com/fwlink/p/?LinkId=820597)
- [Azure AD 接続アカウントとアクセス許可](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Azure AD 接続の同期: Azure AD のサービス アカウントを管理する方法](https://go.microsoft.com/fwlink/p/?LinkId=820599)
- [Azure Active Directory が停止するか、またはディレクトリ同期は 1 日以上で、同期していない登録されている警告メッセージが表示しています。](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-office-365-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**パスワード ハッシュが同期されていない、または最近使用したパスワード ハッシュの同期がありますされていない Office 365 管理センターの警告が表示**
- [Azure AD 接続の同期でのパスワード ハッシュの同期を実装します。](https://go.microsoft.com/fwlink/p/?LinkId=820600)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**オブジェクト クォータを超過したアラートが表示します。**
- サービスを保護するための組み込みオブジェクトのクォータがあります。Office 365 に同期する必要のあるディレクトリに多数のオブジェクトがある場合は、クォータを増やすには、[ビジネス製品に関するサポートの連絡先](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)に必要があります。

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**どの属性が同期されているか知る必要があります。**
- オンプレミスとクラウド[は、ここで右](https://go.microsoft.com/fwlink/p/?LinkId=396719)の間で同期されるすべての属性の一覧が表示されます。

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**管理またはクラウドに同期されたオブジェクトを削除できません。**
- クラウドのみでオブジェクトを管理する準備ができて、ですか。または、オブジェクトを削除した設置が、クラウドに詰まっているではないでしょうか。見てこの[同期中にエラーのトラブルシューティング](https://go.microsoft.com/fwlink/p/?linkid=842044)とガイダンスの[サポート資料](https://go.microsoft.com/fwlink/p/?LinkId=396720)をこれらの問題を解決する方法にします。

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**会社で同期可能なオブジェクトの数を超えたというエラー メッセージが表示されました。**
- 詳細を読み取ることができますこの問題について[は、ここ](https://go.microsoft.com/fwlink/p/?LinkId=396721)です。
   
## <a name="other-resources"></a>その他のリソース

- [重複するユーザー プリンシパル名を解決するためのスクリプト](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [ディレクトリ同期 (.local ドメイン) などのルーティング不可能なドメインを準備する方法](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [同期オブジェクトの総数をカウントするためのスクリプト](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [AD FS 2.0 のトラブルシューティングを行う](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [PowerShell を使用して、メールが有効なグループを空の DisplayName 属性を修正するには](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [PowerShell を使用して、重複する UPN を解決するには](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [PowerShell を使用して、重複する電子メール アドレスを修正するには](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>診断ツール

[IDFix ツール](prepare-directory-attributes-for-synch-with-idfix.md)を使用して、Office 365 への移行の準備として、オンプレミス Active Directory 環境での検出と id オブジェクトとその属性の修復を実行します。IDFix は、Active Directory の管理者は、Office 365 サービスとディレクトリ同期の責任です。 

Microsoft ダウンロード センターから[IDFix ツールをダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=396718)をしてください。