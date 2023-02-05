---
layout: default.ja
title: Usability Considerations
navOrder: 10
navTitle: Usability
permalink: /sp800-63b/usability/
anchor: sec10
section: 10
---

# Usability Considerations {#sec10}

_This section is informative._

<!--
> Note: In this section, the term *users* means *claimants* or *subscribers.*
-->

本セクションでは, *ユーザー* という用語は *Claimant* ないし *Subscriber* を意味する.

<!--
[[ISO/IEC9241-11]](references.md#ref-ISOIEC9241) defines usability as the "extent to which a system, product, or service can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, their goals, and the context of use as key elements necessary for achieving effectiveness, efficiency, and satisfaction. A holistic approach that accounts for these key elements is necessary to achieve usability.
-->

[[ISO/IEC9241-11]](references.md#ref-ISO9241) は Usability を "特定の利用コンテキストにおいて, 特定のユーザーが, あるシステム, プロダクトないしはサービスを利用して, 特定の目標を, どの程度有効的, 効率的かつ満足のいくレベルで達成できるかの度合い" と定義している.
この定義はユーザー, 目標および利用コンテキストを, 有効性, 効率性および満足度の達成に必要な重要要素として捉えている.
Usability を実現するには, これらの重要要素を考慮した総合的なアプローチが必要となる.

<!--
A user's goal for accessing an information system is to perform an intended task. Authentication is the function that enables this goal. However, from the user's perspective, authentication stands between them and their intended task. Effective design and implementation of authentication makes it easy to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens.
-->

ユーザーが情報システムに Access する際の目標とは, 彼らが意図した何らかのタスクの実行にある.
Authentication とは, その目的を可能とする機能である.
しかしながらユーザー視点で見ると, Authentication は彼らと彼らの意図したタスクの間に存在するものである.
Authentication の効果的な設計および実装は, 正しいことの実行を容易にし, 誤ったことの実行を困難にし, 間違いが起こった場合のリカバリーを容易にする.

<!--
Organizations need to be cognizant of the overall implications of their stakeholders' entire digital authentication ecosystem. Users often employ multiple authenticators, each for a different RP. They then struggle to remember passwords, to recall which authenticator goes with which RP, and to carry multiple physical authentication devices. Evaluating the usability of authentication is critical, as poor usability often results in coping mechanisms and unintended workarounds that can ultimately degrade the effectiveness of security controls.
-->

組織は, ステークホルダーの Digital Authentication エコシステムへの全体的な影響を認識する必要がある.
ユーザーはしばしば複数の Authenticator をそれぞれ異なる RP に対して利用しており, パスワードを覚えるために苦闘し, どの Authenticator がどの RP 向けであったか思い出すために苦闘し, 複数の物理的な Authentication デバイスを持ち運ぶために苦闘している.
Authentication の Usability を評価することは不可欠であり, Usability が低いと最終的にセキュリティコントロールの有効性を損ねかねない対処策や意図しない回避策が生じることもしばしばである.

<!--
Integrating usability into the development process can lead to authentication solutions that are secure and usable while still addressing users' authentication needs and organizations' business goals.
-->

Usability を開発プロセスに組み込むことで, ユーザーの Authentication へのニーズと組織のビジネス目標に対応しながら, 安全で使いやすい Authentication ソリューションを実現できる.

<!--
The impact of usability across digital systems needs to be considered as part of the risk assessment when deciding on the appropriate AAL. Authenticators with a higher AAL sometimes offer better usability and should be allowed for use with lower AAL applications.
-->

適切な AAL の決定の際は, リスク評価の一環として Digital システム全体の Usability を考慮する必要がある.
より高い AAL の Authenticator のほうが Usability が良い場合もあり, より低い AAL の Authentication においてもそういった Authenticator の利用を許可すべき場合がある.

<!--
Leveraging federation for authentication can alleviate many of the usability issues, though such an approach has its own tradeoffs, as discussed in [[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}.
-->

[[SP800-63C]](../_sp800-63c/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63C"}　で述べるように, そのアプローチ自体にもトレードオプが存在するものの, Authentication のために Federation を活用すると多くの Usability の問題を軽減できる可能性もある.

<!--
This section provides general usability considerations and possible implementations, but does not recommend specific solutions. The implementations mentioned are examples to encourage innovative technological approaches to address specific usability needs. Further, usability considerations and their implementations are sensitive to many factors that prevent a one-size-fits-all solution. For example, a font size that works in the desktop computing environment may force text to scroll off of a small OTP device screen. Performing a usability evaluation on the selected authenticator is a critical component of implementation. It is important to conduct evaluations with representative users, realistic goals and tasks, and appropriate contexts of use.
-->

本セクションでは一般的な Usability 上の考慮事項と取りうる実装について述べるが, 特定のソリューションを推奨するものではない.
ここで言及する実装は, 特定の Usability ニーズに対応するための革新的技術アプローチを促すための例に過ぎない.
さらに, Usability 上の考慮事項とこれらの実装は, 1つで全てを解決する万能なソリューションを妨げるような, 多くの要因を含みがちである.
例えば, デスクトップコンピューター環境においては適切なフォントサイズでも, 小さな OTP デバイスのスクリーンで見た際は文字がはみ出してしまうかもしれない.
選択された Authenticator に対する Usability 評価の実施は, 実装上の不可欠な要素である.
評価を行う際は, 代表的なユーザー, 現実的な目標とタスク, 適切な利用コンテキストのもとで行うことが重要である.

<!--
Guidelines and considerations are described from the users' perspective.
-->

ガイドラインと考慮事項はユーザー目線で記述されている.

<!--
Accessibility differs from usability and is out of scope for this document. Section 508 [[Section508]](references.md#ref-Section508) was enacted to eliminate barriers in information technology and require federal government agencies to make their online public content accessible to people with disabilities. Refer to Section 508 law and standards for accessibility guidance.
-->

Usability とは異なり, アクセシビリティに関しては本ドキュメントのスコープ外とする.
[[Section508]](references.md#ref-Section508) は情報技術の障壁を取り除くために制定され, 連邦政府機関に対して電子および情報技術の公開コンテンツを障害を持つ人にもアクセスできるように要求している.
アクセシビリティガイドラインに関しては Section 508 の法律および標準を参照のこと.

## Usability Considerations Common to Authenticators {#usabilitycommon}

<!--
When selecting and implementing an authentication system, consider usability across the entire lifecycle of the selected authenticators (e.g., typical use and intermittent events), while being mindful of the combination of users, their goals, and context of use.
-->

Authentication システムの選択および実装の際は, 選択した Authenticator のライフサイクル全体 (e.g., 通常の使用や断続的イベント) における Usability を考慮すること.
またその際は, ユーザー, ユーザーの目標および利用コンテキストの組み合わせに注意すること.

<!--
A single authenticator type usually does not suffice for the entire user population. Therefore, whenever possible — based on AAL requirements — CSPs should support alternative authenticator types and allow users to choose based on their needs. Task immediacy, perceived cost benefit tradeoffs, and unfamiliarity with certain authenticators often impact choice. Users tend to choose options that incur the least burden or cost at that moment. For example, if a task requires immediate access to an information system, a user may prefer to create a new subscriber account and password rather than select an authenticator requiring more steps. Alternatively, users may choose a federated identity option — approved at the appropriate AAL — if they already have a subscriber account with an identity provider. Users may understand some authenticators better than others, and have different levels of trust based on their understanding and experience.
-->

通常, 単一の Authenticator Type ではユーザー母集団全体の要求を満たすには不十分である.
従って可能であれば - AAL 要件に基づき - CSP は代替の Authenticator Type をサポートすべきであり, それらをユーザーのニーズに合わせて選択させるべきである.
タスクの緊急度, 認識される費用対効果のトレードオフ, 特定の Authenticator への習熟度などが, しばしば選択に影響を及ぼすことになる.
ユーザーは, その時点で最も負担やコストの低い選択肢を選ぶ傾向がある.
例えば, タスクが情報システムへの即時 Access を必要とする場合, ユーザーはより多くのステップを必要とする Authenticator を選択するよりも, 新しい Subscriber Account と Password を作成することを選好する可能性もある.
代わりに, Identity Provider に Subscriber Account を持っている場合, ユーザーは - 適切な AAL で承認された - Federated Identity という選択肢を選ぶ可能性もある.
ユーザーはある Authenticator を他の Authenticator よりもよく理解しており, 理解と経験に基づいて異なるレベルの信頼感を持っている可能性もある.

<!--
Positive user authentication experiences are integral to the success of an organization achieving desired business outcomes. Therefore, they should strive to consider authenticators from the users' perspective. The overarching authentication usability goal is to minimize user burden and authentication friction (e.g., the number of times a user has to authenticate, the steps involved, and the amount of information they have to track). Single sign-on exemplifies one such minimization strategy.
-->

ユーザーによるポジティブな Authentication エクスペリエンスは, 望ましいビジネス上の成果を達成する組織の成功に不可欠である.
従って, 組織はユーザーの視点に立って Autheenticator を検討するよう努力すべきである.
Authentication Usability における非常に重要な目標として, ユーザーの負担と Authentication により生じる摩擦 (e.g., ユーザーが Authenticate しなければならない回数, それにかかるステップ数, 確認しなければならない情報量) の最小化が挙げられる.
Single Sign-on はそのような最小化戦略の一例である.

<!--
Usability considerations applicable to most authenticators are described below. Subsequent sections describe usability considerations specific to a particular authenticator.
-->

以下に, 大抵の Authenticator に適用可能な Usability 上の考慮事項を示す.
また, 後続のセクションは, 特定の Authenticator に特化した Usability 上の考慮時を鵜を説明するものである.

<!--
Usability considerations for typical usage of all authenticators include:
-->

すべての Authenticator の通常利用 (Typical Usage) における Usability 上の考慮事項として, 以下のようなものが挙げられる.

<!--
* Provide information on the use and maintenance of the authenticator, e.g., what to do if the authenticator is lost or stolen, and instructions for use — especially if there are different requirements for first-time use or initialization.
-->

* Authenticator の利用および保守に関する情報を提供する. e.g., Authenticator を紛失したり盗難にあった場合の対処方法, および使用手順 - 特に初回利用時または初期化時に異なる要件がある場合

<!--
* Authenticator availability should also be considered as users will need to remember to have their authenticator readily available. Consider the need for alternate authentication options to protect against loss, damage, or other negative impacts to the original authenticator.
-->

* ユーザーは自身の Authenticator をすぐ利用できるようにしておく必要があるため, Authenticator の Availability (可用性) も考慮すべきである. 紛失, 損傷, その他のオリジナルの Authenticator への悪影響から保護するため, 代替となる Authentication の選択肢の必要性も検討すること.

<!--
* Whenever possible, based on AAL requirements, users should be provided with alternate authentication options. This allows users to choose an authenticator based on their context, goals, and tasks (e.g., the frequency and immediacy of the task). Alternate authentication options also help address availability issues that may occur with a particular authenticator.
-->

* 可能な限り, AAL 要件に基づき, ユーザーに代替の Authentication の選択肢を提供するべきである. これによりユーザーは自身のコンテキスト, 目標, タスク (e.g., タスクの頻度や緊急度) に基づき Authenticator を選択することができるようになる. 代替の Authentication の選択肢は, 特定の Authenticator で発生する可能性のある Availablility (可用性) の問題に対処する際にも役に立つ.

<!--
* Characteristics of user-facing text:
  * Write user-facing text (e.g., instructions, prompts, notifications, error messages) in plain language for the intended audience. Avoid technical jargon and write for the audience's expected literacy level.
  * Consider the legibility of user-facing and user-entered text, including font style, size, color, and contrast with surrounding background. Illegible text contributes to user entry errors. To enhance legibility, consider the use of:
    * High contrast. The highest contrast is black on white.
    * Sans serif fonts for electronic displays. Serif fonts for printed materials.
    * Fonts that clearly distinguish between easily confusable characters (e.g., the capital letter "O" and the number "0").
    * A minimum font size of 12 points as long as the text fits for display on the device.
-->

* ユーザーに表示するテキストの特徴
  * ユーザーに表示するテキスト (e.g., 手順書, プロンプト, 通知, エラーメッセージ) は, 対象読者向けに平易な言葉で記述すること. 専門用語を避け, 読者に想定されるリテラシーレベルに合わせた記述にすること.
  * ユーザーに表示するテキストとユーザーが入力するテキストの読みやすさを考慮すること. これにはフォントスタイル, サイズ, 色, 周囲の背景とのコントラストなどを含む. 読みにくいテキストは, ユーザーの入力エラーの元となる. 読みやすさを向上させるため, 以下の採用を検討すること.
    * ハイコントラスト. 最大のハイコントラストは白地に黒である.
    * 電子的表示用には Sans Serif フォント. 印刷物用には Serif フォント.
    * 混同しやすい文字 (e.g., 大文字の "O" と数字の "0") を明確に区別できるフォント.
    * テキストがデバイスのディスプレイでの表示に治る限り, 最小フォントサイズは12ポイント.

<!--
* User experience during authenticator entry:
  * Offer the option to display text during entry, as masked text entry is error-prone. Once a given character is displayed long enough for the user to see, it can be hidden. Consider the device when determining masking delay time, as it takes longer to enter memorized secrets on mobile devices (e.g., tablets and smartphones) than on traditional desktop computers. Ensure masking delay durations are consistent with user needs.
  * Ensure the time allowed for text entry is adequate (i.e., the entry screen does not time out prematurely). Ensure allowed text entry times are consistent with user needs.
  * Provide clear, meaningful and actionable feedback on entry errors to reduce user confusion and frustration. Significant usability implications arise when users do not know they have entered text incorrectly.
  * Allow at least 10 entry attempts for authenticators requiring the entry of the authenticator output by the user. The longer and more complex the entry text, the greater the likelihood of user entry errors.
  * Provide clear, meaningful feedback on the number of remaining allowed attempts. For rate limiting (i.e., throttling), inform users how long they have to wait until the next attempt to reduce confusion and frustration.
-->

* Authenticator 入力中のユーザーエクスペリエンス
  * マスクされたテキスト入力はエラーを引き起こしやすいため, 入力中にテキストを表示するオプションを提供すること. 入力文字をユーザーが視認するのに十分長い間表示した後は, 非表示にしてもよい. 従来のデスクトップコンピューターよりモバイルデバイス (e.g., タブレットやスマートフォン) のほうが Memorized Secret の入力に時間がかかるので, マスキング遅延時間を決定する際はデバイスを考慮すること. マスキング遅延時間がユーザーのニーズに合致していることを保証すること.
  * テキスト入力に十分な時間が与えられている (i.e., 入力画面が途中でタイムアウトにならない) ことを保証すること. 許可されたテキスト入力時間がユーザーのニーズに合致していることを保証すること.
  * ユーザーの混乱とフラストレーションを軽減するため, 入力エラーについての明確で意味のある対応可能なフィードバックを提供すること. ユーザーがテキスト誤入力に気づかないと, ユーザビリティに重大な影響を及ぼす.
  * ユーザーに Authenticator Output を入力させるような Authenticator に関しては, 少なくとも10回の入力試行を許可すること. 入力テキストが長くふつ雑になればなるほど, ユーザーの入力エラー率も高くなる.
  * 許可された残りの試行回数について, 明確で意味のあるフィードバックを提供すること. レート制限 (i.g., スロットリング) については, 混乱とフラストレーションを軽減するため, 次に試行までどれくらい待つ必要があるのかをユーザーに知らせること.

<!--
* Minimize the impact of form-factor constraints, such as limited touch and display areas on mobile devices:
  * Larger touch areas improve usability for text entry since typing on small devices is significantly more error prone and time consuming than typing on a full-size keyboard. The smaller the onscreen keyboard, the more difficult it is to type, due to the size of the input mechanism (e.g., a finger) relative to the size of the on-screen target.
  * Follow good user interface and information design for small displays.
-->

* モバイルデバイスのタッチおよびディスプレイ領域の制限など, フォームファクターの制約による影響を最小化すること.
  * 小さなデバイス上でのタイピングはフルサイズキーボードでのタイピングと比べてはるかにエラー率が高く時間もかかるため, より大きなタッチ領域はテキスト入力の Usability を向上させる. スクリーン上のキーボードが小さいほど, 入力メカニズム (e.g., 指) のサイズとスクリーン上の対象物のサイズとの兼ね合いで, より入力が困難になる.
  * 小さなディスプレイ向けの優れたユーザーインタフェースおよび情報デザインに従うこと.

<!--
Intermittent events include events such as reauthentication, subscriber account lock-out, expiration, revocation, damage, loss, theft, and non-functional software.
-->

断続的イベント (Intermittent Events) には, Reauthentication, Subscriber Account のロックアウト, 期限切れ, 失効, 損傷, 紛失, 盗難, 機能しないソフトウェアといったイベントが含まれる.

<!--
Usability considerations for intermittent events across authenticator types include:
-->

すべての Authenticator Type における断続的イベントに関する Usability 上の考慮事項には以下のようなものが挙げられる.

<!--
* To prevent users from needing to reauthenticate due to user inactivity, prompt users in order to trigger activity just before (e.g., 2 minutes) an inactivity timeout would otherwise occur.
-->

* ユーザーが非アクティブであることが原因でユーザーが Reauthentication する必要がないように, 非アクティブタイムアウトが発生する直前 (e.g., 2分前) にアクティビティをトリガーするようユーザーに促すこと.

<!--
* Prompt users with adequate time (e.g., 1 hour) to save their work before the fixed periodic reauthentication event required regardless of user activity.
-->

* ユーザーのアクティビティに関係なく固定の定期的な Reauthentication イベントが必要な場合, その前に十分な時間 (e.g., 1時間) を設けてユーザーに作業を保存するよう促すこと.

<!--
* Clearly communicate how and where to acquire technical assistance. For example, provide users with information such as a link to an online self-service feature, chat sessions or a phone number for help desk support. Ideally, sufficient information can be provided to enable users to recover from intermittent events on their own without outside intervention.
-->

* 技術支援を受ける方法と場所を明確に伝えること. 例えば, オンラインのセルフサービス機能へのリンク, チャット Session, ヘルプデスクサポート用の電話番号などの情報をユーザーに提供すること. 理想的には, ユーザーが外部の介入なしに自身で断続的イベントからリカバリーできるよう十分な情報を提供されることが望ましい.

## Usability Considerations by Authenticator Type

<!--
In addition to the previously described general usability considerations applicable to most authenticators ([Sec. 10.1](sec10_usability.md#usabilitycommon)), the following sections describe other usability considerations specific to particular authenticator types.
-->

前述の大抵の Authenticator に適用可能な一般的な Usability 上の考慮事項 (([Sec. 10.1](sec10_usability.md#usabilitycommon))) に加え, 以下のセクションでは特定の Authenticator Type 固有の Usability 上の考慮事項について述べる.

### Memorized Secrets {#memorizedsecrets}

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Users manually input the memorized secret (commonly referred to as a password or PIN).
-->

ユーザーは手動で Memorized Secret (一般的には Password や PIN と呼ばれる) を入力する.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* Memorability of the memorized secret
  * The likelihood of recall failure increases as there are more items for users to remember. With fewer memorized secrets, users can more easily recall the specific memorized secret needed for a particular RP.
  * The memory burden is greater for a less frequently used password.
-->

* Memorized Secret の記憶可能性
  * ユーザーが覚える項目が多いほど, 思い出せずに失敗する可能性が高くなる. Memorized Secret が少ければ少ないほど, ユーザーは特定の RP のために必要な特定の Memorized Secret をより簡単に思い出すことができる.

<!--
* User experience during entry of the memorized secret
  * Support copy and paste functionality in fields for entering memorized secrets, including passphrases.
-->

* Memorized Secret 入力中のユーザーエクスペリエンス
  * Passphrase を含む Memorized Secret 入力フィールドにおいてコピーアンドペースト機能をサポートすること.

<!--
**_Intermittent Events_**
-->

**_Intermittent Events (断続的イベント)_**

<!--
Usability considerations for intermittent events include:
-->

断続的イベントにおける Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* When users create and change memorized secrets:
  * Clearly communicate information on how to create and change memorized secrets.
  * Clearly communicate memorized secret requirements, as specified in [Sec. 5.1.1](sec5_authenticators.md#memsecret).
  * Allow at least 64 characters in length to support the use of passphrases. Encourage users to make memorized secrets as lengthy as they want, using any characters they like (including spaces), thus aiding memorization.
  * Do not impose other composition rules (e.g. mixtures of different character types) on memorized secrets.
  * Do not require that memorized secrets be changed arbitrarily (e.g., periodically) unless there is a user request or evidence of authenticator compromise. (See [Sec. 5.1.1](sec5_authenticators.md#memsecret) for additional information).
-->

* ユーザーが Memorized Secret を生成・変更する際
  * Memorized Secret の生成・変更方法に関する情報を明確に伝えること.
  * Memorized Secret の要件 ([Sec. 5.1.1](sec5_authenticators.md#memsecret) 参照) を明確に伝えること.
  * Passphrase には最低でも64文字を許容すること. 記憶しやすいようユーザーが選好する文字 (スペースを含む) を使用して, 好きなだけ長い Memorized Secret を作成することを推奨すること.
  * Memorized Secret に他の構成ルール (e.g., 異なる文字種の混合) を課さないこと.
  * ユーザーの要求や Authenticator 侵害の証拠がない限り, Memorized Secret の変更を恣意的 (e.g., 定期的) に要求しないこと. (追加情報に関しては [Sec. 5.1.1](sec5_authenticators.md#memsecret) 参照)

<!--
* Provide clear, meaningful and actionable feedback when chosen passwords are rejected (e.g., when it appears on a "blocklist" of unacceptable passwords or has been used previously).
-->

* 選択した Password を拒否する場合 (e.g., 受け入れられない Password の "Blocklist" に含まれる場合や, 以前に使用されているものと同じである場合) は, 明確で意味のある対応可能なフィードバックを提供すること.

### Look-Up Secrets

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Users use the authenticator — printed or electronic — to look up the appropriate secret(s) needed to respond to a verifier's prompt. For example, a user may be asked to provide a specific subset of the numeric or character strings printed on a card in table format.
-->

ユーザーは - 印刷物または電子的な - Authenticator を使用して, Verifier のプロンプトに応答するために必要とされる適切なシークレットを見つけ出す. 例えば, ユーザーはカードに表形式で印刷された数値または文字列の特定のサブセットを提供するよう求められる場合がある.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* User experience during entry of look-up secrets.
  * Consider the prompts' complexity and size. The larger the subset of secrets a user is prompted to look up, the greater the usability implications. Both the cognitive workload and physical difficulty for entry should be taken into account when selecting the quantity and complexity of look-up secrets for authentication.
-->

* Look-up Secret 入力中のユーザーエクスペリエンス
  * プロンプトの複雑さとサイズを考慮すること. ユーザーが検索するよう求められるシークレットのサブセットが大きいほど, Usability への影響も大きくなる. Authentication のための Look-up Secret の量と複雑さを決定する際には, 認知作業負荷と入力の物理的な困難さの両方を考慮するべきである.

### Out-of-Band {#usability-oob}

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Out-of-band authentication requires users have access to a primary and secondary communication channel.
-->

Out-of-band Authentication では, ユーザーはプライマリおよびセカンダリなコミュニケーションチャネルへの Access を必要とする.

<!--
Usability considerations for typical usage:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* Notify users of the receipt of a secret on a locked device. However, if the out-of-band device is locked, authentication to the device should be required to access the secret.
-->

* ロックされているデバイスにシークレットを送信したことをユーザーに伝えること. ただし, Out-of-band Device がロックされている場合, シークレットに Access するためにデバイスへの Authenttication が要求されるべきである.

<!--
* Depending on the implementation, consider form-factor constraints as they are particularly problematic when users must enter text on mobile devices. Providing larger touch areas will improve usability for entering secrets on mobile devices.
-->

* 実装によっては, ユーザーがモバイルデバイス上でテキスト入力を行う必要がある場合に特に問題となるため, フォームファクターの制約を考慮すること. より大きなタッチ領域を提供することで, モバイルデバイス上でのシークレット入力の Usability を向上することができる.

<!--
* A better usability option is to offer features that do not require text entry on mobile devices (e.g., a single tap on the screen, or a copy feature so users can copy and paste out-of-band secrets). Providing users such features is particularly helpful when the primary and secondary channels are on the same device. For example, it is difficult for users to transfer the authentication secret on a smartphone because they must switch back and forth &mdash; potentially multiple times &mdash; between the out-of-band application and the primary channel.
-->

* さらに良い Usability のオプションは, モバイルデバイス上でテキスト入力を必要としない機能 (e.g., スクリーンを一回タップするだけだったり, Out-of-band シークレットをコピーアンドペーストできるようにコピーできるようにするなど) を提供することである. このような機能を提供すると, プライマリチャネルとセカンダリチャネルが同一デバイス上にある場合, 特に役に立つ. 例えば, スマートフォン上で - 場合によっては複数回 - Out-of-band アプリケーションとプライマリチャネルの間を行ったり来たりして Authentication Secret を移動させるのは困難である.

### Single-Factor OTP Device

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Users access the OTP generated by the single-factor OTP device. The authenticator output is typically displayed on the device and the user enters it for the verifier.
-->

ユーザーは Single-factor OTP Device で生成された OTP に Access する.
Authenticator Output は通常デバイス上に表示され, ユーザーがそれを Verifier に入力する.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* Authenticator output allows at least one minute between changes, but ideally allows users the full two minutes as specified in [Sec. 5.1.4.1](sec5_authenticators.md#sfotpa). Users need adequate time to enter the authenticator output (including looking back and forth between the single-factor OTP device and the entry screen).
-->

* Authenticator Output は切り替わるまでに少なくとも1分間の猶予があるが, 理想的には [Sec. 5.1.4.1](sec5_authenticators.md#sfotpa) にあるようにユーザーにフルで2分間の猶予を与えることが望ましい. ユーザーは Authenticator Output の入力 (Single-factor OTP Device と入力画面の間の行き来を含む) に十分な時間を必要とする.

<!--
* Depending on the implementation, the following are additional usability considerations for implementers:
  * If the single-factor OTP device supplies its output via an electronic interface (e.g, USB) this is preferable since users do not have to manually enter the authenticator output. However, if a physical input (e.g., pressing a button) is required to operate, the location of the USB ports could pose usability difficulties. For example, the USB ports of some computers are located on the back of the computer and will be difficult for users to reach.
  * Limited availability of a direct computer interface such as a USB port could pose usability difficulties. For example, the number of USB ports on laptop computers is often very limited. This may force users to unplug other USB peripherals in order to use the single-factor OTP device.
-->

* 実装によっては, 実証者向けの以下のような追加の Usability 上の考慮事項が挙げられる.
  * Single-factor OTP Device が電子的インタフェース (e.g., USB) を介して出力を提供できると, ユーザーは Authenticator Output を手動で入力する必要がないため, そのような実装が望ましい. しかしながら, 操作に物理的な入力 (e.g., ボタンを押す) が必要な場合, USB ポートの位置によっては Usability 上の問題をひきおをす可能性がある. 例えば, 一部のコンピューターの USB ポートはコンピューターの背面にあり, ユーザーがアクセスしにくい場合がある.
  * USB ポートなどの直接的コンピューターインタフェースの可用性 (Availability) に関する制約が Usability 上の問題を引き起こす可能性もある. 例えば, ラップトップコンピューターの USB ポート数はしばしば非常に限られている. これによりユーザーは Single-factor OTP Device を使用するために他の USB 周辺機器を取り外す必要があるかもしれない.

### Multi-Factor OTP Device

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Users access the OTP generated by the multi-factor OTP device through a second authentication factor. The OTP is typically displayed on the device and the user manually enters it for the verifier. The second authentication factor may be achieved through some kind of integral entry pad to enter a memorized secret, an integral biometric (e.g., fingerprint) reader, or a direct computer interface (e.g., USB port). Usability considerations for the additional factor apply as well — see [Sec. 10.2.1](sec10_usability.md#memorizedsecrets) for memorized secrets and [Sec. 10.4](sec10_usability.md#biomusability) for biometrics used in multi-factor authenticators.
-->

ユーザーは Multi-factor OTP Device で生成された OTP に Access する.
OTP は通常デバイス上に表示され, ユーザーがそれを Verifier に入力する.
2nd Authentication Factor は, Memorized Secret を入力するためのある種の一体型入力パッド, 一体型 Biometric (e.g., 指紋) リーダー, または直接的なコンピューターインタフェース (e.g., USB ポート) を介してもたらされる可能性がある.
ここでは追加の Authentication Factor に対する Usability 上の考慮事項も適用される - Multi-factor Authenticator 内で用いられる Memorized Secret に対しては [Sec. 10.2.1](sec10_usability.md#memorizedsecrets), Biometrics に対しては [Sec. 10.4](sec10_usability.md#biomusability) を参照.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* User experience during manual entry of the authenticator output.
  * For time-based OTP, provide a grace period in addition to the time during which the OTP is displayed. Users need adequate time to enter the authenticator output, including looking back and forth between the multi-factor OTP device and the entry screen.
  * Consider form-factor constraints if users must unlock the multi-factor OTP device via an integral entry pad or enter the authenticator output on mobile devices. Typing on small devices is significantly more error prone and time-consuming than typing on a traditional keyboard. The smaller the integral entry pad and onscreen keyboard, the more difficult it is to type. Providing larger touch areas improves usability for unlocking the multi-factor OTP device or entering the authenticator output on mobile devices.
  * Limited availability of a direct computer interface like a USB port could pose usability difficulties. For example, laptop computers often have a limited number of USB ports, which may force users to unplug other USB peripherals to use the multi-factor OTP device.
-->

* Authenticator Output の手入力中のユーザーエクスペリエンス
  * Time-based OTP の場合, OTP が表示されている時間にプラスして猶予時間を設けること. ユーザーは Multi-factor OTP Device と入力画面の間を行き来することを含め, ユーザーは Authenticator Output の入力に十分な時間を要する.
  * ユーザーが, 一体型入力パッドを介して Multi-factor OTP Device のロックを解除したり, Authenticator Output をモバイルデバイスに入力する必要がある場合, フォームファクターの制約を考慮すること. 小型デバイスでの入力は, 従来のキーボードでの入力よりも大幅にエラーが発生しやすく, 時間がかかるものである. 一体型入力パッドとオンスクリーンキーボードが小さければ小さいほど入力は難しくなる. より大きなタッチ領域を提供することで, Multi-factor OTP Device のロックを解除したり, モバイルデバイスに Authenticator Output を入力する際の Usability が向上する.
  * USB ポートなどの直接的コンピューターインタフェースの可用性 (Availability) に関する制約が Usability 上の問題を引き起こす可能性もある. 例えば, ラップトップコンピューターの USB ポート数はしばしば非常に限られている. これによりユーザーは Multi-factor OTP Device を使用するために他の USB 周辺機器を取り外す必要があるかもしれない.

### Single-Factor Cryptographic Software

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Users authenticate by proving possession and control of the cryptographic software key.
-->

ユーザーは Cryptographic Software Key を保持および管理していることを証明することにより Authenticate を行う.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* Give cryptographic keys appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users from having to deal with multiple similarly and ambiguously named cryptographic keys. Selecting from multiple cryptographic keys on smaller mobile devices may be particularly problematic if the names of the cryptographic keys are shortened due to reduced screen size.
-->

* ユーザーはどの Authentication タスクにどの Cryptographic Key を使用するかを認識し思い出す必要があるため, Cryptographic Key には適切でわかりやすい名前をつけること. これによりユーザーは似たような曖昧な名前の複数の Cryptographic Key を扱う必要がなくなる. 小型のモバイルデバイスで複数の Cryptographic Key から選択する場合, 画面サイズが小さくなったために Cryptographic Key の名前が短縮されていると, 特に問題になる可能性がある.

### Single-Factor Cryptographic Device

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Users authenticate by proving possession of the single-factor cryptographic device.
-->

ユーザーは Single-Factor Cryptographic Device を保持していることを証明することにより Authenticate を行う.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* Requiring a physical input (e.g., pressing a button) to operate the single-factor cryptographic device could pose usability difficulties. For example, some USB ports are located on the back of computers, making it difficult for users to reach.
-->

* Single-Factor Cryptographic Device を操作するために物理的な入力 (e.g., ボタンを押す) を必要とすると, Usability 上の問題を引き起こす可能性がある. 例えば, 一部の USB ポートはコンピューターの背面に配置されているため, ユーザーの手に届きにくい場所にある.

<!--
* Limited availability of a direct computer interface like a USB port could pose usability difficulties. For example, laptop computers often have a limited number of USB ports, which may force users to unplug other USB peripherals to use the single-factor cryptographic device.
-->

* USB ポートなどの直接的コンピューターインタフェースの可用性 (Availability) に関する制約が Usability 上の問題を引き起こす可能性もある. 例えば, ラップトップコンピューターの USB ポート数はしばしば非常に限られている. これによりユーザーは Single-Factor Cryptographic Device を使用するために他の USB 周辺機器を取り外す必要があるかもしれない.

### Multi-Factor Cryptographic Software

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
In order to authenticate, users prove possession and control of the cryptographic key stored on disk or some other "soft" media that requires activation. The activation is through the input of a second authentication factor, either a memorized secret or a biometric characteristic. Usability considerations for the additional factor apply as well — see [Sec. 10.2.1](sec10_usability.md#memorizedsecrets) for memorized secrets and [Sec. 10.4](sec10_usability.md#biomusability) for biometrics used in multi-factor authenticators.
-->

Authenticate するため, ユーザーは Activation が必要なディスクまたはその他の "ソフト" メディアに保存されている Cryptographic Key の保持および管理を証明する.
Activation は 2nd Authenticator Factor, Memorized Secret または Biometrics の特徴のいずれか, の入力により行われる.
ここでは追加の Authentication Factor に対する Usability 上の考慮事項も適用される - Multi-factor Authenticator 内で用いられる Memorized Secret に対しては [Sec. 10.2.1](sec10_usability.md#memorizedsecrets), Biometrics に対しては [Sec. 10.4](sec10_usability.md#biomusability) を参照.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* Give cryptographic keys appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users from having to deal with multiple similarly and ambiguously named cryptographic keys. Selecting from multiple cryptographic keys on smaller mobile devices may be particularly problematic if the names of the cryptographic keys areas shortened due to reduced screen size.
-->

* ユーザーはどの Authentication タスクにどの Cryptographic Key を使用するかを認識し思い出す必要があるため, Cryptographic Key には適切でわかりやすい名前をつけること. これによりユーザーは似たような曖昧な名前の複数の Cryptographic Key を扱う必要がなくなる. 小型のモバイルデバイスで複数の Cryptographic Key から選択する場合, 画面サイズが小さくなったために Cryptographic Key の名前が短縮されていると, 特に問題になる可能性がある.

### Multi-Factor Cryptographic Device

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
Users authenticate by proving possession of the multi-factor cryptographic device and control of the protected cryptographic key. The device is activated by a second authentication factor, either a memorized secret or a biometric. Usability considerations for the additional factor apply as well — see [Sec. 10.2.1](sec10_usability.md#memorizedsecrets) for memorized secrets and [Sec. 10.4](sec10_usability.md#biomusability) for biometrics used in multi-factor authenticators.
-->

ユーザーは Multi-Factor Cryptographic Device を保持していること, および保護されている Cryptographic Key を管理していることを証明することにより Authenticate を行う.
Activation は 2nd Authenticator Factor, Memorized Secret または Biometrics の特徴のいずれか, の入力により行われる.
ここでは追加の Authentication Factor に対する Usability 上の考慮事項も適用される - Multi-factor Authenticator 内で用いられる Memorized Secret に対しては [Sec. 10.2.1](sec10_usability.md#memorizedsecrets), Biometrics に対しては [Sec. 10.4](sec10_usability.md#biomusability) を参照.

<!--
Usability considerations for typical usage include:
-->

通常利用における Usability 上の考慮事項としては以下のようなものが挙げられる.

<!--
* Do not require users to keep multi-factor cryptographic devices connected following authentication. Users may forget to disconnect the multi-factor cryptographic device when they are done with it (e.g., forgetting a smartcard in the smartcard reader and walking away from the computer).
  * Users need to be informed regarding whether the multi-factor cryptographic device is required to stay connected or not.
-->

* Authentication 後に Multi-factor Cryptographic Key を接続したままにしておくことを要求しないこと. ユーザーは Multi-factor Cryptographic Key を使い終わった後も取り外すのを忘れる (e.g., スマートカードリーダーにスマートカードを入れ忘れたままコンピューターから離れてしまう) 可能性がある.
  * 接続を維持するために Multi-factor Cryptographic Device が必要かどうか, ユーザーに通知する必要がある.

<!--
* Give cryptographic keys appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users being faced with multiple similarly and ambiguously named cryptographic keys. Selecting from multiple cryptographic keys on smaller mobile devices (such as smartphones) may be particularly problematic if the names of the cryptographic keys are shortened due to reduced screen size.
-->

* ユーザーはどの Authentication タスクにどの Cryptographic Key を使用するかを認識し思い出す必要があるため, Cryptographic Key には適切でわかりやすい名前をつけること. これによりユーザーは似たような曖昧な名前の複数の Cryptographic Key を扱う必要がなくなる. 小型のモバイルデバイス (スマートフォンなど) で複数の Cryptographic Key から選択する場合, 画面サイズが小さくなったために Cryptographic Key の名前が短縮されていると, 特に問題になる可能性がある.

<!--
* Limited availability of a direct computer interface like a USB port could pose usability difficulties. For example, laptop computers often have a limited number of USB ports, which may force users to unplug other USB peripherals to use the multi-factor cryptographic device.
-->

* USB ポートなどの直接的コンピューターインタフェースの可用性 (Availability) に関する制約が Usability 上の問題を引き起こす可能性もある. 例えば, ラップトップコンピューターの USB ポート数はしばしば非常に限られている. これによりユーザーは Multi-Factor Cryptographic Device を使用するために他の USB 周辺機器を取り外す必要があるかもしれない.

## Summary of Usability Considerations

<!--
[Figure 3](sec10_usability.md#fig-3) summarizes the usability considerations for typical usage and intermittent events for each authenticator type. Many of the usability considerations for typical usage apply to most of the authenticator types, as demonstrated in the rows. The table highlights common and divergent usability characteristics across the authenticator types. Each column allows readers to easily identify the usability attributes to address for each authenticator. Depending on users' goals and context of use, certain attributes may be valued over others. Whenever possible, provide alternative authenticator types and allow users to choose between them.
-->

[Figure 3](sec10_usability.md#fig-3) は各 Authenticator Type 毎に通常利用 (Typical Usage) および断続的イベント (Intermittent Events) における Usability 上の考慮事項をまとめたものである.
表を見ても分かる通り, 通常利用における Usability 上の考慮事項の多くが, ほとんどの Authenticator Type に当てはまる.
この表は Authenticator Type 全体にわたって共通するさまざまな Usability の特徴を示している.
各カラムにより, 読者は各 Authenticator に対応するための Usability Attribute を簡単に識別することができる.
ユーザーの目標と利用コンテキストに応じて, 特定の Attribute が他の Attribute より高く評価される場合もある.
可能な限り代替の Authenticator Type を提供し, ユーザーがそれらの中から選択できるようにすることが望ましい.

<!--
Multi-factor authenticators (e.g., multi-factor OTP devices, multi-factor cryptographic software, and multi-factor cryptographic devices) also inherit their secondary factor's usability considerations. As biometrics are only allowed as an activation factor in multi-factor authentication solutions, usability considerations for biometrics are not included in [Figure 3](sec10_usability.md#fig-3) and are discussed in [Sec. 10.4](sec10_usability.md#biomusability).
-->

Multi-factor Authenticator (e.g., Multi-factor OTP Device, Multi-factor Cryptographic Software, Multi-factor Cryptographic Device) は, さらにセカンダリーファクターに関する Usability 上の考慮事項も受け継いでいる.
Biometrics は Multi-factor Authentication ソリューションの Activation Factor としてのみ許容されているため, Biometirics に関する Usability 上の考慮事項は [Figure 3](sec10_usability.md#fig-3) には含まれず, [Sec. 10.4](sec10_usability.md#biomusability) で述べられている.

[Figure 3 Usability Considerations Summary by Authenticator Type](sec10_usability.md#t3){:name="fig-3"}
{:latex-ignore="true"}

![Table showing which usability considerations apply to each authenticator type]({{site.baseurl}}/{{page.collection}}/media/use.png 'Usability Considerations Summary by Authenticator Type'){:latex-src="use.png" latex-fig="3" latex-place="p"}

~~~
\clearpage
~~~
{:latex-literal="true"}

## Biometrics Usability Considerations {#biomusability}

<!--
This section provides a high-level overview of general usability considerations for biometrics. A more detailed discussion of biometric usability can be found in *Usability & Biometrics, Ensuring Successful Biometric Systems* [[UsabilityBiometrics]](references.md#ref-use-and-bio).
-->

本セクションでは, Biometrics の一般的な Usability 上の考慮点について概説する.
Biometrics の Usability に関するより詳細な議論は *Usability & Biometrics, Ensuring Successful Biometric Systems* [[UsabilityBiometrics]](references.md#ref-use-and-bio) を参照のこと.

<!--
Although there are other biometric modalities, the following three biometric modalities are more commonly used for authentication: fingerprint, face and iris.
-->

Biometrics の様式は多様であるが, 以下で述べる3つの Biometrics 様式, 指紋, 顔, 虹彩は, その中でもより一般的に Authentication に用いられる.

<!--
**_Typical Usage_**
-->

**_Typical Usage (通常利用)_**

<!--
* For all modalities, user familiarity and practice with the device improves performance.
-->

* 全ての様式について, ユーザーがデバイスに慣れて実践することで, そのパフォーマンスは向上する.

<!--
* Device affordances (i.e., properties of a device that allow a user to perform an action), feedback, and clear instructions are critical to a user's success with the biometric device. For example, provide clear instructions on the required actions for liveness detection.
-->

* デバイスのアフォーダンス (i.e., ユーザーがアクションを実行できるようにするデバイスのプロパティ), フィードバックおよび明確な手順書は, ユーザーが Biometrics デバイスを使用して成功体験を得るのに不可欠である. 例えば, Liveness Detection に必要なアクションに関する明確な手順書を提供すること.

<!--
* Ideally, users can select the modality they are most comfortable with for their second authentication factor. The user population may be more comfortable and familiar with — and accepting of — some biometric modalities than others.
-->

* 理想的には, ユーザーが 2nd Authentication Factor として最も使いやすい様式を選択できることが望ましい. ユーザー母集団はある Biometrics 様式に他より慣れ親しんで - かつ受け入れて - いる可能性がある.

<!--
* User experience with biometrics as an activation factor.
  * Provide clear, meaningful feedback on the number of remaining allowed attempts. For example, for rate limiting (i.e., throttling), inform users of the time period they have to wait until next attempt to reduce user confusion and frustration.
-->

* Activation Factor としての Biometrics のユーザーエクスペリエンス
  * 許可された残りの試行回数について, 明確で意味のあるフィードバックを提供すること. レート制限 (i.g., スロットリング) については, 混乱とフラストレーションを軽減するため, 次に試行までどれくらい待つ必要があるのかをユーザーに知らせること.

<!--
* Fingerprint Usability Considerations:
  * Users have to remember which finger(s) they used for initial enrollment.
  * The amount of moisture on the finger(s) affects the sensor's ability for successful capture.
  * Additional factors influencing fingerprint capture quality include age, gender, and occupation (e.g., users handling chemicals or working extensively with their hands may have degraded friction ridges).
-->

* 指紋認証に関する Usability 上の考慮事項
  * ユーザーはどの指を登録したか覚えておく必要がある.
  * 指の湿気がセンサーの読取精度に影響する.
  * 指紋読取精度に影響を与えるその他の要因として, 年齢, 性別, 職業 (e.g., 化学薬品を扱ったり手を酷使する仕事についているユーザーは, 指紋が劣化している可能性がある) などが挙げられる.

<!--
* Face Usability Considerations:
  * Users have to remember whether they wore any artifacts (e.g., glasses) during enrollment because it affects facial recognition accuracy.
  * Differences in environmental lighting conditions can affect facial recognition accuracy.
  * Facial expressions affect facial recognition accuracy (e.g., smiling versus neutral expression).
  * Facial poses affect facial recognition accuracy (e.g., looking down or away from the camera).
-->

* 顔認証に関する Usability 上の考慮事項
  * 顔認識精度に影響するため, ユーザーは Enrollment 時に人工物 (e.g., メガネ) を着用していたかどうか覚えておく必要がある.
  * 環境光条件の違いが顔認識精度に影響を及ぼす可能性がある.
  * 表情 (e.g., 笑顔と無表情) は顔認識精度に影響を与える.
  * 顔のポーズ (e.g., 下を向いている, カメラから離れている) は顔認識精度に影響を与える.

<!--
* Iris Usability Considerations:
  * Wearing colored contacts may affect the iris recognition accuracy.
  * Users who have had eye surgery may need to re-enroll post-surgery.
  * Differences in environmental lighting conditions can affect iris recognition accuracy, especially for certain iris colors.
-->

* 虹彩認証に関する Usability 上の考慮事項
  * カラーコンタクトを着用すると, 虹彩認識精度に影響を与える可能性がある.
  * 目の手術を受けたユーザーは, 手術後に再度 Enrollment を行う必要があるかもしれない.
  * 環境光条件の違いが, 特に特定の虹彩の色について, 虹彩認識精度に影響を与える可能性がある.

<!--
**_Intermittent Events_**
-->

**_Intermittent Events (断続的イベント)_**

<!--
As biometrics are only permitted as a second factor for multi-factor authentication, usability considerations for intermittent events with the primary factor still apply. Intermittent events with biometrics use include, but are not limited to, the following, which may affect recognition accuracy:
-->

Biometrics は Multi-factor Authentication における 2nd ファクターとしてのみ許容されている一方, 1つめの Authentication Factor における断続的イベントに関する Usability 上の考慮事項も適用される.
Biometrics の利用に関する断続的イベントとしては, 認識精度に影響を与える以下のようなものが挙げられる. ここに挙げるものは例であり全てとは限らない.

<!--
* If users injure their enrolled finger(s), fingerprint recognition may not work. Fingerprint authentication will be difficult for users with degraded fingerprints.
* The time elapsed between the time of facial recognition for authentication and the time of the initial enrollment can affect recognition accuracy as a user's face changes naturally over time. A user's weight change may also be a factor.
* Iris recognition may not work for people who had eye surgery, unless they re-enroll.
-->

* ユーザーが登録した指を傷つけた場合, 指紋認識が不能になる可能性がある. 指紋認証 (Fingerprint Authentication) は指紋を損傷したユーザーにとっては困難であろう.
* ユーザーの顔は時間の経過とともに自然に変化するため, 最初の登録時点から Authentication のための顔認識時点までに時間が経過していると, 認識精度に影響を与える可能性がある. ユーザーの体重変化もその要因となり得る.
* 目の手術を受けたユーザーは, 手術後に再度 Enrollment を行うまで虹彩認識が不能になるかもしれない.

<!--
Across all biometric modalities, usability considerations for intermittent events include:
-->

全ての Biometrics 様式において, 断続的イベントにおける Usability 上の考慮事項として以下が挙げられる.

<!--
* An alternative authentication method must be available and functioning. In cases where biometrics do not work, allow users to use a memorized secret as an alternative second factor.
* Provisions for technical assistance:
  * Clearly communicate information on how and where to acquire technical assistance. For example, provide users information such as a link to an online self-service feature and a phone number for help desk support. Ideally, provide sufficient information to enable users to recover from intermittent events on their own without outside intervention.
  * Inform users of factors that may affect the sensitivity of the biometric sensor (e.g., cleanliness of the sensor).
-->

* 代替の Authentication 手段が利用可能かつ機能している必要がある. Biometrics が機能しない場合, ユーザーが Memorized Secret を代替の 2nd ファクターとして利用できるようにすること.
* 技術支援を提供すること.
  * 技術支援を受ける方法と場所を明確に伝えること. 例えば, オンラインのセルフサービス機能へのリンク, ヘルプデスクサポート用の電話番号などの情報をユーザーに提供すること. 理想的には, ユーザーが外部の介入なしに自身で断続的イベントからリカバリーできるよう十分な情報を提供されることが望ましい.
  * Biometric センサーの感度に影響を与える可能性のある要因 (e.g., センサーの清潔さ) をユーザーに知らせること.
