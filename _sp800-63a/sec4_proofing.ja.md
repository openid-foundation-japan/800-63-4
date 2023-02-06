---
layout: default.ja
title: Identity Resolution, Validation, and Verification
navOrder: 4
navTitle: Proofing
permalink: /sp800-63a/proofing/
anchor: ipv-section
section: 4
---

# Identity Resolution, Validation, and Verification {#ipv-section}

_This section is normative._

このセクションでは、Identity Proofingおよびエンロールメントプロセスの概要、ならびにapplicantがclaimするアイデンティティのresolution、validation、verificationをサポートするための要件について説明する。また、Identity Proofingプロセスの追加的な側面に関するガイドラインも提供する。 これらの要件は、claimされたアイデンティティが実世界に存在し、applicantがそのアイデンティティに関連付けられた個人であることを確かなものにすることを意図している。あわせて、Identity Proofingプロセスの要素というのは、エンロールされた多数のsubscribersに影響を与える CSP のアイデンティティサービスに対する攻撃が、保護されるデータの価値よりも大きな時間とコストを必要とすることを確かなものにするよう設計されている。

さらに、このガイドラインは、resolution、validation、およびverificationを完了できる複数の方法、ならびにIdentity Proofingプロセスをサポートする可能性のある複数のタイプのIdentity Evidenceを規定している。実用的な範囲で、CSP および組織は、手段、能力、および技術へのアクセスの面で異なる人々に対してアクセスを促進するために、Identity Proofingサービスおよびプロセスを実装するときにオプションを有効にするべきである（**SHOULD**）。少なくとも、これには、複数種類のIdentity Evidenceおよび組み合わせを許容し、複数のデータvalidationソースのサポート、アイデンティティvalidationの複数の方法の有効化（例：trusted refereesの活用）、エンゲージメント用の複数のチャネル（例：対面、リモート）、およびapplicantsのための支援メカニズムの提供（例：applicant references） を含めるべきである（**SHOULD**）。

{% comment %}
This section provides and overview of the identity proofing and enrollment process as well as requirements to support the resolution, validation, and verification of the identity claimed by an applicant. It also provides guidelines on additional aspects of the identity proofing process.  These requirements are intended to ensure that the claimed identity exists in the real world and that the applicant is the individual associated with that identity. Collectively, the elements of the identity proofing process are designed to ensure that attacks against a CSP's identity service that affect a large number of enrolled subscribers require greater time and cost than the value of the data being protected.

Additionally, these guidelines provide for multiple methods by which resolution, validation, and verification can be completed as well as multiple types of identity evidence that may support the identity proofing process. To the extent practical, CSPs and organizations **SHOULD** enable optionality when implementing their identity proofing services and processes to promote access for those with different means, capabilities, and technology access. At a minimum, this **SHOULD** include accepting multiple types and combinations of identity evidence, supporting multiple data validation sources, enabling multiple methods for verifying identity (e.g., use of trusted referees), multiple channels for engagement (e.g., in-person, remote), and offering assistance mechanisms for applicants (e.g., applicant references). 
{% endcomment %}

## Identity Proofing and Enrollment

本書では、Applicant が Identity Proofing と Enrollment プロセスを受ける一般的なパターンについて説明する。そのプロセスでは Applicant の Identity Evidence および Attribute が収集され、特定の集団またはコンテキストにおいて単一のアイデンティティに一意に Resolve され、Validate および Verify される。どのように最も適切な IAL を選択するかの詳細については、[[SP800-63]](../_sp800-63/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63"} を参照。CSP はこれらの Attribute を Authenticator にバインドすることができる（[[SP800-63B]](../_sp800-63b/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63B"}で記述されている）。

