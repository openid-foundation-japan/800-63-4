---
layout: default.ja
title: Identity Assurance Level Requirements
navOrder: 5
navTitle: IAL
permalink: /sp800-63a/ial/
anchor: ial-section
section: 5
---

# Identity Assurance Level 要件 {#ial-section}

{% comment %}
# Identity Assurance Level Requirements {#ial-section}
{% endcomment %}

_This section is normative._

本セクションはIdentity ProofingとEnrollmentのサービスを運営するCSPに対する要件を提供する。この要件には各IALのIdentity Proofingの要件が含まれる。本セクションでは、自分達でIdentityサービスを提供するか外部のCSPを用いるかどうかにかかわらず、連邦機関向けの追加の要件も含んでいる。

{% comment %}
This section provides requirements for CSPs that operate identity proofing and enrollment services, including requirements for identity proofing at each of the IALs. This section also includes additional requirements for Federal Agencies regardless of whether they operate their own identity service or use an external CSP. 
{% endcomment %}

## 一般的な要件 {#genProofReqs}
{% comment %}
## General Requirements {#genProofReqs}
{% endcomment %}

本セクションの要件は、任意のIALでIdentity Proofingを実施するすべてのCSPに適用される。
{% comment %}
The requirements in this section apply to all CSPs performing identity proofing at any IAL.
{% endcomment %}

### Identity Service Documentation and Records {#DocRecReqs}

{% comment %}
### Identity Service Documentation and Records {#DocRecReqs}
{% endcomment %}


CSPは、定義されたIALを達成するために実装されているすべてのIdentiy Proofingプロセスを詳細化するPractice Statementに従って、オペレーションを実施するものとする(**SHALL**)。Practice Statementは少なくとも次の内容を含むものとする(**SHALL**): 

