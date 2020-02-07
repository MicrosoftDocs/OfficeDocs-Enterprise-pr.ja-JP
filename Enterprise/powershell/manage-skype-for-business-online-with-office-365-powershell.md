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
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: 概要:Office 365 PowerShell を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。
ms.openlocfilehash: 699f799e823df6192a65147210130ae6493f52eb
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844228"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="8e0c7-103">Office 365 PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="8e0c7-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

<span data-ttu-id="8e0c7-104">Skype for Business Online 管理者にとって主要なタスクの 1 つはポリシーを管理することです。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-104">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="8e0c7-105">Microsoft 365 管理センターでもこれらのタスクの一部を実行できますが、他のタスクについては、Office 365 PowerShell のほうがより早く簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="8e0c7-106">始める前に</span><span class="sxs-lookup"><span data-stu-id="8e0c7-106">Before you start</span></span>

<span data-ttu-id="8e0c7-107">[Skype For Business Online Connector モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をダウンロードしてインストールし、メッセージが表示された場合はコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-107">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="8e0c7-108">Skype for Business Online 管理者のアカウント名とパスワードを使用して接続する</span><span class="sxs-lookup"><span data-stu-id="8e0c7-108">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="8e0c7-109">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="8e0c7-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="8e0c7-110">[ **Windows PowerShell 資格情報の要求**] ダイアログボックスで、Skype For business Online 管理者のアカウント名とパスワードを入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-110">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="8e0c7-111">多要素認証を使用して Skype for Business Online 管理者アカウントを使用して接続する</span><span class="sxs-lookup"><span data-stu-id="8e0c7-111">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="8e0c7-112">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="8e0c7-112">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="8e0c7-113">**新しい-Cssession**コマンドによってメッセージが表示されたら、Skype For business Online 管理者のアカウント名を入力します。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-113">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="8e0c7-114">[**アカウントにサインインする**] ダイアログボックスで、Skype For business Online 管理者パスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-114">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="8e0c7-115">[**アカウントにサインイン**する] ダイアログボックスの指示に従って、検証コードなどの追加の認証情報を入力し、[**確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-115">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="8e0c7-116">詳細については、以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8e0c7-116">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="8e0c7-117">Office 365 PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="8e0c7-117">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="8e0c7-118">Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる</span><span class="sxs-lookup"><span data-stu-id="8e0c7-118">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="8e0c7-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e0c7-119">See also</span></span>

[<span data-ttu-id="8e0c7-120">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="8e0c7-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8e0c7-121">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="8e0c7-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="8e0c7-122">Skype for Business PowerShell コマンドレットリファレンス</span><span class="sxs-lookup"><span data-stu-id="8e0c7-122">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

