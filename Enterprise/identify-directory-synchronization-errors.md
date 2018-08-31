---
title: Office 365 のディレクトリ同期のエラーを表示します
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Office 365 管理センターのディレクトリ同期のエラーを表示する方法について説明します。
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541663"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Office 365 のディレクトリ同期のエラーを表示します

Office 365 の管理センターでは、ディレクトリ同期のエラーを表示できます。ユーザー オブジェクトのエラーのみが表示されます。PowerShell を使用してエラーを表示するには、 [DirSyncProvisioningErrors を識別するオブジェクト](https://go.microsoft.com/fwlink/p/?LinkId=798300)を参照してください。

表示後、は、特定された問題を修正するのには[Office 365 のディレクトリ同期の問題を解決する](fix-problems-with-directory-synchronization.md)を参照してください。
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>管理センターのディレクトリ同期のエラーを表示します。

管理センターのすべてのエラーを参照してください。
  
1. 職場または学校のアカウントを使用して、Office 365 にサインインします。 
    
2. [[Office 365 の管理センター](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)に移動します。
    
3. **[ホーム**] ページで、**ディレクトリ同期の状態**のタイルが表示されます。 
    
    ![管理センターのプレビュー] で、ディレクトリ同期の状態を並べて表示します。](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. 並べて表示]、[**ディレクトリ同期の状態**] ページに移動するのには**ディレクトリ同期のステータス**を選択します。 
    
    ページの下部には、ディレクトリ同期のエラーがあるかどうかを確認できます。
    
    ![[ディレクトリ同期の状態] ページで、ディレクトリ同期オブジェクトのエラーがあるかどうかを確認できます。](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    **ディレクトリ同期オブジェクトのエラーを検出**ディレクトリ同期のエラーの詳細なビューに移動するを選択します。 
    
    > [!NOTE]
    > [**ディレクトリ同期の状態**] タイル**ディレクトリ同期オブジェクトのエラーが検出されたこと**を選択した場合も、目的の**ディレクトリ同期のエラー**ページに移動できます。 
  
![ディレクトリ同期エラーのページ](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. **ディレクトリ同期エラー** ] ページで、エラーとその修正方法に関するヒントについての情報の詳細ペインを表示するには、エラーのいずれかを選択します。 
