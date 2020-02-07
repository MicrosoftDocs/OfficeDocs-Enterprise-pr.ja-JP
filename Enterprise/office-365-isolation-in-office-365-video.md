---
title: Office 365 のテナント分離 (Office 365)
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: '概要: Office 365 Video でのテナントの分離について説明します。'
ms.openlocfilehash: c7fb97180fbe6c96d2849be7725958a788309558
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843658"
---
# <a name="tenant-isolation-in-office-365-video"></a>Office 365 ビデオ でのテナントの分離

> [!NOTE]
> Office 365 のビデオは、Microsoft Stream に置き換えられます。 ビデオコラボレーションにインテリジェンスを追加する新しいエンタープライズビデオサービスの詳細と、現在の Office 365 ビデオのお客様の移行計画については、「 [office 365 からストリームへの移行](https://docs.microsoft.com/stream/)」を参照してください。

## <a name="introduction"></a>概要

Azure Storage は、Office 365 ビデオおよび Sway を含む複数の Office 365 サービスのデータを格納するために使用されます。 Azure ストレージには、構造化されていないデータを格納するために使用される拡張性の高い REST ベースのクラウドオブジェクトストアである Blob ストレージが含まれています。 Azure ストレージは、シンプルなアクセス制御モデルを使用します。各 Azure サブスクリプションは、1つ以上のストレージアカウントを作成できます。 各ストレージアカウントには、そのストレージアカウントのすべてのデータへのアクセスを制御するために使用される単一のシークレットキーがあります。 これは、ストレージがアプリケーションに関連付けられており、それらのアプリケーションが関連するデータを完全に制御する一般的なシナリオをサポートします。たとえば、Sway は Azure ストレージにコンテンツを格納します。 Sway のすべての顧客コンテンツは、共有の Azure ストレージアカウントに保存されます。 各ユーザーのコンテンツは、Azure ストレージ内の blob の独立したディレクトリツリーにあります。

お客様の環境へのアクセスを管理するシステム (たとえば、Azure Portal、SMAPI など) は、Microsoft が運用している Azure アプリケーション内で分離されています。 これにより、顧客のアクセスインフラストラクチャが顧客アプリケーションとストレージ層から論理的に分離されます。

## <a name="tenant-isolation-in-office-365-video"></a>Office 365 ビデオ でのテナントの分離

[Office 365 video](https://support.office.com/article/Meet-Office-365-Video-ca1cc1a9-a615-46e1-b6a3-40dbd99939a6)は、企業に対して、セキュリティで保護された、組織全体で、ビデオコンテンツを投稿、共有、および検出するための、高度にセキュリティで保護された場所を提供するエンタープライズポータルです。 Office 365 のビデオでは、各テナントのビデオはすべての場所で分離され、暗号化されています。また、組織のビデオに対するアクセス許可とアクセス許可を持つ認証されたユーザーのみが使用できます。 Office 365 Video は、次のようなテクノロジを組み合わせて使用します。

- SharePoint Online は、ビデオファイルとメタデータ (ビデオタイトル、説明など) を格納するために使用されます。 また、セキュリティおよびコンプライアンス層 (認証を含む) と検索機能も提供します。
- Azure Media Services では、トランスコーディング、アダプティブストリーミング、セキュリティで保護された配信 (AES 暗号化を使用)、およびサムネイル機能が提供されます。

[Azure Media Services](https://azure.microsoft.com/services/media-services/)は、クラウドでエンドツーエンドのメディアワークフローを有効にするためのサービスとしてのプラットフォームです。 プラットフォームは、アップロード、エンコード、暗号化 (PlayReady を使用)、および世界中の Azure データセンターを使用したメディアの配信用の REST API を提供します。

Office 365 ビデオのすべてのアップロードは HTTPS 経由で行われます。 ビデオファイルがアップロードされると、SharePoint Online に格納され、ファイルのコピーが暗号化されたチャネルを介して Azure メディアサービスに送信されます。 Azure Media Services は、ビデオをコード変換の表示用に最適化された複数の形式 (モバイル、低帯域幅、高帯域幅など) に変換します。 これらのファイルは、アップロード中に取得した元のファイルと共に、Azure Blob ストレージに格納されます。 これらのファイルは、再生用の MPEG 共通暗号化パッケージアルゴリズム (または以前の PlayReady バージョン) ごとに AES 128 を使用して暗号化され、Azure Blob ストレージに保存される前に AES 256 ストレージ暗号化を使用して暗号化されます。 (Azure Media Services クライアント SDK を使用して、お客様はどの暗号化を使用するかを制御できます。 たとえば、azure Blob ストレージをアップロードする前に、お客様は Azure メディアサービスストレージ暗号化 (AES 256) を高価値メディアアセットに適用することができます。

また、Azure Media Services はビデオのサムネイルを生成し、暗号化されたチャネルを介して SharePoint Online にサムネイルメタデータと共に送信します。