1. それぞれの提供されたIALにおいて CSP がApplicantのIdentity Proofingを行うために従う特定のステップを含む、完全なサービスの説明。 
2. CSPが受け入れる、Evidence強度要件を満たすためのIdentity Evidenceの種類。 
3. 該当する場合、必要なIdentity Evidenceを所有していないApplicant個人が、Identity Proofingプロセスを完了するための代替手法 [^alternatives]。 
4. CSP が Core Attributesであると見なす Attribute。Core Attributesには、CSP が Identity Resolutionを行うために必要な最小限のAttributeのセットのほか、Identity Proofing、詐欺の軽減、法律または法的プロセスの遵守、あるいはAttribute Assertionを介したRelying Party(RP)への伝達を目的とし、CSPが収集、validateする追加のAttributeを含んでいる。
5. Identity Proofingのエラーに対処するための CSP のポリシーとプロセス。
6. 疑わしい、あるいは確認済みの不正なアカウントを識別し、RPや影響をうける個人に対して伝達するための、CSP のポリシーとプロセス。
7. サービス変更（例：データソース、統合ベンダー、またはバイオメトリックアルゴリズムの変更）を管理し、RP に伝達するための、 CSP のポリシー。
8. 定期的な見直しのタイミングと、更新されたプライバシーリスク評価をトリガーする具体的な条件を含む、プライバシーリスク評価の実施に関するCSPのポリシー([セクション 5.1.2](sec5_ial.ja.md#PrivacyReqs) を参照）
9. 潜在的なEquityへの影響を判断するためのアセスメントを実施する CSP のポリシー。これには、定期的なレビューのタイミングと、サイクル外レビューの契機となる特定条件を含む（[セクション 5.1.3](sec5_ial.ja.md#EquityReqs) 参照）；更に、

{% comment %}
The CSP **SHALL** conduct its operations according to a practice statement that details all identity proofing processes as they are implemented to achieve the defined IAL. The practice statement **SHALL** include, at a minimum:  

1. A complete service description including the particular steps the CSP follows to identity proof applicants at each offered assurance level;
2. Types of identity evidence the CSP accepts to meet the evidence strength requirements;
3. If applicable, alternative ways for an individual applicant who does not possess the required identity evidence to complete the identity proofing process[^alternatives];
4. The attributes the CSP considers to be core attributes. Core attributes include the minimum set of attributes the CSP needs to perform identity resolution as well as any additional attributes the CSP collects and validates for the purposes of identity proofing, fraud mitigation, complying with laws or legal process, or conveying to relying parties (RPs) through attribute assertions;
5. The CSP's policy and process for dealing with identity proofing errors;
6. The CSP's policy and process for identifying and communicating suspected or confirmed fraudulent accounts to RPs and affected individuals;
7. The CSP's policy for managing and communicating service changes (e.g., change in data sources, integrated vendors, or biometric algorithms) to RPs;
8. The CSP's policy for conducting privacy risk assessments, including the timing of its periodic reviews and specific conditions that will trigger an updated privacy risk assessment (see [Section 5.1.2](sec5_ial.md#PrivacyReqs));
9. The CSP's policy for conducting assessments to determine potential equity impacts, including the timing of its periodic reviews and any specific conditions that will trigger an out-of-cycle review (see [Section 5.1.3](sec5_ial.md#EquityReqs)); and
{% endcomment %}


#### 営業停止
{% comment %}
#### Ceasing Operations
{% endcomment %}

1. CSP は、その業務を停止するときのポリシーと計画を文書化するものとする(**SHALL**)。
2. この計画には、CSP のIdentityサービスが保持要件の対象であるかどうか、さらに保持期間中に機微データ （Identity Attribute、Subscriberアカウント内に含まれる情報や、監査ログに含まれる情報）をどのように保護するかどうか含まれるものとする(**SHALL**)。
3. 要求される保持期間の終了時に、CSP はすべての機微データを完全に廃棄または破壊する責任を負うものとする(**SHALL**)。

{% comment %}
1. The CSP **SHALL** document its policy and plan for when it ceases its operations. 
2. This plan **SHALL** include whether the CSP's identity service is subject to retention requirements and how it will protect any sensitive data (including identity attributes, and information contained in subscriber accounts and audit logs) during the period of retention. 
3. At the end of any required retention period, the CSP **SHALL** be responsible for fully disposing of or destroying all sensitive data.
{% endcomment %}

#### 不正行為の緩和策

{% comment %}
#### Fraud Mitigation Measures
{% endcomment %}

1. CSP は、不正行為の緩和策（例：Applicantのデバイス特性の調査、行動特性の評価、デスマスターファイル （[[DMF]](sec11_references.ja.md#ref-dmf) などの重要統計情報リポジトリの確認）を使用してIdentity Proofingの信頼性を高めるものとする(**SHALL**)。
2. CSP が不正行為の緩和策を使用する場合、CSP はこれらの緩和策についてプライバシー影響評価を実施するものとする(**SHALL**)。
3. そのようなアセスメントでは、何らかのプライバシーリスクの緩和策（例：リスクの受容、転嫁、保持の制限、使用制限、通知）またはその他の技術的な緩和策（例：暗号化）が含まれ、これらのガイドラインに従って文書化されなければならない。

[^alternatives]。Applicantの代表者がいるかどうかに関わらず、Trusted Refereeの使用は1つのオプションである。補足的なIdentity Evidenceのタイプについては、[セクション 5.1.9](../ial/#TRs-ARs) を参照すること。

{% comment %}
1. The CSP **SHOULD** obtain additional confidence in identity proofing using fraud mitigation measures (e.g., examining the device characteristics of the applicant, evaluating behavioral characteristics, and checking vital statistic repositories such as the Death Master File ([[DMF]](sec11_references.md#ref-dmf)). 
2. In the event the CSP uses fraud mitigation measures, the CSP **SHALL** conduct a privacy risk assessment for these mitigation measures. 
3. Such assessments **SHALL** include any privacy risk mitigations (e.g., risk acceptance or transfer, limited retention, use limitations, notice) or other technological mitigations (e.g., cryptography), and be documented per these guidelines.


[^alternatives]: Options include using a Trusted Referee, with or without an Applicant Representative; see [Sec. 5.1.9](../ial/#TRs-ARs) for supplemental identity evidence types. 
{% endcomment %}

### 一般的なプライバシー要件 {#PrivacyReqs}

{% comment %}
### General Privacy Requirements {#PrivacyReqs}
{% endcomment %}

次のプライバシー要件は、任意のIALでIdentityサービスを提供するすべてのCSPに該当する。
{% comment %}
The following privacy requirements apply to all CSPs providing identity services at any IAL. 
{% endcomment %}

#### プライバシーリスク評価
{% comment %}
#### Privacy Risk Assessment
{% endcomment %}

1. CSP は、Identity Proofingとエンロールメントに用いるプロセスについて、プライバシーリスク評価を実施し、 文書化しなければならない [^privacyframework]。
	1. Identity Proofingとエンロールメントを目的とした、PII の任意の処理（Identity Attribute、バイオメトリクス、画像、ビデオ、スキャン、またはIdentity Evidenceのコピーなど）。
	2. ここで指定されている必須要件を超えて、ApplicantのIdentityをVerifyするために CSP が取る追加のステップ。
	3. 法律または法的手続きに遵守する場合を除き、Identity Proofingとエンロールメントのスコープ外で行われる、PII に対する任意の処理。
	4. Identityレコードおよび PII の保持スケジュール。さらに、
	5. CSP に代わってサードパーティサービスが処理する任意のPII。
	{:.letter-list}
2. プライバシーリスク評価の結果に基づいて、CSP は、自らが処理する PII の分離可能性、予測可能性、管理性、機密性、完全性、および可用性を維持するために講じる手段を文書化するものとする(**SHALL**)。このような措置を決定する際、CSP は *NIST Privacy Framework* [[NIST-Privacy]](sec11_references.ja.md#ref-NIST-Privacy) および NIST Special Publication [[SP800-53]](sec11_references.ja.md#ref-SP800-53) を参考にするものとする(**SHALL**)。
3. CSP は、PII の処理に影響を与えるIdentityサービスの変更を行う場合は、いつでもプライバシーリスクを再評価し、プライバシーリスク評価を更新しなければならない。
4. CSP は、Practice Statementに記載されているとおり、定期的にプライバシーリスク評価をレビューし、 PII の処理に関連する最新のリスクを正確に反映するようにしなければならない。(**SHALL**) 
5. CSP は、そのサービスを使用するすべての組織に対して、プライバシーリスク評価のサマリーを提供できる状態にするものとする(**SHALL**)。そのサマリーは、当該組織がデューディリジェンスを行えるように、十分な詳細であるものとする(**SHALL**)。

{% comment %}
1. The CSP **SHALL** conduct and document a privacy risk assessment for the processes used for identity proofing and enrollment.[^privacyframework]  At a minimum, the privacy risk assessment **SHALL** assess the risks associated with:

	1. Any processing of PII for the purpose of identity proofing and enrollment, including identity attributes, biometrics, images, video, scans, or copies of identity evidence;
	2. Any additional steps the CSP takes to verify the identity of an applicant beyond the mandatory requirements specified herein;
	3. Any processing of PII for purposes outside the scope of identity proofing and enrollment except to comply with law or legal process;
	4. The retention schedule for identity records and PII; and,
	5. Any PII that is processed by a third party service on behalf of the CSP.
	{:.letter-list}
2. Based on the results of its privacy risk assessment, the CSP **SHALL** document the measures it takes to maintain the disassociability, predictability, manageability, confidentiality, integrity, and availability of the PII it processes. In determining such measures, the CSP **SHALL** consult the *NIST Privacy Framework* [[NIST-Privacy]](sec11_references.md#ref-NIST-Privacy) and NIST Special Publication [[SP800-53]](sec11_references.md#ref-SP800-53).
3. The CSP **SHALL** re-assess privacy risks and update its privacy risk assessment any time it makes changes to its identity service that affect the processing of PII.
4. The CSP **SHALL** review its privacy risk assessment periodically, as documented in its practice statement, to ensure it accurately reflects the current risks associated with the processing of PII.
5. The CSP **SHALL** make a summary of its privacy risk assessment available to any organizations that use its services. The summary **SHALL** be in sufficient detail to enable such organizations to do due dilligence.
{% endcomment %}

#### 追加のプライバシー保護策

{% comment %}
#### Additional Privacy Protective Measures
{% endcomment %}

1. PII のProcessingは、ClaimされたIdentityの実在性をvalidateし、ClaimされたIdentityをApplicantに関連付け、RPに対しては認可の判断に利用するAttributeを提供するために、必要最低限のものに限られるものとする(**SHALL**)。
2. CSP は、[Sec. 5.1.2](sec5_ial.ja.md#PrivacyReqs) のプライバシー要件に従って、Identity Resolutionに必要な場合に社会保障番号 (SSN) をAttributeとして収集してもよい(**MAY**)。加えて、CSP は、SSN データの拡散と保持を制限するために、プライバシー保護技術（例：完全なAttribute値そのものではなく、派生したAttribute値を送受信）を実装するものとする(**SHALL**)。SSN を把握していることは、Identity Proofingと見なされないものとする(**SHALL NOT**)。
3. 収集時に、CSP は、Identity Proofingに必要なAttributeを収集する目的をApplicantに対して明示的に通知するものとする(**SHALL**)。目的としては、そのようなAttributeがIdentity Proofingプロセスを完了するために任意であるか必須であるかどうか、CSP がApplicantから変化するSubscriberアカウントに保存するつもりの特定のAttributeおよび他の機微データ、Attributeを提供しない場合の結果、そして何らかのレコード保持要件がある場合はその詳細などが含まれる。
4. CSP は、Applicantの苦情およびIdentity Proofingに起因する問題を救済するためのメカニズムを提供するものとする(**SHALL**)。これらのメカニズムは、Applicantが見つけやすく、利用しやすいものであるものとする(**SHALL**)。CSP は、苦情または問題の解決を達成するために、そのメカニズムが効果的であるかをアセスメントするものとする(**SHALL**)。

[^privacyframework]: プライバシーリスク評価の詳細については、NIST プライバシーフレームワークを参照: エンタープライズリスクマネジメントを通じてプライバシーを改善するためのツール <https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.01162020.pdf>

[^notice]: [[NISTIR8062]](sec11_references.ja.md#ref-NISTIR8062) では、予測可能性と管理可能性の概要について、これら目標を達成する方法の例を含め示している。

{% comment %}
1. Processing of PII **SHALL** be limited to the minimum necessary to validate the existence of the claimed identity, associate the claimed identity with the applicant, and provide RPs with attributes they may use to make authorization decisions.
2. The CSP **MAY** collect the Social Security Number (SSN) as an attribute when necessary for identity resolution, in accordance with the privacy requirements in [Sec. 5.1.2](sec5_ial.md#PrivacyReqs). Additionally, CSPs **SHALL** implement privacy protective techniques (e.g., transmitting and accepting derived attribute values rather than full attribute values themselves) to limit the proliferation and retention of SSN data. Knowledge of the SSN **SHALL NOT** be considered identity evidence.
3. At the time of collection, the CSP **SHALL** provide explicit notice to the applicant regarding the purpose for collecting attributes necessary for identity proofing, including whether such attributes are voluntary or mandatory to complete the identity proofing process, the specific attributes and other sensitive data that the CSP intends to store in the applicant's subsequent subscriber account, the consequences for not providing the attributes, and the details of any records retention requirement if one is in place.
4. The CSP **SHALL** provide mechanisms for redress of applicant complaints and for problems arising from the identity proofing. These mechanisms **SHALL** be easy for applicants to find and use. The CSP **SHALL** assess the mechanisms for their efficacy in achieving resolution of complaints or problems.

[^privacyframework]: For more information about privacy risk assessments, refer to the NIST Privacy Framework: A Tool for Improving Privacy through Enterprise Risk Management at <https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.01162020.pdf>.

[^notice]: [[NISTIR8062]](sec11_references.md#ref-NISTIR8062) provides an overview of predictability and manageability including examples of how these objectives can be met.
{% endcomment %}

### 一般的な Equity 要件 {#EquityReqs}

{% comment %}
### General Equity Requirements {#EquityReqs}
{% endcomment %}

Equityの向上というゴールをサポートし、全体的なリスクアセスメントプロセスの一環で、CSP はそのIdentityサービスの要素をアセスメントして、あるグループのメンバーが他のグループと比較して、不公平なアクセス、処遇、あるいは結果になる可能性があるプロセスまたは技術を特定するものとする(**SHALL**)。 不公平なアクセスあるいは結果となりえるIdentity Proofingプロセスおよび技術の非網羅的なリストについては、[Sec. 10](sec10_equity.ja.md#EquityConsiderations)を参照すること。


大統領令 13985 [[EO13985]](sec11_references.ja.md#ref-EO13985) は、_Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_ として、政府プログラムと政策が有色人種およびその他十分な便益を享受できていないグループのための機会および便益に対する組織的障壁を存続させてしまっていないかどうか、その程度がどれほどであるか、評価するよう各連邦機関に求めていることに注意すること。 

{% comment %}
In support of the goal of improved equity, and as part of its overall risk assessment process, the CSP **SHALL** assess the elements of its identity service to identify processes or technologies that can possibly result in inequitable access, treatment, or outcomes for members of one group as compared to others.  See [Sec. 10](sec10_equity.md#EquityConsiderations) for a non-exhaustive list of identity proofing processes and technologies that may be subject to inequitable access or outcomes. 


Note that executive order 13985 [[EO13985]](sec11_references.md#ref-EO13985), _Advancing Racial Equity and Support for Underserved Communities Through the Federal Government_, requires each federal agency to assess whether, and to what extent, its programs and policies perpetuate systemic barriers to opportunities and benefits for people of color and other underserved groups.  
{% endcomment %}

アクセス、処遇、結果の不公平のリスクを評価する場合、以下の要件が適用される。

1.  リスク評価の結果に基づいて、CSP は、不公平なアクセス、処遇、または結果を生じる可能性を軽減するために講じる措置を文書化するものとする(**SHALL**)。 
2.  CSP は、プロセスまたは技術に影響を与えるIdentityサービスの変更を行う場合は、公平なアクセス、処遇、または成果に対するリスクを再評価するものとする(**SHALL**)。
3.  CSP は、そのサービスに関連する現在のリスクを正確に反映するように、公平なアクセス、処遇、または成果に対するリスクを定期的に再評価するものとする(**SHALL**)。
4.  CSP は、これらのリスクアセスメントへのApplicantの参加を義務付けることはしないものとする(**SHALL NOT**)。
5.  CSP は、不公平なアクセス、処遇、または結果に関連するリスクの評価結果、および関連する軽減策を、そのサービスを使用するすべての組織または個人が利用できるようにするものとする(**SHALL**)。
6.  CSP は、その評価結果も一般に公開するものとする(**SHALL**)。 

{% comment %}
When assessing the risk of inequitable access, treatment, or outcomes, the following requirements apply:

1.  Based on the results of its risk assessment, the CSP **SHALL** document the measures it takes to mitigate the possibility of inequitable access, treatment, or outcomes.
2.  The CSP **SHALL** re-assess the risks to equitable access, treatment, or outcomes any time it makes changes to its identity service that affect the processes or technologies.
3.  The CSP **SHALL** re-assess the risks to equitable access, treatment, or outcomes periodically to ensure it accurately reflects the current risks associated with its service.
4.  The CSP **SHALL NOT** make applicant participation in these risk assessments mandatory.
5.  The CSP **SHALL** make the results of its assessment of risks associated with inequitable access, treatment, or outcomes, and any associated mitigations, available to any organizations or individuals that use its service.
6.  The CSP **SHALL** also make the results of its assessment publicly available.    
{% endcomment %}


### 一般的なセキュリティ要件 {#SecurityReqs}

{% comment %}
### General Security Requirements {#SecurityReqs}
{% endcomment %}

1. 第三者が関与する取引を含め、Identity Proofingプロセス内の各オンライン取引は、認証された保護チャネルを介して行うものとする(**SHALL**）。
2. Identity Proofingプロセスの一環として収集されたIdentity Attributeのフォームのすべての PII は、情報の機密性と完全性を確保するために保護されるものとする(**SHALL**）。
3. CSP は、NIST リスク管理フレームワーク [[NIST-RMF]](sec11_references.ja.md#ref-NIST-RMF) に従ってそのIdentityサービスの運用に関連するリスクを評価し、適切なベースラインセキュリティコントロールを適用するものとする(**SHALL**)。

{% comment %}
1. Each online transaction within the identity proofing process, including transactions that involve third parties, **SHALL** occur over an authenticated protected channel.
2. All PII, in the form of identity attributes, collected as part of the identity proofing process **SHALL** be protected to ensure the confidentiality and integrity of the information.
3. The CSP **SHALL** assess the risks associated with operating its identity service, according to the NIST risk management framework [[NIST-RMF]](sec11_references.md#ref-NIST-RMF), and apply an appropriate baseline security controls. 
{% endcomment %}

### 連邦機関向けの追加要件 {#Feds}

{% comment %}
### Additional Requirements for Federal Agencies {#Feds}
{% endcomment %}

以下の要件は、連邦機関が独自のIdentityサービスを運用するか、Identityサービスの一部として外部 CSP を使用するかどうかに関係なく、連邦機関に適用される。

1. 機関は、Senior Agency Official for Privacy（SAOP）と協議し、Identity Proofingを行うためのバイオメトリクスを含む PII の収集が、Privacy Actの要件を発動するかどうかを決定する分析を行うものとする(**SHALL**)。
2. 機関は SAOP と協議して、Identity Proofingを行うためのバイオメトリクスを含む PII の収集が 2002 年のE-Government Act [[E-Gov]](sec11_references.ja.md#ref-E-Gov) の要件を発動するかどうかを決定する分析を実施するものとする(**SHALL**)。
3. 機関は、該当する場合、そのような収集を対象とするSystem of Records Notice（SORN）を公開するものとする(**SHALL**)。
4. 機関は、該当する場合、当該収集を対象とするプライバシー影響評価(PIA)を公開するものとする(**SHALL**)。
5. 機関は、ダイバーシティー、Equity、インクルージョン、およびアクセシビリティ（DEIA）を担当する上級職員、事業所、または統治機関と協議し、サービスを受けるすべての集団のニーズを満たすためにIdentity Proofingサービスをどのように設計、調達、および管理すべきかを判断するものとする(**SHALL**)。
6. 機関は、組織内の広報およびコミュニケーションの専門家と協議し、Identity Proofingに関連する要件を含む新しいプロセスの展開または既存のプロセスの更新に伴って、コミュニケーションまたは一般認識戦略を立てるべきかどうかを決定するものとする(**SHALL**)。これにはサービスに関連する技術の使用方法に関する詳細情報を示す資料、よくある質問（FAQ）ページ、Identity Proofingプロセスに参加するための前提条件（必要なEvidenceなど）、ウェビナー またはその他のライブもしくは録画済み情報 Session 、あるいはユーザー受け入れのサポートや、Applicantに質問、問題、フィードバックを伝える仕組みを提供するその他の媒体を含めることができる。
5. 第三者の CSP を使用する場合、機関は、PIA プロセスの一環として CSP のプライバシーリスク評価に依拠する前に、独自のプライバシーリスク評価を実施するか、デューデリジェンスを行う責任を負うものとする(**SHALL**)。
6. 第三者の CSP を使用する場合、機関は、CSP のEquityリスク評価を、自らのEquityリスク評価に組み込むものとする(**SHALL**)。

{% comment %}
The following requirements apply to federal agencies, regardless of whether they operate their own identity service or use an external CSP as part of their identity service:

1. The agency **SHALL** consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis determining whether the collection of PII, including biometrics, to conduct identity proofing triggers Privacy Act requirements.
2. The agency **SHALL** consult with their SAOP to conduct an analysis determining whether the collection of PII, including biometrics, to conduct identity proofing triggers E-Government Act of 2002 [[E-Gov]](sec11_references.md#ref-E-Gov) requirements.
3. The agency **SHALL** publish a System of Records Notice (SORN) to cover such collection, as applicable.
4. The agency **SHALL** publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.
5. The agency **SHALL** consult with the senior official, office, or governance body responsible for diversity, equity, inclusion, and accessibility (DEIA) for their agency to determine how the identity proofing service should be designed, resourced, and administered to meet the needs of all served populations.
6. The agency **SHOULD** consult with public affairs and communications professionals within their organization to determine if a communications or public awareness strategy should be developed to accompany the roll-out of any new process, or an update to an existing process, including requirements associated with identity proofing. This may include materials detailing information about how to use the technology associated with the service, a Frequently Asked Questions (FAQs) page, prerequisites to participate in the identity proofing process (such as required evidence), webinars or other live or pre-recorded information sessions, or other media to support adoption and provide applicants with a mechanism to communicate questions, issues, and feedback.
5. If the agency uses a third-party CSP, the agency SHALL be responsible for conducting its own privacy risk assessments or doing due diligence before relying on the CSP’s privacy risk assessment as part of its PIA process.
6. If the agency uses a third-party CSP, the agency **SHALL** incorporate the CSP’s assessment of equity risks into its own assessment of equity risks.
{% endcomment %}

###  Enrollment コード要件 {#EnrollCodes}

{% comment %}
###  Requirements for Enrollment Codes {#EnrollCodes}
{% endcomment %}

Enrollmentコードは、Applicantが有効なアドレスにアクセスできることを確認するために使用されます。Identity ProofingとEnrollmentが 1 回の Session で完了しない場合、Enrollmentコードは、Enrollmentプロセスを完了する目的で、ApplicantのEnrollmentレコードへのバインドを再確立するために使用することもできる。

以下の要件は、任意の IAL でEnrollmentコードを使用するすべての CSP に適用される。

1. Enrollmentコードは、有効なアドレス（郵便番号、電話番号、電子メールアドレスなど）に送信されるものとする(**SHALL**)。
2. Applicantは、Identity Proofing手続きを行うために有効なEnrollmentコードを提示するものとする(**SHALL**)。  
3. 3. Enrollmentコードは、以下のいずれかから構成されるものとする(**SHALL**)。
    1. 少なくとも20ビットのエントロピーを持つ承認された乱数発生器によって生成された6桁のランダムな数字。
    2. 適切に構築された Session ID（少なくとも64ビットのエントロピー）を含む、一意に識別されるアドレスに配信される安全なリンク、または、
    3. 少なくとも20ビットのエントロピーを持つランダムなシークレットを含む機械可読な光学的なラベル（QRコードなど）。
    {:.letter-list} 
4. Enrollmentコードの有効期限は以下の通りとするものとする(**SHALL**)。
    1. 米国本土内のValidateされた郵便物の宛先に送付された場合、最大 21 日間有効である。
    2. 米国本土以外のValidateされた郵便物の宛先に送られた場合は、30日間。
    3. Validateされたな電話番号（SMSまたは音声）に送信された場合、10分間。
    4. Validateされたな電子メールアドレスに送信された場合、24時間。
    {:.letter-list}
5. Enrollmentコードは、認証要素として使用してはならない(**SHALL NOT**)。

{% comment %}
Enrollment codes are used to confirm an applicant has access to a validated address. If identity proofing and enrollment are not completed in a single session, an enrollment code can also be used to re-establish an applicant’s binding to their enrollment record for the purposes of completing the enrollment process.

The following requirements apply to all CSPs that employ enrollment codes at any IAL:

1. Enrollment codes **SHALL** be sent to a validated address (e.g., postal address, telephone number, or email address).
2. The applicant **SHALL** present a valid enrollment code to complete the identity proofing process.
3. Enrollment codes **SHALL** be comprised of one of the following:
    1. A random six digit number generated by an approved random number generator with at least 20 bits of entropy;
    2. A secure link delivered to a uniquely identified address containing an appropriately constructed session ID (at least 64 bits of entropy); or
    3. A machine readable optical label (such as a QR code) that contains a random secret with at least 20 bits of entropy.
    {:.letter-list}
4. Enrollment codes **SHALL** be valid for at most:
    1. 21 days, when sent to a validated postal address within the contiguous United States;
    2. 30 days, when sent to a validated postal address outside the contiguous United States;
    3. 10 minutes, when sent to a validated telephone number (SMS or voice); or
    4. 24 hours, when sent to a validated email address.
    {:.letter-list}
5. The enrollment code **SHALL NOT** be used as an authentication factor. 
{% endcomment %}

### Identity Proofingの通知要件 {#ProofingNotifs}

{% comment %}
###  Requirements for Notifications of Identity Proofing {#ProofingNotifs}
{% endcomment %}

Proofing通知は、Applicantの有効なアドレスに送付され、Identity Proofingに成功したことを通知する。 これら通知により、Identity Proofing対象の人物が、ClaimされたIdentityの所有者であることをさらに保証する。
以下の要件は、任意の IAL での Identity Proofingプロセスの一部としてProofing通知を送信するすべての CSP に適用される。

Proofingの通知は:

1.  有効な記録上のアドレス（郵便番号、電話番号、電子メール・アドレスなど）に送信されるものとする(**SHALL**)。可能な限り、CSP は、ProofingおよびEnrollmentコードの通知を異なる有効なアドレスに送信するものとする(**SHALL**)。  
2.  Identityサービスの名前およびIdentity Proofingが完了した日付など、Identity Proofingイベントに関する詳細を含むものとする(**SHALL**)。
3.  受取人がIdenitty Proofingイベントを否認する場合に取るべき行動について、連絡先情報を含む 明確な指示を提供するものとする(**SHALL**)。
4.  組織または CSP が収集する情報のセキュリティおよびプライバシーを保護する方法、およびIdentityサービスのSubscriberとして受信者が負う責任などの追加情報を提供するものとする(**SHALL**)。

{% comment %}
Notifications of proofing are sent to the applicant's validated address notifying them that they have been successfully identity proofed.  These notices provide added assurance that the person who underwent identity proofing is the owner of the claimed identity. 

The following requirements apply to all CSPs that send notifications of proofing as part of their identity proofing processes at any IAL.

Notifications of proofing:

1.  **SHALL** be sent to a validated address (e.g., postal address, telephone number, or email address) of record. Whenever possible, CSPs **SHOULD** send notifications of proofing and enrollment codes to different validated addresses.
2.  **SHALL** include details about the identity proofing event, such as the name of the identity service and the date the identity proofing was completed.
3.  **SHALL** provide clear instructions, including contact information, on actions to take in the case the recipient repudiates the identity proofing event.
4.  **SHOULD** provide additional information, such as how the organization or CSP protects the security and privacy of the information it collects and any responsibilities the recipient has as a subscriber of the identity service.

{% endcomment %}

###  バイオメトリクスの利用要件 {#ProofBios}
{% comment %}
###  Requirements for Use of Biometrics {#ProofBios}
{% endcomment %}

バイオメトリクスとは、個人を認識するために使用できる生物学的及び行動的特徴、すなわち（これらに限定されるわけではないが）指紋、虹彩構造、顔の特徴などに基づく個人の自動認識のことである。このガイドラインで使用されるバイオメトリックデータは、生物学的および行動学的特徴の、capture、storage、またはprocessingのどの段階においても、アナログまたはデジタルで表現されたもののことである。これには、Applicantからの生きたバイオメトリックサンプル（例：顔画像、指紋）、およびEvidenceから得られたバイオメトリックリファレンス （例：運転免許証の顔画像、ID カード上の指紋特徴点テンプレート）が含まれる。Identity Proofingプロセスに適用されるように、CSP はバイオメトリクスを使用して、所定の集団またはコンテキスト内で個人のIdentityを一意に解決し、個人がIdentity Evidenceの正当な対象者であることをverifyし、その個人をIdentity Evidenceまたはクレデンシャルの新たな要素と結びつけることができる。

{% comment %}
Biometrics is the automated recognition of individuals based on their biological and behavioral characteristics such as, but not limited to, fingerprints, iris structures, or facial features that can be used to recognize an individual. As used in these guidelines, biometric data refers to any analog or digital representation of biological and behavioral characteristics at any stage of their capture, storage, or processing. This includes live biometric samples from applicants (e.g., facial images, fingerprint), as well as biometric references obtained from evidence (e.g., facial image on a driver’s license, fingerprint minutiae template on identification cards). As applied to the identity proofing process, CSPs may use biometrics to uniquely resolve an individual identity within a given population or context, verify that an individual is the rightful subject of identity evidence, and/or bind that individual to a new piece of identity evidence or credential.
{% endcomment %}

以下の要件は、Identity Proofingプロセスの一部としてバイオメトリックメカニズムを採用する CSP に適用される: 

1. CSP は、バイオメトリクスのすべての利用について、収集されるバイオメトリックデータが何であるか、その保存方法、加えて適用法と規制に照らしたバイオメトリック情報の削除の方法について明確で公開された情報を提供するものとする(**SHALL**)。
2. CSPは、バイオメトリック情報を収集する前に、すべてのApplicantから明示的にバイオメトリックについての同意を得るものとする(**SHALL**)。
3. CSPは、バイオメトリックについての同意を、Subscriberのアカウントに保管するものとする(**SHALL**)。
4. CSPは、すべてのバイオメトリック情報の削除プロセスとデフォルトの保存期間を文書化し、公開するものとする(**SHALL**)。
5. CSPは、規制、法律、または制定法によって別途制限される場合を除き、個人がいつでも自分のバイオメトリック情報の削除を要求するのを認めるものとする(**SHALL**)。
6. CSPは、すべてのバイオメトリック・アルゴリズムについて、独立したエンティティ（例：認定ラボラトリや研究機関）による性能テスト（人口統計グループ間の性能を含む）を実施するものとする(**SHALL**)。
7. すべてのアルゴリズムのテストは、所定の評価様式が、公開されている ISO/IEC 標準との一貫性を有するものとする(**SHALL**)。
9. CSPは、バイオメトリックの使用に際して最低性能基準値を満たすものとする(**SHALL**):
	- 他人受入率(False match rate): 1:10,000 またはそれ以上。
	- 本人拒否率(False non-match rate): 1:10,000 またはそれ以上 
10. CSP は、異なる人口統計学的グループ（人種的背景、性別、民族性など）のApplicantに対して同様の性能特性を提供するバイオメトリック・テクノロジーを採用するものとする(**SHALL**)。人口統計学的グループ間で性能に差があることが判明した場合、CSP は、影響を受ける個人に救済オプションを提供し、性能の差を解消するために迅速に行動するものとする(**SHALL**)。
11. CSPは、すべての性能テストおよび運用テストの結果を公開するものとする(**SHALL**)。
11. CSPは、システムの運用環境およびユーザ母集団と高い類似性のある条件下で、採用したバイオメトリック技術の性能と人口統計学的な影響を評価するものとする(**SHALL**)。このような評価に実在するユーザが含まれる場合、ユーザの参加は任意であるものとする(**SHALL**)。
12. CSPは、すべての性能および運用テストの結果を公開するものとする(**SHALL**)。

{% comment %}
The following requirements apply to CSPs that employ biometric mechanisms as part of their identity proofing process: 

1. CSPs **SHALL** provide clear, publicly available information about all uses of biometrics, what biometric data is collected, how it is stored, and information on how to remove biometric information consistent with applicable laws and regulations.
2. CSPs **SHALL** collect an explicit biometric consent from all applicants before collecting biometric information.
3. CSPs **SHALL** store the biometric consent with the subscriber's account.
4. CSPs **SHALL** have a documented, and publicly available, deletion process and default retention period for all biometric information.
5. CSPs **SHALL** allow individuals to request deletion of their biometric information at any time, except where otherwise restricted by regulation, law, or statute.
6. CSPs **SHALL** have all biometric algorithms tested by an independent entity (e.g., accredited laboratory or research institution) for performance, including performance across demographic groups.
7. Testing of all algorithms **SHALL** be consistent with published ISO/IEC standards for the given modality.
9. CSPs **SHALL** meet the minimum performance thresholds for biometric usage:
	- False match rate: 1:10,000 or better; and
	- False non-match rate: 1:100 or better
10. CSPs **SHALL** employ biometric technologies that provide similar performance characteristics for applicants of different demographic groups (racial background, gender, ethnicity, etc.). If performance differences across demographic groups are discovered, CSPs **SHALL** act expeditiously to provide redress options to affected individuals and to close performance gaps.
11. CSPs **SHALL** make all performance and operational test results publicly available.
11. CSPs **SHALL** assess the performance and demographic impacts of employed biometric technologies in conditions substantially similar to the operational environment and user base of the system. When such assessments include real-world users, participation by users **SHALL** be voluntary.
12. CSPs **SHALL** make all performance and operational test results publicly available.
{% endcomment %}

以下の要件は、Applicantからバイオメトリックの特徴を収集する CSP に適用される:  

1. CSP は、バイオメトリックはApplicantから収集されたものであり、別の対象から取得したものではないことを保証する方法で、バイオメトリクスを収集するものとする(**SHALL**）。
2. バイオメトリクスをリモートで収集し比較する場合、CSP は、生存する人間が本当にそこに存在していることを確認し、スプーフィングとなりすましの試みを軽減するために、生存検出機能を実装するものとする(**SHALL**)。
3. 個人でバイオメトリクスを収集する場合、CSPはオペレータにバイオメトリクス・ソース（例：指、顔）にnon-naturalな物質が存在するかどうかを確認させ、Proofingプロセスの一環としてそのような検査を実行するものとする(**SHALL**)。

{% comment %}
The following requirements apply to CSPs who collect biometric characteristics from applicants:  

1. CSP **SHALL** collect biometrics in such a way that ensures that the biometric is collected from the applicant, and not another subject.
2. When collecting and comparing biometrics remotely, the CSP **SHALL** implement liveness detection capabilities to confirm the genuine presence of a live human being and to mitigate spoofing and impersonation attempts.
3. When collecting biometrics in person, the CSP **SHALL** have the operator view the biometric source (e.g., fingers, face) for presence of non-natural materials and perform such inspections as part of the proofing process.
{% endcomment %}

###  Trusted Referees と Applicant References {#TRs-ARs}

{% comment %}
###  Trusted Referees and Applicant References {#TRs-ARs}
{% endcomment %}

アクセス性を向上させ、オンライン政府サービスへの平等なアクセスを促進するために、CSP は _trusted referees_ を提供する。Trusted Referee は、特定の IAL へのIdentity Proofing要件を満たすことができない個人が、Identity ProofingおよびEnrollmentを円滑に進めるために利用される。そのような個人および人口統計学的グループは次のような個人が例として挙げられる: 必要なIdentity Evidenceを所有せず入手できない個人、障害者、高齢者、ホームレス経験者、オンライン・サービスまたはコンピューティング・ デバイスにほとんどまたは全くアクセスできない個人、銀行口座を持たないあるいはクレジット履歴が限定されている人、Identity盗難被害者、自然災害で避難したまたは影響を受けた個人、および 18 才未満の児童


{% comment %}
To increase accessibility and promote equal access to online government services, CSPs provide _trusted referees_. Trusted referees are used to facilitate the identity proofing and enrollment of individuals who are otherwise unable to meet the requirements for identity proofing to a specific IAL. Examples of such individuals and demographic groups include: individuals who do not possess and cannot obtain the required identity evidence; persons with disabilities; older individuals; persons experiencing homelessness; individuals with little or no access to online services or computing devices; persons without a bank account or with limited credit history; victims of identity theft; individuals displaced or affected by natural disasters; and children under 18.
{% endcomment %}

Trusted Refereeは、自力でIdentity Proofingプロセスを完了できない、または所定の IAL で指定されている要件を満たせない個人のIdentity ProofingおよびEnrollmentを促進するために、リスクに基づく判断を行う訓練を受けて認可された、CSP またはその パートナーの代理人である。

加えて、Identity ProofingプロセスへのApplicantの積極的な参加を妨げる、あるいは不可能にする状況が存在する場合がありうる。そのような状況は、身体的または精神的な制限、障害、入院、あるいはIdentity Proofingへの積極的な参加を困難にする他の一時的または恒常的な状況によるものである可能性がある。_Applicant Reference_ は、Applicantの特定の状況を裏付け、Identity ProofingプロセスにおいてApplicantを積極的に支援することを想定している。

{% comment %}
Trusted referees are agents of the CSP or its partners who are trained and authorized to make risk-based decisions to facilitate the identity proofing and enrollment of individuals who are unable to complete the identity proofing process on their own or meet the specified requirements for a given IAL.

Additionally, there may be circumstances that encumber or preclude the active participation of an applicant in the identity proofing process. Such circumstances may be due to physical or mental limitations, disabilities, hospitalization, or other temporary or permanent conditions that make active participation in the identity proofing difficult. An _applicant reference_ may vouch for an applicant's particular circumstances and may also actively assist the applicant in the identity proofing process.
{% endcomment %}

Applicant Referenceとは、ApplicantがIdentity Proofing要件を満たすことを支援するために、ApplicantのIdentity Proofingに参加する個人をいう。このような支援には、Applicantの状況を裏付けることや、Identity Proofingプロセス完了のためにApplicantを積極的に支援することが含まれる。Applicant Referenceは CSP の代理人ではないが、ApplicantのIdentity ProofingおよびEnrollmentを円滑に進めるために、通常はTrusted Refreeと連動する。Applicant Referenceから提供された情報は、ApplicantのIdentity Proofingで使用され、依拠されることがあるため、Applicant Referenceは、Applicantと同等以上の IAL でIdentity Proofingされる。Applicant Referenceの役割は、Identity Proofingプロセスを円滑に進めることに限定されており、Applicant Referenceは、RP との取引においてSubscriberを代理する権限を持たない。指定された IAL での Identity Proofing要件を満たすことができるApplicantにとって、単に物理的、技術的、言語翻訳または他の類似の支援を提供する個人は、Applicant Referenceとはみなされず、Identity Proofingを必要としない。

{% comment %}
Applicant references are individuals who participate in the identity proofing of an applicant in order to assist the applicant in meeting the identity proofing requirements. Such assistance may include vouching for the applicant’s circumstances and actively assisting the applicant in completing the identity proofing process. Applicant references are not agents of the CSP but they would typically work in conjunction with a trusted referee to facilitate the identity proofing and enrollment of an applicant. Since information provided by the applicant reference may be used and relied upon in the identity proofing of the applicant, the applicant reference is identity proofed to the same or higher IAL as the applicant. The role of applicant reference is limited to facilitating the identity proofing process and applicant references are not authorized to represent subscribers in transactions with RPs. Persons who simply provide physical, technical, language translation or other similar assistance to an applicant who is otherwise able to meet the requirements for identity proofing to the specified IAL are not considered to be applicant references and do not require identity proofing.
{% endcomment %}


####  Trusted Referees の要件 {#TrustedRefs}
{% comment %} 
####  Requirements for Trusted Referees {#TrustedRefs}
{% endcomment %}

CSPは、IAL 1および2で、リモートで実施するIdentity Proofingにおいて、Trusted Refereeを利用するオプションを提供するものとする(**SHALL**)。

以下の要件は、Trusted Refereeが提案される場面において、その利用に適用される:  

1. CSP は、[Sec. 5.1.1](sec5_ial.ja.md#DocRecReqs) で指定するように、Trusted Refereeの使用に関するポリシーと手続きを、Practice Statementの一部として文書で確立するものとする(**SHALL**)。
2. CSP は、Applicant固有の状況に基づいてApplicantのIdentity Proofingが成功するよう、リスクベースの判断を行うためにTrusted Refereeを訓練するものとする(**SHALL**)。
3. CSP は、Trusted Refereeサービスが利用できるかどうか、さらに当該サービスをどのように得ることができるのかについて、公に通知するものとする(**SHALL**)。

{% comment %}
CSPs **SHALL** provide the option for the use of trusted referees for remote identity proofing at IALs 1 and 2. 

CSPs **SHALL** provide the option for the use of trusted referees for remote identity proofing at IALs 1 and 2.

Where trusted referees are offered, the following requirements apply to their use:

1. The CSP **SHALL** establish written policies and procedures for the use of trusted referees as part of its practice statement, as specified in [Sec. 5.1.1](sec5_ial.md#DocRecReqs).
2. The CSP **SHALL** train its trusted referees to make risk-based decisions that allow applicants to be successfully identity proofed based on their unique circumstances.
3. The CSP **SHALL** provide notification to the public of the availability of trusted referee services and how such services are obtained.
{% endcomment %}
 
####  Applicant References の要件{#ApplicantRefs}
{% comment %}
####  Requirements for Applicant References {#ApplicantRefs}
{% endcomment %}

CSPはApplicant Referenceの利用を許可すべきである(**SHOULD**)。

以下の要件は、Applicant Referenceが利用に対して適用される:  

1. CSP は、Applicant Referenceを使用するための方針と手続きを、[Sec. 5.1.1](sec5_ial.ja.md#DocRecReqs) で指定されているように、Practice Statementの一部として文書で確立するものとする(**SHALL**)。
2. CSP は、Applicant Referenceを、Applicantに意図された同等以上の IAL でIdentity Proofingするものとする。
3. CSP がApplicant Referenceの使用を許可する場合、CSP はApplicant Referenceの許容範囲およびReferenceとApplicantの関係要件について、公に通知するものとする(**SHALL**)。


{% comment %}
CSPs **SHOULD** allow the use of applicant references. 

####  Requirements for Applicant References {#ApplicantRefs}

CSPs **SHOULD** allow the use of applicant references.

The following requirements apply to the use of applicant references at any IAL:

1. The CSP **SHALL** establish written policies and procedures for the use of applicant references as part of its practice statement, as specified in [Sec. 5.1.1](sec5_ial.md#DocRecReqs).
2. The CSP **SHALL** identity proof an applicant reference to the same or higher IAL intended for the applicant.
3. If the CSP allows for the use of applicant references, it **SHALL** provide notification to the public of the allowability of applicant references and any requirements for the relationship between the reference and the applicant.
{% endcomment %}

### Requirements for Interacting with Minors {#Minors}
{% comment %}
### Requirements for Interacting with Minors {#Minors}
{% endcomment %}

以下の要件は、任意のIALでIdentity Proofingサービスを未成年者に対して提供するすべてのCSPに対して適用される:

1.  CSP は、特定の IAL のEvidence要件を満たせない可能性のある未成年者のIdentity Proofingの方針および手順について、Practice Statementの一部として文書で確立するものとする(**SHALL**)。
2.  13 歳未満の個人とやり取りする際に、CSP は 1998 年のChildren’s Online Privacy Protection Act [[COPPA]](sec11_references.ja.md#ref-COPPA) に確実に準拠するものとする(**SHALL**)。
3.  CSP は、18 歳未満の個人とやり取りする際に、Applicant Referenceの使用することをサポートするものとする(**SHALL**)。

{% comment %}
The following requirements apply to all CSPs providing identity proofing services to minors at any IAL.

1.  The CSP **SHALL** establish written policy and procedures as part of its practice statement for identity proofing minors who may not be able to meet the evidence requirements for a given IAL.
2.  When interacting with persons under the age of 13, the CSP **SHALL** ensure compliance with the Children’s Online Privacy Protection Act of 1998 [[COPPA]](sec11_references.md#ref-COPPA).
3.  CSPs **SHALL** support the use of applicant references when interacting with individuals under the age or 18. 
{% endcomment %}


##  Identity Proofing プロセス {#id-proof-process}
{% comment %}
##  Identity Proofing Process {#id-proof-process}
{% endcomment %}

本書はいくつかの異なるIdentity Proofing手法に適用する要件を定める。取りうる手法は次を含む:

* 完全自動化されたリモートプロセス。
* CSPオペレータ支援によるリモート・プロセス 
* 自動化されたリモート・プロセスとオペレーター支援によるリモート・プロセスの組み合わせ。
* Applicantとの対面による物理的な対話プロセス、および 
* IAL3 監視下でのリモート(Supervised Remote)Identity Proofingプロセス

IAL1 および IAL2 でのIdentity Proofingは、これらのプロセスのいずれも使用することができるが、 IAL3 では、Applicantとの直接の物理的対話または IAL3 監視下にあるリモートIdentity Proofingを必要とする。

以下のセクションでは、各 IAL でのIdentity Proofingに関する要件を示す。

{% comment %}
This document provides requirements that apply to several different identity proofing methods. These possible methods include: 

* A fully automated, remote process;
* A CSP operator-assisted remote process;
* A combination of automated and operator-assisted remote process;
* An in-person, physical interaction with the applicant process; and
* An IAL3 Supervised Remote Identity Proofing process.

Identity proofing at IAL1 and IAL2 allow for any of the these processes to be used, while IAL3 requires in-person, physical interaction with the applicant or IAL3 Supervised Remote Identity Proofing.

The following sections provide requirements for identity proofing at each IAL.
{% endcomment %}

## Identity Assurance Level 1 {#IAL1}

IAL1 では、リモートおよび対面でのIdentity Proofingを認めています。IAL1 における Identity Proofing プロセスは、悪意のあるアクターによる不正な Identity の提示を検出するために、許容される様々な技術を認める一方で、ユーザー受け入れを促進し、偽陰性や申請からの離脱（Identity Proofingを正常に完了しない正当なApplicant）を最小化するものである。注目すべきは、IAL1 において、提供されたEvidenceと顔写真との自動比較などのバイオメトリクス照合の使用は任意であり、そのようなEvidenceの収集が実現不可能な場合や、プライバシーおよびEquityリスクがセキュリティの考慮事項を上回るような場合でも、ProofingおよびEnrollmentを進めることができるということである。 

以下の要件は、IAL1においてIdentity ProofingおよびEnrollmentサービスを提供するすべての CSP に適用される。

{% comment %}
IAL1 permits both remote and in-person identity proofing. Identity proofing processes at IAL1 allow for a range of acceptable techniques in order to detect the presentation of fraudulent identities by a malicious actor while facilitating user adoption and minimizing false negatives and application departures (legitimate applicants who do not successfully complete identity proofing). Notably, the use of biometric matching, such as the automated comparison of a facial portrait to supplied evidence, at IAL1 is optional, providing pathways to proofing and enrollment where such collection may not be viable or where privacy and equity risks outweigh security considerations.  


The following requirements apply to all CSPs providing identity proofing and enrollment services at IAL1.
{% endcomment %}


###  自動化された攻撃の防御
{% comment %}
###  Automated Attack Prevention
{% endcomment %}

CSP は、Identity Proofing プロセスに対する自動化された攻撃を防ぐための手段を実装するものとする(**SHALL**)。許容される手段には、ボットの検出、緩和、および管理ソリューション、行動分析、Web アプリケーションファイアウォール設定、およびトラフィック分析が含まれるが、これらに限定されない。

{% comment %}
The CSP **SHALL** implement a means to prevent automated attacks on the identity proofing process. Acceptable means include, but are not limited to: bot detection, mitigation, and management solutions; behavioral analytics; web application firewall settings; and traffic analysis.
{% endcomment %}

### Evidence および Core Attributes の収集要件

#### Evidence 収集
{% comment %}
### Evidence and Core Attributes Collection Requirements

#### Evidence Collection
{% endcomment %}

リモートまたは対面での Identity Proofing の場合、CSP は Applicant から以下のいずれかを収集するものとする(**SHALL**)。

1. SUPERIOR Evidence 1 つ、または
2. STRONG Evidence 1 つ、およびFAIR Evidence 1 つ。

{% comment %}
For remote or in-person identity proofing, the CSP **SHALL** collect _one_ of the following from the applicant:

1. One piece of SUPERIOR evidence, or
2. One piece of STRONG evidence and one piece of FAIR evidence 
{% endcomment %}


#### 追加 Attribute の収集
{% comment %}
#### Collection of Additional Attributes
{% endcomment %}

ValidateされたEvidenceが Identity Attribute の Source として好ましい。提示された Identity Evidence に、CSP が Core Attributes と考えるすべてのAttributeが含まれていなければ、CSP はApplicantが自己申告するAttributeを収集してもよい（**MAY**）。

{% comment %}
Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant. 
{% endcomment %}

### Evidence および Core Attributes の Validation 要件
{% comment %}
### Evidence and Core Attributes Validation Requirements
{% endcomment %}

CSPは、以下のいずれか _1つ_ の要件に従って SUPERIOR と STRONG の Evidence の真正性を検証するものとする(**SHALL**)。

1. 訓練を受けた担当者による目視検査
2. 物理的なセキュリティ機能の完全性を確認する技術の利用、またはEvidenceが詐称されているか不適切に変更されているかを検出することができる技術の利用
3. 存在する場合、デジタルセキュリティ機能の完全性を確認する。

CSPは、訓練を受けた担当者による目視検査によって、FAIR Evidenceが真正であることをValidateするものとする(**SHALL**)。

CSPは、以下の _両方_ の方法ですべての Core Attributes を Validate するものとする(**SHALL**)。

1. Evidenceの一部から取得したAttribute（口座番号または参照番号、名前、生年月日など）の正確性を、Authoritativeまたは信頼できるSourceと比較することでValidateする。
2. 自己申告のAttributeの正確性を、Authoritativeまたは信頼できるSourceと比較することでValidateする。
	
さらに保証を強めるため、CSP は、さまざまなSourceによってValidateされた Core Attributes を、全体的な一貫性があるかという観点で評価するものとする(**SHALL**)。

{% comment %}
The CSP **SHALL** validate the genuineness of each piece of SUPERIOR and STRONG evidence by _one_ of the following:

1. Visual inspection by trained personnel
2. The use of technologies that can confirm the integrity of physical security features or detect if the evidence is fraudulent or has been inappropriately modified
3. If present, confirming the integrity of digital security features

The CSP **SHALL** validate the genuineness of each piece of FAIR evidence by visual inspection by trained personnel.

The CSP **SHALL** validate all core attributes by _both_:

1. Validating the accuracy of attributes (such as account or reference number, name, and date of birth) obtained from pieces of evidence by comparison with authoritative or credible sources, and
2. Validating the accuracy of self-asserted attributes by comparison with authoritative or credible sources. 
	
For added assurance, the CSP **SHALL** evaluate the core attributes, as validated by various sources, for overall consistency.  
{% endcomment %}


### Identity Verification 要件
{% comment %}
### Identity Verification Requirements
{% endcomment %}

CSPは、以下のいずれか _1つ_ の要件に従って Applicant が ClaimされたIdentityとバインドできるかどうかをVerifyするものとする(**SHALL**)。

1.	Applicantの顔との物理的な比較、またはSUPERIORやSTRONG Evidenceに含まれる顔写真とApplicantの顔画像とバイオメトリクス比較、または
2.	AAL1 認証または AAL1 および FAL1 フェデレーションプロトコルを介したデジタルアカウントとの関連性の実証、または
3.	Applicantが有効なEnrollmentコードを提示してきたことのVerification [Sec.5.1.6](sec5_ial.ja.md#EnrollCodes)

{% comment %}
The CSP **SHALL** verify the binding of the applicant to the claimed identity by _one_ of the following:

1.	Physical comparison of the applicant’s face or biometric comparison of the facial image of the applicant to the facial portrait included on a piece of SUPERIOR or STRONG evidence, or
2.	Demonstrated association with a digital account through an AAL1 authentication or an AAL1 and FAL1 federation protocol, or
3.	Verification of the applicant's return of a valid enrollment code [Sec. 5.1.6](sec5_ial.md#EnrollCodes)
{% endcomment %}


### Proofing の通知要件
{% comment %}
### Notification of Proofing Requirement
{% endcomment %}

IAL1 での Identity Proofing が正常に完了すると、CSP は [Sec. 5.1.7](sec5_ial.ja.md#ProofingNotifs) で指定されているように、Applicantの有効なアドレスにProofing通知を送信するものとする(**SHALL**)。

{% comment %}
Upon the successful completion of identity proofing at IAL1, the CSP **SHOULD** send a notification of proofing to a validated address for the applicant, as specified in [Sec. 5.1.7](sec5_ial.md#ProofingNotifs). 

{% endcomment %}

## Identity Assurance Level 2 {#IAL2}
IAL1 と同様に、IAL2の Identity Proofingでは、なりすまし攻撃やその他のIdentity Proofingのエラーを軽減しながら、アクセシビリティを最大化するために、リモートおよび対面でのIdentity Proofingプロセスの両方が認められる。CSPは、リモートでのIAL2 Identity Proofingを、完全に自動化されたプロセス、CSP オペレータが参加するプロセス、またはその 2 つの組み合わせにより、達成することができる。

{% comment %}
Like IAL1, IAL2 identity proofing allows for both remote and in-person identity proofing processes in order to maximize accessibility while still mitigating against impersonation attacks and other identity proofing errors.  Remote IAL2 identity proofing can be accomplished by the CSP via a fully automated process, a CSP operator attended process, or a combination of the two. 
{% endcomment %}

###  自動化された攻撃の防御
{% comment %}
###  Automated Attack Prevention
{% endcomment %}

CSP は、Identity Proofing プロセスに対する自動化された攻撃を防ぐための手段を実装するものとする(**SHALL**)。許容される手段には、ボットの検出、緩和、および管理ソリューション、行動分析、Web アプリケーションファイアウォール設定、およびトラフィック分析が含まれるが、これらに限定されない。

{% comment %}
The CSP **SHALL** implement a means to prevent automated attacks on the identity proofing process. Acceptable means include, but are not limited to: bot detection, mitigation, and management solutions; behavioral analytics; web application firewall settings; and traffic analysis. 
{% endcomment %}


### Evidence および Core Attributes の収集要件

#### Evidence 収集
{% comment %}
### Evidence and Core Attributes Collection Requirements

#### Evidence Collection
{% endcomment %}

リモートまたは対面での Identity Proofing の場合、CSP は Applicant から以下のいずれかを収集するものとする(**SHALL**)。

1. SUPERIOR Evidence 1 つ、または
2. STRONG Evidence 1 つ、およびFAIR Evidence 1 つ。

{% comment %}
For remote or in-person identity proofing, the CSP **SHALL** collect _one_ of the following from the applicant:

1. One piece of SUPERIOR evidence
2. One piece of STRONG evidence and one piece of FAIR evidence
{% endcomment %}

#### Attribute の収集
{% comment %}
#### Collection of Attributes
{% endcomment %}

ValidateされたEvidenceが Identity Attribute の Source として好ましい。提示された Identity Evidence に、CSP が Core Attributes と考えるすべてのAttributeが含まれていなければ、CSP はApplicantが自己申告するAttributeを収集してもよい（**MAY**）。

{% comment %}
Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant. 
{% endcomment %}

### Evidence および Core Attributes の Validation 要件
{% comment %}
### Evidence and Core Attributes Validation Requirements
{% endcomment %}

CSPは、以下のいずれか _1つ_ の要件に従って SUPERIOR と STRONG の Evidence の真正性を検証するものとする(**SHALL**)。

1. 訓練を受けた担当者による目視検査
2. 物理的なセキュリティ機能の完全性を確認する技術の利用、またはEvidenceが詐称されているか不適切に変更されているかを検出することができる技術の利用
3. 存在する場合、デジタルセキュリティ機能の完全性を確認する。

CSPは、以下の方法ですべての Core Attributes を Validate するものとする(**SHALL**)。

1. Evidenceの一部から取得したAttribute（口座番号または参照番号、名前、生年月日など）の正確性を、Authoritativeまたは信頼できるSourceと比較することでValidateする。
2. 自己申告のAttributeの正確性を、Authoritativeまたは信頼できるSourceと比較することでValidateする。

さらに保証を強めるため、CSP は、さまざまなSourceによってValidateされた Core Attributes を、全体的な一貫性があるかという観点で評価するものとする(**SHALL**)。

{% comment %}
The CSP **SHALL** validate the genuineness of each piece of SUPERIOR and STRONG evidence by one of the following:

1. Visual inspection by trained personnel
2. The use of technologies that can confirm the integrity of physical security features or detect if the evidence is fraudulent or has been inappropriately modified
3. If present, confirming the integrity of digital security features

The CSP **SHALL** validate all core attributes by:

1. Validating the accuracy of attributes (such as account or reference number, name, and date of birth) obtained from pieces of evidence by comparison with authoritative or credible sources, and

2. validating the accuracy of self-asserted attributes by comparison with authoritative or credible sources


For added assurance, the CSP **SHALL** evaluate the core attributes, as validated by various sources, for overall consistency.  
{% endcomment %}


### Identity Verification 要件
{% comment %}
### Identity Verification Requirements
{% endcomment %}

#### リモートでの Identity Proofing
{% comment %}
#### Remote Identity Proofing
{% endcomment %}

CSPは、以下のいずれか _1つ_ の要件に従って Applicant が ClaimされたIdentityとバインドできるかどうかをVerifyするものとする(**SHALL**)。

1.	顔画像など収集したバイオメトリクス特性と、SUPERIORやSTRONG Evidenceに含まれており、関連付けられているリファレンスのバイオメトリクスとの比較、または
2.	AAL2 認証または AAL2 および FAL2 フェデレーションプロトコルを介したデジタルアカウントとの関連性の実証

{% comment %}
The CSP **SHALL** verify the binding of the applicant to the claimed identity by _one_ of the following: 

1.	Comparison of a collected biometric characteristic, such as a facial image, to the associated reference biometric contained on a piece of presented SUPERIOR or STRONG evidence  
2.	Demonstrated association with a digital account through an AAL2 authentication or an AAL2 and FAL2 federation protocol 
{% endcomment %}

#### 対面での Identity Proofing
{% comment %}
#### In-person Identity Proofing
{% endcomment %}

CSPは、提示されたSUPERIOR または STRONG Evidenceに含まれる顔写真と、Applicantの顔画像の物理的またはバイオメトリクス比較によって、Applicant が ClaimされたIdentityとバインドできるかどうかをVerifyするものとする(**SHALL**)。

{% comment %}
The CSP **SHALL** verify the binding of the applicant to the claimed identity by physical or biometric comparison of the facial image of the applicant to the facial portrait contained on a piece of presented SUPERIOR or STRONG evidence.
{% endcomment %}


### Proofing の通知要件
{% comment %}
### Notification of Proofing Requirement
{% endcomment %}

IAL2 での Identity Proofing が正常に完了すると、CSP は [Sec. 5.1.7](sec5_ial.ja.md#ProofingNotifs) で指定されているように、Applicantの有効なアドレスにProofing通知を送信するものとする(**SHALL**)。

{% comment %}
Upon the successful completion of identity proofing at IAL2, the CSP **SHALL** send a notification of proofing to a validated address for the applicant, as specified in [Sec. 5.1.7](sec5_ial.md#ProofingNotifs). 
{% endcomment %}

## Identity Assurance Level 3 {#IAL3}

IAL3 は、IAL2 で要求される手順にさらなる厳密さを加えたもので、Identity と RP をなりすまし、詐欺、 または他の著しく有害な損害から一層保護するための追加的かつ特定のプロセス（バイオメトリクス情報の 比較、収集、保持の実施を含む）が対象となる。さらに、IAL3 における Identity Proofingは、対面で行われる（ただし [Sec. 5.5.8](sec4_proofing.ja.md#IAL3supervised)に定義される監視下でのリモート Identity Proofingを含む）。

{% comment %}
IAL3 adds additional rigor to the steps required at IAL2 and is subject to additional and specific processes (including the use of biometric information comparison, collection, and retention) to further protect the identity and RP from impersonation, fraud, or other significantly harmful damages. In addition, identity proofing at IAL3 is performed in person (to include supervised remote identity proofing defined in [Sec. 5.5.8](sec4_proofing.md#IAL3supervised)).
{% endcomment %}

###  自動化された攻撃の防御
{% comment %}
###  Automated Attack Prevention
{% endcomment %}

CSP は、Identity Proofing プロセスに対する自動化された攻撃を防ぐための手段を実装するものとする(**SHALL**)。許容される手段には、ボットの検出、緩和、および管理ソリューション、行動分析、Web アプリケーションファイアウォール設定、およびトラフィック分析が含まれるが、これらに限定されない。

{% comment %}
The CSP **SHALL** implement a means to prevent automated attacks on the identity proofing process. Acceptable means include, but are not limited to: bot detection, mitigation, and management solutions; behavioral analytics; web application firewall settings; and traffic analysis.
{% endcomment %}


### Evidence および Core Attributes の収集要件

#### Evidence 収集
{% comment %}
### Evidence and Core Attributes Collection Requirements

#### Evidence Collection
{% endcomment %}

CSP は以下のいずれかに従い、ApplicantからEvidenceを収集するものとする(**SHALL**)。

1. SUPERIOR Evidence 2 つ、または
2. SUPERIOR Evidence 1 つ、およびSTRONG Evidence 1 つ、または
3. STRONG Evidence 2 つ、およびFAIR Evidence 1 つ

{% comment %}
The CSP **SHALL** collect evidence from the applicant according to _one_ of the following options:

1. Two pieces of SUPERIOR evidence, or
2. One piece of SUPERIOR evidence and one piece of STRONG evidence, or
3. Two pieces of STRONG evidence and one piece of FAIR evidence
{% endcomment %}

#### Attribute の収集
{% comment %}
#### Collection of Attributes
{% endcomment %}

ValidateされたEvidenceが Identity Attribute の Source として好ましい。提示された Identity Evidence に、CSP が Core Attributes と考えるすべての Attribute が含まれていなければ、CSP はApplicant が自己申告する Attribute を収集してもよい（**MAY**）。

{% comment %}
Validated evidence is the preferred source of identity attributes. If the presented identity evidence does not provide all the attributes the CSP considers core attributes, it **MAY** collect attributes that are self-asserted by the applicant. 
{% endcomment %}

### Validation 要件 {#s-4-5-3}
{% comment %}
### Validation Requirements {#s-4-5-3}
{% endcomment %}

#### Evidence Validation 要件
{% comment %}
#### Evidence Validation Requirements
{% endcomment %}

CSPは、暗号セキュリティ機能の完全性を確認し、何らかのデジタル署名をValidateすることによって、SUPERIOR Evidence の真正性を検証するものとする(**SHALL**)。

CSPは、以下のいずれか _1つ_ の要件に従って STRONG の Evidence の真正性を検証するものとする(**SHALL**)。

1. 訓練を受けた担当者による目視検査
2. 物理的なセキュリティ機能の完全性を確認する技術の利用、またはEvidenceが詐称されているか不適切に変更されているかを検出することができる技術の利用
3. 存在する場合、デジタルセキュリティ機能の完全性を確認する。これには、発行者のデジタル署名のValidationが含まれる。
{% comment %}
The CSP **SHALL** validate the genuineness of each piece of SUPERIOR evidence by confirming the integrity of its cryptographic security features and validating any digital signatures. 

The CSP **SHALL** validate the genuineness of each piece of STRONG evidence by _one_ of the following:

1. Visual inspection by trained personnel
2. The use of technologies that can confirm the integrity of physical security features and detect if the evidence is fraudulent or has been inappropriately modified
3. If present, confirming the integrity of digital security features, including the validity of the issuer's digital signature
{% endcomment %}


#### Core Attributes Validation 要件
{% comment %}
#### Core Attribute Validation Requirements
{% endcomment %}

CSPは、以下の _両方_ の方法ですべての Core Attributes を Validate するものとする(**SHALL**)。

1. Evidenceから、あるいは自己申告で取得したAttributeの正確性を、Authoritativeまたは信頼できるSourceと比較することでValidateする。
2. 前述したような方法で、提示されたデジタルEvidenceの暗号機能をValidateする。

さらに保証を強めるため、CSP は、さまざまなSourceによってValidateされた Core Attributes を、全体的な一貫性があるかという観点で評価するものとする(**SHALL**)。

{% comment %}
The CSP **SHALL** validate all core attributes by _both_:

1. Validating the accuracy of attributes obtained from pieces of evidence or applicant self-assertion by comparison with authoritative or credible sources
2. Validating the cryptographic features of any presented digital evidence, as described above

	
For added assurance, the CSP **SHALL** evaluate the core attributes, as validated by various sources, for overall consistency.  
{% endcomment %}

### Identity Verification 要件
{% comment %}
### Identity Verification Requirements
{% endcomment %}

CSPは、以下のいずれか _1つ_ の要件に従って Applicant が ClaimされたIdentityとバインドできるかどうかをVerifyするものとする(**SHALL**)。

1.	顔画像など収集したバイオメトリクス特性と、提示されたSUPERIORやSTRONG Evidenceに含まれており、関連付けられているリファレンスのバイオメトリクスとの比較、または
2.	少なくとも AAL2 認証または AAL2 および FAL2 フェデレーションプロトコルを介したデジタルアカウントとの関連性の実証

{% comment %}
The CSP **SHALL** verify the binding of the applicant to the claimed identity by _one_ of the following: 

1.	Comparison of a collected biometric characteristic, such as a facial image, to the associated reference biometric characteristic contained on a piece of presented SUPERIOR or STRONG evidence
2.	Demonstrated association with a digital account through, at a minimum, an AAL2 authentication or an AAL2 and FAL2 federation protocol
{% endcomment %}

### Proofing の通知要件
{% comment %}
### Notification of Proofing Requirement
{% endcomment %}

IAL3 での Identity Proofing が正常に完了すると、CSP は [Sec. 5.1.7](sec5_ial.ja.md#ProofingNotifs) で指定されているように、Applicantの有効なアドレスにProofing通知を送信するものとする(**SHALL**)。

{% comment %}
Upon the successful completion of identity proofing at IAL3, the CSP **SHALL** send a notification of proofing to a validated address for the applicant, as specified in [Sec. 5.1.7](sec5_ial.md#ProofingNotifs). 
{% endcomment %}

### バイオメトリックの収集
{% comment %}
### Biometric Collection
{% endcomment %}

CSPは、非否認と再Proofingを目的として、Proofing時にバイオメトリックサンプル（例：顔画像、指紋）を収集、記録するものとする(**SHALL**)

{% comment %}
The CSP **SHALL** collect and record a biometric sample at the time of proofing (e.g., facial image, fingerprints) for the purposes of non-repudiation and re-proofing.
{% endcomment %}

### 対面での Proofing 要件 {#vip}
{% comment %}
### In-person Proofing Requirements {#vip}
{% endcomment %}

IAL3 における対面でのProofingは、以下の 2 つの方法のうち _1つ_ の方法で実施されるものとする(**SHALL**)。

- Applicantと CSP オペレーターとの対面での対話、または
- [Sec. 5.5.8](sec5_ial.ja.md#IAL3supervised)  _IAL3 Supervised Remote Identity Proofing_ の要件に基づき、オペレータ監視下でのApplicantとのリモートでの対話

{% comment %}
In-person proofing at IAL3 **SHALL** be conducted in _one_ of two ways:

- An in-person interaction between the applicant and a CSP operator, or
- A remote interaction with the applicant, supervised by an operator, based on the requirements in [Sec. 5.5.8](sec5_ial.md#IAL3supervised), _IAL3 Supervised Remote Identity Proofing_.
{% endcomment %}

CSP がどちらの方法を採用するかにかかわらず、IAL3 での Identity Proofing には以下の要件が適用される。

1. CSP は、バイオメトリクス・ソース（例：指、顔）にnon-naturalな物質が存在するかどうかをオペレーターに確認させるものとする(**SHALL**)。
2. CSP は、バイオメトリックはApplicantから収集されたものであり、別の対象から取得したものではないことを保証する方法で、バイオメトリクスを収集するものとする(**SHALL**）。


{% comment %}
Regardless of which of the two methods the CSP employs, the following requirements apply to identity proofing at IAL3:

1. The CSP **SHALL** have the operator view the biometric source (e.g., fingers, face) for the presence of any non-natural materials.
2. The CSP **SHALL** collect biometrics in such a way that ensures that the biometric is collected from the applicant, and not another subject.
{% endcomment %}

### IAL3 Supervised Remote Identity Proofing　要件 {#IAL3supervised}
{% comment %}
### Requirements for IAL3 Supervised Remote Identity Proofing {#IAL3supervised}
{% endcomment %}

IAL3 監視下でのリモートIdentity Proofing は、Applicantとの直接の対話に匹敵するレベルの信頼性とセキュリティを達成することを意図している。

以下の要件は、すべての IAL3 監視下でのリモートIdentity Proofing Session に適用されます。

1. CSP は、Identity Proofing Session 全体を監視し、Applicantが Identity Proofing Session 全体にわたって継続的に存在していることを確認するものとする(**SHALL**)。たとえば、Applicantの高解像度ビデオ伝送を継続的に実施する方法が挙げられる。
2. CSP は、Identity Proofing Session の全期間中、Applicantと一緒に生身のオペレータをリモートから参加させるものとする(**SHALL**)。
3. CSP は、Identity Proofing中にApplicantが取ったすべての行動が、リモートのオペレータにはっきりと見えるようにすることを要求するものとする(**SHALL**)。
4. CSP は、EvidenceのすべてのデジタルVerification（例：チップまたは無線技術を介したもの）が、統合されたスキャナおよびセンサ（例：組み込み指紋リーダ）によって実行されることを要求するものとする(**SHALL**)。
5. CSP は、オペレーターが、潜在的な不正行為を検出し、監視下でのリモートProofing Session を適切に実行するためのトレーニング・プログラムの受講を必須とする(**SHALL**)。
6. CSP は、配置される環境に適した物理的な改ざん検出および耐タンパ機能を採用するものとする(**SHALL**)。例えば、制限エリアまたは信頼できる個人によって監視されている場所にあるキオスクは、ショッピングモールのコンコースなどの半公共エリアにあるものよりも改ざん検出の必要性が低い。
7. CSP は、すべての通信が、相互に認証された保護チャネルで行われることを保証するものとする(**SHALL**)。

{% comment %}
IAL3 Supervised Remote Identity Proofing is intended to achieve comparable levels of confidence and security to an in-person interaction with the applicant.

The following requirements apply to all IAL3 Supervised Remote Identity Proofing sessions:

1. The CSP **SHALL** monitor the entire identity proofing session, and **SHALL** ensure the applicant is continuously present during the entire identity proofing session — for example, by a continuous high-resolution video transmission of the applicant.
2. The CSP **SHALL** have a live operator participate remotely with the applicant for the entirety of the identity proofing session.
3. The CSP **SHALL** require all actions taken by the applicant during the identity proofing session to be clearly visible to the remote operator.
4. The CSP **SHALL** require that all digital verification of evidence (e.g., via chip or wireless technologies) be performed by integrated scanners and sensors (e.g., embedded fingerprint reader).
5. The CSP **SHALL** require operators to have undergone a training program to detect potential fraud and to properly perform a supervised remote proofing session.
6. The CSP **SHALL** employ physical tamper detection and resistance features appropriate for the environment in which it is located. For example, a kiosk located in a restricted area or one where it is monitored by a trusted individual requires less tamper detection than one that is located in a semi-public area such as a shopping mall concourse.
7. The CSP **SHALL** ensure that all communications occur over a mutually authenticated protected channel.
{% endcomment %}

## Summary of Requirements

[表 1](sec5_ial.md#table-1) は、各Identity Assurance Levelの要件のサマリーである:

[表 1 IAL 要件サマリ](sec5_ial.ja.md#table-1){:name="table-1"}
{:latex-ignore="true"}


要件 | IAL1 | IAL2 | IAL3
------------|-------|-------|-------
Presense|リモート または 対面|リモート または 対面|対面 または 監視下でのリモート Identity Proofing
Resolution|Resolutionするのに必要な最低限のAttribute|IAL1と同様|IAL1と同様
Evidence|1 つの SUPERIOR、または 1 つの STRONG と 1 つの FAIR|1 つの SUPERIOR、または 1 つの STRONG と 1 つの FAIR|2 つの SUPERIOR、または 1 つの SUPERIOR と 1 つの STRONG、または 2 つの STRONG と 1 つの FAIR 
Validation|Evidenceは真正性、正確性, 最新性の観点でValidateされる。すべての Core Attributes はAuthoritativeまたは信頼できるsourceによってValidateされる。|IAL1と同様|IAL1と同様
Verification|Enrollmentコードの提示、またはAAL1かFAL1でのまたはデジタルアカウントへのアクセスの実証|バイオメトリクス比較、またはAAL2かFAL2でのデジタルアカウントへのアクセスの実証|バイオメトリクス比較、またはAAL2かFAL2でのデジタルアカウントへのアクセスの実証
Biometric Collection|オプション|オプション|必須
{:latex-table="1" latex-caption="IAL Requirements Summary" latex-columns="p@0.15\textwidth,p@0.22\textwidth,p@0.22\textwidth,p@0.22\textwidth"}

{% comment %}
[Table 1](sec5_ial.md#table-1) summarizes the requirements for each of the identity assurance levels:

[Table 1 IAL Requirements Summary](sec5_ial.md#table-1){:name="table-1"}
{:latex-ignore="true"}

Requirement | IAL1 | IAL2 | IAL3
------------|-------|-------|-------
Presence|Remote or In-person|Remote or In-person|In-person or Supervised Remote Identity Proofing
Resolution|Minimum attributes to accomplish resolution|Same as IAL1| Same as IAL1
Evidence|1 piece of SUPERIOR or 1 piece of STRONG plus 1 piece of FAIR|1 piece of SUPERIOR or 1 piece of STRONG plus 1 piece of FAIR|2 pieces of SUPERIOR or 1 piece of SUPERIOR plus 1 piece of STRONG or 2 pieces of STRONG plus 1 piece of FAIR
Validation|Evidence is validated for genuineness, accuracy, and currency. All core attributes are validated by authoritative or credible sources|Same as IAL1|Same as IAL1
Verification|Return of an enrollment code or Demonstrated access to a digital account at AAL1 or FAL1|Biometric comparison or Demonstrated access to a digital account at AAL2 or FAL2|Biometric comparison or Demonstrated access to a digital account at AAL2 or FAL2
Biometric Collection|Optional|Optional|Mandatory
{:latex-table="1" latex-caption="IAL Requirements Summary" latex-columns="p@0.15\textwidth,p@0.22\textwidth,p@0.22\textwidth,p@0.22\textwidth"}
{% endcomment %}
