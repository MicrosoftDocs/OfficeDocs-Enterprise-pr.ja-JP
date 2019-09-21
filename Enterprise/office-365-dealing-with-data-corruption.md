---
title: Office 365 データ破損を処理する
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
description: Office 365 でのデータ破損の説明と、Microsoft による防止と復旧の取り組み。
ms.openlocfilehash: 9a1c0b2e1ebd0c9f1faa698fa12756d32783914c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067619"
---
# <a name="dealing-with-data-corruption-in-office-365"></a><span data-ttu-id="6832f-103">Office 365 でのデータ破損の処理</span><span class="sxs-lookup"><span data-stu-id="6832f-103">Dealing with Data Corruption in Office 365</span></span>

<span data-ttu-id="6832f-104">大規模なクラウドサービスを実行するための困難な側面の1つは、大量のデータと独立したシステムがある場合に、データの破損を処理する方法です。</span><span class="sxs-lookup"><span data-stu-id="6832f-104">One of the challenging aspects of running a large-scale cloud service is how to handle data corruption, given the large volume of data and independent systems.</span></span> <span data-ttu-id="6832f-105">データの破損は、次のような場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="6832f-105">Data corruption can be caused by:</span></span>

- <span data-ttu-id="6832f-106">アプリケーションまたはインフラストラクチャのバグ。アプリケーション状態の一部またはすべてが破損している</span><span class="sxs-lookup"><span data-stu-id="6832f-106">Application or infrastructure bugs, corrupting some or all of the application state</span></span>
- <span data-ttu-id="6832f-107">データ損失またはデータの読み取りができない原因となるハードウェアの問題</span><span class="sxs-lookup"><span data-stu-id="6832f-107">Hardware issues that result in lost data or an inability to read data</span></span>
- <span data-ttu-id="6832f-108">人的運用エラー</span><span class="sxs-lookup"><span data-stu-id="6832f-108">Human operational errors</span></span>
- <span data-ttu-id="6832f-109">悪意のあるハッカーおよび不満を持つ従業員</span><span class="sxs-lookup"><span data-stu-id="6832f-109">Malicious hackers and disgruntled employees</span></span>
- <span data-ttu-id="6832f-110">データの損失が発生する外部サービスのインシデント</span><span class="sxs-lookup"><span data-stu-id="6832f-110">Incidents in external services that result in some loss of data</span></span>

<span data-ttu-id="6832f-111">データ整合性の復元性が高いと、データ破損インシデントが減少するため、Microsoft は Office 365 保護メカニズムを組み込み、破損が発生しないようにします。また、そのような場合にデータを回復できるようにするシステムとプロセスも組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="6832f-111">Because greater resiliency in data integrity means fewer data corruption incidents, Microsoft has built into Office 365 protection mechanisms to prevent corruption from happening, as well as systems and processes that enable us to recover data if it does.</span></span> <span data-ttu-id="6832f-112">エンジニアリングリリースプロセスのさまざまな段階内に存在するチェックとプロセスは、データ破損に対する復元性を向上させるために、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="6832f-112">Checks and processes exist within the various stages of the engineering release process to increase resiliency against data corruption, including:</span></span>

- <span data-ttu-id="6832f-113">システムデザイン</span><span class="sxs-lookup"><span data-stu-id="6832f-113">System Design</span></span>
- <span data-ttu-id="6832f-114">コードの編成と構造</span><span class="sxs-lookup"><span data-stu-id="6832f-114">Code organization and structure</span></span>
- <span data-ttu-id="6832f-115">コードレビュー</span><span class="sxs-lookup"><span data-stu-id="6832f-115">Code review</span></span>
- <span data-ttu-id="6832f-116">単体テスト、統合テスト、およびシステムテスト</span><span class="sxs-lookup"><span data-stu-id="6832f-116">Unit tests, integration tests, and system tests</span></span>
- <span data-ttu-id="6832f-117">トリップワイヤテスト/ゲート</span><span class="sxs-lookup"><span data-stu-id="6832f-117">Trip wires tests/gates</span></span>

<span data-ttu-id="6832f-118">Office 365 の運用環境では、データセンター間のピアレプリケーションによって、データのライブコピーが常に複数存在することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="6832f-118">Within Office 365 production environments, peer replication between datacenters ensures that there are always multiple live copies of any data.</span></span> <span data-ttu-id="6832f-119">失われたサーバーを回復するために標準的な画像とスクリプトを使用し、レプリケーションされたデータを使用して顧客データを復元します。</span><span class="sxs-lookup"><span data-stu-id="6832f-119">Standard images and scripts are used to recover lost servers, and replicated data is used to restore customer data.</span></span> <span data-ttu-id="6832f-120">組み込みのデータ復元チェックとプロセスにより、Microsoft は Office 365 情報システムのドキュメント (セキュリティ関連のドキュメントを含む) のみをバックアップし、SharePoint Online に組み込みのレプリケーションを使用し、内部コードを保持しています。リポジトリツール、ソースの修理工場。</span><span class="sxs-lookup"><span data-stu-id="6832f-120">Because of the built-in data resiliency checks and processes, Microsoft maintains backups only of Office 365 information system documentation (including security-related documentation), using built-in replication in SharePoint Online and our internal code repository tool, Source Depot.</span></span> <span data-ttu-id="6832f-121">システムドキュメントは SharePoint Online に格納されており、ソースの引き取りにはシステムとアプリケーションのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6832f-121">System documentation is stored in SharePoint Online, and Source Depot contains system and application images.</span></span> <span data-ttu-id="6832f-122">SharePoint Online とソース引き取りの両方がバージョン管理を使用し、ほぼリアルタイムでレプリケートされます。</span><span class="sxs-lookup"><span data-stu-id="6832f-122">Both SharePoint Online and Source Depot use versioning and are replicated in near real time.</span></span>
