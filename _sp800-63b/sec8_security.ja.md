---
layout: default.ja
title: Threats and Security Considerations
navOrder: 8
navTitle: Security
permalink: /sp800-63b/security/
anchor: sec8
section: 8
---

# Threats and Security Considerations {#sec8}

*This section is informative.*

## Authenticator Threats

<!--
An attacker who can gain control of an authenticator will often be able to masquerade as the authenticator's owner. Threats to authenticators can be categorized based on attacks on the types of authentication factors that comprise the authenticator:
-->

Authenticator のコントロールを取得できる Attacker は, 多くの場合 Authenticator 所有者になりすますことができる.
Authenticator に対する脅威は, Authenticator を構成する Authentication Factor タイプに対する Attack に基づいて分類できる.

<!--
* *Something you know* may be disclosed to an attacker. The attacker might guess a memorized secret. Where the authenticator is a shared secret, the attacker could gain access to the CSP or verifier and obtain the secret value or perform a dictionary attack on a hash of that value. An attacker may observe the entry of a PIN or passcode, find a written record or journal entry of a PIN or passcode, or may install malicious software (e.g., a keyboard logger) to capture the secret. Additionally, an attacker may determine the secret through offline attacks on a password database maintained by the verifier.
-->

* *Something you know* には, Attacker に対する露呈のリスクがある. Attacker は Memorized Secret を推測できるかもしれない. Authenticator が Shared Secret の場合, Attacker は CSP または Verifier への Access を得てシークレット値を取得したり, シークレットのハッシュ値に対する辞書攻撃を実行するかもしれない. Attacker は PIN やパスコードの入力を監視したり, PIN やパスコードのメモ書き等を見つけたり, 悪意あるソフトウェア (e.g., キーロガー) をインストールしてシークレットを取得する可能性もある. さらに Attacker は Verifier が管理する Password データベースへのオフライン攻撃を通じてシークレットを特定するかもしれない.

<!--
* *Something you have* may be lost, damaged, stolen from the owner, or cloned by an attacker. For example, an attacker who gains access to the owner's computer might copy a software authenticator. A hardware authenticator might be stolen, tampered with, or duplicated. Out-of-band secrets may be intercepted by an attacker and used to authenticate their own session.
-->

* *Something you have* には, 紛失, 損傷, 所有者からの盗難, Attacker による複製などのリスクがある. 例えば所有者のコンピューターへの Access を得た Attacker は, Software Authenticator を複製するかもしれない. Hardware Authenticator は盗難, 改ざん, 複製されるかもしれない. Out-of-band Secret は Attacker に傍受され, Attacker 自身の Session の Authenticate に使用される可能せがある.

<!--
* *Something you are* may be replicated. For example, an attacker may obtain a copy of the subscriber's fingerprint and construct a replica.
-->

* *Something you are* には, 複製のリスクがある. 例えば, Attacker は Subscriber の指紋のコピーを取得し, レプリカを作成する可能性がある.

