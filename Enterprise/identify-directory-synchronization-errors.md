---
title: Microsoft 365 でのディレクトリ同期エラーの表示
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Microsoft 365 管理センターでディレクトリ同期エラーを表示する方法について説明します。
ms.openlocfilehash: 57ca9ce125679931adcca93621474cec9ee9b82f
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842079"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Microsoft 365 でのディレクトリ同期エラーの表示

Microsoft 365 管理センターでディレクトリ同期エラーを確認できます。 ユーザーオブジェクトのエラーのみが表示されます。 PowerShell でエラーを表示するには、「[オブジェクトを識別する (Dirsyncプロビジョニングエラー](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency))」を参照してください。

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターでディレクトリ同期エラーを表示する

Microsoft 365 管理センターでエラーを表示するには、次のようにします。
  
1. グローバル管理者アカウントを使用して、 [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインします。 
    
2. **ホーム**ページに、**ユーザー管理**カードが表示されます。 
    
    ![Microsoft 365 管理センターのユーザー管理カード](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. カードで、[ **AZURE AD Connect** ] の [**エラーの同期**] を選択して、[**ディレクトリ同期エラー** ] ページのエラーを表示します。   
    
    ![ディレクトリ同期エラーページの例](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. エラーのいずれかを選択すると、エラーに関する情報と、その修正方法に関するヒントが詳細ウィンドウに表示されます。

   ![ディレクトリ同期エラーの詳細例](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
表示されたら、「 [Microsoft 365 のディレクトリ同期に関する問題を解決](fix-problems-with-directory-synchronization.md)して、特定の問題を修正する」を参照してください。

