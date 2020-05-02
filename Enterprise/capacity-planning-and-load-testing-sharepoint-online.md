---
title: SharePoint Online のキャパシティ プランニングとロード テスト
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: この記事では、従来のロードテストを実行せずに SharePoint Online に展開する方法について説明します。これは許可されていないためです。
ms.openlocfilehash: d082dbd93f9724080118f5e387713dc374e50643
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004610"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>SharePoint Online のキャパシティ プランニングとロード テスト
この記事では、SharePoint Online でロードテストが許可されていないため、従来のロードテストを行わずに SharePoint Online に展開する方法について説明します。 SharePoint Online は、クラウドサービスであり、サービスの負荷の負荷の状態、正常性、および全体的なバランスが Microsoft によって管理されます。
  
サイトを正常に起動するための最善の方法は、「[ポータルの起動を計画](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)する」で強調表示されている基本的な原則、ベストプラクティス、推奨事項に従うことです。

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>SharePoint Online が容量計画を実行する方法の概要 
オンプレミス展開による SharePoint Online の主な利点の1つは、クラウドの弾力性、および分散した地域におけるユーザーのための最適化です。 この大規模な環境では、数百万のユーザーに対して日常的にサービスを提供するように設定されているため、ファームを分散および拡張することによって処理能力を効果的に処理することが重要です。
  
多くの場合、1つのファームの1つのテナントに対する成長は予測できませんが、集約された要求の合計は予測可能です。 SharePoint Online の拡張傾向を特定することで、今後の拡張を計画できます。
  
キャパシティを効率的に使用し、予期しない成長に対処するために、どのファームでも、サービスのさまざまな要素を追跡および監視する自動化があります。 複数の測定値が使用されており、メインのいずれかが CPU 負荷になっています。これは、フロントエンドサーバーをスケールアップするための信号として使用されます。 さらに、SQL 環境は時間の経過と共に負荷と成長に応じて拡大または縮小し、フェーズと波形に従うことによって、その負荷と成長の適切な配分が可能になるため、[段階的なアプローチを採用](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out)することをお勧めします。 

キャパシティは継続的にハードウェアを追加するだけではなく、その容量を管理および制御して、有効なロード要求を処理していることを確認することにも関連しています。 推奨されているガイダンスに従ってお客様に最適な環境を確保することをお勧めします。 また、サービスでの "不適切な動作" の動作を許可しないように、調整パターンと制御を適所に配置することも意味します。 すべての "不良" 動作は意図的なものではありませんが、その動作の影響が抑制されるようにする必要があります。 調整の詳細とその回避方法の詳細については、「[ガイダンスの調整を回避する方法](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)」を参照してください。

## <a name="why-you-cannot-load-test-sharepoint-online"></a>テスト SharePoint Online を読み込むことができない理由
オンプレミス環境では、負荷テストを使用してスケールの仮定を検証し、最終的にはファームの限界点を見つけます。負荷で飽和状態にします。 

SharePoint Online では、スケールが相対的に流動的で、一定のヒューリスティックに基づいて負荷を調整、調整し、制御するため、異なる操作を行う必要があります。 このような大規模なマルチテナント環境の場合は、同じファーム内のすべてのテナントを保護する必要があるため、すべてのロードテストが自動的に調整されます。 ただし、調整を試みるのではなく、テストをロードしようとすると、disappointing となる可能性がある結果を得ることができます。これは、今日テストしたファームにはテスト期間中にスケール変更があり、テスト後は規模の変更が行われている可能性があるためです。

テスト SharePoint をサービスとして読み込もうとするのではなく、推奨されている手順に従うようにして、[正常なポータルガイダンスを作成、起動、および維持](https://go.microsoft.com/fwlink/?linkid=2105838)する方法について説明します。
