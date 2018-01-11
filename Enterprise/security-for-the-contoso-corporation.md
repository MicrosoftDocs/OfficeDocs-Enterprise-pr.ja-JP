---
title: "Contoso Corporation のセキュリティ"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 8f6f9894-5394-4110-8b0a-b8765028c10b
description: "概要: Contoso 社がどのように Microsoft のクラウド製品の機能にセキュリティ要件をマップし、クラウド セキュリティの準備計画を決定したかについて理解します。"
ms.openlocfilehash: 4d38f58595f0043e1a02106b6428b92dabad2e17
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="security-for-the-contoso-corporation"></a><span data-ttu-id="551de-103">Contoso Corporation のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="551de-103">Security for the Contoso Corporation</span></span>

 <span data-ttu-id="551de-104">**概要:** Contoso 社がどのように Microsoft のクラウド製品の機能にセキュリティ要件をマップし、クラウド セキュリティの準備計画を決定したかについて理解します。</span><span class="sxs-lookup"><span data-stu-id="551de-104">**Summary:** Understand how Contoso mapped their security requirements to features in Microsoft's cloud offerings and determined a path to cloud security readiness.</span></span>
  
<span data-ttu-id="551de-p101">Contoso 社は、情報セキュリティと保護について真剣に取り組んでいます。IT インフラストラクチャを、クラウドを含むインフラストラクチャに移行する際に、オンプレミスのセキュリティ要件がサポートされ、Microsoft のクラウド製品に実装されていることを確認しました。</span><span class="sxs-lookup"><span data-stu-id="551de-p101">Contoso is serious about their information security and protection. When transitioning their IT infrastructure to a cloud-inclusive one, they made sure that their on-premises security requirements were supported and implemented in Microsoft's cloud offerings.</span></span>
  
## <a name="contosos-security-requirements-in-the-cloud"></a><span data-ttu-id="551de-107">Contoso 社のクラウド内のセキュリティ要件</span><span class="sxs-lookup"><span data-stu-id="551de-107">Contoso's security requirements in the cloud</span></span>

<span data-ttu-id="551de-108">Contoso 社のクラウドのセキュリティ要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="551de-108">Here are Contoso's security requirements for the cloud:</span></span>
  
- <span data-ttu-id="551de-109">クラウド リソースに対する強力な認証</span><span class="sxs-lookup"><span data-stu-id="551de-109">Strong authentication to cloud resources</span></span>
    
    <span data-ttu-id="551de-110">クラウド リソースへのアクセスは認証される必要があり、可能であれば多要素認証を活用します。</span><span class="sxs-lookup"><span data-stu-id="551de-110">Cloud resource access must be authenticated and, where possible, leverage multi-factor authentication.</span></span>
    
- <span data-ttu-id="551de-111">インターネット経由でのトラフィックのための暗号化</span><span class="sxs-lookup"><span data-stu-id="551de-111">Encryption for traffic across the Internet</span></span>
    
    <span data-ttu-id="551de-p102">インターネット経由で送信されるデータはプレーンテキスト形式ではありません。常に HTTPS 接続、IPsec、その他のエンド ツー エンドのデータ暗号化方式を使用します。</span><span class="sxs-lookup"><span data-stu-id="551de-p102">No data sent across the Internet is in plain text form. Always use HTTPS connections, IPsec, or other end-to-end data encryption methods.</span></span>
    
- <span data-ttu-id="551de-114">クラウド内の保存データの暗号化</span><span class="sxs-lookup"><span data-stu-id="551de-114">Encryption for data at rest in the cloud</span></span>
    
    <span data-ttu-id="551de-115">ディスク上またはクラウド内の別の場所に格納されているすべてのデータは、暗号化された形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="551de-115">All data stored on disks or elsewhere in the cloud must be in an encrypted form.</span></span>
    
- <span data-ttu-id="551de-116">最小限の特権を持つアクセスの ACL</span><span class="sxs-lookup"><span data-stu-id="551de-116">ACLs for least privilege access</span></span>
    
    <span data-ttu-id="551de-117">クラウド内のリソースにアクセスするためのアカウントのアクセス許可と、許可されているアクションは、最小限の特権のガイドラインに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="551de-117">Account permissions to access resources in the cloud and what they are allowed to do must follow least-privilege guidelines.</span></span>
    
