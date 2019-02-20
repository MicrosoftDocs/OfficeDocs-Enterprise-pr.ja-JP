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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: PowerShell を使用して Office 365 のディレクトリ同期を無効にする方法について説明します。
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085076"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期を無効にする
PowerShell を使用して、ディレクトリ同期を無効にすることができます。ただし、トラブルシューティング手順としてディレクトリ同期を無効にすることはお勧めしません。ディレクトリ同期のトラブルシューティングに関してサポートが必要な場合は、「 [Office 365 のディレクトリ同期の問題を解決](fix-problems-with-directory-synchronization.md)する」の記事を参照してください。 
  
必要に応じて、ビジネス製品の[サポートに問い合わせて](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)ください。
  
## <a name="turn-off-directory-synchronization"></a>ディレクトリ同期を無効にする  
ディレクトリ同期を無効にするには、次のようにします。
  
1. 最初に、必要なソフトウェアをインストールし、Office 365 サブスクリプションに接続します。両方の手順については、「 [Office 365 PowerShell に接続する](https://go.microsoft.com/fwlink/p/?LinkId=821938)」を参照してください。
    
2. ディレクトリ同期を無効にするには[、MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)を使用します。 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```