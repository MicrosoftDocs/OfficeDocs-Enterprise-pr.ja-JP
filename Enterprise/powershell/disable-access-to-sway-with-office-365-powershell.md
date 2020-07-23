---
title: Microsoft 365 の PowerShell で Sway へのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: ManageSway.ps1 PowerShell スクリプトをダウンロードする場所について説明します。これにより、Microsoft 365 組織の Sway へのアクセスを無効にすることができます。
ms.openlocfilehash: d02a197e2767a1883abcc8fcb4074f3ac92de88a
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230703"
---
# <a name="disable-access-to-sway-with-powershell-for-microsoft-365"></a><span data-ttu-id="8a4ad-103">Microsoft 365 の PowerShell で Sway へのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="8a4ad-103">Disable access to Sway with PowerShell for Microsoft 365</span></span>

<span data-ttu-id="8a4ad-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="8a4ad-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="8a4ad-105">ManageSway.ps1 PowerShell スクリプトを使用すると、Sway を含む Microsoft 365 組織のサービスを表示したり、無効にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="8a4ad-105">The ManageSway.ps1 PowerShell script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="8a4ad-106">このスクリプトは、以下のトピックで説明する手順を自動化します。</span><span class="sxs-lookup"><span data-stu-id="8a4ad-106">This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="8a4ad-107">PowerShell を使用してライセンスとサービスを表示する</span><span class="sxs-lookup"><span data-stu-id="8a4ad-107">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="8a4ad-108">PowerShell を使用してサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="8a4ad-108">Disable access to services with PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="8a4ad-109">スクリプトに関連付けられている 2 つのファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a4ad-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="8a4ad-110">ManageSway.ps1 スクリプト: [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span><span class="sxs-lookup"><span data-stu-id="8a4ad-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="8a4ad-111">スクリプト用のヘルプ ファイル: [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span><span class="sxs-lookup"><span data-stu-id="8a4ad-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

