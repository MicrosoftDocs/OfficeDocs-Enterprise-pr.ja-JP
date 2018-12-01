---
title: ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Office 365 PowerShell を使って、ライセンスのあるユーザー アカウントとライセンスのないユーザー アカウントを表示する方法について説明します。
ms.openlocfilehash: 61f94664a62b6a5cb178579c1a5777b208d0b2ec
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123364"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="39d38-103">ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する</span><span class="sxs-lookup"><span data-stu-id="39d38-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="39d38-104">**概要:** Office 365 PowerShell を使って、ライセンスのあるユーザー アカウントとライセンスのないユーザー アカウントを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d38-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="39d38-p101">Office 365 組織のユーザー アカウントには、組織で使用可能なライセンス プランからユーザー アカウントに割り当てることのできるライセンスが一部またはすべて存在する場合や、まったく存在しない場合があります。Office 365 PowerShell を使うと、組織内でライセンスのあるユーザーとライセンスのないユーザーをすばやく検索できます。</span><span class="sxs-lookup"><span data-stu-id="39d38-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="39d38-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="39d38-107">Before you begin</span></span>

- <span data-ttu-id="39d38-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39d38-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="39d38-110">_-All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="39d38-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="viewing-licensed-and-unlicensed-users"></a><span data-ttu-id="39d38-111">ライセンスおよびライセンスのないユーザーの表示</span><span class="sxs-lookup"><span data-stu-id="39d38-111">Viewing licensed and unlicensed users</span></span>

<span data-ttu-id="39d38-112">組織内のすべてのユーザー アカウントとライセンスの状態を一覧表示するには、Office 365 PowerShell で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="39d38-112">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="39d38-113">組織内でライセンスのないすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="39d38-113">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="39d38-114">組織内でライセンスのあるすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="39d38-114">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="39d38-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="39d38-115">See also</span></span>

<span data-ttu-id="39d38-116">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39d38-116">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="39d38-117">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="39d38-117">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="39d38-118">Where-Object</span><span class="sxs-lookup"><span data-stu-id="39d38-118">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

