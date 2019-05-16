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
ms.openlocfilehash: 33c7247686cc8eb308b8db6d4900c89f693004fb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068733"
---
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="fe79d-103">Office 365 PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="fe79d-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="fe79d-104">**概要:** Office 365 PowerShell を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。</span><span class="sxs-lookup"><span data-stu-id="fe79d-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="fe79d-105">Skype for Business Online 管理者にとって主要なタスクの 1 つはポリシーを管理することです。</span><span class="sxs-lookup"><span data-stu-id="fe79d-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="fe79d-106">これらのタスクの一部は Office 365 管理センターで実行できますが、Office 365 PowerShell では、他のタスクがより速く、簡単になります。</span><span class="sxs-lookup"><span data-stu-id="fe79d-106">Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="fe79d-107">始める前に</span><span class="sxs-lookup"><span data-stu-id="fe79d-107">Before you start</span></span>

<span data-ttu-id="fe79d-108">[Skype For Business Online Connector モジュール](https://www.microsoft.com/en-us/download/details.aspx?id=39366)をダウンロードしてインストールし、メッセージが表示された場合はコンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="fe79d-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="fe79d-109">Skype for Business Online 管理者のアカウント名とパスワードを使用して接続する</span><span class="sxs-lookup"><span data-stu-id="fe79d-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="fe79d-110">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="fe79d-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="fe79d-111">[ **Windows PowerShell 資格情報の要求**] ダイアログボックスで、Skype For business Online 管理者のアカウント名とパスワードを入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe79d-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="fe79d-112">多要素認証を使用して Skype for Business Online 管理者アカウントを使用して接続する</span><span class="sxs-lookup"><span data-stu-id="fe79d-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="fe79d-113">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="fe79d-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="fe79d-114">**新しい-Cssession**コマンドによってメッセージが表示されたら、Skype For business Online 管理者のアカウント名を入力します。</span><span class="sxs-lookup"><span data-stu-id="fe79d-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="fe79d-115">[**アカウントにサインインする**] ダイアログボックスで、Skype For business Online 管理者パスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe79d-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="fe79d-116">[**アカウントにサインイン**する] ダイアログボックスの指示に従って、検証コードなどの追加の認証情報を入力し、[**確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe79d-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="fe79d-117">詳細については、以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fe79d-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="fe79d-118">Office 365 PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="fe79d-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="fe79d-119">Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる</span><span class="sxs-lookup"><span data-stu-id="fe79d-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="fe79d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe79d-120">See also</span></span>

[<span data-ttu-id="fe79d-121">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="fe79d-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fe79d-122">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="fe79d-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="fe79d-123">Skype for Business PowerShell コマンドレットリファレンス</span><span class="sxs-lookup"><span data-stu-id="fe79d-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

