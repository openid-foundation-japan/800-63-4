---
layout: default.ja
title: Usability
navOrder: 9
navTitle: Usability
permalink: /sp800-63a/usability/
anchor: usability
section: 9
---

# Usability 考慮事項 {#usability}
{% comment %}
# Usability Considerations {#usability}
{% endcomment %}
_This section is informative._

> 備考: 本セクションでは、ユーザーは Applicant または Subscriber のことを意味する。

このセクションは、Enrollment および Identity Proofing に関連する Usability の考慮事項に対する実装者の意識を高めることを目的としている（典型的な Authenticator の使用および断続的なイベントに対する Usability の考慮事項については、[[SP800-63B]](./_sp800-63b/sec10_usability.ja.md#sec10){:latex-href="#ref-SP800-63B"}）の Sec. 10を参照。

[ISO/IEC9241-11]] (sec11_references.md#ref-ISO9241) では、 Usability を「システム、製品、またはサービスが、特定のユーザーによって、特定の使用状況において、効果、効率、満足を伴って特定の目標を達成できる度合い」と定義している。この定義では、効果、効率、満足を達成するために必要な要素として、ユーザー、目標、使用状況に着目している。 Usability の実現には、これらのキーとなる要素を考慮する全体的なアプローチが必要である。
{% comment %}
> Note: In this section, the term "users" means "applicants" or "subscribers."

This section is intended to raise implementers' awareness of the usability considerations associated with enrollment and identity proofing (for usability considerations for typical authenticator usage and intermittent events, see [[SP800-63B]](../_sp800-63b/sec10_usability.md#sec10){:latex-href="#ref-SP800-63B"} Sec. 10.

[[ISO/IEC9241-11]](sec11_references.md#ref-ISO9241) defines usability as the "extent to which a system, product, or service can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, goals, and context of use as the necessary elements for achieving effectiveness, efficiency, and satisfaction. A holistic approach considering these key elements is necessary to achieve usability.
{% endcomment %}
登録および Identity Proofing における Usability の包括的な目標は、ユーザーの負担（例：時間、フラストレーション） および Enrollment の摩擦（例：完了すべきステップの数、追跡すべき情報の量）を最小限に抑えることにより、ユーザーにとって円滑かつポジティブな登録プロセスを促進することである。この目標を達成するために、組織はまずユーザーのことをよく知らなければならない。

Enrollment および Identity Proofing のプロセスは、ユーザーと特定の CSP およびユーザーがアクセスするオンラインサービスとやりとりする前準備である。ネガティブな第一印象は、その後のやりとりに対するユーザーの認識に影響するため、組織はプロセスを通じてポジティブなユーザーエクスペリエンスを促進する必要がある。

 Usability は、断片的な方法で達成できない。Enrollment および Identity Proofing のプロセスに関する Usability 評価を実施することは非常に重要である。代表的なユーザー、現実的なゴールやタスク、および適切な使用状況で Usability 評価を実施することが重要である。Enrollment および Identity Proofing プロセスは、ユーザが正しいことを行うのは簡単で、間違ったことを行うのは困難であり、間違ったことが起こったときに回復するのが簡単であるように設計および実装されるべきである。

{% comment %}
The overarching goal of usability for enrollment and identity proofing is to promote a smooth, positive enrollment process for users by minimizing user burden (e.g., time and frustration) and enrollment friction (e.g., the number of steps to complete and amount of information to track). To achieve this goal, organizations have to first familiarize themselves with their users.

The enrollment and identity proofing process sets the stage for a user's interactions with a given CSP and the online services that the user will access; as negative first impressions can influence user perception of subsequent interactions, organizations need to promote a positive user experience throughout the process.

Usability cannot be achieved in a piecemeal manner. Performing a usability evaluation on the enrollment and identity proofing process is critical. It is important to conduct usability evaluation with representative users, realistic goals and tasks, and appropriate contexts of use. The enrollment and identity proofing process should be designed and implemented so it is easy for users to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens.
{% endcomment %}

ユーザーの視点から見ると、Enrollment および Identity Proofing の 3 つの主要なステップは、Enrollment 前の準備、 Enrollment および Proofing の Session 、および Enrollment 後のアクションである。これらのステップは 1 回の Session で行われることもあれば、各 Session の間にかなりの時間（例えば、数日または数週間）が経過することもありうる。

一般的な Usability と各ステップ固有の Usability の考慮事項については、以下のサブセクションで説明する。

ガイドラインおよび考慮事項は、ユーザーの視点から記述されている。

アクセシビリティは Usability と異なるため、このドキュメントの対象外である。[Section508]](sec11_references.ja.md#ref-Section508)は、情報技術におけるバリアーを取り除き、連邦機関が電子および情報技術の公共コンテンツを障害者が利用できるようにするために制定されたものである。アクセシビリティの指針としては、Section 508 の法律と規格を参照すること。

{% comment %}
From the user's perspective, the three main steps of enrollment and identity proofing are pre-enrollment preparation, the enrollment and proofing session, and post-enrollment actions. These steps may occur in a single session or there could be significant time elapsed between each one (e.g., days or weeks).

General and step-specific usability considerations are described in sub-sections below.

Guidelines and considerations are described from the users' perspective.

Accessibility differs from usability and is out of scope for this document. [[Section508]](sec11_references.md#ref-Section508) was enacted to eliminate barriers in information technology and require federal agencies to make their electronic and information technology public content accessible to people with disabilities. Refer to Section 508 law and standards for accessibility guidance.
{% endcomment %}

## Enrollment および Identity Proofing における一般的なユーザー考慮事項
{% comment %}
## General User Considerations During Enrollment and Identity Proofing
{% endcomment %}
このサブセクションでは、Enrollment プロセスのすべてのステップに適用される Usability に関する考慮事項を提供する。各ステップに固有の Usability に関する考慮事項は、[Sec. 9.2](sec9_usability.ja.md#sec9_2) から [Sec. 9.4](sec9_usability.ja.md#sec9_4) で詳細化されている。

* Enrollment に必要なプロセスをできるだけ明確かつ容易にし、ユーザーの不満を解消する。

* 技術的な支援を受ける方法と場所を明確に伝える。例えば、オンライン・セルフサービス機能へのリンク、チャット Session 、ヘルプデスクサポートの電話番号など、役に立つ情報を提供する。理想的には、外部からの干渉なしに、ユーザーが自分で Enrollment の準備の質問に答えられる十分な情報が提供されてるべきである。

* 誰がなぜデータを収集するのかを明確に説明すること。また、データがどのような経路をたどるのか、特にデータがどこに保存されるのかを示すこと。

{% comment %}
This sub-section provides usability considerations that are applicable across all steps of the enrollment process. Usability considerations specific to each step are detailed in Secs. [9.2](sec9_usability.md#sec9_2) to [9.4](sec9_usability.md#sec9_4).

* To avoid user frustration, streamline the process required for enrollment to make each step as clear and easy as possible.

* Clearly communicate how and where to acquire technical assistance. For example, provide helpful information such as a link to online self-service feature, chat sessions, and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to answer their own enrollment preparation questions without outside intervention.

* Clearly explain who is collecting their data and why. Also indicate the path their data will take, in particular where the data is being stored.
{% endcomment %}

* 提示されたすべての情報が利用可能であることを確認する。
  * すべてのユーザー向け資料（例：データ収集の通知や記入フォーム）について、優れた情報デザインのプラクティスに従うこと。
  * 資料は平易な言葉で書き、専門用語は避けること。適切な場合は、対象者の識字レベルに合わせて言語を調整すること。能動態かつ会話調を利用すること、理論的に主要なポイントを並べること、混乱を避けるため同義語ではなく同じ単語を一貫して使用すること、読みやすくするために必要に応じて箇条書き、数字、書式を使用すること。
  * フォントのスタイル、サイズ、色、周囲の背景とのコントラストなど、テキストの読みやすさを考慮すること。最もコントラストが高いのは白地に黒である。ユーザーの視力はそれぞれ異なるため、テキストの読みやすさは重要である。読みにくいテキストは、ユーザーの理解誤りや入力ミスの原因となる（例：記入フォームの記入時）。電子資料には Sans Serif 体のフォントを、紙資料には Serif 体のフォントを使用ること。可能な限り、混同しやすい文字（例えば、文字「O」と数字「0」）を明確に区別できないフォントは避けること。これは、特に Enrollment コードにおいて重要である。文字サイズは12ポイント以上とし、ディスプレイのサイズに合うようにする。
* 各ステップについて、代表的なユーザーによる Usability 評価を実施すること。 Usability 評価では、現実的なゴールやタスク、適切な使用状況を設定すること。

{% comment %}
* Ensure all information presented is usable.
  * Follow good information design practice for all user-facing materials (e.g., data collection notices and fillable forms).
  * Write materials in plain language and avoid technical jargon. If appropriate, tailor language to the literacy level of the intended population. Use active voice and conversational style, logically sequence main points, use the same word consistently rather than synonyms to avoid confusion, and use bullets, numbers, and formatting where appropriate to aid readability.
  * Consider text legibility, such as font style, size, color, and contrast with surrounding background. The highest contrast is black on white. Text legibility is important because users have different levels of visual acuity. Illegible text will contribute to user comprehension errors or user entry errors (e.g., when completing fillable forms). Use sans serif font styles for electronic materials and serif fonts for paper materials. When possible, avoid fonts that do not clearly distinguish between easily confusable characters (such as the letter "O" and the number "0"). This is especially important for enrollment codes. Use a minimum font size of 12 points, as long as the text fits the display.
* Perform a usability evaluation for each step with representative users. Establish realistic goals and tasks, and appropriate contexts of use for the usability evaluation.
{% endcomment %}


## Enrollment 前準備 {#sec9_2_2}
{% comment %}
## Pre-Enrollment Preparation {#sec9_2_2}
{% endcomment %}

このセクションでは、ユーザーが、難しく苛立たしい Enrollment Session を回避できるように、Enrollment 前の十分な準備を促進する効果的なアプローチについて記載する。ユーザが Enrollment Session に対して可能な限り準備できるようにすることは、Enrollment および Identity Proofing プロセスの全体的な成功と Usability にとって重要である。

このような準備は、ユーザーが、必要な情報（例：必要な文書など）を適切な時間枠のなかで使用可能な形で受け取る場合にのみ可能である。これには、どのような Identity Evidence が必要とされるかをユーザに正確に認識させることが含まれる。ユーザは IAL について何も知る必要はなく、要求される Identity Evidence が「FIAR」、「STRONG」、 「SUPERIOR」のいずれと類されるかどうかを知る必要はないが、組織は特定のシステムへのアクセスにどの IAL が要求されるかを知る必要がある。

Enrollment プロセスを進めるかどうか、および Session に何が必要かについて、ユーザが十分な情報を得た上で判断できるようにするため、ユーザに以下の情報を提供する:

* 各ステップで何を期待するかなど、プロセス全体に関する情報。
  * ユーザーの計画の参考となるように、予想される時間枠を明確に説明する。

* なぜ意味があることなのかを理解できるように、ユーザーに対して Identity Proofing の必要性および利点を説明する。

* 金額、利用可能な支払い方法、および Enrollment 費用があるかどうかについての情報。利用可能な支払方法の種類を増やすことで、ユーザーは自分の好きな支払方法を選択することができる。

{% comment %}
This section describes an effective approach to facilitate sufficient pre-enrollment preparation so users can avoid challenging, frustrating enrollment sessions. Ensuring users are as prepared as possible for their enrollment sessions is critical to the overall success and usability of the enrollment and identity proofing process.

Such preparation is only possible if users receive the necessary information (e.g., required documentation) in a usable format in an appropriate timeframe. This includes making users aware of exactly what identity evidence will be required. Users do not need to know anything about IALs or whether the identity evidence required is scored as "fair," "strong," or "superior," whereas organizations need to know what IAL is required for access to a particular system.

To ensure users are equipped to make informed decisions about whether to proceed with the enrollment process, and what will be needed for their session, provide users:

* Information about the entire process, such as what to expect in each step.
  * Clear explanations of the expected timeframes to allow users to plan accordingly.

* Explanation of the need for — and benefits of — identity proofing to allow users to understand the value proposition.

* Information on the monetary amount and acceptable forms of payment, and if there is an enrollment fee. Offering a larger variety of acceptable forms of payment allows users to choose their preferred payment operation.
{% endcomment %}

* ユーザーの Enrollment Session が対面式かリモートチャネルでの対面式か、またユーザーが選択できるかどうかについての情報。Session の許可されたオプションに関連する情報のみを提供する。
  * 対面式またはリモートチャネルでの対面式の Session に必要な、場所に関する情報について、ユーザーが希望する場所を選択できるかどうか、必要なロジスティック情報を提供する。紛失や盗難の危険性が増すため、ユーザは Identity Proofing を特定の公共の場所（銀行とスーパーマーケットの違い） に持参することを嫌がる場合があることに注意すること。
  * リモート Session の技術要件（例：インターネットアクセスの要件）に関する情報。
  * 待ち時間を最小限にするために、対面またはリモートチャネルでの対面 Identity Proofing Session の予約を設定するオプションがあること。立ち寄りが許可されている場合、予約なしでは待ち時間が長くなる可能性があることをユーザーに明確にする。
    * Enrollment Session の予約、リマインダー、および既存の予約の再スケジュール方法について、明確な指示を提供する。
    * 予約のリマインダーを提供し、ユーザーが希望する予約のリマインダー形式（郵便、ボイスメール、電子メール、テキストメッセージなど）を指定できるようにする。ユーザーは、日付、時間、場所、および必要な Identity Evidence の説明などの情報を必要とする。
* 許容される、要求される ID の証拠および属性、それぞれの部分が任意か必須か、および ID 証拠の完全なセットを提供しない場合の結果に関する情報。ユーザーは、ID 証拠の一部（出生証明書の隆起した印など）に固有の要件など、ID 証拠の具体的な組み 合わせを知る必要がある。これは、必要な ID 証拠の調達が困難になる可能性があるため、特に重要である。
  * 可能な場合は、必要な Identity Evidence の入手を容易にするためのツールを実装する。
  * 未成年者や特殊なニーズを持つ人々に対する特別な要件について、ユーザーに通知する。たとえば、Applicant Reference および／または Trusted Referee のプロセスが利用可能かどうか、 およびそれらのプロセスを使用するために必要な情報をユーザに提供する（[Sec. 5.1.9](sec5_ial.ja.md#TRs-ARs) を参照）。
  * フォームが必要な場合は:
     * Enrollment Session の事前、またはその際に記入可能なフォームを提供する。プリンターへのアクセスをユーザーに要求しない。
     * フォームが長いと、ユーザーは苛だちやすく、ミスを起こしやすいため、ユーザーがフォームに入力しなければならない情報量を最小限に抑える。可能であれば、フォームにあらかじめ情報を入力する。

{% comment %}
* Information on whether the user's enrollment session will be in-person or in-person over remote channels, and whether a user can choose. Only provide information relevant to the allowable session option(s).
  * Information on the location(s), whether a user can choose their preferred location, and necessary logistical information for in-person or in-person over remote channels session. Note that users may be reluctant to bring identity evidence to certain public places (bank versus supermarket), as it increases exposure to loss or theft.
  * Information on the technical requirements (e.g., requirements for internet access) for remote sessions.
  * An option to set an appointment for in-person or in-person over remote channels identity proofing sessions to minimize wait times. If walk-ins are allowed, make it clear to users that their wait times may be greater without an appointment.
    * Provide clear instructions for setting up an enrollment session appointment, reminders, and how to reschedule existing appointments.
    * Offer appointment reminders and allow users to specify their preferred appointment reminder format(s) (e.g., postal mail, voicemail, email, text message). Users need information such as date, time, location, and a description of required identity evidence.
* Information on the allowed and required identity evidence and attributes, whether each piece is voluntary or mandatory, and the consequences for not providing the complete set of identity evidence. Users need to know the specific combinations of identity evidence, including requirements specific to a piece of identity evidence (e.g., a raised seal on a birth certificate). This is especially important due to potential difficulties procuring the necessary identity evidence.
  * Where possible, implement tools to make it easier to obtain the necessary identity evidence.
  * Inform users of any special requirements for minors and people with unique needs. For example, provide users with the information on whether applicant reference and/or trusted referee processes are available and information necessary to use those processes (see [Sec. 5.1.9](sec5_ial.md#TRs-ARs)).
  * If forms are required:
     * Provide fillable forms before and at the enrollment session. Do not require users to have access to a printer.
     * Minimize the amount of information users must enter on a form, as users are easily frustrated and more error-prone with longer forms. Where possible, pre-populate forms.
{% endcomment %}

## Enrollment and Proofing Session
Enrollment セッションに特有の Usability の考慮事項は以下を含む: 

* Identity Proofing Session の開始時に、ユーザーに手続きをリマインドする。Enrollment 前準備の段階で説明した手順を覚えていることを期待してはいけない。Enrollment Session がEnrollment 前準備の直後に行われない場合は、Proofing と Enrollment のステップの完了に要する標準的な時間をユーザに明確に思い出させることが特に重要である。
* 対面、またはリモートチャネルを介した対面のための予約変更のオプションを提供する。
* Enrollment Session を進めるために必要な Identity Evidence (Enrollment コードを含む) をユーザーが所持していることを確認するために、許容されており、かつ必須の Identity Evidence を記載したチェックリストを提供する（該当する場合）。ユーザが完全な Identity Evidence 一式を持っていない場合、Identity Proofing Session を部分的に完了できるかどうかに関して通知する必要がある。
* どの情報が破棄されるか、どの情報が将来のフォローアップ Session のために保持されるか、将来の Session を完了するためにどのような Identity Evidence を持参する必要があるかについて、ユーザーに通知する。理想的には、ユーザ Identity Proofing Session を部分的に完了したいかどうかを選択できる。
* 過去の Identity Verification の体験がユーザーの期待値を左右することがあるものとして、Enrollment Session の結果に関するユーザーの期待値を設定すること（例：対面で運転免許証を受け取る、パスポートを郵便で受け取る）。
* Enrollment Session が無事に終了した際に、ユーザーがすぐに Authenticator を受領できるのか、対面で受領するために予約を取る必要があるのか、郵便で受け取れるのか、いつ受け取れるかを明確に示す。

{% comment %}
Usability considerations specific to the enrollment session include:

* At the start of the identity proofing session, remind users of the procedure. Do not expect them to remember the procedures described during the pre-enrollment preparation step. If the enrollment session does not immediately follow pre-enrollment preparation, it is especially important to clearly remind users of the typical timeframe to complete the proofing and enrollment phase.
* Provide rescheduling options for in-person or in-person over remote channels.
* Provide a checklist with the allowed and required identity evidence to ensure users have the requisite identity evidence to proceed with the enrollment session, including enrollment codes, if applicable. If users do not have the complete set of identity evidence, they must be informed regarding whether they can complete a partial identity proofing session.
* Notify users regarding what information will be destroyed, what, if any, information will be retained for future follow-up sessions, and what identity evidence they will need to bring to complete a future session. Ideally, users can choose whether they would like to complete a partial identity proofing session.
* Set user expectations regarding the outcome of the enrollment session as prior identity verification experiences may drive their expectations (e.g., receiving a driver's license in person, receiving a passport in the mail).
* Clearly indicate whether users will receive an authenticator immediately at the end of a successful enrollment session, if users have to schedule an appointment to pick it up in person, or if users will receive it in the mail and when they can expect to receive it.
{% endcomment %}

* Enrollment Session を通じて、どのようなデータが CSP によって保持されるかなど、Identity Proofing の際にユーザーに明示的な通知を行う必要がある（通知に関する詳細な要件については、[Sec. 5.1](sec5_ial.ja.md#genProofReqs) と [Sec. 8](sec8_privacy.ja.md#privacy-section-header) を参照）。4.2 要件 (5) に従って、CSP が Identity Proofing、Authentication、Authorization、または Attribute Assertion 以外の目的で、追加の Attribute またはその Attribute の使用についてユーザから同意を求める場合、追加の Attribute またはその使用を要求することをユーザーは希望しない、あるいはそれがユーザを不快に感じさせる可能性があることを CSP は認識すること。ユーザが追加の収集または使用に利点を感じず、余計なリスクであると受け止める場合、同意の提供やプロセスの継続を嫌がったりためらったりするかもしれない。利用者に対して、追加要件について明示的に通知すること。

{% comment %}
* During the enrollment session, there are several requirements to provide users with explicit notice at the time of identity proofing, such as what data will be retained on record by the CSP (see [Sec. 5.1](sec5_ial.md#genProofReqs) and [Sec. 8](sec8_privacy.md#privacy-section-header) for detailed requirements on notices). If CSPs seek consent from a user for additional attributes or uses of their attributes for any purpose other than identity proofing, authentication, authorization or attribute assertions, per 4.2 requirement (5), make CSPs aware that requesting additional attributes or uses may be unexpected or may make users uncomfortable. If users do not perceive benefit(s) to the additional collection or uses, but perceive extra risk, they may be unwilling or hesitant to provide consent or continue the process. Provide users with explicit notice of the additional requirements.
{% endcomment %}

* Enrollment コードが発行された場合:
    * 先立って、Enrollment コードを受け取ること、それを期待する時期、コードの有効期間、およびそれらの配達方法（例：物理的な所在地への郵便、SMS、固定電話、電子メール、または郵便の送り先住所）を事前にユーザーに通知すること。
    * Enrollment コードをユーザーに配布する際には、コードの使用方法、コードの有効期限を記載してください。[Sec. 5.1.6](sec5_ial.ja.md#EnrollCodes) で規定されているように、有効期間が短いため、特に重要である。
    * QR コードのような機械読み取り可能な光学ラベルを発行する場合 ([Sec. 5.1.6](sec5_ial.ja.md#EnrollCodes) 参照)、QR コード読み取り機能を得るための情報をユーザーに提供すること (例: 使用可能な QR コードアプリケーション)。
    * Enrollment コードの有効期限が切れたり、利用前に紛失した場合は、再度 Enrollment 手続きが必要であることを利用者に伝えること。
    * すべてのユーザーが公平に技術にアクセスし利用できるわけではないことを踏まえ、ユーザーに代替手段を提供すること。例えば、このアプローチの実現に求められる技術をユーザーが有していない可能性がある、ということを想定するということである。

{% comment %}
* If an enrollment code is issued:
    * Notify users in advance that they will receive an enrollment code, when to expect it, the length of time for which the code is valid, and how it will arrive (e.g., physical mail, SMS, landline telephone, email, or physical mailing address).
    * When an enrollment code is delivered to a user, include instructions on how to use the code, and the length of time for which the code is valid. This is especially important given the short validity timeframes specified in [Sec. 5.1.6](sec5_ial.md#EnrollCodes).
    * If issuing a machine-readable optical label, such as a QR Code (see [Sec. 5.1.6](sec5_ial.md#EnrollCodes)), provide users with information on how to obtain QR code scanning capabilities (e.g., acceptable QR code applications).
    * Inform users that they will be required to repeat the enrollment process if enrollment codes expire or are lost before use.
    * Provide users with alternative options as not all users are able to access and use technology equitably. For example, users may not have the technology needed for this approach to be feasible.
{% endcomment %}

* Enrollment Session の終了時に: 
  * Enrollment が成功した場合、ユーザーに対して、Enrollment の成功に関する確認と次のステップに関する情報（例：いつどこで Authenticator を受け取るか、いつ郵送されるか）を伝える。
  * ユーザーが完全な Identity Evidence 一式を持っていない、ユーザーが手続きの停止を選択した、または Session のタイムアウトが発生したことにより、Enrollment が部分的に完了した場合、ユーザーに次のことを連絡する: 
  	* どのような情報が破棄されるのか。
  	* 今後のフォローアップ Session のために保持される情報がある場合は、その内容。
  	* 情報が保持される期間。
  	* 将来の Session に持参する必要のある Identity Evidence について。
  * Enrollment が失敗した場合、代替の Enrollment Session タイプについて明確な指示をユーザーに提供する。例えば、リモートでの Proofing を完了できないユーザーに対して対面での Proofing を提供するといったことである。
* Enrollment Session の中でユーザーが Authenticator を受け取る場合、Authenticator の使用および保守に関する情報を提供する。例えば、情報としては、使用方法（特に、初回使用または初期化について異なる要件がある場合）、Authenticator の有効期限に関する情報、Authenticator の保護方法、Authenticator の紛失または盗難時の対処方法などを含めることができる。

{% comment %}
* At the end of the enrollment session,
  * If enrollment is successful, send users confirmation regarding the successful enrollment and information on next steps (e.g., when and where to pick up their authenticator, when it will arrive in the mail).
  * If enrollment is partially complete (due to users not having the complete set of identity evidence, users choosing to stop the process, or session timeouts), communicate to users:
  	* what information will be destroyed;
  	* what, if any, information will be retained for future follow-up sessions;
  	* how long the information will be retained; and
  	* what identity evidence they will need to bring to a future session.
  * If enrollment is unsuccessful, provide users with clear instructions for alternative enrollment session types, for example, offering in-person proofing for users that can not complete remote proofing.
* If users receive the authenticator during the enrollment session, provide users information on the use and maintenance of the authenticator. For example, information could include instructions for use (especially if there are different requirements for first-time use or initialization), information on authenticator expiration, how to protect the authenticator, and what to do if the authenticator is lost or stolen.
{% endcomment %}

* 対面および遠隔での Identity Proofing 双方について、追加の Usability の考慮事項が適用される: 
  * Enrollment Session の開始時に、オペレータまたは係員はその役割をユーザーに説明する必要がある （例：オペレータまたは係員が Enrollment Session を通じてユーザーを案内するか、静かに見守り必要な場合のみ対話するか）。
  * Enrollment Session の開始時に、ユーザーに対して、Enrollment 中に離席してはならないこと、Enrollment 中の行動が見えるようにすることを、伝える。
  * Enrollment Session を通じてバイオメトリクスを収集する場合は、収集プロセスを完了するための明確な指示をユーザーに提供する。この指示は、プロセスの直前に与えるのが最適である。生身のオペレーターからの口頭で指示、修正フィードバックを行うのが最も効果的です（例：バイオメトリックセンサーがどこにあるか、いつ開始するか、センサーとどのように対話するか、バイオメトリクスの収集がいつ完了するかをユーザーに指示する）。

{% comment %}
* For both in-person and remote identity proofing, additional usability considerations apply:
  * At the start of the enrollment session, operators or attendants need to explain their role to users (e.g., whether operators or attendants will walk users through the enrollment session or observe silently and only interact as needed).
  * At the start of the enrollment session, inform users that they must not depart during the session, and that their actions must be visible throughout the session.
  * When biometrics are collected during the enrollment session, provide users clear instructions on how to complete the collection process. The instructions are best given just prior to the process. Verbal instructions with corrective feedback from a live operator are the most effective (e.g., instruct users where the biometric sensor is, when to start, how to interact with the sensor, and when the biometric collection is completed).
{% endcomment %}

* リモート Identity Proofing はオンラインで行われるため、一般的なWeb Usability の原則に従うこと。例えば: 
  * Enrollment プロセスを通じてユーザーを案内するユーザーインターフェイスを設計する。
  * ユーザーが記憶する負荷を軽減する。
  * インターフェイスに一貫性を持たせる。
  * 連続するステップを明確に表示する。
  * スタート地点を明確にする。
  * 複数のプラットフォームやデバイスのサイズに対応したデザインを行う
  * ナビゲーションに一貫性を持たせ、見つけやすく、分かりやすくする。

{% comment %}
* Since remote identity proofing is conducted online, follow general web usability principles. For example:
  * Design the user interface to walk users through the enrollment process.
  * Reduce users' memory load.
  * Make the interface consistent.
  * Clearly label sequential steps.
  * Make the starting point clear.
  * Design to support multiple platforms and device sizes.
  * Make the navigation consistent, easy to find, and easy to follow.
{% endcomment %}


## Enrollment 後 {#sec9_2_4}
{% comment %}
## Post-Enrollment {#sec9_2_4}
{% endcomment %}

Enrollment 後とは、Enrollment 直後から、Authenticator の典型的な利用の前のステップを指す(Authenticator の典型的な利用と、断続的なイベントに対する Usability の考慮については、[[SP800-63B]](../_sp800-63b/sec1_purpose.ja.md#purpose){:latex-href="#ref-SP800-63B"}, Sec. 10. を参照。前述の通り、ユーザーはEnrollment Session の完了時に、Authenticator を受け取るために期待される配送（またはピックアップ）メカニズムについて、既に通知されている。

Enrollment 後の Usability に関する考慮事項は以下を含む: 

* Authenticator が到着するまでの待ち時間を最小限にする。待ち時間を短くすることで、情報システムやサービスに素早くアクセスできるようになる。

* Authenticator をピックアップするために、現地に行く必要があるかどうかをユーザーに知らせる。予約とリマインダに関して前述の Usability の考慮事項が適用される。

* Authenticator とともに、その使用と維持に関連する情報をユーザーに提供する。これには、特に初回使用時または初期化時に異なる要件がある場合の使用説明、Authenticator の有効期限に関する情報、Authenticator が紛失または盗難にあった場合の対処方法が含まれることがある。

{% comment %}
Post-enrollment refers to the step immediately after enrollment but prior to typical usage of an authenticator (for usability considerations for typical authenticator usage and intermittent events, see [[SP800-63B]](../_sp800-63b/sec1_purpose.md#purpose){:latex-href="#ref-SP800-63B"}, Sec. 10. As described above, users have already been informed at the end of their enrollment session regarding the expected delivery (or pick-up) mechanism by which they will receive their authenticator.

Usability considerations for post-enrollment include:

* Minimize the amount of time that users wait for their authenticator to arrive. Shorter wait times will allow users to access information systems and services more quickly.

* Inform users whether they need to go to a physical location to pick up their authenticators. The previously identified usability considerations for appointments and reminders still apply.

* Along with the authenticator, give users information relevant to the use and maintenance of the authenticator; this may include instructions for use, especially if there are different requirements for first-time use or initialization, information on authenticator expiration, and what to do if the authenticator is lost or stolen.
{% endcomment %}