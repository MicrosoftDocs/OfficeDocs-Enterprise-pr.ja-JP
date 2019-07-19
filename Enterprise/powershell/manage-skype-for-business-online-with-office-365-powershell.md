---
title: Office 365 PowerShell を使用して Skype for Business Online を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 概要:Office 365 PowerShell を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。
ms.openlocfilehash: 80d8308a1c9b32fcafd47d1df2f699141e41accd
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782137"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Office 365 PowerShell を使用して Skype for Business Online を管理する

 **概要:** Office 365 PowerShell を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。
  
Skype for Business Online 管理者にとって主要なタスクの 1 つはポリシーを管理することです。 Microsoft 365 管理センターでもこれらのタスクの一部を実行できますが、他のタスクについては、Office 365 PowerShell のほうがより早く簡単に実行できます。 

## <a name="before-you-start"></a>始める前に

[Skype For Business Online Connector モジュール](https://www.microsoft.com/en-us/download/details.aspx?id=39366)をダウンロードしてインストールし、メッセージが表示された場合はコンピューターを再起動します。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>Skype for Business Online 管理者のアカウント名とパスワードを使用して接続する

1. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. [ **Windows PowerShell 資格情報の要求**] ダイアログボックスで、Skype For business Online 管理者のアカウント名とパスワードを入力し、[ **OK**] をクリックします。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>多要素認証を使用して Skype for Business Online 管理者アカウントを使用して接続する

1. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. **新しい-Cssession**コマンドによってメッセージが表示されたら、Skype For business Online 管理者のアカウント名を入力します。

3. [**アカウントにサインインする**] ダイアログボックスで、Skype For business Online 管理者パスワードを入力し、[**サインイン**] をクリックします。

4. [**アカウントにサインイン**する] ダイアログボックスの指示に従って、検証コードなどの追加の認証情報を入力し、[**確認**] をクリックします。

詳細については、以下のトピックをご覧ください。
  
- [Office 365 PowerShell を使用して Skype for Business Online を管理する](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>関連項目

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

[Skype for Business PowerShell コマンドレットリファレンス](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