{% comment %}
This document describes the common pattern in which an applicant undergoes an identity proofing and enrollment process whereby their identity evidence and attributes are collected, uniquely resolved to a single identity within a given population or context, then validated and verified. See [[SP800-63]](../_sp800-63/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63"} for details on how to choose the most appropriate IAL. A CSP can then bind these attributes to an authenticator (described in [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}).
{% endcomment %}

Identity Proofingの目的は、Applicantが、自身でclaimした人と同じであることを特定のレベルの確実性で確かにしていくことである。Identity Proofingは、給付金への適合性または資格を決定するために行われるのではない。Identity Proofingプロセスには、Identity Proofingを達成するために必要最低限のattributesの提示およびvalidationが含まれる。 最低限で目的に足りるattributesのセットには様々異なるものがあるが、CSP はapplicantsのプライバシーとユーザビリティ、およびデジタルアイデンティティの将来の使用で必要になる可能性のあるattributesを考慮してこのセットを選択する。たとえば、そのようなattributesは、必要最低限である限りにおいて、以下を含むことができる。

1. フルネーム
2. 生年月日
3. 自宅住所

本書は、CSPがIdentity Proofingを超えた別の目的に利用される追加の情報の収集についての要件も規定している。

{% comment %}
The objective of identity proofing is to ensure, to a stated level of certainty, the applicant is who they claim to be. Identity proofing is not conducted to determine suitability or entitlement to benefits. The identity proofing process involves the presentation and validation of the minimum attributes necessary to accomplish identity proofing.  There can be many different sets of attributes that suffice as the minimum, so CSPs choose this set by considering applicants' privacy and the usability, as well as the likely attributes needed in future uses of the digital identity. For example, such attributes, to the extent they are the minimum necessary, could include:

1. Full name
2. Date of birth
3. Home address

This document also provides requirements for CSPs collecting additional information used for purposes other than identity proofing.
{% endcomment %}

~~~
\clearpage
~~~
{:latex-literal="true"}

### Process Flow

_This section is informative._

[図 1](sec4_proofing.md#fig-1) は、Identity Proofingとエンロールメントの基本的な流れを示している。

[図 1. Identity Proofing プロセス](sec4_proofing.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Identity Proofingとエンロールメントのステップ図]({{site.baseurl}}/{{page.collection}}/media/ProofingProcess.png 'Identity Proofingプロセス'){:style="width:1074px;height:496px;;min-width: 1074px;min-height: 496px;" latex-src="ProofingProcess.png" latex-fig="1" latex-place="h"}

{% comment %}
[Figure 1](sec4_proofing.md#fig-1) outlines the basic flow for identity proofing and enrollment.

[Figure 1. Identity Proofing Process](sec4_proofing.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Illustration of steps in identity proofing and enrollment]({{site.baseurl}}/{{page.collection}}/media/ProofingProcess.png 'Identity Proofing Process'){:style="width:1074px;height:496px;;min-width: 1074px;min-height: 496px;" latex-src="ProofingProcess.png" latex-fig="1" latex-place="h"}
{% endcomment %}

以下は、IAL2 のリモートIdentity Proofingプロセスにおいて CSP およびapplicantがどのようにやりとりするかについて例を示している。

1. **Resolution** 
    1. CSP はapplicantから、名前、住所、生年月日、電子メール、電話番号などのattributesを収集する。
    2. CSP、運転免許証やパスポートなど、1つまたは複数のIdentity Evidenceも収集する。
    {:.letter-list} 
2. **Validation**
    1. CSP は、ステップ 1a で取得したattributesを、authoritativeソースまたは信頼できるソースと照合することで、validateする。
    2. CSPは、提示されたエビデンスの真正性、正確性、および最新性を Validate する。
    {:.letter-list} 
3. **Verification**
    1. CSP は、applicantに自分自身の写真を撮影するよう依頼し、生存性のチェックを行う。
    2. CSPは、免許証とパスポートの写真と、前のステップで撮影したApplicant当人の写真とを比較し、一致すると判断する。
    3. Validateされた電話番号にエンロールメントコードを送信し、ApplicantがエンロールメントコードをCSPに提供し、CSPは両者が一致することを確認し、ApplicantがValidateされた電話番号を所有し管理していることをVerifyする。
    4. ApplicantのIdentity Proofingが完了し、Subscriberアカウントにエンロールすることができる。
    {:.letter-list}

{% comment %}
The following provides an example of how a CSP and an applicant might interact during a remote identity proofing process at IAL2:

1. **Resolution**
    1. The CSP collects attributes from the applicant, such as name, address, date of birth, email, and phone number.
    2. The CSP also collects one or more pieces of identity evidence, such as a driver's license or a passport.
    {:.letter-list}
2. **Validation**
    1. The CSP validates the attributes obtained in steps 1a by checking them against authoritative or credible sources.
    2. The CSP validates the authenticity, accuracy, and currency of the presented evidence.
    {:.letter-list}
3. **Verification**
    1. The CSP asks the applicant to take a photo of themself, with liveness checks.
    2. The CSP compares the pictures on the license and the passport to the photo of the live applicant's photo from the previous step and determines they match.
    3. The CSP sends an enrollment code to the validated phone number of the applicant, the applicant provides the enrollment code to the CSP, and the CSP confirms they match, verifying they the applicant is in possession and control of the validated phone number.
    4. The applicant has been successfully identity proofed and can be enrolled into a subscriber account.
    {:.letter-list}
{% endcomment %}


## Identity Resolution {#resolve}


Identity Resolutionのゴールは、最小限のAttributesセットを使用し、特定の集団またはコンテキスト内で個人を一意に区別することである。Identity ResolutionはIdentity Proofingプロセス全体において出発点であり、潜在的な不正を初期に検出するためのものだが、決してIdentity Proofingのトランザクションが成功裏に完了したことを意味するものではない。

{% comment %}
The goal of identity resolution is to use the smallest set of attributes to uniquely distinguish an individual within a given population or context. While identity resolution is the starting point in the overall identity proofing process, to include the initial detection of potential fraud, it in no way represents a complete and successful identity proofing transaction.
{% endcomment %}

## Identity Validation and Identity Evidence Collection {#evidence-collection}

Identity Validationのゴールは、Applicantから最も適切なIdentity EvidenceおよびAttribute情報を収集し、それが真正で、正確で、最新かつ期限切れでないことを判断することである。Identity Validationは 3 つのプロセス・ステップで構成される。1) 適切なIdentity Evidenceを収集する、2) Evidenceが真正なものであることを確認する、3) Identity Evidenceに含まれる主要なデータが妥当で、最新で、実存するSubjectに関連していることを確認する。

