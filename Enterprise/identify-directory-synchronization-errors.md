---
title: Office 365 でのディレクトリ同期エラーの表示
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Microsoft 365 管理センターでディレクトリ同期エラーを表示する方法について説明します。
ms.openlocfilehash: b1cda68590131967ea2fe91506c8e71769f4c32b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067523"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Office 365 でのディレクトリ同期エラーの表示

[Microsoft 365 管理センター](https://admin.microsoft.com)でディレクトリ同期エラーを確認できます。 ユーザーオブジェクトのエラーのみが表示されます。 PowerShell を使用してエラーを表示するには、「 [Dirsyncプロビジョニングエラーでオブジェクトを識別](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)する」を参照してください。

表示された後、「 [Office 365 のディレクトリ同期に関する問題を解決](fix-problems-with-directory-synchronization.md)して、特定の問題を修正する」を参照してください。
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>管理センターでディレクトリ同期エラーを表示する

管理センターでエラーを表示するには、次のようにします。
  
1. 職場または学校のアカウントを使用して、Office 365 にサインインします。 
    
2. [[管理センターについて](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23)] に移動します。
    
3. **ホーム**ページに [ **DirSync Status** ] タイルが表示されます。 
    
    ![管理センタープレビューの [DirSync Status] タイル](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. タイルの [ **DirSync status** ] を選択して、[**ディレクトリ同期の状態**] ページに移動します。 
    
    ページの下部に、DirSync エラーがあるかどうかが表示されます。
    
    ![[ディレクトリ同期の状態] ページで、DirSync オブジェクトエラーが発生しているかどうかを確認できます。](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    ディレクトリ同期エラーの詳細表示に移動するには、 **DirSync オブジェクトのエラーが検出**されたことを選択します。 
    
    > [!NOTE]
    > Dirsync の**状態**のタイルで**dirsync オブジェクトのエラーが検出**された場合は、[ **dirsync errors** ] ページに移動することもできます。 
  
![DirSync errors ページ](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. [ **DirSync errors** ] ページで、表示されているいずれかのエラーを選択して詳細ウィンドウにエラーに関する情報とその修正方法に関するヒントを表示します。 
