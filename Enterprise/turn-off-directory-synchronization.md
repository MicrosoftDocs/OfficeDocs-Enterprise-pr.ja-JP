---
title: Microsoft 365 のディレクトリ同期を無効にする
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
description: PowerShell を使用して Microsoft 365 のディレクトリ同期を無効にする方法について説明します。
ms.openlocfilehash: 935d7e26c7b99aba876500e6b9d428557aed5b9c
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906210"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="cf715-103">Microsoft 365 のディレクトリ同期を無効にする</span><span class="sxs-lookup"><span data-stu-id="cf715-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="cf715-104">PowerShell を使用して、ディレクトリ同期を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf715-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="cf715-105">ただし、トラブルシューティング手順としてディレクトリ同期を無効にすることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="cf715-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="cf715-106">ディレクトリ同期のトラブルシューティングに関してサポートが必要な場合は、「 [Microsoft 365 のディレクトリ同期の問題を解決](fix-problems-with-directory-synchronization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf715-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="cf715-107">必要に応じて、ビジネス製品の[サポートに問い合わせて](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)ください。</span><span class="sxs-lookup"><span data-stu-id="cf715-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="cf715-108">ディレクトリ同期を無効にする</span><span class="sxs-lookup"><span data-stu-id="cf715-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="cf715-109">ディレクトリ同期を無効にするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="cf715-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="cf715-110">最初に、必要なソフトウェアをインストールし、Microsoft 365 サブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="cf715-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="cf715-111">手順については、「 [Windows PowerShell 用 Microsoft Azure Active Directory モジュールとの接続](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf715-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="cf715-112">ディレクトリ同期を無効にするには[、MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)を使用します。</span><span class="sxs-lookup"><span data-stu-id="cf715-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
