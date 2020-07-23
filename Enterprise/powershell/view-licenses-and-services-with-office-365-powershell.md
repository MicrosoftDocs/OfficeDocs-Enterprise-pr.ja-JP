---
title: PowerShell を使用して Microsoft 365 ライセンスとサービスを表示する
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
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: PowerShell を使用して、Microsoft 365 組織で利用できるライセンスプラン、サービス、ライセンスに関する情報を表示する方法について説明します。
ms.openlocfilehash: f0b7d6cd5981bec09e7773d10d82ff81c0f34d4e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230213"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>PowerShell を使用して Microsoft 365 ライセンスとサービスを表示する

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 のすべてのサブスクリプションは、次の要素で構成されます。

- **ライセンスプラン**これらは、ライセンスプランまたは Microsoft 365 プランとも呼ばれます。 ライセンスプランでは、ユーザーが使用できる Microsoft 365 サービスが定義されています。 Microsoft 365 サブスクリプションには、複数のライセンスプランを含めることができます。 ライセンスプランの例としては、Microsoft 365 E3 があります。
    
- **サービス**これらはサービスプランとも呼ばれます。 サービスは、Microsoft 365 製品、機能、および各ライセンスプランで利用可能な機能であり、たとえば、Exchange Online や Microsoft 365 Apps for enterprise (旧称 Office 365 ProPlus) です。 ユーザーは、さまざまなサービスへのアクセスを許可するさまざまなライセンス プランから割り当てられた複数のライセンスを持つことができます。
    
- **ライセンス**各ライセンスプランには、購入したライセンスの数が含まれています。 ライセンスプランで定義されている Microsoft 365 サービスを使用できるように、ユーザーにライセンスを割り当てます。 すべてのユーザーアカウントでは、Microsoft 365 にログオンしてサービスを使用できるように、1つのライセンスプランから少なくとも1つのライセンスが必要です。
    
Microsoft 365 の PowerShell を使用して、Microsoft 365 組織の利用可能なライセンスプラン、ライセンス、およびサービスに関する詳細を表示できます。 別の Office 365 サブスクリプションで利用可能な製品、機能、サービスについての詳細は、「[Office 365 プランのオプション](https://go.microsoft.com/fwlink/p/?LinkId=691147)」を参照してください。


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
  
現在のライセンスプランおよび各プランで使用可能なライセンスに関する概要情報を表示するには、次のコマンドを実行します。
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

結果には次のものが含まれます。
  
- **Skupartnumber:** 組織の利用可能なライセンスプランを表示します。 たとえば、 `ENTERPRISEPACK` は Office 365 Enterprise E3 のライセンスプラン名です。
    
- **有効:** 特定のライセンスプランで購入したライセンスの数。
    
- **ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。
    
すべてのライセンスプランで利用可能な Microsoft 365 サービスの詳細を確認するには、最初にライセンスプランの一覧を表示します。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

次に、ライセンスプラン情報を変数に格納します。

```powershell
$licenses = Get-AzureADSubscribedSku
```

次に、特定のライセンスプランでサービスを表示します。

```powershell
$licenses[<index>].ServicePlans
```

\<index>は、コマンドの表示からライセンスプランの行番号を指定する整数値から `Get-AzureADSubscribedSku | Select SkuPartNumber` 1 を引いた値です。

たとえば、コマンドの表示は次の `Get-AzureADSubscribedSku | Select SkuPartNumber` ようになります。

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

次に、ENTERPRISEPREMIUM ライセンスプランのサービスを表示するコマンドは次のようになります。

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM は3番目の行です。 したがって、インデックス値は (3-1) または2です。

ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

>[!Note]
>このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。 具体的には、このスクリプトを使用すると、Sway を含む Microsoft 365 組織のサービスを表示したり、無効にしたりできます。 詳細については、「 [PowerShell を使用して Sway へのアクセスを無効](disable-access-to-sway-with-office-365-powershell.md)にする」を参照してください。
>
    
現在のライセンスプランおよび各プランで使用可能なライセンスに関する概要情報を表示するには、次のコマンドを実行します。
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

結果には次の情報が含まれます。
  
- **AccountSkuId:** 構文を使用して、組織で使用可能なライセンスプランを表示し `<CompanyName>:<LicensingPlan>` ます。  _\<CompanyName>_ は、Microsoft 365 に登録したときに指定した値で、組織に固有のものです。 _\<LicensingPlan>_ の値は、すべてのユーザーに対して同じです。 たとえば、値 `litwareinc:ENTERPRISEPACK` では、会社名が `litwareinc`、ライセンス プラン名が  `ENTERPRISEPACK` で、これが Office 365 Enterprise E3 のシステム名になります。
    
- **Activeunits:** 特定のライセンスプランで購入したライセンスの数。
    
- **WarningUnits:** 更新していないライセンス プランのライセンスの数。30 日の猶予期間を過ぎると有効期限切れになります。
    
- **ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。
    
すべてのライセンスプランで利用可能な Microsoft 365 サービスの詳細を表示するには、次のコマンドを実行します。
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

次の表に、最も一般的なサービスの Microsoft 365 サービスプランとそのフレンドリ名を示します。 実際のサービス プランの一覧とは、異なる場合があります。 
  
|**サービス プラン**|**説明**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 enterprise 用アプリ *(旧称 Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online プラン 2  <br/> |
   
ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。

特定のライセンスプランで利用可能な Microsoft 365 サービスに関する詳細を表示するには、次の構文を使用します。
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

この例は、litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3) ライセンスプランで利用可能なサービスを示しています。
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>関連項目

[PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)
