---
title: PowerShell を使用して Skype for Business Online を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: '概要: PowerShell for Microsoft 365 を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。'
ms.openlocfilehash: 10587dad171c3df9de6985ad314bc1791080b8a1
ms.sourcegitcommit: 839236443410eb804372c4aae969ac9a82ba683b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "46592211"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>PowerShell を使用して Skype for Business Online を管理する

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

Skype for Business Online 管理者の主要なタスクの 1 つは、ポリシーの管理です。 Microsoft 365 管理センターでもこれらのタスクの一部を実行できますが、他のタスクについては、PowerShell のほうがより早く簡単に実行できます。 

## <a name="before-you-start"></a>始める前に

[Skype for Business Online Connector モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をダウンロードしてインストールし、コンピューターを再起動します。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Skype for Business Online 管理者のアカウント名とパスワードを使用して接続する

1. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します: 
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. [**Windows PowerShell 資格情報の要求**] ダイアログ ボックスに Skype for Business Online 管理者のアカウント名とパスワードをを入力し、[**OK**] をクリックします。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a>多要素認証で Skype for Business Online 管理者アカウントを使用して接続する

1. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. **New-CsOnlineSession** コマンドでダイアログ ボックスが表示されたら、Skype for Business Online 管理者のアカウント名を入力します。

3. [**アカウントにサインイン**] ダイアログ ボックスで、Skype for Business Online 管理者のパスワードを入力し、[**サインイン**] をクリックします。

4. [**アカウントにサインイン**] ダイアログ ボックスの手順に従い、確認コードなどのその他の認証情報を入力し、[**確認**] をクリックします。

詳細については、次のトピックをご覧ください。
  
- [PowerShell を使用して Skype for Business Online を管理する](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>関連項目

[PowerShell で Microsoft 365を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 用 PowerShell の使用を開始する](getting-started-with-office-365-powershell.md)

[Skype for Business PowerShell のコマンドレット リファレンス](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

