---
title: Microsoft 365 データ破損の処理
ms.author: josephd
author: JoeDavies-MSFT
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
description: Microsoft 365 でのデータ破損の説明と、Microsoft による防止と復旧の取り組み。
ms.openlocfilehash: 674f2a3a026c5706f5c3a23db6e2d968ed815656
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998451"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a><span data-ttu-id="738cc-103">Microsoft 365 でのデータ破損の処理</span><span class="sxs-lookup"><span data-stu-id="738cc-103">Dealing with Data Corruption in Microsoft 365</span></span>

<span data-ttu-id="738cc-104">大規模なクラウドサービスを実行するための困難な側面の1つは、大量のデータと独立したシステムがある場合に、データの破損を処理する方法です。</span><span class="sxs-lookup"><span data-stu-id="738cc-104">One of the challenging aspects of running a large-scale cloud service is how to handle data corruption, given the large volume of data and independent systems.</span></span> <span data-ttu-id="738cc-105">データの破損は、次のような場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="738cc-105">Data corruption can be caused by:</span></span>

- <span data-ttu-id="738cc-106">アプリケーションまたはインフラストラクチャのバグ。アプリケーション状態の一部またはすべてが破損している</span><span class="sxs-lookup"><span data-stu-id="738cc-106">Application or infrastructure bugs, corrupting some or all of the application state</span></span>
- <span data-ttu-id="738cc-107">データ損失またはデータの読み取りができない原因となるハードウェアの問題</span><span class="sxs-lookup"><span data-stu-id="738cc-107">Hardware issues that result in lost data or an inability to read data</span></span>
- <span data-ttu-id="738cc-108">人的運用エラー</span><span class="sxs-lookup"><span data-stu-id="738cc-108">Human operational errors</span></span>
- <span data-ttu-id="738cc-109">悪意のあるハッカーおよび不満を持つ従業員</span><span class="sxs-lookup"><span data-stu-id="738cc-109">Malicious hackers and disgruntled employees</span></span>
- <span data-ttu-id="738cc-110">データの損失が発生する外部サービスのインシデント</span><span class="sxs-lookup"><span data-stu-id="738cc-110">Incidents in external services that result in some loss of data</span></span>

<span data-ttu-id="738cc-111">データ整合性の弾力性が高いと、データ破損インシデントが減少するため、Microsoft は、破損が発生しないように Microsoft 365 保護メカニズムに組み込みました。また、そのような場合にデータを回復できるようにするためのシステムとプロセスも組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="738cc-111">Because greater resiliency in data integrity means fewer data corruption incidents, Microsoft has built into Microsoft 365 protection mechanisms to prevent corruption from happening, as well as systems and processes that enable us to recover data if it does.</span></span> <span data-ttu-id="738cc-112">エンジニアリングリリースプロセスのさまざまな段階内に存在するチェックとプロセスは、データ破損に対する復元性を向上させるために、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="738cc-112">Checks and processes exist within the various stages of the engineering release process to increase resiliency against data corruption, including:</span></span>

- <span data-ttu-id="738cc-113">システムデザイン</span><span class="sxs-lookup"><span data-stu-id="738cc-113">System Design</span></span>
- <span data-ttu-id="738cc-114">コードの編成と構造</span><span class="sxs-lookup"><span data-stu-id="738cc-114">Code organization and structure</span></span>
- <span data-ttu-id="738cc-115">コードレビュー</span><span class="sxs-lookup"><span data-stu-id="738cc-115">Code review</span></span>
- <span data-ttu-id="738cc-116">単体テスト、統合テスト、およびシステムテスト</span><span class="sxs-lookup"><span data-stu-id="738cc-116">Unit tests, integration tests, and system tests</span></span>
- <span data-ttu-id="738cc-117">トリップワイヤテスト/ゲート</span><span class="sxs-lookup"><span data-stu-id="738cc-117">Trip wires tests/gates</span></span>

<span data-ttu-id="738cc-118">Microsoft 365 の運用環境では、データセンター間のピアレプリケーションによって、データのライブコピーが常に複数存在することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="738cc-118">Within Microsoft 365 production environments, peer replication between datacenters ensures that there are always multiple live copies of any data.</span></span> <span data-ttu-id="738cc-119">失われたサーバーを回復するために標準的な画像とスクリプトを使用し、レプリケーションされたデータを使用して顧客データを復元します。</span><span class="sxs-lookup"><span data-stu-id="738cc-119">Standard images and scripts are used to recover lost servers, and replicated data is used to restore customer data.</span></span> <span data-ttu-id="738cc-120">組み込まれているデータの復元チェックとプロセスにより、Microsoft は Microsoft 365 information system のドキュメント (セキュリティ関連ドキュメントを含む) のみをバックアップし、SharePoint Online の組み込みレプリケーションおよび内部コードリポジトリツールであるソースの引き取り修理を使用しています。</span><span class="sxs-lookup"><span data-stu-id="738cc-120">Because of the built-in data resiliency checks and processes, Microsoft maintains backups only of Microsoft 365 information system documentation (including security-related documentation), using built-in replication in SharePoint Online and our internal code repository tool, Source Depot.</span></span> <span data-ttu-id="738cc-121">システムドキュメントは SharePoint Online に格納されており、ソースの引き取りにはシステムとアプリケーションのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="738cc-121">System documentation is stored in SharePoint Online, and Source Depot contains system and application images.</span></span> <span data-ttu-id="738cc-122">SharePoint Online とソース引き取りの両方がバージョン管理を使用し、ほぼリアルタイムでレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="738cc-122">Both SharePoint Online and Source Depot use versioning and are replicated in near real time.</span></span>
