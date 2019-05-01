---
title: Office 365 PowerShell を使った Sway へのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 7221a4c9-ae03-4598-81fe-a655c02f40ab
description: Office 365 組織における Sway へのアクセスを無効化するための ManageSway.ps1 PowerShell スクリプトをどこからダウンロードするか説明します。
ms.openlocfilehash: 38f50a483f7bb42ad2d944cf95c49050cf35bfb1
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491303"
---
# <a name="disable-access-to-sway-with-office-365-powershell"></a><span data-ttu-id="6ffc6-103">Office 365 PowerShell を使った Sway へのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="6ffc6-103">Disable access to Sway with Office 365 PowerShell</span></span>

<span data-ttu-id="6ffc6-104">**概要:** ManageSway.ps1 という PowerShell スクリプトを使用して、Office 365 組織における Sway へのアクセスを無効化します。</span><span class="sxs-lookup"><span data-stu-id="6ffc6-104">**Summary** Use the ManageSway.ps1 PowerShell script to disable access to Sway in your Office 365 organization.</span></span>
  
<span data-ttu-id="6ffc6-p101">ManageSway.ps1 PowerShell スクリプトにより、Office 365 組織のサービス (Sway を含む) を表示し、無効化できます。このスクリプトは、次のトピックで説明されている手順を自動化します。</span><span class="sxs-lookup"><span data-stu-id="6ffc6-p101">The ManageSway.ps1 PowerShell script lets you view and disable services in your Office 365 organization, including Sway. This script automates the procedures that are described in the following topics:</span></span>
  
- [<span data-ttu-id="6ffc6-107">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="6ffc6-107">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="6ffc6-108">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="6ffc6-108">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
<span data-ttu-id="6ffc6-109">スクリプトに関連付けられている 2 つのファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ffc6-109">You need to download the two files that are associated with the script:</span></span>
  
- <span data-ttu-id="6ffc6-110">ManageSway.ps1 スクリプト: [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span><span class="sxs-lookup"><span data-stu-id="6ffc6-110">The ManageSway.ps1 script at [https://go.microsoft.com/fwlink/p/?LinkId=785070](https://go.microsoft.com/fwlink/p/?LinkId=785070)</span></span>
    
- <span data-ttu-id="6ffc6-111">スクリプト用のヘルプ ファイル: [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span><span class="sxs-lookup"><span data-stu-id="6ffc6-111">The help file for the script at [https://go.microsoft.com/fwlink/p/?LinkId=785072](https://go.microsoft.com/fwlink/p/?LinkId=785072)</span></span>
    

