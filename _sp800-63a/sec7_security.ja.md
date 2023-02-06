---
layout: default.ja
title: Security
navOrder: 7
navTitle: Security
permalink: /sp800-63a/security/
anchor: security
section: 7
---

# Threats and Security Considerations {#security}

_This section is informative._

効果的にIdentity Proofingプロセスを保護するには、特定のApplicantとのトランザクション全体を通じてセキュリティコントロールとプロセスを重ね合わせていくことが必要である。これを達成するためには、脅威がどこでどのように発生し、Enrollmentを危殆化するかを理解する必要がある。Identity Proofingプロセスに対する脅威には、3 つの一般的なカテゴリがある: 

{% comment %}
Effective protection of identity proofing processes requires the layering of security controls and processes throughout a transaction with a given applicant. To achieve this, it is necessary to understand where and how threats can arise and compromise enrollments. There are three general categories of threats to the identity proofing process: 
{% endcomment %}

* **なりすまし**: Attacker が他の正当な個人を語る試み(例：Identity 盗難)

* **虚偽・詐称表現**: Attacker が虚偽のIdentityを作り出す、あるいはIdentityについての虚偽のClaimを行う可能性(例: 合成 Identity 詐称)

* **インフラストラクチャ**: Attacker がインフラストラクチャ、データ、ソフトウェア、あるいは CSP による Identity Proofing プロセスを支える人たちを危殆化させる可能性

{% comment %}
 * **Impersonation**: where an attacker attempts to pose as another, legitimate, individual (e.g., identity theft)

 * **False or Fraudulent Representation**: where an attacker may create a false identity or false claims about an identity (e.g., synthetic identity fraud)

 * **Infrastructure**: where attackers may seek to compromise confidentiality, availability, and integrity of the infrastructure, data, software, or people supporting the CSPs identity proofing process (e.g., distributed denial of service, insider threats)
{% endcomment %}