<!--
This document assumes that the subscriber is not colluding with an attacker who is attempting to falsely authenticate to the verifier. With this assumption in mind, the threats to the authenticators used for digital authentication are listed in [Table 3](sec8_security.md#table-3), along with some examples.
-->

本ドキュメントは, Subscriber が Verifier に対して偽って Authenticate しようとしている Attacker と共謀していないことを前提とする.
この前提の元, Digital Authentication に用いられる Authenticator に対する脅威を, いくつかの例とともに [Table 3](sec8_security.md#table-3) に示す.

[Table 3  Authenticator Threats](sec8_security.md#table-3){:name="table-3"}
{:latex-ignore="true"}

<!--
| Authenticator Threat/Attack  | Description  | Examples |
|------------------------------------|------------------|--------------|
| **Assertion Manufacture or Modification** | The attacker generates a false assertion | Compromised CSP asserts identity of a claimant who has not properly authenticated |
| | The attacker modifies an existing assertion | Compromised proxy that changes AAL of an authentication assertion |
| **Theft** | A physical authenticator is stolen by an Attacker. | A hardware cryptographic device is stolen. |
| | | An OTP device is stolen. |
| | | A look-up secret authenticator is stolen. |
| | | A cell phone is stolen. |
| **Duplication** | The subscriber's authenticator has been copied with or without their knowledge. | Passwords written on paper are disclosed.
| | | Passwords stored in an electronic file are copied. |
| | | Software PKI authenticator (private key) copied. |
| | | Look-up secret authenticator copied. |
| | | Counterfeit biometric authenticator manufactured. |
| **Eavesdropping** | The authenticator secret or authenticator output is revealed to the attacker as the subscriber is authenticating. | Memorized secrets are obtained by watching keyboard entry. |
| | | Memorized secrets or authenticator outputs are intercepted by keystroke logging software. |
| | | A PIN is captured from a PIN pad device. |
| | | A hashed password is obtained and used by an attacker for another authentication (*pass-the-hash attack*). |
| | An out-of-band secret is intercepted by the attacker by compromising the communication channel. | An out-of-band secret is transmitted via unencrypted Wi-Fi and received by the attacker. |
| **Offline Cracking** | The authenticator is exposed using analytical methods outside the authentication mechanism. | A software PKI authenticator is subjected to dictionary attack to identify the correct password to use to decrypt the private key. |
| **Side Channel Attack** | The authenticator secret is exposed using physical characteristics of the authenticator. | A key is extracted by differential power analysis on a hardware cryptographic authenticator. |
| | | A cryptographic authenticator secret is extracted by analysis of the response time of the authenticator over a number of attempts. |
| **Phishing or Pharming** | The authenticator output is captured by fooling the subscriber into thinking the attacker is a verifier or RP. | A password is revealed by subscriber to a website impersonating the verifier.
| | | A memorized secret is revealed by a bank subscriber in response to an email inquiry from a phisher pretending to represent the bank. |
| | | A memorized secret is revealed by the subscriber at a bogus verifier website reached through DNS spoofing.
| **Social Engineering** | The attacker establishes a level of trust with a subscriber in order to convince the subscriber to reveal their authenticator secret or authenticator output. | A memorized secret is revealed by the subscriber to an officemate asking for the password on behalf of the subscriber's boss. |
| | | A memorized secret is revealed by a subscriber in a telephone inquiry from an attacker masquerading as a system administrator. |
| | | An out of band secret sent via SMS is received by an attacker who has convinced the mobile operator to redirect the victim's mobile phone to the attacker. |
| **Online Guessing** | The attacker connects to the verifier online and attempts to guess a valid authenticator output in the context of that verifier. | Online dictionary attacks are used to guess memorized secrets. |
| | | Online guessing is used to guess authenticator outputs for an OTP device registered to a legitimate claimant. |
| **Endpoint Compromise** | Malicious code on the endpoint proxies remote access to a connected authenticator without the subscriber's consent. | A cryptographic authenticator connected to the endpoint is used to authenticate remote attackers. |
| | Malicious code on the endpoint causes authentication to other than the intended verifier. | Authentication is performed on behalf of an attacker rather than the subscriber.
| | | A malicious app on the endpoint reads an out-of-band secret sent via SMS and the attacker uses the secret to authenticate.
| | Malicious code on the endpoint compromises a multi-factor software cryptographic authenticator. | Malicious code proxies authentication or exports authenticator keys from the endpoint.
| **Unauthorized Binding** | An attacker is able to cause an authenticator under their control to be bound to a subscriber account. | An attacker intercepts an authenticator or provisioning key en route to the subscriber. |
{:latex-table="3" latex-caption="Authenticator Threats" latex-longtable="true"  latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}
-->

| Authenticator Threat/Attack  | Description  | Examples |
|------------------------------------|------------------|--------------|
| **Assertion Manufacture or Modification** | Attacker が偽の Assertion を生成する. | 侵害された CSP が正しく Authenticate されていない Claimant の Identity を主張する. |
| | Attacker が既存 Assertion を改ざんする. | 侵害された Proxy が Authentication Assertion の AAL を書き換える. |
| **Theft** | 物理 Authenticator が Attacker に盗まれる. | Hardware Cryptographic Device が盗まれる. |
| | | OTP Device が盗まれる. |
| | | Look-up Secret Authenticator が盗まれる. |
| | | 携帯電話が盗まれる. |
| **Duplication** | Subscriber の Authenticator が, 知覚の有無を問わずコピーされる. | 紙に書かれた Password が露呈する.
| | | 電子ファイルに保存された Password がコピーされる. |
| | | Software PKI Authenticator (Private Keye) がコピーされる. |
| | | Look-up Secret Authenticator がコピーされる. |
| | | Biometric Authenticator が偽造される. |
| **Eavesdropping** | Subscriber が Authenticate している間に, Authenticator Secret や Authenticator Output が Attacker に露呈する. | キーボード入力の監視により Memorized Secret が取得される. |
| | | Memorized Secret や Authenticator Output がキーロガーソフトウェアに傍受される. |
| | | PIN が PIN パッドデバイスから捕捉される. |
| | | ハッシュ化された Password が取得され, Attacker によって別の Authentication に利用される. (*pass-the-hash attack*). |
| | Out-of-band Secret がコミュニケーションチャネルの侵害により Attacker に傍受される. | Out-of-band Secret が暗号化されていない Wi-Fi を介して送信され, Attacker に受信される. |
| **Offline Cracking** | Authenticator が Authentication メカニズム外部の分析手段により露呈する. | Software PKI Authenticator が辞書攻撃を受け, Private Key 復号用の正しい Password が特定される. |
| **Side Channel Attack** | Authenticator の物理特性を利用して Authenticator Secret が露呈する. | Hardware Cryptographic Authenticator に対する差分電力分析により, 鍵が抽出される. |
| | | Cryptographic Authenticator Secret が, 大量の試行にわたる Authenticator レスポンスタイムの分析により抽出される. |
| **Phishing or Pharming** | Subscriber を騙して Attacker を Verifier ないし RP だと思い込ませることで, Authenticator Output が捕捉される. | Subscriber が Verifier を装う Web サイトに Password を開示してしまう. |
| | | 銀行の Subscriber が, 銀行を装う詐欺師からの電子メールでの問い合わせに応じて, Memorized Secret を開示してしまう. |
| | | Subscriber が, DNS スプーフィングによって偽の Verifier Web サイトに到達し, Memorized Secret を開示してしまう. |
| **Social Engineering** | Attacker が Subscriber と一定レベルの信頼を確立し, Subscriber に自身の Authenticator Secret や Authenticator Output を開示するよう言い聞かせる. | Subscriber が, Subscriber の上司の代理として Password を要求する同僚に, Memorized Secret を開示してしまう. |
| | | Subscriber が, システム管理者になりすました Attacker からの電話問い合わせにより, Memorized Secret を開示してしまう. |
| | | SMS で送られた Out-of-band Secret が, 被害者の携帯電話を Attacker にリダイレクトするよう言い聞かされた携帯電話会社により, Attacker に送られる. |
| **Online Guessing** | Attacker がオンラインで Verifier に接続し, Verifier のコンテキストで有効な Authenticator Output を推測する. | Memorized Secret の推測のためオンライン辞書攻撃が行われる. |
| | | 正規の Claimant に登録された OTP Device の Authenticator Output 推測のため, オンライン推測が行われる. |
| **Endpoint Compromise** | エンドポイント上の悪意あるコードが Subscriber の同意なしに接続された Authenticator への Remote Access を Proxy する. | エンドポイントに接続した Cryptographic Authenticator が Remote Attacker の Authenticate に使用される. |
| | エンドポイント上の悪意あるコードが原因となり, 意図した Verifier 以外に Authentication が行われる. | Authentication が Subscriber ではなく Attacker を代理して行われる. |
| | | エンドポイント上の悪意あるアプリが SMS で送られた Out-of-band Secret を読み取り, Attacker がそのシークレットを Authenticate に利用する. |
| | エンドポイント上の悪意あるコードが Multi-factor Software Cryptographic Authenticator を侵害する. | 悪意あるコードが Authentication やエンドポイントからの Authenticator 鍵のエクスポートを Proxy する. |
| **Unauthorized Binding** | Attacker が自身のコントロール下にある Authenticator を Subscriber Account に紐づけることができる. | Attacker が Subscriber に届く途中の Authenticator や Provisioning 鍵を横取りする. |
{:latex-table="3" latex-caption="Authenticator Threats" latex-longtable="true"  latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}

## Threat Mitigation Strategies

<!--
Related mechanisms that assist in mitigating the threats identified above are summarized in [Table 4](sec8_security.md#table-4).
-->

上記で特定された脅威を軽減するための手助けとなる関連メカニズムを [Table 4](sec8_security.md#table-4) に示す.

[Table 4 Mitigating Authenticator Threats](sec8_security.md#table-4){:name="table-4"}
{:latex-ignore="true"}

<!--
| Authenticator Threat/Attack | Threat Mitigation Mechanisms | Normative References |
|---------------------------------|----------------------------------|-------|
| **Theft** | Use multi-factor authenticators that need to be activated through a memorized secret or biometric.| [4.2.1](sec4_aal.md#aal2types), [4.3.1](sec4_aal.md#aal3types) |
| | Use a combination of authenticators that includes a memorized secret or biometric. | [4.2.1](sec4_aal.md#aal2types), [4.3.1](sec4_aal.md#aal3types) |
| **Duplication** |  Use authenticators from which it is difficult to extract and duplicate long-term authentication secrets. | [4.2.2](sec4_aal.md#aal2req), [4.3.2](sec4_aal.md#aal3req), [5.1.7.1](sec5_authenticators.md#sfcda) |
| **Eavesdropping** | Ensure the security of the endpoint, especially with respect to freedom from malware such as key loggers, prior to use. | [4.2.2](sec4_aal.md#aal2req) |
| | Avoid use of unauthenticated and unencrypted communication channels to send out-of-band authenticator secrets. | [5.1.3.1](sec5_authenticators.md#ooba) |
| | Authenticate over authenticated protected channels (e.g., observe lock icon in browser window). | [4.1.2](sec4_aal.md#aal1req), [4.2.2](sec4_aal.md#aal2req), [4.3.2](sec4_aal.md#aal3req) |
| | Use authentication protocols that are resistant to replay attacks such as *pass-the-hash*. | [5.2.8](sec5_authenticators.md#replay) |
| | Use authentication endpoints that employ trusted input and trusted display capabilities. | [5.1.6.1](sec5_authenticators.md#sfcsa), [5.1.8.1](sec5_authenticators.md#mfcsa) |
| **Offline Cracking** | Use an authenticator with a high entropy authenticator secret. | [5.1.2.1](sec5_authenticators.md#lusa), [5.1.4.1](sec5_authenticators.md#sfotpa), [5.1.5.1](sec5_authenticators.md#mfotpa), [5.1.7.1](sec5_authenticators.md#sfcda), [5.1.9.1](sec5_authenticators.md#mfcda) |
| | Store centrally verified memorized secrets in a salted, hashed form, including a keyed hash. | [5.1.1.1.2](sec5_authenticators.md#memsecretver), [5.2.7](sec5_authenticators.md#verifier-secrets) |
| **Side Channel Attack** | Use authenticator algorithms that are designed to maintain constant power consumption and timing regardless of secret values. | [4.3.2](sec4_aal.md#aal3req)
| **Phishing or Pharming** | Use authenticators that provide phishing resistance. | [5.2.5](sec5_authenticators.md#verifimpers) |
| **Social Engineering** | Avoid use of authenticators that present a risk of social engineering of third parties such as customer service agents. | [6.1.2.1](sec6_lifecycle.md#bindexisting), [6.1.2.3](sec6_lifecycle.md#replacement) |
| **Online Guessing** | Use authenticators that generate high entropy output. | [5.1.2.1](sec5_authenticators.md#lusa), [5.1.7.1](sec5_authenticators.md#sfcda), [5.1.9.1](sec5_authenticators.md#mfcda) |
| | Use an authenticator that locks up after a number of repeated failed activation attempts. | [5.2.2](sec5_authenticators.md#throttle) |
| **Endpoint Compromise** | Use hardware authenticators that require physical action by the subscriber. | [5.2.9](sec5_authenticators.md#intent) |
| | Maintain software-based keys in restricted-access storage. | [5.1.3.1](sec5_authenticators.md#ooba), [5.1.6.1](sec5_authenticators.md#sfcsa), [5.1.8.1](sec5_authenticators.md#mfcsa) |
| **Unauthorized Binding** | Use AitM-resistant protocols for provisioning of authenticators and associated keys. | [6.1](sec6_lifecycle.md#binding) |
{:latex-table="4" latex-caption="Mitigating Authenticator Threats" latex-longtable="true"  latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}
-->


| Authenticator Threat/Attack | Threat Mitigation Mechanisms | Normative References |
|---------------------------------|----------------------------------|-------|
| **Theft** | Memorized Secret や Biometric により Activate する必要のある Multi-factor Authenticator を使用する. | [4.2.1](sec4_aal.md#aal2types), [4.3.1](sec4_aal.md#aal3types) |
| | Memorized Secret や Biometrics を含む Autheticator の組み合わせを使用する. | [4.2.1](sec4_aal.md#aal2types), [4.3.1](sec4_aal.md#aal3types) |
| **Duplication** | Long-term Authentication Secret の抽出や複製が困難な Authenticator を使用する. | [4.2.2](sec4_aal.md#aal2req), [4.3.2](sec4_aal.md#aal3req), [5.1.7.1](sec5_authenticators.md#sfcda) |
| **Eavesdropping** | エンドポイントのセキュリティを保証する. 特に使用前にキーロガーなどのマルウェアに侵されていないか確認すること. | [4.2.2](sec4_aal.md#aal2req) |
| | Out-of-band Authenticator Secret の送信時, Authenticate されておらず暗号化もされていないコミュニケーションチャネルを避ける. | [5.1.3.1](sec5_authenticators.md#ooba) |
| | Authenticated Protected Channel を介して Authenticate する. (e.g., ブラウザウィンドウの鍵アイコンを視認する) | [4.1.2](sec4_aal.md#aal1req), [4.2.2](sec4_aal.md#aal2req), [4.3.2](sec4_aal.md#aal3req) |
| | *pass-the-hash* などの Replay Attack 耐性のある Authentication Protocol を使用する. | [5.2.8](sec5_authenticators.md#replay) |
| | 信頼できる入力機能と信頼できる表示機能を備えた Authentication エンドポイントを使用する. | [5.1.6.1](sec5_authenticators.md#sfcsa), [5.1.8.1](sec5_authenticators.md#mfcsa) |
| **Offline Cracking** | 高 Entropy な Authenticator Secret を持つ Authenticator を使用する. | [5.1.2.1](sec5_authenticators.md#lusa), [5.1.4.1](sec5_authenticators.md#sfotpa), [5.1.5.1](sec5_authenticators.md#mfotpa), [5.1.7.1](sec5_authenticators.md#sfcda), [5.1.9.1](sec5_authenticators.md#mfcda) |
| | 中央で検証された Memorized Secret を, 鍵付きハッシュを含む Salt 付きハッシュ形式で保存する. | [5.1.1.1.2](sec5_authenticators.md#memsecretver), [5.2.7](sec5_authenticators.md#verifier-secrets) |
| **Side Channel Attack** | シークレット値に関係なく一定の電力消費およびタイミングを維持するよう設計された Authenticator アルゴリズムを使用する. | [4.3.2](sec4_aal.md#aal3req)
| **Phishing or Pharming** | Phishing 耐性のある Authenticator を使用する. | [5.2.5](sec5_authenticators.md#verifimpers) |
| **Social Engineering** | カスタマーサービス代行業者等の 3rd-party の Social Engineering リスクをもたらす Authenticator の使用を避ける. | [6.1.2.1](sec6_lifecycle.md#bindexisting), [6.1.2.3](sec6_lifecycle.md#replacement) |
| **Online Guessing** | 高 Entropy な Output を生成する Authenticator を使用する. | [5.1.2.1](sec5_authenticators.md#lusa), [5.1.7.1](sec5_authenticators.md#sfcda), [5.1.9.1](sec5_authenticators.md#mfcda) |
| | Activation が一定回数以上連続して失敗した際にロックされるような Authenticator を使用する.  | [5.2.2](sec5_authenticators.md#throttle) |
| **Endpoint Compromise** | Subscriber の物理アクションを要求するようなハードウェア Authenticator を使用する. | [5.2.9](sec5_authenticators.md#intent) |
| | Access が制限されたストレージ内でソフトウェアベースの鍵を管理する. | [5.1.3.1](sec5_authenticators.md#ooba), [5.1.6.1](sec5_authenticators.md#sfcsa), [5.1.8.1](sec5_authenticators.md#mfcsa) |
| **Unauthorized Binding** | Authenticator および関連する鍵の Provisioning には AitM 耐性のあるプロトコルを使用する. | [6.1](sec6_lifecycle.md#binding) |
{:latex-table="4" latex-caption="Mitigating Authenticator Threats" latex-longtable="true"  latex-columns="p@0.20\textwidth,p@0.35\textwidth,p@0.35\textwidth"}

<!--
Several other strategies may be applied to mitigate the threats described in [Table 3](sec8_security.md#table-3):
-->

[Table 3](sec8_security.md#table-3) に挙げた脅威の軽減には, 他にもいくつかの戦略が適用可能である.

<!--
* *Multiple factors* make successful attacks more difficult to accomplish. If an attacker needs to both steal a cryptographic authenticator and guess a memorized secret, then the work to discover both factors may be too high.
-->

* *多要素 (Multiple factors)* により, Attack の成功はさらに困難になる. Attacker が Cryptographic Authenticator を盗んだ上で Memorized Secret を推測しなければならない場合, 両方のファクターを見つけ出すための仕事量は多すぎる可能性がある.

<!--
* *Physical security mechanisms* may be employed to protect a stolen authenticator from duplication. Physical security mechanisms can provide tamper evidence, detection, and response.
-->

* *物理セキュリティメカニズム (Physical security mechanism)* を採用し, 盗まれた Autheticator を複製から保護することも可能である. 物理セキュリティメカニズムは改ざんの証拠, 検出, 応対も可能にしうる.

<!--
* *Requiring the use of long memorized secrets* that don't appear in common dictionaries may force attackers to try every possible value.
-->

* *長い Memorized Secret の使用を要求 (Requiring the use of long memorized secrets)* する. そのようなシークレットは一般的な辞書には載っておらず, Attacker は全ての取りうる値を総当たりしなければならなくなる可能性がある.

<!--
* *System and network security controls* may be employed to prevent an attacker from gaining access to a system or installing malicious software.
-->

* *システムおよび Network セキュリティコントロール (System and network security controls)* を採用し, Attacker がシステムへの Access を得たり不正なソフトウェアをインストールすることを防ぐことも可能である.

<!--
* *Periodic training* may be performed to ensure subscribers understand when and how to report compromise — or suspicion of compromise — or otherwise recognize patterns of behavior that may signify an attacker attempting to compromise the authentication process.
-->

* *定期的なトレーニング (Periodic training)* を実施し, Subscriber がいつどのように侵害 - または侵害の疑い - を報告すべきか, いつどのように Attacker が Authentication プロセスを侵害しようとしていることを示しているかもしれない行動パターンを認識しうるかを理解できるようにすることもできる.

<!--
* *Out of band techniques* may be employed to verify proof of possession of registered devices (e.g., cell phones).
-->

* *Out-of-band なテクニック (Out of band techniques)* を採用し, 登録デバイス (e.g., 携帯電話) の保持証明を検証することもできる.

## Authenticator Recovery

<!--
The weak point in many authentication mechanisms is the process followed when a subscriber loses control of one or more authenticators and needs to replace them. In many cases, the options remaining available to authenticate the subscriber are limited, and economic concerns (e.g., cost of maintaining call centers) motivate the use of inexpensive, and often less secure, backup authentication methods. To the extent that authenticator recovery is human-assisted, there is also the risk of social engineering attacks.
-->

多くの Authentication メカニズムの弱点は, Subscriber が1つ以上の Authenticator のコントロールを失いそれらをリプレイスする必要がある際のプロセスにある.
多くの場合, Subscriber を Authenticate するために残された利用可能な手段は限られており, 経済的な懸念 (e.g., コールセンターの維持費) が安価でしばしば安全性の低いバックアップ Authentication 手法を利用するモチベーションにつながっている.
また, Authenticator リカバリーが人間の支援によるものである限り, Social Engineering Attack のリスクもつきものである.

<!--
To maintain the integrity of the authentication factors, it is essential that it not be possible to leverage an authentication involving one factor to obtain an authenticator of a different factor. For example, a memorized secret must not be usable to obtain a new list of look-up secrets.
-->

Authentication Factor の Integrity (完全性) を維持するには, あるファクターを含む Authentication を利用して別のファクターの Authenticator を取得できないようにすることが不可欠である.
例えば, Memorized Secret は Look-up Secret の新しいリストを取得するために利用可能であってはならない.

## Session Attacks

<!--
The above discussion focuses on threats to the authentication event itself, but hijacking attacks on the session following an authentication event can have similar security impacts. The session management guidelines in [Sec. 7](sec7_session.md#sec7) are essential to maintain session integrity against attacks, such as XSS. In addition, it is important to sanitize all information to be displayed [[OWASP-XSS-prevention]](references.md#ref-OWASP-XSS-prevention) to ensure that it does not contain executable content. These guidelines also recommend that session secrets be made inaccessible to mobile code in order to provide extra protection against exfiltration of session secrets.
-->

上記は Authentication イベント自体に対する脅威にフォーカスしているが, Authentication イベントに後続する Session に対する Hijacking Attack も同様のセキュリティインパクトを及ぼしうる.
[Sec. 7](sec7_session.md#sec7) の Session Management ガイドラインは, XSS などの Attack に対する Session Integrity (完全性) 維持に不可欠である.
さらに表示される情報を全てサニタイズして [[OWASP-XSS-prevention]](references.md#ref-OWASP-XSS-prevention), 実行可能なコンテンツが含まれないようにすることも重要である.
これらのガイドラインは, Session Secret の流出に対するさらなる保護策として, Mobile Code が Session Secret にアクセスできないようにすることも推奨している.

<!--
Another post-authentication threat, cross-site request forgery (CSRF), takes advantage of users' tendency to have multiple sessions active at the same time. It is important to embed and verify a session identifier into web requests to prevent the ability for a valid URL or request to be unintentionally or maliciously activated.
-->

もう一つの Authentication 後の脅威である Cross-site Request Forgery (CSRF) は, 複数の Session を同時にアクティブにするユーザーの傾向を利用する.
Session 識別子を Web リクエストに埋め込んで検証し, 有効な URL ないしリクエストが意図せずにまたは悪意を持ってアクティベートされるのを防ぐことが重要である.
