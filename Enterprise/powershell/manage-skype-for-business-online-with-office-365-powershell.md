---
title: Office 365 PowerShell を使用して Skype for Business Online を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 概要:Office 365 PowerShell を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。
ms.openlocfilehash: a91803316972337aa31e2b979f841ac1cfbe8566
ms.sourcegitcommit: 053db5479f93478a65d4c36ffe44c6a7bcb60e3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "23965194"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a>Office 365 PowerShell を使用して Skype for Business Online を管理する

 **概要:** Office 365 PowerShell を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。
  
ポリシーを管理するオンライン ビジネス管理者は、Skype の主なタスクの 1 つです。Office 365 の管理センターでこれらのタスクのいくつかの操作を行うことができます、その他のタスクはかなり迅速かつ簡単に Office 365 の PowerShell。 

## <a name="before-you-start"></a>始める前に

ダウンロードおよびインストール[ビジネス オンライン コネクタ モジュールの Skype](https://www.microsoft.com/en-us/download/details.aspx?id=39366)では、および要求された場合、コンピューターを再起動します。


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a>オンライン ビジネス管理者のアカウント名とパスワードは、Skype を使用して接続します。

1. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します: 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. **Windows PowerShell の資格情報の要求**] ダイアログ ボックスでは、オンライン ビジネスの管理者のアカウント名とパスワードは、Skype を入力し、し、[ **OK**] をクリックします。


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a>マルチファクター認証方法とオンライン ビジネスの管理者アカウントに、Skype を使用して接続します。

1. Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. **新しい CsOnlineSession**コマンドによってダイアログ ボックスが表示されたら、オンライン ビジネスの管理者アカウント名を Skype を入力します。

3. **アカウントにサイン イン**] ダイアログ ボックスで、Skype をオンライン ビジネスの管理者パスワードを入力し、し、[**サインイン**] をクリックします。

4. 検証コードなどの追加の認証情報を提供する**お客様のアカウントにサインイン**する] ダイアログ ボックスの指示に従って、[**確認**] をクリックします。

詳細については、以下のトピックを参照してください。
  
- [Office 365 PowerShell を使用して Skype for Business Online ポリシーを管理する](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a>関連項目

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

[ビジネスの PowerShell コマンドレットの参照のための Skype](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

