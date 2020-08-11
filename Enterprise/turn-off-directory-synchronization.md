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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: この記事では、PowerShell を使用して Microsoft 365 のディレクトリ同期を無効にする方法についての情報を確認します。
ms.openlocfilehash: 815d20ff6a0697f1533e44305e20e61a9282312b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603649"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="7dbfe-103">Microsoft 365 のディレクトリ同期を無効にする</span><span class="sxs-lookup"><span data-stu-id="7dbfe-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="7dbfe-104">PowerShell を使用して、ディレクトリ同期を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="7dbfe-105">ただし、トラブルシューティング手順としてディレクトリ同期を無効にすることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="7dbfe-106">ディレクトリ同期のトラブルシューティングに関してサポートが必要な場合は、「 [Microsoft 365 のディレクトリ同期の問題を解決](fix-problems-with-directory-synchronization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="7dbfe-107">必要に応じて、ビジネス製品の[サポートに問い合わせて](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)ください。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="7dbfe-108">ディレクトリ同期を無効にする</span><span class="sxs-lookup"><span data-stu-id="7dbfe-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="7dbfe-109">ディレクトリ同期を無効にするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="7dbfe-110">最初に、必要なソフトウェアをインストールし、Microsoft 365 サブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="7dbfe-111">手順については、「 [Windows PowerShell 用 Microsoft Azure Active Directory モジュールとの接続](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="7dbfe-112">ディレクトリ同期を無効にするには[、MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)を使用します。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
><span data-ttu-id="7dbfe-113">このコマンドを使用する場合、ディレクトリ同期を再び有効にするには、72時間待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dbfe-113">If you use this command, you must wait 72 hours before you can turn directory synchronization back on.</span></span>
>
 