## <a name="contosos-data-sensitivity-classification"></a><span data-ttu-id="551de-118">Contoso 社のデータ秘密度の分類</span><span class="sxs-lookup"><span data-stu-id="551de-118">Contoso's data sensitivity classification</span></span>

<span data-ttu-id="551de-119">Contoso 社は、Microsoft の[データ分類ツールキット]((https://msdn.microsoft.com/library/hh204743.aspx))の情報を使用し、データの分析を行って次のレベルを決定しました。</span><span class="sxs-lookup"><span data-stu-id="551de-119">Using the information in Microsoft's [Data Classification Toolkit]((https://msdn.microsoft.com/library/hh204743.aspx)), Contoso performed an analysis of their data and determined the following levels.</span></span>
  
|<span data-ttu-id="551de-120">**レベル 1:低いビジネス価値**</span><span class="sxs-lookup"><span data-stu-id="551de-120">**Level 1: Low business value**</span></span>|<span data-ttu-id="551de-121">**レベル 2:中程度のビジネス価値**</span><span class="sxs-lookup"><span data-stu-id="551de-121">**Level 2: Medium business value**</span></span>|<span data-ttu-id="551de-122">**レベル 3:高いビジネス価値**</span><span class="sxs-lookup"><span data-stu-id="551de-122">**Level 3: High business value**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="551de-123">データは暗号化され、認証されたユーザーのみが使用できる</span><span class="sxs-lookup"><span data-stu-id="551de-123">Data is encrypted and available only to authenticated users</span></span>  <br/> <span data-ttu-id="551de-p103">オンプレミスとクラウドベースのストレージとワークロード (Office 365 など) に格納されているすべてのデータに提供されます。データは、サービス内に存在している間、およびサービスとクライアント デバイス間の転送中は暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="551de-p103">Provided for all data stored on premises and in cloud-based storage and workloads, such as Office 365. Data is encrypted while it resides in the service and in transit between the service and client devices.</span></span>  <br/> <span data-ttu-id="551de-126">レベル 1 のデータの例には、通常のビジネス通信 (電子メール) や、管理、販売、およびサポート ワーカー用のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="551de-126">Examples of Level 1 data are normal business communications (email) and files for administrative, sales, and support workers.</span></span>  <br/> |<span data-ttu-id="551de-127">レベル 1 以上の強力な認証とデータ損失保護</span><span class="sxs-lookup"><span data-stu-id="551de-127">Level 1 plus strong authentication and data loss protection</span></span>  <br/> <span data-ttu-id="551de-p104">強力な認証には、SMS 検証を使用した多要素認証が含まれています。データ損失の防止により、機密情報または重要な情報がオンプレミス ネットワークの外部に漏出しないようにします。</span><span class="sxs-lookup"><span data-stu-id="551de-p104">Strong authentication includes multi-factor authentication with SMS validation. Data loss prevention ensures that sensitive or critical information does not travel outside the on-premises network.</span></span>  <br/> <span data-ttu-id="551de-130">レベル 2 のデータの例には、財務情報や法的情報、新製品の研究開発データがあります。</span><span class="sxs-lookup"><span data-stu-id="551de-130">Examples of Level 2 data are financial and legal information and research and development data for new products.</span></span>  <br/> |<span data-ttu-id="551de-131">レベル 2 以上の最高レベルの暗号化、認証、監査</span><span class="sxs-lookup"><span data-stu-id="551de-131">Level 2 plus the highest levels of encryption, authentication, and auditing</span></span>  <br/> <span data-ttu-id="551de-132">保存データおよびクラウド内のデータに対する最高レベルの暗号化。地域の規制に準拠し、スマート カードや詳細な監査と警告を使用する多要素認証と組み合わされています。</span><span class="sxs-lookup"><span data-stu-id="551de-132">The highest levels of encryption for data at rest and in the cloud, compliant with regional regulations, combined with multi-factor authentication with smart cards and granular auditing and alerting.</span></span>  <br/> <span data-ttu-id="551de-133">レベル 3 のデータの例には、顧客およびパートナーの個人を特定できる情報や、製品のエンジニアリング仕様と独自の製造技術があります。</span><span class="sxs-lookup"><span data-stu-id="551de-133">Examples of Level 3 data are customer and partner personally identifiable information and product engineering specifications and proprietary manufacturing techniques.</span></span>  <br/> |
   
## <a name="mapping-microsoft-cloud-offerings-and-features-to-contosos-data-levels"></a><span data-ttu-id="551de-134">Contoso 社のデータ レベルへの Microsoft クラウド製品および機能のマッピング</span><span class="sxs-lookup"><span data-stu-id="551de-134">Mapping Microsoft cloud offerings and features to Contoso's data levels</span></span>

<span data-ttu-id="551de-135">次の表は、Microsoft のクラウド製品の機能への Contoso 社のデータ レベルのマッピングを示しています。</span><span class="sxs-lookup"><span data-stu-id="551de-135">The following table shows the mapping of Contoso's data levels to features in Microsoft's cloud offerings:</span></span>
  
||<span data-ttu-id="551de-136">**SaaS**</span><span class="sxs-lookup"><span data-stu-id="551de-136">**SaaS**</span></span>|<span data-ttu-id="551de-137">**Azure PaaS**</span><span class="sxs-lookup"><span data-stu-id="551de-137">**Azure PaaS**</span></span>|<span data-ttu-id="551de-138">**Azure IaaS**</span><span class="sxs-lookup"><span data-stu-id="551de-138">**Azure IaaS**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="551de-139">レベル 1:低いビジネス価値</span><span class="sxs-lookup"><span data-stu-id="551de-139">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="551de-140">すべての接続の HTTPS</span><span class="sxs-lookup"><span data-stu-id="551de-140">HTTPS for all connections</span></span> <br/>  <span data-ttu-id="551de-141">暗号化</span><span class="sxs-lookup"><span data-stu-id="551de-141">Encryption at rest</span></span> <br/> | <span data-ttu-id="551de-142">HTTPS 接続のみをサポート</span><span class="sxs-lookup"><span data-stu-id="551de-142">Support only HTTPS connections</span></span> <br/>  <span data-ttu-id="551de-143">Azure に格納されたファイルを暗号化</span><span class="sxs-lookup"><span data-stu-id="551de-143">Encrypt files stored in Azure</span></span> <br/> | <span data-ttu-id="551de-144">サーバー アクセスに HTTPS または IPsec が必要</span><span class="sxs-lookup"><span data-stu-id="551de-144">Require HTTPS or IPsec for server access</span></span> <br/>  <span data-ttu-id="551de-145">Azure ディスク暗号化</span><span class="sxs-lookup"><span data-stu-id="551de-145">Azure disk encryption</span></span> <br/> |
|<span data-ttu-id="551de-146">レベル 2:中程度のビジネス価値</span><span class="sxs-lookup"><span data-stu-id="551de-146">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="551de-147">SMS による Azure AD 多要素認証 (MFA)</span><span class="sxs-lookup"><span data-stu-id="551de-147">Azure AD multi-factor authentication (MFA) with SMS</span></span> <br/> | <span data-ttu-id="551de-148">暗号化キーに Azure Key Vault を使用</span><span class="sxs-lookup"><span data-stu-id="551de-148">Use Azure Key Vault for encryption keys</span></span> <br/>  <span data-ttu-id="551de-149">SMS による Azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="551de-149">Azure AD MFA with SMS</span></span> <br/> | <span data-ttu-id="551de-150">SMS による MFA</span><span class="sxs-lookup"><span data-stu-id="551de-150">MFA with SMS</span></span> <br/> |
|<span data-ttu-id="551de-151">レベル 3:高いビジネス価値</span><span class="sxs-lookup"><span data-stu-id="551de-151">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="551de-152">Azure Rights Management System (RMS)</span><span class="sxs-lookup"><span data-stu-id="551de-152">Azure Rights Management System (RMS)</span></span> <br/>  <span data-ttu-id="551de-153">スマート カードによる Azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="551de-153">Azure AD MFA with smart cards</span></span> <br/>  <span data-ttu-id="551de-154">Intune 条件付きアクセス</span><span class="sxs-lookup"><span data-stu-id="551de-154">Intune conditional access</span></span> <br/> | <span data-ttu-id="551de-155">Azure RMS</span><span class="sxs-lookup"><span data-stu-id="551de-155">Azure RMS</span></span> <br/>  <span data-ttu-id="551de-156">スマート カードによる Azure AD MFA</span><span class="sxs-lookup"><span data-stu-id="551de-156">Azure AD MFA with smart cards</span></span> <br/> | <span data-ttu-id="551de-157">スマート カードによる MFA</span><span class="sxs-lookup"><span data-stu-id="551de-157">MFA with smart cards</span></span> <br/> |
   
## <a name="contosos-information-policies"></a><span data-ttu-id="551de-158">Contoso 社の情報ポリシー</span><span class="sxs-lookup"><span data-stu-id="551de-158">Contoso's information policies</span></span>

<span data-ttu-id="551de-159">次の表に、Contoso 社の情報ポリシーを示します。</span><span class="sxs-lookup"><span data-stu-id="551de-159">The following table lists Contoso's information policies.</span></span>
  
||<span data-ttu-id="551de-160">**Access**</span><span class="sxs-lookup"><span data-stu-id="551de-160">**Access**</span></span>|<span data-ttu-id="551de-161">**データ保存期間**</span><span class="sxs-lookup"><span data-stu-id="551de-161">**Data retention**</span></span>|<span data-ttu-id="551de-162">**情報保護**</span><span class="sxs-lookup"><span data-stu-id="551de-162">**Information protection**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="551de-163">レベル 1:低いビジネス価値</span><span class="sxs-lookup"><span data-stu-id="551de-163">Level 1: Low business value</span></span>  <br/> | <span data-ttu-id="551de-164">すべてのユーザーに対してアクセスを許可</span><span class="sxs-lookup"><span data-stu-id="551de-164">Allow access to all</span></span> <br/> |<span data-ttu-id="551de-165">6 か月</span><span class="sxs-lookup"><span data-stu-id="551de-165">6 months</span></span>  <br/> |<span data-ttu-id="551de-166">暗号化を使用</span><span class="sxs-lookup"><span data-stu-id="551de-166">Use encryption</span></span>  <br/> |
|<span data-ttu-id="551de-167">レベル 2:中程度のビジネス価値</span><span class="sxs-lookup"><span data-stu-id="551de-167">Level 2: Medium business value</span></span>  <br/> | <span data-ttu-id="551de-168">Contoso 社の従業員、下請業者、パートナーに対してアクセスを許可</span><span class="sxs-lookup"><span data-stu-id="551de-168">Allow access to Contoso employees, subcontractors, and partners</span></span> <br/>  <span data-ttu-id="551de-169">MFA、TLS、MAM を使用</span><span class="sxs-lookup"><span data-stu-id="551de-169">Use MFA, TLS, and MAM</span></span> <br/> |<span data-ttu-id="551de-170">2 年</span><span class="sxs-lookup"><span data-stu-id="551de-170">2 years</span></span>  <br/> |<span data-ttu-id="551de-171">データ整合性のためにハッシュ値を使用</span><span class="sxs-lookup"><span data-stu-id="551de-171">Use hash values for data integrity</span></span>  <br/> |
|<span data-ttu-id="551de-172">レベル 3:高いビジネス価値</span><span class="sxs-lookup"><span data-stu-id="551de-172">Level 3: High business value</span></span>  <br/> | <span data-ttu-id="551de-173">エグゼクティブ、およびエンジニアリングと製造の潜在顧客に対してアクセスを許可</span><span class="sxs-lookup"><span data-stu-id="551de-173">Allow access to executives and leads in engineering and manufacturing</span></span> <br/>  <span data-ttu-id="551de-174">管理されたネットワーク デバイスのみの RMS</span><span class="sxs-lookup"><span data-stu-id="551de-174">RMS with managed network devices only</span></span> <br/> |<span data-ttu-id="551de-175">7 年</span><span class="sxs-lookup"><span data-stu-id="551de-175">7 years</span></span>  <br/> |<span data-ttu-id="551de-176">否認防止のためにデジタル署名を使用</span><span class="sxs-lookup"><span data-stu-id="551de-176">Use digital signatures for non-repudiation</span></span>  <br/> |
   
## <a name="contosos-path-to-cloud-security-readiness"></a><span data-ttu-id="551de-177">Contoso 社のクラウド セキュリティ準備完了までのプロセス</span><span class="sxs-lookup"><span data-stu-id="551de-177">Contoso's path to cloud security readiness</span></span>

<span data-ttu-id="551de-178">Contoso 社は、Microsoft クラウド用に自社のセキュリティを準備するために、次の手順を行いました。</span><span class="sxs-lookup"><span data-stu-id="551de-178">Contoso used the following steps to ready their security for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="551de-179">クラウドの管理者アカウントを最適化する</span><span class="sxs-lookup"><span data-stu-id="551de-179">Optimize administrator accounts for the cloud</span></span>
    
    <span data-ttu-id="551de-180">Contoso 社では、既存の Windows Server AD 管理者アカウントの広範なレビューを行い、一連のクラウド管理者アカウントおよびグループを設定しました。</span><span class="sxs-lookup"><span data-stu-id="551de-180">Contoso did an extensive review of the existing Windows Server AD administrator accounts and set up a series of cloud administrator accounts and groups.</span></span>
    
2. <span data-ttu-id="551de-181">データ分析を行い 3 つのレベルに分類する</span><span class="sxs-lookup"><span data-stu-id="551de-181">Perform data classification analysis into three levels</span></span>
    
    <span data-ttu-id="551de-182">Contoso 社は慎重なレビューを行い、3 つのレベルを決定しました。これらのレベルは、Contoso 社の最も重要なデータを保護するための Microsoft クラウド製品の機能の決定に使用されました。</span><span class="sxs-lookup"><span data-stu-id="551de-182">Contoso performed a careful review and determined the three levels, which was used to determine the Microsoft cloud offering features to protect Contoso's most valuable data.</span></span>
    
3. <span data-ttu-id="551de-183">各データ レベルについてアクセス、保持、情報保護ポリシーを決定する</span><span class="sxs-lookup"><span data-stu-id="551de-183">Determine access, retention, and information protection policies for data levels</span></span>
    
    <span data-ttu-id="551de-184">データ レベルに基づき、Contoso 社は詳細な要件を決定しました。これらの要件は、クラウドに移動する将来の IT ワークロードを制限するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="551de-184">Based on the data levels, Contoso determined detailed requirements, which will be used to qualify future IT workloads being moved to the cloud.</span></span>
    
## <a name="contosos-use-of-office-365-security-best-practices"></a><span data-ttu-id="551de-185">Contoso 社における Office 365 のセキュリティのベスト プラクティスの使用</span><span class="sxs-lookup"><span data-stu-id="551de-185">Contoso's use of Office 365 security best practices</span></span>

<span data-ttu-id="551de-186">Office 365 のセキュリティのベスト プラクティスに基づき、Contoso 社のセキュリティ管理者と IT 部門は以下を展開しました。</span><span class="sxs-lookup"><span data-stu-id="551de-186">In accordance with Office 365 security best practices, Contoso's security administrators and IT department have deployed the following:</span></span>
  
- <span data-ttu-id="551de-187">**非常に強力なパスワードを設定した全体管理者専用アカウント**</span><span class="sxs-lookup"><span data-stu-id="551de-187">**Dedicated global administrator accounts with very strong passwords**</span></span>
    
    <span data-ttu-id="551de-p105">Contoso 社では、日常的に使うユーザー アカウントに全体管理者ロールを割り当てるのではなく、非常に強力なパスワードを設定した全体管理者専用アカウントを 3 つ作成しました。全体管理者アカウントでサインインするのは特定の管理タスクを実行するときのみで、パスワードは指定されたスタッフにのみ知らされています。Contoso 社のセキュリティ管理者は、IT 担当者の職務と責任に従って、各アカウントに管理者ロールを割り当てました。</span><span class="sxs-lookup"><span data-stu-id="551de-p105">Rather than assign the global admin role to everyday user accounts, Contoso has create three, dedicated global administrator accounts with very strong passwords. Signing in with a global administrator account is only done for specific administrative tasks and the passwords are only known to designated staff. Contoso's security administrators have assigned admin roles to accounts that are appropriate to that IT person's job function and responsibility.</span></span>
    
    <span data-ttu-id="551de-191">詳細については、「[Office 365 の管理者ロールについて]((https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="551de-191">For more information, see [About Office 365 admin roles]((https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)).</span></span>
    
- <span data-ttu-id="551de-192">**重要なユーザー アカウントに対する多要素認証 (MFA)**</span><span class="sxs-lookup"><span data-stu-id="551de-192">**Multi-factor authentication (MFA) for important user accounts**</span></span>
    
    <span data-ttu-id="551de-p106">MFA を使用すると、サインイン プロセスの保護の層が厚くなり、パスワードを正しく入力した後、ユーザーに対して、電話、テキスト メッセージ、スマートフォンのアプリ通知のいずれかを通して確認が求められます。MFA を使用すれば、アカウント パスワードが漏えいした場合であっても、Office 365 ユーザー アカウントは承認されていないサインイン イベントから保護されます。</span><span class="sxs-lookup"><span data-stu-id="551de-p106">MFA adds an additional layer of protection to the sign-in process by requiring users to acknowledge a phone call, text message, or an app notification on their smart phone after correctly entering their password. With MFA, Office 365 user accounts are protected against unauthorized sign-in even if an account password is compromised.</span></span>
    
  - <span data-ttu-id="551de-195">Contoso 社では、Office 365 サブスクリプションが危害を受けるのを防ぐため、3 つの全体管理者アカウントすべてで MFA を有効にしました。</span><span class="sxs-lookup"><span data-stu-id="551de-195">To protect against a compromise of the Office 365 subscription, Contoso enabled MFA on all three global administrator accounts.</span></span>
    
  - <span data-ttu-id="551de-196">組織内の信頼されている人の資格情報が漏えいし、攻撃者が悪意のある電子メールを送信するというフィッシング攻撃からの保護を目的として、Contoso 社では経営幹部を含む管理職のすべてのユーザー アカウントで MFA を有効にしました。</span><span class="sxs-lookup"><span data-stu-id="551de-196">To protect against phishing attacks, in which an attacker compromises the credentials of a trusted person in the organization and sends malicious emails, Contoso enabled MFA on all user accounts for managers, including the executive staff.</span></span>
    
    <span data-ttu-id="551de-197">詳細については、「[Office 365 展開用の多要素認証の計画]((https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="551de-197">For more information, see [Plan for multi-factor authentication for Office 365 Deployments]((https://support.office.com/article/Plan-for-multifactor-authentication-for-Office-365-Deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba))</span></span>
    
- <span data-ttu-id="551de-198">**高度なセキュリティ管理 (ASM)**</span><span class="sxs-lookup"><span data-stu-id="551de-198">**Advanced Security Management (ASM)**</span></span>
    
    <span data-ttu-id="551de-p107">ASM では、構成済みのポリシーを使用して異常な動作を監視します。Contoso 社のセキュリティ管理者は ASM を使用して警告をセットアップし、大量のデータのダウンロード、サインインしようとして繰り返される失敗、不明なまたは危険な IP アドレスからのサインインなど、通常とは異なるユーザー動作や危険なユーザー動作があると、IT 管理者が通知を受けるようにします。</span><span class="sxs-lookup"><span data-stu-id="551de-p107">ASM uses configured policies to monitor for anomalous activity. Contoso security administrators set up alerts with ASM so that IT administrators are notified of unusual or risky user activity, such as downloading large amounts of data, multiple failed sign-in attempts, or sign-ins from unknown or dangerous IP addresses</span></span>
    
    <span data-ttu-id="551de-201">詳細については、「[Office 365 の Advanced Security Management の概要]((https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="551de-201">For more information, see [Overview of Advanced Security Management in Office 365 ]((https://support.office.com/article/Overview-of-Advanced-Security-Management-in-Office-365-81f0ee9a-9645-45ab-ba56-de9cbccab475)).</span></span>
    
- <span data-ttu-id="551de-202">**セキュリティで保護されたメール フローとメールボックス監査ログ**</span><span class="sxs-lookup"><span data-stu-id="551de-202">**Secure email flow and mailbox audit logging**</span></span>
    
    <span data-ttu-id="551de-p108">Contoso 社のセキュリティ専門家は、電子メール経由で送信される不明なマルウェア、ウイルス、悪意のある URL からの保護を目的として、Exchange Online Protection と Advanced Threat Protection (ATP) を使用しています。Contoso 社では、メールボックス監査ログを有効にして、ユーザーのメールボックスにログインしてメッセージを送信したのはだれかや、メールボックス所有者、委任ユーザー、管理者が実行した他の操作を判別しています。</span><span class="sxs-lookup"><span data-stu-id="551de-p108">Contoso security specialists are using Exchange Online Protection and Advanced Threat Protection (ATP) to protect against unknown malware, viruses, and malicious URLs transmitted through emails. Contoso has also enabled mailbox audit logging to determine who has logged into user mailboxes, sent messages, and other activities performed by the mailbox owner, a delegated user, or an administrator.</span></span>
    
    <span data-ttu-id="551de-205">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="551de-205">For more information, see:</span></span> 
    
  - <span data-ttu-id="551de-206">[Office 365 メールのスパム対策保護]((https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586))</span><span class="sxs-lookup"><span data-stu-id="551de-206">[Office 365 Email Anti-Spam Protection]((https://support.office.com/article/Office-365-Email-AntiSpam-Protection-6a601501-a6a8-4559-b2e7-56b59c96a586))</span></span>
    
  - <span data-ttu-id="551de-207">[安全な添付ファイルと安全なリンクのための Advanced Threat Protection]((https://technet.microsoft.com/library/mt148491.aspx))</span><span class="sxs-lookup"><span data-stu-id="551de-207">[Advanced threat protection for safe attachments and safe links]((https://technet.microsoft.com/library/mt148491.aspx))</span></span>
    
  - [<span data-ttu-id="551de-208">Office 365 でメールボックスの監査を有効にする</span><span class="sxs-lookup"><span data-stu-id="551de-208">Enable mailbox auditing in Office 365</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=626109)
    
- <span data-ttu-id="551de-209">**データ損失防止 (DLP)**</span><span class="sxs-lookup"><span data-stu-id="551de-209">**Data Loss Prevention (DLP)**</span></span>
    
    <span data-ttu-id="551de-210">Contoso 社は機密性の高いデータを識別し、故意か偶然かを問わずユーザーがデータを共有することがないように、Exchange Online、SharePoint Online、OneDrive 用の DLP ポリシーを構成しています。</span><span class="sxs-lookup"><span data-stu-id="551de-210">Contoso has identified its sensitive data and configured DLP policies for Exchange Online, SharePoint Online, and OneDrive to help prevent users from accidentally or intentionally sharing the data.</span></span> 
    
    <span data-ttu-id="551de-211">詳しくは、「[データ損失防止ポリシーの概要]((https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="551de-211">For more information, see [Overview of data loss prevention policies]((https://support.office.com/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="551de-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="551de-212">See Also</span></span>

[<span data-ttu-id="551de-213">Microsoft Cloud の Contoso</span><span class="sxs-lookup"><span data-stu-id="551de-213">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="551de-214">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="551de-214">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="551de-215">[Microsoft のエンタープライズ クラウド ロードマップ:IT 意思決定者のリソース]((https://sway.com/FJ2xsyWtkJc2taRD))</span><span class="sxs-lookup"><span data-stu-id="551de-215">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers]((https://sway.com/FJ2xsyWtkJc2taRD))</span></span>
  
<span data-ttu-id="551de-216">[Office 365 のセキュリティのベスト プラクティス]((https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3))</span><span class="sxs-lookup"><span data-stu-id="551de-216">[Security best practices for Office 365]((https://support.office.com/article/Security-best-practices-for-Office-365-9295e396-e53d-49b9-ae9b-0b5828cdedc3))</span></span>




