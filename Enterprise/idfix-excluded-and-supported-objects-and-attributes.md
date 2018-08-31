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
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 除外され、IdFix ツールでサポートされている属性の一覧を表示します。
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541662"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a>IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性
IdFix が保持するルール セットは、マルチテナントと 専用の/ITAR の 2 種類です。現時点で、2 つのルール セットは同じオブジェクト、属性、および属性値を検索対象から除外します。この点は、将来のリリースで変更される可能性があります。
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a>IdFix によるマルチテナントおよび 専用の のエラー除外
このセクションには、オブジェクト、属性、および IdFix は、ディレクトリの検索から除外する値が一覧表示されます。アスタリスク (\*) の代わりに他の文字をワイルドカードです。
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a>IdFix 検索で除外されるオブジェクト、属性、および値

|**除外**|**使用例**|
|:-----|:-----|
|Admini\* |管理者 |
|CAS_ {\*  |CAS_{fe35fc98e69e4d08} |
|DiscoverySearchMailbox\*  |DiscoverySearchMailbox  |
|FederatedEmail\* |FederatedEmail。*GUID* |
|ゲスト\* ||
|HTTPConnector\*  |HTTPConnector |
|krbtgt\* |ms DS KrbTgt リンク |
|iusr _\* |iusr _*コンピューター名* |
|iwam\*  |Iwam _*コンピューター名* |
|msol\* |MSOL_AD_SYNC |
|support_\* ||
|SystemMailbox\* |Systemmailbox { *GUID* }|
|WWIOadmini\*  ||
|\*$ ||
|識別名が含まれています"\0ACNF:"|"\0ACNF: *GUID* " |
|オブジェクトには IsCriticalSystemObject 属性が含まれる |[IsCriticalSystemObject の属性](https://go.microsoft.com/fwlink/p/?LinkId=401169)を参照してください。 |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a>IdFix によって検査されるマルチテナントおよび 専用の のオブジェクト
IdFix でエラーをチェックされている属性は、「ディレクトリ オブジェクトと属性の準備」で[IdFix ツールを使用して Office 365 と同期の準備ディレクトリの属性](prepare-directory-attributes-for-synch-with-idfix.md)で説明します。
  

