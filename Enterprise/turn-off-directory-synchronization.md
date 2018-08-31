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
# <a name="turn-off-directory-synchronization-for-office-365"></a>Office 365 のディレクトリ同期を無効にする
PowerShell を使用すると、ディレクトリ同期をオフにします。ただし、トラブルシューティングの手順として、ディレクトリの同期をオフにすることをしないお勧めします。ディレクトリ同期のトラブルシューティングに関するサポートが必要な場合は、 [Office 365 のディレクトリ同期の問題を修正](fix-problems-with-directory-synchronization.md)この資料を参照してください。 
  
ビジネスの製品が必要な場合の[取引先担当者をサポート](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)をします。
  
## <a name="turn-off-directory-synchronization"></a>ディレクトリ同期をオフにします。  
ディレクトリ同期をオフにするには
  
1. 最初に、必要なソフトウェアをインストールし、Office 365 サービスに接続します。両方の手順については、 [Office 365 の PowerShell への接続](https://go.microsoft.com/fwlink/p/?LinkId=821938)を参照してください。
    
2. [セット MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939)を使用して、ディレクトリ同期を無効にします。 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```