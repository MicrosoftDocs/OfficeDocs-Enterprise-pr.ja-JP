---
title: PowerShell を使用して Skype for Business Online を管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: '概要: Microsoft 365 の PowerShell を使用して、Skype for Business Online ポリシー、ユーザーごとのポリシー、会議の設定を管理します。'
ms.openlocfilehash: f66b3186a5b29bbf0756a629b85c626caf2c1e36
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230443"
---
# <a name="manage-skype-for-business-online-with-powershell"></a><span data-ttu-id="59014-103">PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="59014-103">Manage Skype for Business Online with PowerShell</span></span>

<span data-ttu-id="59014-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="59014-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="59014-105">Skype for Business Online 管理者にとって主要なタスクの 1 つはポリシーを管理することです。</span><span class="sxs-lookup"><span data-stu-id="59014-105">One of the primary tasks of any Skype for Business Online administrator is managing policies.</span></span> <span data-ttu-id="59014-106">これらのタスクの一部は Microsoft 365 管理センターで実行できますが、PowerShell では、他のタスクがより速く、簡単になります。</span><span class="sxs-lookup"><span data-stu-id="59014-106">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier in PowerShell.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="59014-107">始める前に</span><span class="sxs-lookup"><span data-stu-id="59014-107">Before you start</span></span>

<span data-ttu-id="59014-108">[Skype For Business Online Connector モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をダウンロードしてインストールし、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="59014-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366), and then restart your computer.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-name-and-password"></a><span data-ttu-id="59014-109">Skype for Business Online 管理者のアカウント名とパスワードを使用して接続する</span><span class="sxs-lookup"><span data-stu-id="59014-109">Connect using a Skype for Business Online administrator account name and password</span></span>

1. <span data-ttu-id="59014-110">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="59014-110">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $userCredential = Get-Credential
  $sfbSession = New-CsOnlineSession -Credential $userCredential
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="59014-111">[ **Windows PowerShell 資格情報の要求**] ダイアログボックスで、Skype For business Online 管理者のアカウント名とパスワードを入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59014-111">In the **Windows PowerShell Credential Request** dialog box, type your Skype for Business Online administrator account name and password, and then click **OK**.</span></span>


## <a name="connect-using-a-skype-for-business-online-administrator-account-with-multi-factor-authentication"></a><span data-ttu-id="59014-112">多要素認証を使用して Skype for Business Online 管理者アカウントを使用して接続する</span><span class="sxs-lookup"><span data-stu-id="59014-112">Connect using a Skype for Business Online administrator account with multi-factor authentication</span></span>

1. <span data-ttu-id="59014-113">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="59014-113">Open a Windows PowerShell command prompt and run the following commands:</span></span>

  ```powershell
  Import-Module SkypeOnlineConnector
  $sfbSession = New-CsOnlineSession
  Import-PSSession $sfbSession
  ```

2. <span data-ttu-id="59014-114">**新しい-Cssession**コマンドによってメッセージが表示されたら、Skype For business Online 管理者のアカウント名を入力します。</span><span class="sxs-lookup"><span data-stu-id="59014-114">When prompted by the **New-CsOnlineSession** command, enter your Skype for Business Online administrator account name.</span></span>

3. <span data-ttu-id="59014-115">[**アカウントにサインインする**] ダイアログボックスで、Skype For business Online 管理者パスワードを入力し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59014-115">In the **Sign in to your account** dialog box, type your Skype for Business Online administrator password, and then click **Sign in**.</span></span>

4. <span data-ttu-id="59014-116">[**アカウントにサインイン**する] ダイアログボックスの指示に従って、検証コードなどの追加の認証情報を入力し、[**確認**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="59014-116">Follow the instructions in the **Sign in to your account** dialog box to provide additional authentication information, such as a verification code, and then click **Verify**.</span></span>

<span data-ttu-id="59014-117">詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="59014-117">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="59014-118">PowerShell を使用して Skype for Business Online のポリシーを管理する</span><span class="sxs-lookup"><span data-stu-id="59014-118">Manage Skype for Business Online policies with PowerShell</span></span>](manage-skype-for-business-online-policies-with-office-365-powershell.md)
    
- [<span data-ttu-id="59014-119">PowerShell を使用してユーザーごとに Skype for Business Online のポリシーを割り当てる</span><span class="sxs-lookup"><span data-stu-id="59014-119">Assign per-user Skype for Business Online policies with PowerShell</span></span>](assign-per-user-skype-for-business-online-policies-with-office-365-powershell.md)
    
## <a name="see-also"></a><span data-ttu-id="59014-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="59014-120">See also</span></span>

[<span data-ttu-id="59014-121">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="59014-121">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="59014-122">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="59014-122">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

[<span data-ttu-id="59014-123">Skype for Business PowerShell コマンドレットリファレンス</span><span class="sxs-lookup"><span data-stu-id="59014-123">Skype for Business PowerShell cmdlet references</span></span>](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)