このセクションでは、なりすましと虚偽・詐称表現の脅威を中心に説明する。インフラストラクチャの脅威は、従来のコンピュータセキュリティコントロール（例：侵入防御、記録保持、独立監査）によって考慮されており、このドキュメントの範囲外であるためです。セキュリティ対策の詳細については、[[[SP800-53]](sec11_references.ja.md#ref-SP800-53) _Recommended Security and Privacy Controls for Federal Information Systems and Organizations_ を参照すること。

{% comment %}
This section focuses on impersonation and false or fraudulent representation threats, as infrastructure threats are addressed by traditional computer security controls (e.g., intrusion protection, record keeping, independent audits) and are outside the scope of this document. For more information on security controls, see [[SP800-53]](sec11_references.md#ref-SP800-53), _Recommended Security and Privacy Controls for Federal Information Systems and Organizations_.
{% endcomment %}

[表 2 Enrollment と Identity Proofing の脅威](sec7_security.md#table-2){:name="table-2"}
{:latex-ignore="true"}


| Attack/Threat |Description | Example |
|---------------|------------------------|------------------|
|自動化された Enrollment 試行| Attacker は、スクリプトや自動化プロセスを活用して大量のEnrollmentを急速に発生させる。| 盗難したデータを利用して、ボットが給付金の申請を行う。|
|Evidence 改ざん | Attacker は Identity を Claim するために Evidence を作成・変更する。| Evidenceとして利用する偽造運転免許証| 
|合成 Identity 詐称 | Attacker は 実際の人物に結び付けられていない Evidence を捏造する| クレジットファイルを作成するたえに偽名でクレジットカードを利用できるようにする|
|Identity 不正利用(Identity 盗難)| Attacker は他の個人の Identity や、Identity Evidenceを利用する。| 盗難されたパスポートの利用 |
|Social Engineering| Attacker は正当なApplicantに対し、Identity Evidenceの提供を求めたり、騙してIdentity Proofingプロセスの完了を促す。| Attacker が将来の雇用主を装って、個人の Identity Evidence を提出させる|
|虚偽 Claim| Attacker は、正当な Identity に虚偽の Attribute や情報を関連付ける| 個人が居住していない州に対して便益を Claim する|
{:latex-table="2" latex-caption="Enrollment and Identity Proofing Threats" latex-columns="p@0.25\textwidth,p@0.35\textwidth,p@0.25\textwidth"}

{% comment %}
[Table 2 Enrollment and Identity Proofing Threats](sec7_security.md#table-2){:name="table-2"}
{:latex-ignore="true"}

| Attack/Threat |Description | Example |
|---------------|------------------------|------------------|
|Automated Enrollment Attempts|Attackers leverage scripts and automated processes to rapidly generate large volumes of enrollments| Bots leverage stolen data to submit benefits claims.|
|Evidence Falsification | Attacker creates or modifies evidence in order claim an identity| A fake driver’s license is used as evidence.|
|Synthetic Identity fraud | Attacker fabricates evidence of identity that is not associated with a real person| Opening a credit cards in a fake name to create a credit file.|
|Fraudulent Use of Identity (Identity Theft)| Attacker fraudulently uses another individuals identity or identity evidence | An individual uses a stolen passport.|
|Social Engineering| Attacker convinces a legitimate applicant to provide identity evidence or complete the identity proofing process under false pretenses| An individual submits their identity evidence to an attacker posing as a potential employer.|
|False Claims| Attacker associates false attributes or information with a legitimate identity| An individual claims benefits from a state in which they do not reside.|
{:latex-table="2" latex-caption="Enrollment and Identity Proofing Threats" latex-columns="p@0.25\textwidth,p@0.35\textwidth,p@0.25\textwidth"}
{% endcomment %}


## 脅威の緩和戦略

{% comment %}
## Threat Mitigation Strategies
{% endcomment %}

Enrollment および Identity Proofing プロセスに対する脅威を [表 2](sec7_security.ja.md#table-2)にまとめている。上記で特定された脅威の緩和を支援する関連メカニズムは、[表 3](sec7_security.ja.md#table-3) にまとめられている。これらの緩和策は包括的なものではなく、各Identity Assurance Levelにおいてより徹底的に詳細化され、[[SP800-63]](../_sp800-63/sec5_DIRM.ja.md#sec5){:latex-href="#ref-SP800-63"} 5 章に詳述されているリスク評価プロセスに基づいて適用されている緩和策のサマリーと認識すべきである。

{% comment %}
Threats to the enrollment and identity proofing process are summarized in [Table 2](sec7_security.md#table-2). Related mechanisms that assist in mitigating the threats identified above are summarized in [Table 3](sec7_security.md#table-3). These mitigations should not be considered comprehensive but a summary of mitigations detailed more thoroughly at each Identity Assurance Level and applied based on the risk assessment processes detailed in [[SP800-63]](../_sp800-63/sec5_DIRM.md#sec5){:latex-href="#ref-SP800-63"} Sec. 5.
{% endcomment %}

[表 3 Enrollment と発行における脅威の緩和戦略](sec7_security.ja.md#table-3){:name="table-3"}
{:latex-ignore="true"}

| Threat/Attack | 緩和戦略 | Normative Reference(s) |
|-------------------|-------------------------|------------------------|
|自動化された Enrollment 試行 | CSP はウェブ・アプリケーション・ファイアウォール（WAF）制御やボット検出技術を実装する。Applicant が真に存在するかどうかを判断するために、バイオメトリクス Verifications および生存性検出メカニズムを実装する。トラフィックおよびネットワーク分析機能を実装し、兆候や悪意のあるトラフィックを特定する。 | 5.3.1, 5.4.1, 5.5.1 |
|Evidence 改ざん | CSP は中核の Attribute を Authoritative または信頼できる source で Validate する。CSP は、提出された Evidence の物理的セキュリティ機能あるいはデジタルセキュリティ機能を確認する。 | 4.3, 5.3.2, 5.3.3, 5.4.2, 5.4.3, 5.5.2, 5.5.3 |
|合成 Identity 詐称 | CSP は、Proofing プロセスをサポートする、複数の Identity Evidence を収集する。CSP は中核の Attribute を Authoritative または信頼できる source で Validate する。 CSP は、Authoritative または信頼できる source から提供され、Validate済みの Identity Evidenceまたはバイオメトリクスデータと、Applicant のバイオメトリクスを比較することで、その Identity をVerify する。 | 4.3, 4.3, 5.3.2, 5.3.3, 5.3.4, 5.4.2, 5.4.3, 5.4.4, 5.5.2, 5.5.3, 5.5.4 |
|Identity 不正利用(Identity 盗難)| CSP は、Authoritative または信頼できる source から提供され、Validate済みの Identity Evidenceまたはバイオメトリクスデータと、Applicant のバイオメトリクスを比較することで、その Identity を Verifyする。CSP は、Identity Evidence が付帯する個人が本当に存在していることを確認するために、Presentation Attack Detection の手法を実装する。CSP は、Out-of-bandでのエンゲージメント（Enrollment コードなど）およびProofing通知を実装する。CSP は、重要統計情報リポジトリ(デスマスターファイルなど)の確認を実施する。CSPは、詐欺、トランザクション、および行動の分析機能を実装して、潜在的に悪意のある口座開設の指標を特定する。| 5.1.1, 5.3.4, 5.4.4, 5.5.4 |
|Social Engineering| CSP は、強要や経済的困窮の兆候を識別するために、Trusted Refereeのトレーニングを実施する。CSP は、Validate済みのアドレスにOut-of-bandでのエンゲージメントとProofingに通知を提供する。CSP は、一般的な脅威と計画に関する情報およびコミュニケーションをエンド・ユーザに提供する。 | 5.1.6, 5.1.7, 5.1.9 |
|虚偽 Claim| CSP はトラフィックに地理的な制限を実装する。CSP は、中核の Attribute および RP が要求するビジネスAttributeを、Authoritative Source または信頼できる Source で Validate する。| 5.1.1, 5.3.2, 5.3.3, 5.4.2, 5.4.3, 5.5.2, 5.5.3 |
{:latex-table="3" latex-caption="Enrollment and Issuance Threat Mitigation Strategies" latex-columns="p@0.20\textwidth,p@0.65\textwidth,p@0.15\textwidth"}

{% comment %}
[Table 3 Enrollment and Issuance Threat Mitigation Strategies](sec7_security.md#table-3){:name="table-3"}
{:latex-ignore="true"}

| Threat/Attack | Mitigation Strategies | Normative Reference(s) |
|-------------------|-------------------------|------------------------|
|Automated Enrollment Attempts | CSP implements Web Application Firewall (WAF) controls and bot detection technology.CSP implements out-of-band engagement (e.g., enrollment codes). CSP implements biometric verification and liveness detection mechanism to determine genuine presence of an applicant. CSP implements traffic and network analysis capabilities to identify indications or malicious traffic | 5.3.1, 5.4.1, 5.5.1 |
|Evidence Falsification | CSP validates core attributes with authoritative or credible sources.  CSP checks physical or digital security features of the presented evidence. | 4.3, 5.3.2, 5.3.3, 5.4.2, 5.4.3, 5.5.2, 5.5.3 |
|Synthetic Identity fraud | CSP collects multiple pieces of identity evidence to support the proofing process. CSP validates core attributes with authoritative or credible sources. CSP verifies identity through biometric comparison of the applicant to validated identity evidence or biometric data provided by an authoritative or credible source. | 4.3, 4.3, 5.3.2, 5.3.3, 5.3.4, 5.4.2, 5.4.3, 5.4.4, 5.5.2, 5.5.3, 5.5.4 |
|Fraudulent Use of Identity (Identity Theft)| CSP verifies identity through biometric comparison of the applicant to validated identity evidence or biometric data provide by an authoritative or credible source. CSP implements presentation attack detection measures to confirm the genuine presence of the individual to whom the identity evidence belongs. CSP implements out-of-band engagement (e.g., enrollment codes) and notice of proofing. CSP conducts checks of vital statistics repositories (e.g., Death Master File).CSP implements fraud,  transaction, and behavioral analysis capabilities to identify indicators of potentially malicious account establishment. | 5.1.1, 5.3.4, 5.4.4, 5.5.4 |
|Social Engineering| CSP conducts training of Trusted Referees to identify indications of coercion or distress. CSP provides out-of-band engagement and notice of proofing to validated address. CSP provides information and communication to end users on common threats and schemes. | 5.1.6, 5.1.7, 5.1.9 |
|False Claims| CSP implements geographic restrictions on traffic. CSP validates core attributes and RP requested business attributes with authoritative or credible sources.| 5.1.1, 5.3.2, 5.3.3, 5.4.2, 5.4.3, 5.5.2, 5.5.3 |
{:latex-table="3" latex-caption="Enrollment and Issuance Threat Mitigation Strategies" latex-columns="p@0.20\textwidth,p@0.65\textwidth,p@0.15\textwidth"}
{% endcomment %}

## 隣接するプログラムとのコラボレーション 

{% comment %}
## Collaboration with Adjacent Programs 
{% endcomment %}

Identity Proofingサービスは、通常、重要なビジネスやサービス機能のフロントドアとして機能する。したがって、これらのサービスは他と関わりを持たない形で運用されるべきではない。Identity Proofingおよび CSP 機能をサイバーセキュリティチーム、脅威インテリジェンス チーム、およびプログラムインテグリティチームと緊密に連携させることにより、Identity Proofing機能を常に改善しながらビジネス機能をより完全に保護することが可能になる。たとえば、プログラム・インテグリティ・チームが収集した支払詐欺データは、漏洩したSubscriberアカウントおよびIdentity Proofing実装の潜在的弱点の指標を提供することができる。同様に、脅威インテリジェンスチームは、Identity Proofingプロセスに影響を与える可能性のある新しい戦術、技術、および手順に関する指標を受け取ることもあるだろう。CSP および RP は、重要なセキュリティおよび詐欺に関するステークホルダー間での情報交換のための一貫したメカニズムを確立するよう努力すべきである。CSP が外部の場合、これは複雑かもしれないが、契約上および法律上の仕組みで考慮されるべきである。収集、送信、または共有されるすべてのデータは最小化され、詳細なプライバシー及び法的評価の対象となるべきである。

{% comment %}
Identity proofing services typically serve as the front door for critical business or service functions. Accordingly, these services should not operate in a vacuum. Close coordination of identity proofing and CSP functions with cybersecurity teams, threat intelligence teams, and program integrity teams can enable a more complete protection of business capabilities while constantly improving identity proofing capabilities. For example, payment fraud data collected by program integrity teams could provide indicators of compromised subscriber accounts and potential weaknesses in identity proofing implementations. Similarly, threat intelligence teams may receive indications of new tactics, techniques, and procedures that may impact identity proofing processes. CSPs and RPs should seek to establish consistent mechanisms for the exchange of information between critical security and fraud stakeholders. Where the CSP is external, this may be complicated, but should be considered in contractual and legal mechanisms. All data collected, transmitted, or shared should be minimized and subject to a detailed privacy and legal assessment.

{% endcomment %}