---
title: Office 365 のディレクトリ同期を無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: PowerShell を使用して Office 365 のディレクトリ同期を無効にする方法について説明します。
ms.openlocfilehash: eab736241372b2d1b6023dc803dff540dded64ae
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841014"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="e1f6d-103">Office 365 のディレクトリ同期を無効にする</span><span class="sxs-lookup"><span data-stu-id="e1f6d-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="e1f6d-104">PowerShell を使用して、ディレクトリ同期を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="e1f6d-105">ただし、トラブルシューティング手順としてディレクトリ同期を無効にすることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="e1f6d-106">ディレクトリ同期のトラブルシューティングに関してサポートが必要な場合は、「 [Office 365 のディレクトリ同期の問題を解決](fix-problems-with-directory-synchronization.md)する」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="e1f6d-107">必要に応じて、ビジネス製品の[サポートに問い合わせて](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)ください。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="e1f6d-108">ディレクトリ同期を無効にする</span><span class="sxs-lookup"><span data-stu-id="e1f6d-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="e1f6d-109">ディレクトリ同期を無効にするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="e1f6d-110">最初に、必要なソフトウェアをインストールし、Office 365 サブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="e1f6d-111">手順については、「 [Windows PowerShell 用 Microsoft Azure Active Directory モジュールとの接続](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="e1f6d-112">ディレクトリ同期を無効にするには[、MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
