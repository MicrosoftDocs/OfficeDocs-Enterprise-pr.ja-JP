---
title: Office 365 のディレクトリ同期を無効にする
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: PowerShell を使用して Office 365 のディレクトリ同期をオフにする方法を学習します。
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541747"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="1a101-103">Office 365 のディレクトリ同期を無効にする</span><span class="sxs-lookup"><span data-stu-id="1a101-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="1a101-p101">PowerShell を使用すると、ディレクトリ同期をオフにします。ただし、トラブルシューティングの手順として、ディレクトリの同期をオフにすることをしないお勧めします。ディレクトリ同期のトラブルシューティングに関するサポートが必要な場合は、 [Office 365 のディレクトリ同期の問題を修正](fix-problems-with-directory-synchronization.md)この資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a101-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="1a101-107">ビジネスの製品が必要な場合の[取引先担当者をサポート](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)をします。</span><span class="sxs-lookup"><span data-stu-id="1a101-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="1a101-108">ディレクトリ同期をオフにします。</span><span class="sxs-lookup"><span data-stu-id="1a101-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="1a101-109">ディレクトリ同期をオフにするには</span><span class="sxs-lookup"><span data-stu-id="1a101-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="1a101-p102">最初に、必要なソフトウェアをインストールし、Office 365 サービスに接続します。両方の手順については、 [Office 365 の PowerShell への接続](https://go.microsoft.com/fwlink/p/?LinkId=821938)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a101-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="1a101-112">[セット MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)を使用して、ディレクトリ同期を無効にします。</span><span class="sxs-lookup"><span data-stu-id="1a101-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```