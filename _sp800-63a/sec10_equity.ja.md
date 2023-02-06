---
layout: default.ja
title: Equity
navOrder: 10
navTitle: Equity
permalink: /sp800-63a/equity/
anchor: equity
section: 10

---

# Equity Considerations {#equity}

_This section is informative._
これは、Identity Evidence プロセスにおいて不公平の対象となり得る領域と、適用可能な緩和策を非網羅的にリストアップしている。CSP は、自社の ID サービス内に不公平なアクセス、処置、または結果のリスクが存在する場所を検 討するための出発点として、このセクションを使用することができる。以下の指針は、ID サービスに関連する公平性リスクの決定的で包括的なリストと見なすことを意図したものでは ない。

このセクションは、Identity Proofing プロセスにおいて不公平な Access、処遇、または結果に関連するリスクの影響を評価する目的（[Sec. 5.1.3](sec5_ial.ja.md#EquityReqs)で要求されている）での指針を提供することを意図している。これは、Identity Proofing プロセスにおいて、不公平の対象となり得る領域と、それに対して適用可能な緩和策を、非網羅的にリストアップしている。CSP はこのセクションを、自身の Identity サービスに存在する不公平なアクセス、処置、または結果のリスクの所在を考慮するためのスタート地点として活用できる。以下の指針が、Identity サービスに関連する決定的で包括的なリストである、とみなすことを意図したものではない。

{% comment %}
This section is intended to provide guidance to CSPs for assessing the risks associated with inequitable access, treatment, or outcomes for individuals using its identity services, as required in [Sec. 5.1.3](sec5_ial.md#EquityReqs). It provides a non-exhaustive list of potential areas in the identity proofing process that may be subject to inequities, as well as possible mitigations that can be applied. CSPs can use this section as a starting point for considering where the risks for inequitable access, treatment, or outcomes exist within its identity service. It is not intended that the below guidance be considered a definitive, all-inclusive list of associated equity risks to identity services.
{% endcomment %}

Equity リスクの評価において、CSP は、Identity Proofing および Enrollment サービスが対象とする利用者母集団の検討から始める。さらに、CSP は、そのサービスを使用する際に不公平なアクセス、処遇、または結果の原因となり得る、共通の特性を持った集団内の利用者のグループをさらに特定する。CSP は、影響を受けるユーザ、グループへの影響を評価することによって、あらゆる緩和策の有効性を評価することが推奨される。Identity サービスを使用するすべての人にとっての全体的な Usability と Equity の改善に役立つ Equity リスク緩和を適用する際に、[Sec. 9](sec9_usability.ja.md#usability) で提供されている Usability の考慮事項も考慮べきである。

{% comment %}
In assessing equity risks, a CSP starts by considering the overall user population served by its identity proofing and enrollment service. Additionally, the CSP further identifies groups of users within the population whose shared characteristic(s) can cause them to be subject to inequitable access, treatment, or outcomes when using that service. CSPs are encouraged to assess the effectiveness of any mitigations by evaluating their impacts on the affected user group(s). The usability considerations provided in [Sec. 9](sec9_usability.md#usability) should also be considered when applying equity risk mitigations to help improve the overall usability and equity for all persons using an identity service.
{% endcomment %}

## Equity and Identity Resolution {#EquityResolve}

Identity Resolution には、Identity サービスが対象とする集団内で、Claim された Identity を単一の一意の個人として識別できるようにするための最小限の Attribute のセットを収集することが含まれる。Attribute は、提示された Identity Proofing、Applicant の自己申告、および／またはバックエンドの Attribute プロバイダから取得される。

このセクションでは、Identity Resolution プロセスに関連する不公平なアクセス、処遇、または結果について、考えられる一連の問題および緩和策を提供する: 

{% comment %}
Identity resolution involves collecting the minimum set of attributes to be able to distinguish the claimed identity as a single, unique individual within the population served by the identity service. Attributes are obtained from presented identity evidence, applicant self-assertion, and/or back-end attribute providers.

This section provides a set of possible problems and mitigations with the inequitable access, treatment, or outcomes associated with the identity resolution process:
{% endcomment %}

**問題の説明： Identity サービスの設計で、Applicant に対して西洋の名前形式（例：ファーストネーム、ラストネーム、オプションのミドルネーム）を使用して自分の名前を入力することを求める。**

緩和策としては、以下が考えられる:

1. 考えられる名前の構成を分析し、名前フィールドを使用してすべての名前を正確に収容する方法を決定する。
2. ユーザーが名前フィールドを使用してすべての名前を入力する方法について、わかりやすく、使いやすいガイダンスを提供する。

{% comment %}
**Description： The identity service design requires an applicant to enter their name using a Western name format (e.g., first name, last name, optional middle name).**

Possible mitigations include:

1. Analyzing possible name configurations and determine how all names can be accurately accommodated using the name fields
2. Providing easy-to-find and use guidance to users on how to enter all names using the name fields
{% endcomment %}

**問題の説明： 名前、性別、またはその他の Attribute が変更されたため、提示された Identity Evidence に一貫性がない、または Attribute Verifier の記録と一致しない Applicant を Identity サービスで受け入れることができない。**

緩和策としては、以下が考えられる:

1. 特定の Applicant の状況に基づいてリスクベースの判断を行うことができる Trusted Referee（[Sec. 5.1.9.1](sec5_ial.ja.md#TrustedRefs)) を提供する。
2. Applicant の Attribute の差異を裏付ける Applicant Reference ([Sec. 5.1.9.2](sec5_ial.ja.md#ApplicantRefs)) を使用することができるようにする。

{% comment %}
**Description: The identity service cannot accommodate applicants whose name, gender, or other attributes have changed and are not consistently reflected on the presented identity evidence or match what is in the attribute verifier's records.**

Possible mitigations include:

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs)) who can vouch for the difference in attributes
{% endcomment %}

## Equity and Identity Validation {#EquityValidation}
Identity Evidence および中核の Attribute の Validation には、提示された Identity Evidence および追加 Attribute の真正性、最新性および正確性を確認することが含まれる。これらの結果は、Authoritative または信頼できる Source が保持するデータに対して Evidence および Attribute を比較することによって達成される。Identity Resolution フェーズと合わせて考えると、成功した Validation フェーズの結果は、Claim された Identity が現実世界に存在することをある程度の確からしさで確認することである。

このセクションでは、Evidence および Attribute の Validation プロセスに関連する不公平なアクセス、処遇、 または結果について、考えられる一連の問題および緩和策を提供する:

{% comment %}
Identity evidence and core attribute validation involves confirming the genuineness, currency, and accuracy of presented identity evidence and the accuracy of any additional attributes. These outcomes are accomplished by comparison of the evidence and attributes against data held by authoritative or credible sources. When considered together with the identity resolution phase, the result of successful validation phase is the confirmation, to some level of confidence, that the claimed identity exists in the real world.

This section provides a set of possible problems and mitigations with the inequitable access, treatment, or outcomes associated with the evidence and attribute validation process:
{% endcomment %}

**問題の説明： 特定のユーザーグループは、与えられた IAL の要件を満たすために必要な最小限の Evidence を持っていない。**

緩和策としては、以下が考えられる:

1. 特定の Applicant の状況に基づいてリスクベースの判断を行うことができる Trusted Referee ([Sec. 5.1.9.1](sec5_ial.ja.md#TrustedRefs)) を提供する。
2. Applicant を裏付ける Applicant Reference ([Sec. 5.1.9.2](sec5_ial.ja.md#ApplicantRefs)) を使用できるようにする。

{% comment %}
**Description: Certain user groups do not possess the necessary minimum evidence to meet the requirements of a given IAL.**

Possible mitigations include:

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs)) who can vouch for the applicant
{% endcomment %}

**問題の説明： 特定のユーザーグループに属する Applicant について、Authoritative または信頼できる Source （例：　モバイルネットワークオペレーターや電話番号検証機関など）が保持する記録が不十分であり、Core Attributes の Validation や提示された Evidence をサポートできない。**

緩和策としては、以下が考えられる:

1. 特定の Applicant の状況に基づいてリスクベースの判断を行うことができる Trusted Referee ([Sec. 5.1.9.1](sec5_ial.ja.md#TrustedRefs)) を提供する。
2. 代替となる Authoritative または信頼できる Source を採用する。

{% comment %}
**Description: Records held by authoritative and credible sources (e.g., mobile network operators and phone number verifiers) are insufficient to support the validation of core attributes or presented evidence for applicants belonging to certain user groups.**

Possible mitigations include:

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Employing alternative authoritative or credible sources
{% endcomment %}

**問題の説明： Authoritative または信頼できる Source が保持する記録には、Identity 詐称の被害者である人物に関する不正確または誤った情報が含まれている可能性がある。**

緩和策としては、以下が考えられる:

1. 特定の Applicant の状況に基づいてリスクベースの判断を行うことができる Trusted Referee ([Sec. 5.1.9.1](sec5_ial.ja.md#TrustedRefs)) を提供する。
2. Applicant の Attribute の差異を裏付ける Applicant Reference ([Sec. 5.1.9.2](sec5_ial.ja.md#ApplicantRefs)) を使用することができるようにする。

{% comment %}
**Description: Records held by authoritative and credible sources may include inaccurate or false information about persons who are the victims of identity fraud.**

Possible mitigations include:

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs)) who can vouch for the difference in attributes
{% endcomment %}


## Equity and Identity Verification {#EquityVerification}
Identity Verification には、Identity Evidence プロセスを進めている Applicant と、Identity Resolution および Validation のステップを通じて確立された有効な現実世界の Identity との間のバインディングを証明することが含まれる。多くの場合、Identity Evidence イベントで撮影されたApplicant の写真（顔画像キャプチャ）を収集し、提示さ れ Validate された Identity Evidence の一部に含まれる写真と比較することを伴う。

このセクションでは、Identity Verification フェーズに関連する不公平な処遇や結果について、考えられる一連の問題と緩和策を提供する。
{% comment %}
Identity verification involves proving the binding between the applicant undergoing the identity proofing process and the validated, real-world identity established through the identity resolution and validation steps. It most often involves collecting a picture (facial image capture) of the applicant taken during the identity proofing event and comparing it a photograph contained on a presented and validated piece of identity evidence.

This section provides a set of possible problems and mitigations with the inequitable treatment or outcomes associated with the identity verification phase:
{% endcomment %}

**問題の説明： 画像キャプチャ技術では、特定の肌色や顔の特徴を比較するのに十分な品質でキャプチャする能力がない。**

緩和策としては、以下が考えられる:

1. 異なる肌色、顔の特徴、および照明状況に対応できる、堅牢な画像キャプチャ技術を採用する。
2. 画像キャプチャ技術によって、意図しないバイアスが生じていないかどうかを判断するための運用テストを実施する。
3. 残存するバイアスと技術的な限界を補う、リスクベースの代替プロセスを提供する。

{% comment %}
**Description: Image capture technologies lack the ability to capture certain skin tones or facial features of sufficient quality to perform a comparison.**

Possible mitigations include:

1. Employing robust image capture technologies that are able to accommodate different skin tones, facial features, and lighting situations
2. Conducting operational testing to determine if the image capture technologies have introduced unintentional biases
3. Providing risk-based alternative processes that compensate for residual bias and technological limitations
{% endcomment %}

**問題の説明： 宗教上の理由で着用されている顔のカバーは、Applicant の顔画像を撮影する能力を妨げる。**

緩和策としては、以下が考えられる:

1. 特定の Applicant の状況に基づいてリスクベースの判断を行うことができる Trusted Referee ([Sec. 5.1.9.1](sec5_ial.ja.md#TrustedRefs)) を提供する。
2. 対面での Profing など、Identity Verification を完了するための代替手段を提供する。

{% comment %}
**Description: Facial coverings worn for religious purposes impede the ability to capture a facial image of an applicant.**

Possible mitigations include:

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who can make risk-based decisions based on the specific applicant circumstances.
2. Providing alternative ways to accomplish identity verification, such as an in-person proofing.
{% endcomment %}

**問題の説明： 1対1の顔画像比較技術を使用する場合、偏った顔比較アルゴリズムにより、本人拒否(false non-match)が発生する可能性がある。**

緩和策としては、以下が考えられる:

1. 人口統計グループや画像の種類によらない一貫した性能を確保するために、独自にテストされたアルゴリズムを使用する。
3. 残存するバイアスと技術的な限界を補うための代替プロセスをサポートする。
4. 継続的な品質モニタリングと運用テストを実施し、人口統計グループ間で性能のばらつきを把握し、必要に応じて是正措置を実行する（例：アルゴリズムの更新、機械学習など）。

{% comment %}
**Description: When using 1:1 facial image comparison technologies, biased facial comparison algorithms may result in false non-matches.**

Possible mitigations include:

1. Using algorithms that are independently tested for consistent performance across demographic groups and image types
3. Supporting alternative processes to compensate for residual bias and technological limitations
4. Conducting ongoing quality monitoring and operational testing to identify performance variances are identified across demographic groups and implementing corrective actions as needed (e.g., updated algorithms, machine learning, etc.)
{% endcomment %}

**問題の説明： CSP オペレータが物理的な顔画像比較を行う場合、顔比較における人間のバイアスや一貫性の無さによって、本人拒否(false non-match)が生じる可能性がある。**

緩和策としては、以下が考えられる:

1. CSP　オペレーター／エージェントによる Applicant の不公平な処遇を低減／排除することを目的としたポリシーと手続きを定める。
2. オペレーターの教育・認定の厳格化
3. 継続的な品質監視を行い、バイアスや不公平な処遇、結果が把握された場合には、是正措置を講じる。

{% comment %}
**Description: When employing physical facial image comparison performed by CSP operators, human biases and inconsistencies in making facial comparisons may result in false non-matches.**

Possible mitigations include:

1. Defining policy and procedures aimed at reducing/eliminating the inequitable treatment of applicants by CSP operators/agents
2. Rigorously training and certifying of operators
3. Conducting ongoing quality monitoring and taking corrective actions when biases, or inequitable treatments or outcomes, are identified
{% endcomment %}
## Equity and User Experience {#EquityUser}
本文書の「Usability 考慮事項」([Sec. 9](sec9_usability.ja.md#usability)) では、Applicant に円滑でポジティブな Identity Proofing 体験を提供する方法について CSP に指針を提供する。このセクションでは、Sec. 9 で提供される特定の考慮事項に加え、CSP に対してユーザー体験の Equity を考慮する際の追加的な考慮事項を提供する。

{% comment %}
The Usability Considerations section of this document ([Sec. 9](sec9_usability.md#usability)) provides CSPs with guidance on how to provide applicants with a smooth, positive identity proofing experience. In addition to the specific considerations provided in Sec. 9, this section provides CSPs with additional considerations when considering the equity of their user experience.
{% endcomment %}

**問題の説明： 必要な技術（例： コネクテッドモバイルデバイスやコンピューター）へのアクセスができない、または利用の困難さによって、一部のユーザーグループに過度な負担がかかっている。**

緩和策としては、以下が考えられる:

1. Identity Proofing の要件を満たすことができる Applicant が、必要な技術や活動を使用する際に支援するヘルパーの使用を許可する。
2. 公的に利用可能なデバイス（コンピュータまたはタブレットなど）の使用を許可し、Applicant が所有していないコンピュータまたはデバイスで Identity Proofing プロセスを完了するためのオンライン・ヘルプ・リソースを提供する。
3. 対面での Proofing オプションを提供する。
{% comment %}
**Description: Lack of access to needed technology (e.g. connected mobile device or computer), or difficulties in using required technologies, unduly burdens some user groups.**

Possible mitigations include:

1. Allowing the use of helpers who assist applicants, who are otherwise able to meet the identity proofing requirements, in the use of the required technologies and activities
2. Allowing the use of publicly-available devices (e.g., computers or tablets) and providing online help resources for completing the identity proofing process on a non-applicant-owned computer or device
3. Providing in-person proofing options
{% endcomment %}

**問題の説明： リモートまたは対面での Identity Proofing プロセスは、障害のある人にとって課題がある。**

リモートでの Identity Proofing の緩和策としては、以下が考えられる:

1. Trusted Referee ([Sec. 5.1.9.1](sec5_ial.ja.md#TrustedRefs)) を提供する。
2. Applicant Reference ([Sec. 5.1.9.2](sec5_ial.ja.md#ApplicantRefs)) を使用することができるようにする。
3. 音声ガイド、スクリーン リーダー、音声認識技術など、アクセシビリティやその他の技術の使用をサポートする。

対面での Identity Proofing の緩和策としては、以下が考えられる:

1. さまざまなニーズや障害を持つ人々 (例: 手話に堪能な人) とコミュニケーションを取り、支援を行う、訓練を受けたオペレーターを提供する。
2. さまざまな高さと角度に調整できる機器とワークステーションを選択する。
3. ADA アクセシビリティガイドラインに準拠した利便性の高い場所を選択する。

{% comment %}
**Description: The remote or in-person identity proofing process presents challenges for persons with disabilities.**

Possible mitigations for remote identity proofing include:

1. Providing Trusted Referees ([Sec. 5.1.9.1](sec5_ial.md#TrustedRefs)) who are trained to communicate and assist people with a variety of needs or disabilities (e.g., fluent in sign language)
2. Allowing for the use of Applicant References ([Sec. 5.1.9.2](sec5_ial.md#ApplicantRefs))
3. Supporting the use of accessibility and other technologies, such as audible instructions, screen readers and voice recognition technologies

Possible mitigations for in-person identity proofing include:

1. Providing trained operators who are trained to communicate and assist people with a variety of needs or disabilities (e.g., fluent in sign language)
2. Choosing equipment and workstations that can be adjusted to different heights and angles
3. Selecting locations that are convenient and comply with ADA accessibility guidelines
{% endcomment %}


