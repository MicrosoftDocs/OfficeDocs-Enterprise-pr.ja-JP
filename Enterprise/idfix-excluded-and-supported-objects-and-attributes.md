---
title: IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: idfix ツールで除外およびサポートされている属性を一覧表示します。
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487183"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性
idfix によって管理されるルールには2つのセットがあります。マルチテナントと専用/ITAR。 現時点では、2つのルールセットは同じオブジェクト、属性、および属性値を検索から除外します。 これは今後のリリースで変更される可能性があります。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>idfix によって使用されるマルチテナントと専用エラーの除外
このセクションでは、idfix によってディレクトリの検索から除外されるオブジェクト、属性、および値の一覧を示します。 アスタリスク (\*) は、他の文字に置き換えることができるワイルドカードです。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>idfix 検索で除外されるオブジェクト、属性、および値

|**除外**|**例**|
|:-----|:-----|
|管理者が\* |管理者 |
|CAS_ {\*  |CAS_ {fe35fc98e69e4d08} |
|discoverysearchmailbox\*  |discoverysearchmailbox  |
|federatedemail.\* |federatedemail.. *GUID* |
|Guest\* ||
|httpconnector\*  |httpconnector |
|krbtgt\* |ms DS-KrbTgt-リンク |
|iusr\* |iusr_ *machinename* |
|iwam\*  |IWAM_ *machinename* |
|msol\* |MSOL_AD_SYNC |
|・\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|wwioadadmini\*  ||
|\*$ ||
|distinguishedName には "\0ACNF:" が含まれています。|"\0ACNF: *GUID* " |
|オブジェクトに IsCriticalSystemObject 属性が含まれている |「 [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)」を参照してください。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>idfix によってチェックされたマルチテナントおよび専用のオブジェクトと属性
idfix によってエラーがチェックされる属性については、 [idfix ツールを使用して Office 365 と同期する](prepare-directory-attributes-for-synch-with-idfix.md)ように、「ディレクトリの属性を準備する」の「ディレクトリオブジェクトと属性の準備」を参照してください。
  

