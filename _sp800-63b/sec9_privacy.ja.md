---
layout: default.ja
title: Privacy Considerations
navOrder: 9
navTitle: Privacy
permalink: /sp800-63b/privacy/
anchor: sec9
section: 9
---

# Privacy Considerations {#sec9}

<!--
*These privacy considerations supplement the guidance in Sec. 4. This section is informative.*
-->

*これらのプライバシー考慮事項は Sec. 4 のガイダンスを補足する. This section is informative.*

## Privacy Risk Assessment

<!--
[Sections 4.1.5](sec4_aal.md#aal1records), [4.2.5](sec4_aal.md#aal2records), and [4.3.5](sec4_aal.md#aal3records) require the CSP to conduct a privacy risk assessment for records retention. Such a privacy risk assessment would include:
-->

[Sections 4.1.5](sec4_aal.md#aal1records), [4.2.5](sec4_aal.md#aal2records), [4.3.5](sec4_aal.md#aal3records) は, CSP が記録保持のためのプライバシーリスク評価を実施することを要求する. このようなプライバシーリスク評価には, 以下を含む:

<!--
1. The likelihood that the records retention could create a problem for the subscriber, such as invasiveness or unauthorized access to the information.
2. The impact if such a problem did occur.
-->

1. 記録の保持によって, Subscriber に情報への侵入や未承認のアクセスなどの問題が起こる可能性.
2. そのような問題が発生した場合の影響.

<!--
CSPs should be able to reasonably justify any response they take to identified privacy risks, including accepting the risk, mitigating the risk, and sharing the risk. The use of subscriber consent is a form of sharing the risk, and therefore appropriate for use only when a subscriber could reasonably be expected to have the capacity to assess and accept the shared risk.
-->

CSP は, リスクの受け入れ, リスクの軽減, リスクの共有を含む識別されたプライバシーリスクに対して行うあらゆる対応を合理的に正当化できる必要がある. Subscriber の同意の使用は, リスクを共有する形式であるため, Subscriber が共有されたリスクを評価して受け入れる能力を持っていると合理的に期待できる場合にのみ使用するのが適切である.

## Privacy Controls

<!--
[Section 4.4](sec4_aal.md#aal_privacy) requires CSPs to employ appropriately tailored privacy controls. [[SP800-53]](references.md#ref-SP800-53) provides a set of privacy controls for CSPs to consider when deploying authentication mechanisms. These controls cover notices, redress, and other important considerations for successful and trustworthy deployments.
-->

[Section 4.4](sec4_aal.md#aal_privacy) は, CSP が適切に調整されたプライバシーコントロールを採用することを要求する. [[SP800-53]](references.md#ref-SP800-53) は, CSP が Authentication メカニズムを展開する際に考慮すべき一連のプライバシーコントロールを提供する. これらのコントロールは, 効果的で信頼に値する展開のための通知, 是正, およびその他の重要な考慮事項をカバーする.

## Use Limitation

<!--
[Section 4.4](sec4_aal.md#aal_privacy) requires CSPs to use measures to maintain the objectives of predictability (enabling reliable assumptions by individuals, owners, and operators about PII and its processing by an information system) and manageability (providing the capability for granular administration of PII, including alteration, deletion, and selective disclosure) commensurate with privacy risks that can arise from the processing of attributes for purposes other than identity proofing, authentication, authorization, or attribute assertion, related fraud mitigation, or to comply with law or legal process [[NISTIR8062]](references.md#ref-NISTIR8062).
-->

[Section 4.4](sec4_aal.md#aal_privacy) は, CSP に対して, Identity Proofing, Authentication, Authorization, または Attribute Assertion, 関連する不正の軽減, または法律と法的手続きの遵守以外の目的でのAttribute の処理から生じる可能性のあるプライバシーリスクに見合った Predictability (個人, 所有者, オペレーターによる, PII と情報システムによる Processing について信頼できるという仮定を可能にする) および Manageability (情報システムによる 変更, 削除, 選択的開示を含む PII の詳細な管理の提供) の目的を維持するための手段を使用することを要求する [[NISTIR8062]](references.md#ref-NISTIR8062). 

<!--
CSPs may have various business purposes for processing attributes, including providing non-identity services to subscribers. However, processing attributes for other purposes than those specified at collection can create privacy risks when individuals are not expecting or comfortable with the additional processing. CSPs can determine appropriate measures commensurate with the privacy risk arising from the additional processing. For example, absent applicable law, regulation or policy, it may not be necessary to get consent when processing attributes to provide non-identity services requested by subscribers, although notices may help subscribers maintain reliable assumptions about the processing (predictability). Other processing of attributes may carry different privacy risks that call for obtaining consent or allowing subscribers more control over the use or disclosure of specific attributes (manageability). Subscriber consent needs to be meaningful; therefore, as stated in [Sec. 4.4](sec4_aal.md#aal_privacy), when CSPs use consent measures, acceptance by the subscriber of additional uses shall not be a condition of providing authentication services.
-->

CSP は, Subscriber に Non-Identity Services を提供することを含む, Attribute を処理するためのさまざまなビジネス目的を持つ場合がある.  しかし, 収集時に指定された以外の目的で Attribute を処理することは, 個人が追加の処理を期待していない, または快適でない場合, プライバシーリスクを作り出す可能性がある.  CSP は, 追加の処理から生じるプライバシーリスクに見合った適切な手段を決定できる. たとえば, 適用される法律, 規制, ポリシーがなければ, Subscriber からリクエストされた Non-Identity Services を提供するために Attribute を処理する際に同意を得る必要はないかもしれないが, 通知は Subscriber が処理に関する信頼できる仮定を維持するのに役立つ場合がある(Predictability).  Attribute のその他の処理には, 同意を取得する必要がある, または Subscriber が特定の Attribute の使用や開示をより詳細に制御できるようにする必要がある, さまざまなプライバシーリスクを運び込む可能性がある(Manageability). Subscriber の同意は意味のあるものである必要がある. したがって, [Sec. 4.4](sec4_aal.md#aal_privacy) で述べられた通り, CSP が同意を手段として使用する場合, Subscriber が追加の使用を受け入れることが Authentication Service を提供する条件になることはない.

<!--
Consult the agency SAOP if there are questions about whether the proposed processing falls outside the scope of the permitted processing or the appropriate privacy risk mitigation measures.
-->

目的とする処理が許可された処理または適切なプライバシーリスク軽減手段の範囲外となるかどうかについて質問がある場合は, 政府機関の SAOP と相談する.


## Agency-Specific Privacy Compliance {#agency-privacy}

<!--
[Section 4.4](sec4_aal.md#aal_privacy) covers specific compliance obligations for federal CSPs. It is critical to involve the agency SAOP in the earliest stages of digital authentication system development in order to assess and mitigate privacy risks and advise the agency on compliance requirements, such as whether or not the collection of PII to issue or maintain authenticators triggers the *Privacy Act of 1974* [[PrivacyAct]](references.md#ref-PrivacyAct) or the *E-Government Act of 2002* [[E-Gov]](references.md#ref-E-Gov) requirement to conduct a PIA. For example, with respect to centralized maintenance of biometrics, it is likely that the Privacy Act requirements will be triggered and require coverage by either a new or existing Privacy Act system of records due to the collection and maintenance of PII and any other attributes necessary for authentication. The SAOP can similarly assist the agency in determining whether a PIA is required.
-->

[Section 4.4](sec4_aal.md#aal_privacy) は, 連邦の CSP の特定のコンプライアンス義務をカバーする. プライバシーリスクを評価して軽減し, Authenticator を発行・維持するための PII の収集が PIA を実施する *Privacy Act of 1974* [[PrivacyAct]](references.md#ref-PrivacyAct) または the *E-Government Act of 2002* [[E-Gov]](references.md#ref-E-Gov) の要件をトリガーするかどうかといったコンプライアンス要件を政府機関にアドバイスするために, Digital Authentication System 開発の一番早いステージで政府機関の SAOP を巻き込むことが非常に重要である. 例えば, Biometrics の集中管理に関しては, ほとんどの場合で Privacy Act requirements がトリガーされ, PII および Authentication に必要なその他の Attribute の収集と管理のために, 新規または既存の Privacy Act システムの記録によるカバーが要求される. 同様に, SAOP は政府機関が PIA が必要かどうかを判断することを支援できる.

<!--
These considerations should not be read as a requirement to develop a Privacy Act SORN or PIA for authentication alone. In many cases it will make the most sense to draft a PIA and SORN that encompasses the entire digital identity process or include the digital authentication process as part of a larger programmatic PIA that discusses the online service or benefit that the agency is establishing.
-->

これらの考慮事項は, Authentication だけのために Privacy Act SORN や PIA を開発するための要件として読まれないほうがよい.  多くの場合, Digital Identity Process 全体を網羅する PIA や SORN の草案を作成するか, 政府機関が確立しようとしているオンラインサービスやベネフィットについて議論する, より大きなプログラムによる PIA の一部として, Digital Identity Process を含めることが最も理にかなっている.

<!--
Due to the many components of digital authentication, it is important for the SAOP to have an awareness and understanding of each individual component. For example, other privacy artifacts may be applicable to an agency offering or using federated CSP or RP services (e.g., Data Use Agreements, Computer Matching Agreements). The SAOP can assist the agency in determining what additional requirements apply. Moreover, a thorough understanding of the individual components of digital authentication will enable the SAOP to thoroughly assess and mitigate privacy risks either through compliance processes or by other means.
-->

Digital Authentication には多くのコンポーネントがあるため, SAOP が個々のコンポーネントを認識し理解することが重要である.  例えば, 他の Privacy Artifact は, 連携された CSP や RP サービス (例: データ使用契約, コンピュータマッチング契約) を提供または使用する政府機関に適用される場合がある. SAOP は, 何の追加要件が適用されるかを政府機関が判断することを支援できる. さらに, Digital Authentication の個々のコンポーネントを十分に理解することは, SAOP が, コンプライアンスプロセスやその他の方法を通じて, プライバシーリスクを十分に評価, 軽減することを可能にする. 