{% comment %}
The goal of identity validation is to collect the most appropriate identity evidence and attribute information from the applicant and determine it is authentic, accurate, current, and unexpired. Identity validation is made up of three process steps: 1) collecting the appropriate identity evidence; 2) confirming the evidence is authentic; and, 3) confirming key data contained on the identity evidence is valid, current, and related to a real-life subject.
{% endcomment %}

Identity Evidenceの収集はIdentity Proofingプロセスをサポートし、2つのステップで構成されている: 1) Identity Proofingの対象となるApplicantによる CSP へのIdentity Evidenceの提示、および 2) 提示されたEvidenceが許容可能であるかどうかについてのCSPの判断。Evidenceは、物理的な文書または文書の写し、スキャンした文書、写真、あるいはデジタルレコードとして提示することができる。許容可能な物理的（文書的）なIdentity Evidenceの性質は [セクション 4.3.1](sec4_proofing.ja.md#physical-evidence)に、許容可能なデジタルEvidenceの性質は [セクション 4.3.2](sec4_proofing.ja.md#digital-evidence) にて示す。

{% comment %}
Identity evidence collection supports the identity validation process and consists of two steps: 1) presentation of identity evidence by the identity proofing applicant to the CSP and 2) determination by the CSP that the presented evidence is acceptable. Evidence can be presented as a physical document or a copy, photograph, or scan of a document, or as a digital record. The characteristics for acceptable physical (documentary) identity evidence are presented in [Sec. 4.3.1](sec4_proofing.md#physical-evidence) and the characteristics for acceptable digital evidence are provided in [Sec. 4.3.2](sec4_proofing.md#digital-evidence).
{% endcomment %}

CSPは、Identity Proofingを目的として提示されたIdentity Evidenceを許容できるかどうか、本セクションのEvidenceの性質に基づいて決定するものとする (**SHALL**)。

{% comment %}
The CSP **SHALL** determine the acceptability of presented identity evidence for identity proofing based on the evidence characteristics in this section.
{% endcomment %}


本セクションで示す性質は、CSP がIdentity ProofingプロセスのためのIdentity Evidenceとして許容可能なものを決定する際の指針となることを意図しており、Evidence強度を示すものではない。CSP が特定の種類のEvidenceを許容できると判断すると、[セクション 4.3.3](sec4_proofing.ja.md#evidence-strength)で示されているように、その強度について判断していく必要がある。

{% comment %}
The characteristics presented in this section are intended to guide CSPs in determining what is acceptable as identity evidence for the identity proofing process and are not an indication of strength of evidence. Once a CSP determines a particular type of evidence is acceptable, a determination must be made as to its strength, as provided in [Sec. 4.3.3](sec4_proofing.ja.md#evidence-strength). 
{% endcomment %}


### 許容可能な Physical Evidence の性質 {#physical-evidence}

{% comment %}
### Characteristics of Acceptable Physical Evidence {#physical-evidence}
{% endcomment %}

許容可能な物理的Evidenceは、以下のすべての性質を含むものとする(**SHALL**)。

1.	提示された文書に、Applicantの印刷された氏名が含まれている。(ApplicantがClaimする氏名と異なるものが印刷されているケースを取り扱う際の指針は、[セクション 10.1](sec10_equity.ja.md#EquityResolve)「Equity and Resolution」参照)。
2.	提示された文書に、少なくとも1つの印刷されたリファレンス番号が含まれている。
3.	提示された文書に、文書の発行者の名称が印刷されている。
4.	文書の発行者が、文書の発行に先立って、ApplicantのIdentity Proofingを実施している。
5.	文書が、意図された人物に届けられたものであるという、合理的な保証がある。


{% comment %}
Acceptable physical evidence **SHALL** contain all of the following characteristics:

1.	The presented document contains the printed name of the applicant. (See [Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution - for guidance on dealing with a printed name that varies from the applicant's claimed identity.)
2.	The presented document contains at least one printed reference number.
3.	The presented document contains the printed name of the issuer of the document.
4.	The issuer of the document performed identity proofing of the applicant prior to issuing the document.
5.	There is reasonable assurance that the document was delivered to the intended person.
{% endcomment %}

### 許容可能なデジタルEvidenceの性質 {#digital-evidence}
{% comment %}
### Characteristics of Acceptable Digital Evidence {#digital-evidence}
{% endcomment %}

許容可能なデジタルEvidenceは、以下のすべての性質を含むものとする(**SHALL**)。

1.	提示されたデジタルEvidenceに、デジタル情報やアカウントのSubjectとしてのApplicantの氏名が含まれている。(ApplicantがClaimするIdentityと異なる名前がデジタルEvidence上に記載されているケースを取り扱う際の指針は、[セクション 10.1](sec10_equity.ja.md#EquityResolve)「Equity and Resolution」参照)。
2.	提示されたデジタルEvidenceに、少なくとも1つの参照番号（例：アカウント番号）が含まれている、あるいはApplicantとデジタル情報とをバインドするのに十分なAttributesが含まれている。
3.	提示されたデジタルEvidenceに、デジタル情報の発行者の名称が含まれている。
4.	デジタルEvidenceの発行者が、デジタルEvidenceの発行に先立って、ApplicantのIdentity Proofingを実施している。
5.	デジタルEvidenceが、意図された人物に届けられた、あるいはアクセス可能とされたものであるという、合理的な保証がある。
6.  許容可能であるならば、評価中のIALに見合ったAALあるいはFALでのAuthenticationを通じて、提示されたデジタルEvidenceがVerify可能である。

{% comment %}
Acceptable digital evidence **SHALL** contain all of the following characteristics:

1.  The presented digital evidence contains the name of the applicant as the subject of the digital information or account. (See [Sec. 10.1](sec10_equity.md#EquityResolve) - Equity and Resolution - for guidance on dealing with a name on digital evidence that varies from the applicant's claimed identity.)
2.  The presented digital evidence contains at least one reference (e.g., account number) or sufficient attributes to bind the digital information to the applicant.
3.  The presented digital evidence contains the name of the issuer of the digital information.
4.  The issuer of the digital evidence performed identity proofing of the applicant prior to issuing the digital evidence.
5.  There is reasonable assurance that the digital evidence was delivered or made accessible to intended person.
6.  If applicable, the presented digital evidence can be verified through authentication at an AAL or FAL commensurate with the assessed IAL. 
{% endcomment %}

###  Evidence の強度要件 {#evidence-strength}

{% comment %}
###  Evidence Strength Requirements {#evidence-strength}
{% endcomment %}

このセクションでは、各強度におけるIdentity Evidenceの要件を定義する。Identity Evidence強度は、3つの側面によって決まる。1) 発行の厳密さ、2) Attributeの正確性と完全性を含む、Validationにおける信頼性を提供する能力、 3) Evidenceを提示するApplicantのVerificationにおける信頼性を提供する能力。すべてのレベルの強度のエビデンスは、最新かつ期限が切れていないものでなければならない。

{% comment %}
This section defines the requirements for identity evidence at each strength. Strength of identity evidence is determined by three aspects: 1) the issuing rigor; 2) the ability to provide confidence in validation, including accuracy and integrity of attributes; and 3) the ability to provide confidence in the verification of the applicant presenting the evidence. Evidence at all levels of strength must be current and unexpired. 
{% endcomment %}

#### Fair Evidence 要件
{% comment %}
#### Fair Evidence Requirements
{% endcomment %}

Identity EvidenceがFAIRであるには、以下の _すべて_ の要件を満たすものとする(**SHALL**):

1.  Evidenceの発行元は、Identity Proofingプロセスを通じて、ClaimされたIdentityを確認した。
2.  Evidenceの発行プロセスが、Evidenceを関係する人物に送り届ける結果となる、と合理的に仮定することができる。
3.  Evidenceは、少なくとも 1 つの参照番号、顔写真、または関連する人物を一意に識別するのに十分なAttributeを含んでいる。
4.  Evidenceの有効期限が切れていないか過去6ヶ月以内に期限が切れた、あるいは有効期限の記載がない場合は過去6ヶ月以内に発行されていること。

{% comment %}
In order to be considered FAIR, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity through an identity proofing process.
2.  It can be reasonably assumed that the evidence issuing process would result in the delivery of the evidence to the person to whom it relates.
3.  The evidence contains at least one reference number, a facial portrait, or sufficient attributes to uniquely identify the person to whom it relates.
4.  The evidence has not expired or it expired within the previous six (6) months, or it was issued within the previous six (6) months if it does not contain an expiration date. 
{% endcomment %}

#### Strong Evidence 要件
{% comment %}
#### Strong Evidence Requirements
{% endcomment %}

Identity EvidenceがSTRONGであるには、以下の _すべて_ の要件を満たすものとする(**SHALL**):

1.  Evidenceの発行元は、その人物の実在のIdentityを把握しているという合理的な確信を形成することができるよう設計された文書化された手続きによって、ClaimeされたIdentityを確認している。このような手続きは、規制や公的な説明責任を有する機関による継続的な監視の対象となる。たとえば、2001年に米国愛国者法に対応して制定されたCustomer Identification Programガイドラインや、 2003 年公正取引法（FACT法）第 114 条に基づく [[RedFlagsRule]](sec11_references.ja.md#ref-rfr) がそれにあたる。
2.  Evidenceの発行プロセスで、Evidenceを関係する人物に送り届ける結果となる可能性が高い。
3.  Evidenceは、参照番号または関連する人物を一意に識別するその他のAttributeを含む。
4.  Evidenceが、関係する人物の顔写真または、他のバイオメトリックな特徴を含んでいる。
5.  Evidenceが、コピー又は再作成を困難にする物理的なセキュリティ機能を含んでいる。
6.  Evidenceに有効期限があり、有効期限内である。

{% comment %}
In order to be considered STRONG, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity through written procedures designed to enable it to form a reasonable belief that it knows the real-life identity of the person. Such procedures are subject to recurring oversight by regulatory or publicly-accountable institutions. For example, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001 or the [[RedFlagsRule]](sec11_references.md#ref-rfr), under Sec. 114 of the Fair and Accurate Credit Transaction Act of 2003 (FACT Act).
2.  There is a high likelihood that the evidence issuing process would result in the delivery of the evidence to the person to whom it relates.
3.  The evidence contains a reference number or other attributes that uniquely identify the person to whom it relates.
4.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
5.  The evidence includes physical security features that make it difficult to copy or reproduce.
6.  The evidence includes an expiration date and is unexpired. 
{% endcomment %}

#### Superior Evidence 要件
{% comment %}
#### Superior Evidence Requirements
{% endcomment %}

Identity EvidenceがSUPERIORであるには、以下の _すべて_ の要件を満たすものとする(**SHALL**):

合理的な確信を形成することができるよう設計された文書化された手続きによって

1.  Evidenceの発行元は、その人物の実在のIdentityを把握しているという高い信頼性を持つことができるように設計された文書化された手続きに従って、ClaimされたIdentityを確認している。このような手続きは、規制や公的な説明責任を有する機関による継続的な監視の対象となる。
2.  発行元は、Applicantを視覚的に識別し、その人物が存在することを確認するために更にチェックを行う。
3.  Evidenceの発行プロセスは、Evidenceが関係する人物の手元に送り届けられたことを確実にする。
4.  Evidenceは、関連する人物を一意に識別する 1 つの参照番号を含む。
5.  Evidenceが、関係する人物の顔写真または他のバイオメトリックな特徴を含んでいる。
6.  Evidenceが、暗号的に署名されたデジタル情報を含む。
7.  Evidenceが、コピーまたは複製を困難にする物理的なセキュリティ機能を含む。
8.  Evidenceに有効期限があり、有効期限内である。

{% comment %}
In order to be considered SUPERIOR, identity evidence **SHALL** meet _all_ the following requirements:

1.  The issuing source of the evidence confirmed the claimed identity by following written procedures designed to enable it to have high confidence that the source knows the real-life identity of the subject. Such procedures are subject to recurring oversight by regulatory or publicly accountable institutions.
2.  The issuing source visually identified the applicant and performed further checks to confirm the existence of that person.
3.  The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.
4.  The evidence contains at least one reference number that uniquely identifies the person to whom it relates.
5.  The evidence contains a facial portrait or other biometric characteristic of the person to whom it relates.
6.  The evidence includes digital information that is cryptographically signed.
7.  The evidence includes physical security features that make it difficult to copy or reproduce.
8.  The evidence includes an expiration date and is unexpired.
{% endcomment %}

### Identity Evidence と Attribute Validation 
{% comment %}
### Identity Evidence and Attribute Validation 
{% endcomment %}

CSPは、Evidenceの収集要件を満たすために収集されたすべてのIdentity Evidenceと、CSP Identity Serviceによって要求されるすべての Core Attributes情報をValidateするものとする(**SHALL**)。

{% comment %}
The CSP **SHALL** validate all identity evidence collected to meet evidence collection requirements and all core attribute information required by the CSP identity service. 
{% endcomment %}


#### Evidence Validation {#validation}

CSPは、提示されたエビデンスの真正性、正確性、および最新性を次の手段によってValidateするものとする(**SHALL**):

- Evidenceが正しい形式であり、Identity Evidenceのタイプに対する完全な情報を含んでいることを確認する。
- Evidenceが偽造されていないこと、および改ざんされていないことを確認する。
- セキュリティ機能を確認する。

CSP は、Evidenceの有効期限を過ぎていない、あるいは有効期限の記載がない場合は過去6ヶ月以内に発行されていることを確認することで、Evidenceが最新であることを検証するものとする(**SHALL**)。

暗号的に保護されているIdentity EvidenceまたはAttribute情報の真正性と正確性は、EvidenceやAttributeデータオブジェクトに対するデジタル署名のVerificationによりValidateすることができる。CSPはデジタル署名されたEvidenceやAttributeデータオブジェクトをVerifyするために、Evidenceの発行 Authority の公開鍵を用いるものとする(**SHALL**)。

{% comment %}
The CSP **SHALL** validate the authenticity, accuracy, and currency of presented evidence by:

- Confirming the evidence is in the correct format and includes complete information for the identity evidence type.
- Confirming the evidence is not counterfeit and that it as not been tampered with.
- Confirming any security features.

The CSP **SHALL** validate that the evidence is current through confirmation that its expiration date has not passed or that evidence without an expiration date was issued within the previous six (6) months.

The authenticity and accuracy of identity evidence or attribute information that is cryptographically protected can be validated through verification of the digital signature on the evidence or the attribute data objects. The CSP **SHALL** use the public key of the issuing authority of the evidence to verify digitally signed evidence or attribute data objects.
{% endcomment %}


#### Attribute Validation

すべてのCore Attributesは、Identity Evidenceから取得したか、Applicantによる自己申告かによらず、Validateされなければならない。本サブセクションでは、Evidenceと収集したAttributesをvalidateするための、許容可能な方法についてガイダンスを提供する。

{% comment %}
All core attributes, whether obtained from identity evidence or applicant self-assertion, must be validated. This subsection provides guidance on acceptable methods for validating evidence and collected attributes.   
{% endcomment %}

#### Evidence and Attribute Validation Methods

提示されたEvidenceをValidateする許容可能な方法は、次を含む:

- 対面でのIdentity Proofingでは、訓練を受けた担当者による目視および触覚検査
- リモートでのIdentity Proofingでは、訓練を受けた担当者による目視検査。
- 適切な技術を使用した、自動化された文書のValidationプロセス。
- Evidenceに含まれるAttributeの、Authoritativeまたは信頼できるソースによるValidation。
- Evidenceの発行Authorityの公開鍵を使用した、デジタルエビデンスまたはAttributeデータオブジェクトを保護するデジタル署名のVerification。

{% comment %}
Acceptable methods for validating presented evidence include:

- Visual and tactile inspection by trained personnel for in-person identity proofing,
- Visual inspection by trained personnel for remote identity proofing,
- Automated document validation processes using appropriate technologies,
- Validation of attributes contained on the evidence with an authoritative or credible source.
- Verification of the digital signature protecting digital evidence or attribute data objects using the public key of the issuing authority of the evidence. 
{% endcomment %}

#### Validation Sources

[セクション 4.3.4.1](sec4_proofing.ja.md#validation) に従ってValidateされたIdentity Evidenceに含まれる Core Attributesは、Validate済みと見なすことができ、この場合、さらなるValidationは必要ない。

Authoritative Sourceとは、次の性質のうち1つ以上によって、Identity Attribute情報の正確性を提供あるいはValidateできるエンティティである。Authoritative sourceは:

- Identity Attributeのオリジナル・ソースである、または 
- Identity Attribute情報を含む Identity Evidenceの発行者であり、発行者は、例えば[[PatriotAct]](sec11_references.ja.md#ref-PatriotAct)の下で確立されたCustomer Identification Program ガイドラインのような規制や公的な説明責任を有する機関による継続的な監視の対象となるような、文書化した Identity Proofingプロセスを通じて、Claimした Identityを確認した場合、または 
- 個人との直接の対話（対面またはリモート）を通じてClaimされたIdentityを確認できるIdentity Proofingプロセスを通じて、Attribute情報を収集してValidateしたもの、または
- Identity Evidenceのピースの発行元まで追跡できるようなエビデンスとAttribute情報へのアクセスを有する。

{% comment %}
Core attributes that are contained on identity evidence that has been validated according to [Sec. 4.3.4.1](sec4_proofing.md#validation) can be considered validated, in which case no further validation is required.

An authoritative source is an entity that can provide or validate the accuracy of identity attribute information through one or more of the following characteristics. An authoritative source:

- Is the original source of the identity attribute(s); or
- Is the issuer of identity evidence containing identity attribute information and the issuer confirmed the claimed identity through documented identity proofing processes that are subject to recurring oversight by regulatory or publicly accountable institutions, such as the Customer Identification Program guidelines established under the [[PatriotAct]](sec11_references.md#ref-PatriotAct); or
- Collected and validated attribute information through an identity proofing process that can confirm the claimed identity through direct interaction with individuals (either in-person or remotely); or
- Has access to evidence and attribute information that can be traced to the issuing source of a piece of identity evidence.
{% endcomment %}

信頼できるソースとは、次の性質のうち 1 つ以上によって Identity EvidenceおよびAttribute情報の正確性を提供またはValidateできるエンティティである。信頼できるソースは:

- Identity Proofingプロセスを通じてValidateされたAttribute情報へのアクセスを有する、または
- Authoritative Sourceまで追跡できるAttribute情報へのアクセスを有する、または
- 正確性、一貫性、および最新性を目的としてデータ相関をチェックされる、複数のソースから取得されたIdentity Attribute情報を保持している。

{% comment %}
A credible source is an entity that can provide or validate the accuracy of identity evidence and attribute information through one or more of the following characteristics. A credible source:

- Has access to attribute information that was validated through an identity proofing process; or
- Has access to attribute information that can be traced to an authoritative source; or
- Maintains identity attribute information obtained from multiple sources that is checked for data correlation for accuracy, consistency, and currency.
{% endcomment %}


## Identity Verification

Identity Verificationのゴールは、ClaimされたIdentityと、Identity Proofingプロセスにエンゲージされた実存するApplicantとの間の関連性を確立し、確認することである。

{% comment %}
The goal of identity verification is to confirm and establish a linkage between the claimed identity and the real-life existence of the applicant engaged in the identity proofing process.   
{% endcomment %}

### Identity Verification Methods

CSP は、[セクション 5](sec5_ial.ja.md#ial-section) で提示される IAL Identity Verification要件に応じて、次の方法のうち 1 つ以上によって、ClaimされたIdentityと、Identity ProofingプロセスにエンゲージされたApplicantとの関連性をVerifyしなければならない。

- [セクション 5.1.6](sec5_ial.ja.md#EnrollCodes)で指定されている **Enrollment code verification**。
- **対面での物理的比較**。CSP 運営者とApplicantは、Identity Proofingイベントのために直接対話する。CSP 運営者は、Identity Evidenceに提示された顔写真と、Identity ProofingイベントにエンゲージされたApplicantの顔との物理的な比較を実行する。
- **リモート（有人および無人）物理的顔画像比較**。CSP 運営者は、Identity Evidence上に存在する顔写真と、Identity ProofingイベントにエンゲージしたApplicantの顔画像との物理的な比較を実行する。CSP 運営者は、Identity Proofingイベントの一部または全部においてApplicantと直接対話（有人）するか、キャプチャしたビデオまたは写真に加えEvidenceのアップロードされたコピーを使用して後で比較（無人）を行うことができる。比較をあとで実施する場合、キャプチャされたビデオまたは写真がIdentity ProofingイベントにエンゲージしているApplicant当人を撮影したものであることを確認するための手順が取られる。 
- **自動化されたバイオメトリクス比較**。バイオメトリクス・システム比較は、対面またはリモートのIdentity Proofingイベントにおいて実施できる。Identity Evidenceに含まれる顔写真、または他のバイオメトリクス特性は、自動化されたバイオメトリクス比較システムによって、Identity Proofingイベント中にApplicantが提出したApplicant当人の顔画像写真、または他のバイオメトリクスの当人サンプルと比較される。自動化されたバイオメトリクス比較システムは、比較のために数学的アルゴリズムを使用する。
- **デジタルアカウントのコントロール**。個人は、認証またはフェデレーション・プロトコルの使用を通じて、デジタルアカウント （例：オンライン銀行口座）または署名済みデジタルアサーション（例：Verifiable Credentials）のコントロールを実証することができる。これは、対面でクレデンシャルをデバイスまたはリーダーに提示することでも実施できるかもしれないが、リモートのIdentity Proofing Session 中に実施されることのほうが多いだろう。


{% comment %}
The CSP **SHALL** verify the linkage of the claimed identity  to the applicant engaged in the identity proofing process through one or more of the following methods, depending on the IAL identity verification requirements presented in [Sec. 5](sec5_ial.md#ial-section).

- **Enrollment code verification** as specified in [Sec. 5.1.6](sec5_ial.md#EnrollCodes).
- **In-person physical comparison**. The CSP operator and applicant interact in person for the identity proofing event. The CSP operator performs a physical comparison of the facial portrait presented on identity evidence to the face of the applicant engaged in the identity proofing event.
- **Remote (attended and unattended) physical facial image comparison**. The CSP operator performs a physical comparison of the facial portrait presented on identity evidence to the facial image of the applicant engaged in the identity proofing event. The CSP operator may interact directly with the applicant during some or all of the identity proofing event (attended) or may conduct the comparison at a later time (unattended) using a captured video or photograph and the uploaded copy of the evidence. If the comparison is performed at a later time, steps are taken to ensure the captured video or photograph was taken from the live applicant present during the identity proofing event.
- **Automated biometric comparison**. Biometric system comparison may be performed for in-person or remote identity proofing events. The facial portrait, or other biometric characteristic, contained on identity evidence is compared by an automated biometric comparison system to the facial image photograph of the live applicant or other biometric live sample submitted by the applicant during the identity proofing event. The automated biometric comparison system uses a mathematical algorithm for the comparison.
- **Control of a digital account**. An individual is able to demonstrate control of a digital account (e.g., online bank account) or signed digital assertion (e.g., verifiable credentials) through the use of authentication or federation protocols. This may be done in person through presentation of the credential to a device or reader, but is more likely to be done during remote identity proofing sessions. 
{% endcomment %}



