---
layout: default.ja
title: Privacy
navOrder: 8
navTitle: Privacy
permalink: /sp800-63a/privacy/
anchor: privacy-section-header
section: 8
---

# プライバシーの考慮事項 {#privacy-section-header}
{% comment %}
# Privacy Considerations {#privacy-section-header}
{% endcomment %}
_This section is informative._

これらのプライバシーの考慮事項は [Sec. 5.1.2](sec5_ial.ja.md#PrivacyReqs)で規定された要件を実装する際に、追加情報を提供する。

{% comment %}
These privacy considerations provide additional information in implementing the requirements set forth in [Sec. 5.1.2](sec5_ial.md#PrivacyReqs).
{% endcomment %}


## 収集とデータ最小化
{% comment %}
## Collection and Data Minimization
{% endcomment %}

ガイドラインは、適切な Identity Resolution、Validation および Verification のための利用可能な最善の方法に基づいて、Claim された Identity の存在を Validate し、Claim された Identity を Applicant と関連付けるために必要な PII のみを収集することを認めている。不必要な PII を収集すると、Identity Proofing サービスに使用されない情報がなぜ収集されるのかについて混乱が生じる恐れがある。これは侵襲性または行き過ぎた懸念につながり、Applicant からの信頼を失う可能性がある。さらに、PII の保持は許可されていないアクセスまたは使用に対して脆弱になる可能性がある。データの最小化により、許可されていないアクセスまたは使用の恐れがある PII の量を減らし、Identity Proofing プロセスに対する信頼を高めることができる。

{% comment %}
The guidelines permit the collection of only the PII necessary to validate the existence of the claimed identity and associate the claimed identity to the applicant, based on best available practices for appropriate identity resolution, validation, and verification. Collecting unnecessary PII can create confusion regarding why information not being used for the identity proofing service is being collected. This leads to invasiveness or overreach concerns, which can lead to loss of applicant trust. Further, PII retention can become vulnerable to unauthorized access or use. Data minimization reduces the amount of PII vulnerable to unauthorized access or use, and encourages trust in the identity proofing process.
{% endcomment %}

### Social Security Numbers
これらのガイドラインは、Identity Resolution で使用するための Attribute として CSP が SSN を収集することを認めている。しかし、SSN への過度の依存は誤用を助長し、Applicant を Identity 盗難 などによる危害のリスクにさらす可能性がある。それでも、SSN は CSP、特に Applicant を機関記録に関連付けるために SSN を使用する連邦機関にとって、Identity Resolution を円滑にする場合がある。本書は、Attribute としての SSN の役割を認識しており、その使用について適切な許容を行う。SSN の知識は Identity Evidence として機能するのに十分ではない。

{% comment %}
These guidelines permit the CSP collection of the SSN as an attribute for use in identity resolution. However, over-reliance on the SSN can contribute to misuse and place the applicant at risk of harm, such as through identity theft. Nonetheless, the SSN may facilitate identity resolution for CSPs, in particular federal agencies that use the SSN to correlate an applicant to agency records. This document recognizes the role of the SSN as an attribute and makes appropriate allowance for its use. Knowledge of the SSN is not sufficient to serve as identity evidence. 
{% endcomment %}

可能な場合、CSP および機関は、Identity Proofingプロセス中の SSN の拡散および露呈を制限するメカニズムを検討する必要がある。これは、Attribute の Validation プロセス中に、SSN が第三者のプロバイダに伝達される場合に特に適切である。可能な限り、プライバシー保護技術およびテクノロジーを適用して、個人の SSN が第三者システムで露呈、保存、または維持されるリスクを軽減する必要がある。この例としては、第三者によって不必要に送信および格納されることを要しない SSN の Validity を確認するための Attribute 要求（たとえば、Validator からの、はい/いいえの回答）の使用が考えられる。Identity Proofing プロセスのすべての Attribute と同様に、処理される各 Attribute の価値とリスクは、プライバシーリスク評価および連邦機関の場合は PIA および SORN の対象となる。SSN は、アプリケーションの保証およびリスクレベルに関連する解決をサポートする目的で必要な場合にだけ収集されるべきである。

{% comment %}
Where possible, CSPs and agencies should consider mechanisms to limit the proliferation and exposure of SSNs during the identity proofing process. This is particularly pertinent where the SSN is communicated to third party providers during attribute validation processes. To the extent possible, privacy protective techniques and technologies should be applied to reduce the risk of an individual’s SSN being exposed, stored, or maintained by third party systems. Examples of this could be the use of attribute claims (e.g., yes/no responses from a validator) to confirm the validity of a SSN without requiring it to be unnecessarily transmitted and stored by the third party. As with all attributes in the identity proofing process, the value and risk of each attribute being processed is subject to a privacy risk assessment and for federal agencies the PIA and SORN. The SSN should only be collected where it is necessary to support resolution associated with the applications assurance and risk levels. 
{% endcomment %}

## 通知と同意 {#consent}
{% comment %}
## Notice and Consent {#consent}
{% endcomment %}

ガイドラインは、CSP が収集時に、Identity Proofing に必要な Attribute の記録を収集し維持する目的、Attribute が Identity Proofing トランザクションを完了するために任意であるか必須であるかどうか、および Attribute を提供しない場合の結果について Applicant に明示的に通知することを要求している。

効果的な通知は、ユーザーエクスペリエンス設計基準と研究、および収集から生じる可能性のあるプライバシーリスクの評価を考慮に入れている。Applicant が Attribute が収集される理由を理解していると誤った推論をすること、収集された情報が他のデータソースと組み合わされる可能性があることなど、さまざまな要素を考慮すべきである。効果的な通知は、Applicant が読んだり理解したりする可能性の低い、複雑で法律的なプライバシーポリシーや一般利用規約へと導くポインタだけでは決してない。
{% comment %}
The guidelines require the CSP to provide explicit notice to the applicant at the time of collection regarding the purpose for collecting and maintaining a record of the attributes necessary for identity proofing, including whether such attributes are voluntary or mandatory in order to complete the identity proofing transactions, and the consequences for not providing the attributes.

An effective notice will take into account user experience design standards and research, and an assessment of privacy risks that may arise from the collection. Various factors should be considered, including incorrectly inferring that applicants understand why attributes are collected, that collected information may be combined with other data sources, etc. An effective notice is never only a pointer leading to a complex, legalistic privacy policy or general terms and conditions that applicants are unlikely to read or understand.
{% endcomment %}
## 利用制限
{% comment %}
## Use Limitation
{% endcomment %}

このガイドラインは、CSP に対して、Identity Proofing、Authentiation、Authorization、または Attribute Assertion、関連する詐欺の軽減、あるいは法律または法的プロセスを遵守する以外の目的で Attribute を処理 (Processing) することから生じ得るプライバシーリスクに見合った、予測可能性（PII および情報システムによるその処理 (Processing) について、個人、所有者、および運用者による信頼性の高い推測を可能にすること）および管理可能性（PII の変更、削除、選択的開示など、粒度の細かい管理のための機能を提供すること）の目標を維持する手段を用いることを求めている [[NISTIR8062]](sec11_references.ja.md#ref-NISTIR8062).。

CSP は、Subscriber に 非 Identity サービスを提供することを含め、Attribute を処理 (Processing) することのために様々なビジネス目的を持っているかもしれない。しかし、Subject に開示される目的以外のために Attribute を処理 (Processing) することは、さらなるプライバシーリスクを生じさせる可能性がある。CSP は、追加的な処理 (Processing) から生じるプライバシーリスクに見合った適切な手段を決定することができる。たとえば、適用される法律、規制、またはポリシーがない場合、Subscriber が要求する非 Identity サービスを提供するために Attribute を処理 (Processing) する際に同意を得る必要はない場合があるが、通知によって Subscriber が処理 (Processing) について信頼性の高い仮定（予測可能性）を維持することは可能であろう。その他の Attribute の処理 (Processing) には、同意を得ること、または特定の Attribute の使用または開示について Subscriber がよりコントロールできるようにすることを必要とする、異なるプライバシーリスクが伴う場合がある（管理可能性）。Subscriber の同意は意味がある必要がある。したがって、CSP が同意手段を使用する場合、追加的な使用に対する Subscriber の承諾を Identity サービス提供の条件とすることはできない。

提案された処理 (Processing) が認められている処理 (Processing) の範囲外であるかどうか、または適切なプライバシーリスク緩和策について疑問がある場合は、SAOP に相談する。

{% comment %}
The guidelines require CSPs to use measures to maintain the objectives of predictability (enabling reliable assumptions by individuals, owners, and operators about PII and its processing by an information system) and manageability (providing the capability for granular administration of PII, including alteration, deletion, and selective disclosure) commensurate with privacy risks that can arise from the processing of attributes for purposes other than identity proofing, authentication, authorization, or attribute assertion, related fraud mitigation, or to comply with law or legal process [[NISTIR8062]](sec11_references.md#ref-NISTIR8062).

CSPs may have various business purposes for processing attributes, including providing non-identity services to subscribers. However, processing attributes for other purposes than those disclosed to a subject can create additional privacy risks. CSPs can determine appropriate measures commensurate with the privacy risk arising from the additional processing. For example, absent applicable law, regulation or policy, it may not be necessary to get consent when processing attributes to provide non-identity services requested by subscribers, although notices may help subscribers maintain reliable assumptions about the processing (predictability). Other processing of attributes may carry different privacy risks that call for obtaining consent or allowing subscribers more control over the use or disclosure of specific attributes (manageability). Subscriber consent needs to be meaningful; therefore, when CSPs do use consent measures, they cannot make acceptance by the subscriber of additional uses a condition of providing the identity service.

Consult your SAOP if there are questions about whether the proposed processing falls outside the scope of the permitted processing or the appropriate privacy risk mitigation measures.
{% endcomment %}

## 再掲
{% comment %}
## Redress
{% endcomment %}

ガイドラインは、CSP が Identity Proofing から生じる Applicant の苦情または問題を救済するための効果的なメカニズムを提供し、加えてメカニズムは Applicant にとって見つけやすい、アクセスしやすいようにすることを要求してい る。
{% comment %}
The guidelines require the CSP to provide effective mechanisms for redressing applicant complaints or problems arising from the identity proofing, and make the mechanisms easy for applicants to find and access.
{% endcomment %}

Privacy Act は、記録システムを維持する連邦政府 CSP に対し、Applicant が記録にアクセスし、誤っている場合は修正できるようにする手順に従うことを求めている。Privacy Actのいずれのステートメントにも、該当する SORN(s) ([Sec. 5.1.2](sec5_ial.ja.md#PrivacyReqs)参照)への参照を含める必要があり、これにはアクセスまたは修正の要求を行う方法に関する指示が Applicant に提示される。連邦政府以外の CSP は、第三者が情報源である場合の連絡先情報を含め、同等の手順を用意すべきである。

{% comment %}
The Privacy Act requires federal CSPs that maintain a system of records to follow procedures to enable applicants to access and, if incorrect, amend their records. Any Privacy Act Statement should include a reference to the applicable SORN(s) (see [Sec. 5.1.2](sec5_ial.md#PrivacyReqs)), which provide the applicant with instructions on how to make a request for access or correction. Non-federal CSPs should have comparable procedures, including contact information for any third parties if they are the source of the information.
{% endcomment %}

CSP は、Applicant がオンラインで Identity Proofing および Enrollment プロセスを完了できない場合、プロセスを完了するための代体手法（例：顧客サービスセンターでの対面）の利用可能性を Applicant に明示する必要がある。

{% comment %}
CSPs should make the availability of alternative methods for completing the process clear to applicants (e.g., in person at a customer service center) in the event an applicant is unable to establish their identity and complete the registration process online.
{% endcomment %}

> 注：Identity Proofing プロセスが成功しなかった場合、CSP は問題に対処するための手順を Applicant に通知する必要があるが、Enrollment が失敗した理由の詳細を Applicant に通知すべきではない（たとえば、「あなたの SSN は当社が記録しているものと一致しませんでした」と Applicant に通知しない）。それをしてしまうと、不正な Applicant が PII の正確性についてさらに知識を得ることができる。

{% comment %}
> Note: If the identity proofing process is not successful, CSPs should inform the applicant of the procedures to address the issue but should not inform the applicant of the specifics of why the registration failed (e.g., do not inform the applicant, "Your SSN did not match the one that we have on record for you"), as doing so could allow fraudulent applicants to gain more knowledge about the accuracy of the PII.
{% endcomment %}

## プライバシーリスク評価
{% comment %}
## Privacy Risk Assessment
{% endcomment %}
本ガイドラインでは、CSP がプライバシーリスク評価を実施することを求めている。プライバシーリスク評価の実施において、CSP は以下を考慮する必要がある。

1. CSP が取る行動（追加の Verification ステップや記録の保持など）が、情報への侵襲や許可されていないアクセスなど、Applicant にとっての問題を生じさせる可能性；および
2. 問題が発生した場合の影響。CSP は、リスクの受容、リスクの軽減、およびリスクの共有を含め、特定されたプライバシーリスクに対して取るあらゆる対応を正当化できるようにすべきである。Applicant の同意の使用は、リスク共有の一つの形式と見なされるべきであり、したがって Applicant が共有リスクを評価・受容する能力を有すると合理的に予想される場合にのみ使用すべきである。
{% comment %}
The guidelines require the CSP to conduct a privacy risk assessment. In conducting a privacy risk assessment, CSPs should consider:

1. The likelihood that the action it takes (e.g., additional verification steps or records retention) could create a problem for the applicant, such as invasiveness or unauthorized access to the information; and
2. The impact if a problem did occur. CSPs should be able to justify any response it takes to identified privacy risks, including accepting the risk, mitigating the risk, and sharing the risk. The use of applicant consent should be considered a form of sharing the risk, and therefore should only be used when an applicant could reasonably be expected to have the capacity to assess and accept the shared risk.
{% endcomment %}

## 政府機関特有のプライバシーコンプライアンス
{% comment %}
## Agency-Specific Privacy Compliance
{% endcomment %}

このガイドラインは、連邦政府 CSP の特定のコンプライアンス義務をカバーしている。Digital Authentication システム開発の初期段階で機関の SAOP を関与させ、プライバシーリスクを評価および軽減し、Ientity Proofing を実施するための PII 収集が 1974 年 Privacy Act[[PrivacyAct]](sec11_references.ja.md#ref-PrivacyAct) や 2002 年の E-Government Act [[E-Gov]](sec11_references.ja.md#ref-E-Gov) がプライバシー影響評価実施を求めるきっかけになるかどうか、準拠要件について機関に助言することが重要である。たとえば、Identity Proofing に関して、Identity Proofing を行うのに必要な PII または他の Attribute の収集および保守のために、Privacy Act の要件がトリガされ、新規または既存の Privacy Act の記録システムによるカバーが必要になると思われる。

{% comment %}
The guidelines cover specific compliance obligations for federal CSPs. It is critical to involve your agency's SAOP in the earliest stages of digital authentication system development to assess and mitigate privacy risks and advise the agency on compliance requirements, such as whether or not the PII collection to conduct identity proofing triggers the Privacy Act of 1974 [[PrivacyAct]](sec11_references.md#ref-PrivacyAct) or the E-Government Act of 2002 [[E-Gov]](sec11_references.md#ref-E-Gov) requirement to conduct a Privacy Impact Assessment. For example, with respect to identity proofing, it is likely that the Privacy Act requirements will be triggered and require coverage by either a new or existing Privacy Act system of records due to the collection and maintenance of PII or other attributes necessary to conduct identity proofing.
{% endcomment %}

SAOP は同様に、PIA が必要かどうかを判断する際に機関を支援することができる。 これらの考慮事項は、Identity Proofing だけのために Privacy Act SORN または PIA を行う要件として読よみとるべきではない。多くの場合、デジタル Identity ライフサイクル全体を包含する PIA および SORN を起草する、あるいは機関がオンラインアクセスを確立しているプログラムまたは便益について議論する、より大きなプログラム的 PIA の一部として Identity Proofing プロセスを含めることが最も理にかなっている。

{% comment %}
The SAOP can similarly assist the agency in determining whether a PIA is required. These considerations should not be read as a requirement to develop a Privacy Act SORN or PIA for identity proofing alone; in many cases it will make the most sense to draft a PIA and SORN that encompasses the entire digital identity lifecycle or includes the identity proofing process as part of a larger, programmatic PIA that discusses the program or benefit to which the the agency is establishing online access.
{% endcomment %}

デジタル Identity ライフサイクルには多くの構成要素があるため、SAOP が個々の構成要素について認識し理解することが重要である。たとえば、データ使用合意、コンピュータ・マッチング合意などの Proofing サービスを提供または使用する機関には、他のプライバシー成果物が適用される場合がある。SAOP は、どのような追加要件が適用されるかを判断する上で、機関を支援することができる。さらに、Digital Authentication の個々の構成要素を十分に理解することで、SAOP は、コンプライアンスプロセスまたは他の手段で、プライバシーリスクを徹底的に評価し、軽減することができる。

{% comment %}
Due to the many components of the digital identity lifecycle, it is important for the SAOP to have an awareness and understanding of each individual component. For example, other privacy artifacts may be applicable to an agency offering or using proofing services such as Data Use Agreements, Computer Matching Agreements, etc. The SAOP can assist the agency in determining what additional requirements apply. Moreover, a thorough understanding of the individual components of digital authentication will enable the SAOP to thoroughly assess and mitigate privacy risks either through compliance processes or by other means.
{% endcomment %}
