---
layout: default.ja
title: Equity Considerations
navOrder: 11
navTitle: Equity
permalink: /sp800-63b/equity/
anchor: sec11
section: 11
---

# Equity Considerations {#sec11}

_This section is informative._

<!--
Accurate and equitable authentication service is an essential element of a digital identity system. While the accuracy aspects of authentication are largely the subject of the security requirements found elsewhere in this document, the ability for all subscribers to authenticate reliably is required to provide equitable access to government services as specified in Executive Order 13985, "Advancing Racial Equity and Support for Underserved Communities Through the Federal Government" [[EO13985]](references.md#ref-EO13985). In assessing equity risks, a CSP should consider the overall user population served by its authentication service. Additionally, the CSP further identifies groups of users within the population whose shared characteristic(s) can cause them to be subject to inequitable access, treatment, or outcomes when using that service. The usability considerations provided in [Sec. 10](sec10_usability.md#sec10) should also be considered to help ensure the overall usability and equity for all persons using authentication services.
-->

正確で公平な Authentication Service は, Digital Identity System の不可欠な要素である. Authentication の正確さの aspect は, 大部分がこのドキュメント以外の場所で見つかるセキュリティ要件の対象だが, Executive Order 13985, "Advancing Racial Equity and Support for Underserved Communities Through the Federal Government" [[EO13985]](references.md#ref-EO13985) で指定されているように, 政府サービスへの公平なアクセスを提供するために, すべての加入者を確実に認証できることが必要である. 連邦政府を通じて十分なサービスを受けていないコミュニティのために」[[EO13985]](references.md#ref-EO13985).  公平性リスクを評価するにあたり, CSP はその Authentication Service によって取り扱われる全体的なユーザの Population を考慮する必要がある. 加えて, CSP はその Service を使用する際に, 共通する特性によって不公平なアクセス, 扱い, または結果にさらされる可能性がある Population 内のユーザのグループをさらに識別する. [Sec. 10](sec10_usability.md#sec10) で提供される使いさすさの考慮事項もまた Authentication Service を使用するすべての人のための全体的な使いやすさと公平性の確保のために考慮される必要がある. 

<!--
A primary aspect of equity is that the CSP needs to anticipate the needs of its subscriber population and offer authenticator options that are suitable for that population. Some examples of authenticator suitability problems are as follows:
-->

公平性の主要な aspect は, CSP がその Subscriber Population のニーズの予測と, その Population に適した Authenticator の選択肢の提供を必要とすることである. Authenticator の適合性の問題の例を以下に示す:

<!--
* SMS-based out-of-band authentication may not be usable for subscribers in rural areas where mobile phone service is not available.
* OTP devices may be difficult for subscribers with vision difficulties to read.
* Out-of-band authentication secrets sent via a voice telephone call may be difficult for subscribers with hearing difficulties to understand.
* Facial matching algorithms may less effectively match facial characteristics of subscribers of some ethnicities.
* The cost of hardware-based authenticators may be beyond the means of some subscribers.
* Accurate manual entry of memorized secrets may be difficult for subscribers with some mobility and dexterity-related physical disabilities.
* The use of certain authenticator types may be challenging for subscribers with some disabilities such as intellectual, developmental, learning, and neurocognitive difficulties.
-->

* SMS-based Out-of-band Authentication は, 携帯電話のサービスが利用できない地域では使いづらい可能性がある.
* OTP デバイスは, 視覚に難しさがある Subscriber にとって読みにくい場合がある. 
* 音声電話で送信される Out-of-band Authentication Secret は, 聞き取りに難しさがある Subscriber にとってはわかりにくい場合がある.
* Facial matching algorithm は, 一部の ethnicity の Subscriber の顔の特徴と効果的に一致しない場合がある.
* ハードウェアベースの Authenticator のコストは, 一部の Subscriber にとってはその意味を超えている場合がある.
* Memorized Secret を正確に手動で入力することは, 動作や器用さに disabilitiy がある Subscriber にとっては難しい場合がある.
* 特定の Authenticator Type の使用は, 知能, 発達, 学習, 神経認知などに disabilitiy がある Subscriber にとっては難しい場合がある.

<!--
Normative requirements have been established requiring CSPs to mitigate the problems in this area that are expected to be most common. However, it is not feasible to anticipate all potential equity problems. Potential equity problems also will vary for different applications. Accordingly, CSPs need to provide mechanisms for subscribers to report inequitable authentication requirements and to advise them on potential alternative authentication strategies.
-->

この分野の最も一般的な問題を軽減するために, CSP に要求する Normative Requirement が確立されている. しかし, すべての潜在的な公平性の問題を予測することは実現不可能である. 潜在的な公平性の問題はまたアプリケーションによって異なる. したがって, CSP は, Subscriber が不公平な Authentication Requirement を報告し, 代替となりえる認証方法について助言するためのメカニズムを提供する必要がある.

<!--
This guideline recommends the binding of additional authenticators to minimize the need for account recovery (see [Sec. 6.1.2.3](sec6_lifecycle.md#replacement)). However, a subscriber might find it difficult to purchase a second hardware-based authenticator as a backup. This inequity can be addressed by making inexpensive authenticators such as look-up secrets (see [Sec. 5.1.2](sec5_authenticators.md#lookupsecrets)) available for use in the event of a primary authenticator failure or loss.
-->

このガイドラインでは, アカウント回復の必要性を最小限に抑えるために, 追加の Authenticator を Bind することを推奨している([Sec. 6.1.2.3](sec6_lifecycle.md#replacement) を参照). しかし, Subscriber は2つ目のハードウェアベースの Authenticator をバックアップとして購入することが難しい場合がある. この不公平性には, Look-up secret ([Sec. 5.1.2](sec5_authenticators.md#lookupsecrets) を参照) などの安価な Authenticator を, Primary Authenticator の障害や紛失の場合に使用できるようにすることで取り組める. 

<!--
CSPs need to be responsive to subscribers that experience authentication challenges that cannot be solved using authenticators they currently support. This might involve supporting a new authenticator type or allowing federated authentication through a trusted service that meets the needs of the subscriber.
-->

CSP は, 現在サポートしている Authenticator を使用して解決できない Authentication の課題に遭遇した Subscriber に対応する必要がある. これには, 新しい Authenticator Type のサポートや, Subscriber のニーズを満たす信頼できるサービスを介した Federated Authentication の許可が含まれる場合がある.