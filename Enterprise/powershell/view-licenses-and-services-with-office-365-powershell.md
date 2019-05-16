---
title: Office 365 PowerShell でライセンスとサービスを確認する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。
ms.openlocfilehash: 9e84797de29337d9414d9a578a98f6799ee816cb
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071093"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Office 365 PowerShell でライセンスとサービスを確認する

**概要:** Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。
  
Office 365 サブスクリプションは、すべて以下の要素で構成されます。

- **ライセンスプラン**これらは、ライセンスプランまたは Office 365 プランとも呼ばれます。 ライセンス プランでは、ユーザーが利用可能な Office 365 サービスを定義します。 Office 365 サブスクリプションには、複数のライセンス プランが含まれる場合があります。 たとえば、Office 365 Enterprise E3 というライセンス プランがあります。
    
- **サービス**これらはサービスプランとも呼ばれます。 サービスとは、各ライセンス プランで利用可能な Office 365 製品および機能のことで、たとえば、Exchange Online や Office Professional Plus があります。 ユーザーは、さまざまなサービスへのアクセスを許可するさまざまなライセンス プランから割り当てられた複数のライセンスを持つことができます。
    
- **ライセンス** すべてのライセンス プランには、購入した数のライセンスが含まれています。ライセンスをユーザーに割り当てると、ライセンス プランで定義した Office 365 サービスが使えるようになります。それぞれのユーザー アカウントに、少なくとも 1 つのライセンス プランからの 1 つのライセンスが必要です。これにより、ユーザーが Office 365 にログオンして、サービスを利用することができます。
    
Office 365 PowerShell を使って、Office 365 組織で利用可能なライセンス プラン、ライセンス、およびサービスに関する詳細を確認することができます。別の Office 365 サブスクリプションで利用可能な製品、機能、サービスについての詳細は、「[Office 365 プランのオプション](https://go.microsoft.com/fwlink/p/?LinkId=691147)」を参照してください。


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
現在のライセンスプランおよび各プランで使用可能なライセンスに関する概要情報を表示するには、次のコマンドを実行します。
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

結果には次の情報が含まれます。
  
- **Skupartnumber:** 組織の利用可能なライセンスプランを表示します。 たとえば、 `ENTERPRISEPACK`は Office 365 Enterprise E3 のライセンスプラン名です。
    
- **有効:** 特定のライセンスプランで購入したライセンスの数。
    
- **ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。
    
すべてのライセンスプランで利用可能な Office 365 サービスの詳細を表示するには、最初にライセンスプランの一覧を表示します。

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

次に、ライセンスプラン情報を変数に格納します。

````
$licenses = Get-AzureADSubscribedSku
````

次に、特定のライセンスプランでサービスを表示します。

````
$licenses[<index>].ServicePlans
````

\<index> は、 `Get-AzureADSubscribedSku | Select SkuPartNumber`コマンドの表示からライセンスプランの行番号を1から引いた数を指定する整数です。

たとえば、 `Get-AzureADSubscribedSku | Select SkuPartNumber`コマンドの表示は次のようになります。

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

次に、ENTERPRISEPREMIUM ライセンスプランのサービスを表示するコマンドは次のようになります。

````
$licenses[2].ServicePlans
````

ENTERPRISEPREMIUM は3番目の行です。 したがって、インデックス値は (3-1) または2です。

ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

>[!Note]
>このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。 具体的には、このスクリプトを使用すると、Sway などの Office 365 組織のサービスを表示したり、無効にしたりできます。 詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。
>
    
現在のライセンスプランおよび各プランで使用可能なライセンスに関する概要情報を表示するには、次のコマンドを実行します。
  
```
Get-MsolAccountSku
```

結果には次の情報が含まれます。
  
- **AccountSkuId:** 構文 `<CompanyName>:<LicensingPlan>` を使用して、組織で利用可能なライセンス プランを表示します。_<CompanyName>_ は Office 365 に登録するときに指定した値で、組織に対して一意です。_<LicensingPlan>_ の値は、すべてのユーザーに対して同じです。たとえば、値 `litwareinc:ENTERPRISEPACK` では、会社名が `litwareinc`、ライセンス プラン名が `ENTERPRISEPACK` で、これが Office 365 Enterprise E3 のシステム名になります。
    
- **Activeunits:** 特定のライセンスプランで購入したライセンスの数。
    
- **WarningUnits:** 更新していないライセンス プランのライセンスの数。30 日の猶予期間を過ぎると有効期限切れになります。
    
- **ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。
    
すべてのライセンス プランで利用できる Office 365 サービスの詳細を参照するには、次のコマンドを実行します。
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

次の表は、Office 365 のサービス プランと最も一般的なサービスのフレンドリ名を示します。 実際のサービス プランの一覧とは、異なる場合があります。 
  
|**サービス プラン**|**説明**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online プラン 2  <br/> |
   
ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。

特定のライセンス プランで利用可能な Office 365 サービスの詳細を確認するには、次の構文を使用します。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

この例は、litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3) ライセンスプランで利用可能な Office 365 サービスを示しています。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>関連項目


[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
