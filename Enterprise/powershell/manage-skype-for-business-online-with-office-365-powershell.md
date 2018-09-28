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
# <a name="manage-skype-for-business-online-with-office-365-powershell"></a><span data-ttu-id="71a86-103">Office 365 PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="71a86-103">Manage Skype for Business Online with Office 365 PowerShell</span></span>

 <span data-ttu-id="71a86-104">**概要:** Office 365 PowerShell を使用して、Skype for Business Online ポリシー、ユーザー単位ポリシー、会議の設定を管理します。</span><span class="sxs-lookup"><span data-stu-id="71a86-104">**Summary:** Use Office 365 PowerShell to manage Skype for Business Online policies, per-user policies, and meeting settings.</span></span>
  
<span data-ttu-id="71a86-p101">ポリシーを管理するオンライン ビジネス管理者は、Skype の主なタスクの 1 つです。Office 365 の管理センターでこれらのタスクのいくつかの操作を行うことができます、その他のタスクはかなり迅速かつ簡単に Office 365 の PowerShell。</span><span class="sxs-lookup"><span data-stu-id="71a86-p101">One of the primary tasks of any Skype for Business Online administrator is managing policies. Although you can accomplish some of these tasks in the Office 365 Admin center, other tasks are much quicker and easier in Office 365 PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="71a86-107">始める前に</span><span class="sxs-lookup"><span data-stu-id="71a86-107">Before you start</span></span>

<span data-ttu-id="71a86-108">ダウンロードおよびインストール[ビジネス オンライン コネクタ モジュールの Skype](https://www.microsoft.com/en-us/download/details.aspx?id=39366)では、および要求された場合、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="71a86-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/en-us/download/details.aspx?id=39366), and then restart your computer if prompted.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="71a86-109">オンライン ビジネス管理者のアカウント名とパスワードは、Skype を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="71a86-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="71a86-110">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="71a86-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="71a86-111">**Windows PowerShell の資格情報の要求**] ダイアログ ボックスでは、オンライン ビジネスの管理者のアカウント名とパスワードは、Skype を入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71a86-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multifactor-authentication"></a><span data-ttu-id="71a86-112">マルチファクター認証方法とオンライン ビジネスの管理者アカウントに、Skype を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="71a86-112">Connect using a Skype for Business Online administrator account with multifactor authentication</span></span>

1. <span data-ttu-id="71a86-113">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="71a86-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="71a86-114">**新しい CsOnlineSession**コマンドによってダイアログ ボックスが表示されたら、オンライン ビジネスの管理者アカウント名を Skype を入力します。</span><span class="sxs-lookup"><span data-stu-id="71a86-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="71a86-115">**アカウントにサイン イン**] ダイアログ ボックスで、Skype をオンライン ビジネスの管理者パスワードを入力し、し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71a86-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="71a86-116">検証コードなどの追加の認証情報を提供する**お客様のアカウントにサインイン**する] ダイアログ ボックスの指示に従って、[**確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="71a86-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="71a86-117">詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="71a86-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="71a86-118">Office 365 PowerShell を使用して Skype for Business Online ポリシーを管理する</span><span class="sxs-lookup"><span data-stu-id="71a86-118">Manage Skype for Business Online policies with Office 365 PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="71a86-119">Office 365 PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる</span><span class="sxs-lookup"><span data-stu-id="71a86-119">Assign per-user Skype for Business Online policies with Office 365 PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="71a86-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="71a86-120">See also</span></span>

[<span data-ttu-id="71a86-121">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="71a86-121">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="71a86-122">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="71a86-122">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="71a86-123">ビジネスの PowerShell コマンドレットの参照のための Skype</span><span class="sxs-lookup"><span data-stu-id="71a86-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

