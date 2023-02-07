---
layout: default.ja
title: Authenticators
navOrder: 5
navTitle: Authenticators
permalink: /sp800-63b/authenticators/
anchor: AAL_SEC5
section: 5
---

# Authenticator and Verifier Requirements {#AAL_SEC5}

_This section is normative._

<!--
This section provides the detailed requirements specific to each type of authenticator. With the exception of reauthentication requirements specified in [Sec. 4](sec4_aal.md#AAL_SEC4) and the requirement for phishing resistance at AAL3 described in [Sec. 5.2.5](sec5_authenticators.md#verifimpers), the technical requirements for each of the authenticator types are the same regardless of the AAL at which the authenticator is used.
-->

このセクションでは, 各 Authenticator タイプ固有の詳細な要件を提供する. [Sec. 4](sec4_aal.md#AAL_SEC4)で指定された Reauthentication の要件および [Sec. 5.2.5](sec5_authenticators.md#verifimpers) で説明された AAL3 での Phishing 耐性のための要件を除いて, Authenticator が使用される AAL に関係なく, 各 Authenticator タイプの技術要件は同じである.

## Requirements by Authenticator Type {#reqauthtype}

### Memorized Secrets {#memsecret}

<!--
A Memorized Secret authenticator — commonly referred to as a _password_ or, if numeric, a _PIN_ — is a secret value intended to be chosen and memorized by the user. Memorized secrets need to be of sufficient complexity and secrecy that it would be impractical for an attacker to guess or otherwise discover the correct secret value. A memorized secret is _something you know_.
{:.authenticator-image}
-->

Memorized Secret Authenticator — 一般に _Password_ または数値の場合は _PIN_ と言われる — は, ユーザによって選択され記憶されることを意図した秘密の値である. Memorized Secret は, Attacker が正しい Secret Value を推測または発見することが現実的でないように, 十分に複雑で秘匿されている必要がある. Memorized Secret は _something you know_ である.
{:.authenticator-image}

<!--
The requirements in this section apply to centrally verified memorized secrets that are used as an independent authentication factor, sent over an authenticated protected channel to the verifier of a CSP. Memorized secrets that are used locally by a multi-factor authenticator are referred to as _activation secrets_ and discussed in [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11).
-->

このセクションの要件は, Authenticated Protected Channel を介して CSP の Verifier に送信される, 独立した Authentication Factor として使用される中央で検証された Memorized Secret に適用される. Multi-Factor Authenticator によってローカルで使用される Memorized Secret は, _Activation Secret_ と呼ばれ, [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11) で議論される.

#### Memorized Secret Authenticators

<!--
Memorized secrets **SHALL** be at least 8 characters in length. Memorized secrets **SHALL** be either chosen by the subscriber or assigned randomly by the CSP.

If the CSP disallows a chosen memorized secret because it is on a blocklist of commonly used, expected, or compromised values (see [Sec. 5.1.1.2](sec5_authenticators.md#memsecretver)), the subscriber **SHALL** be required to choose a different memorized secret. No other complexity requirements for memorized secrets **SHALL** be imposed. A rationale for this is presented in [Appendix A](appA_memorized.md#appA) _Strength of Memorized Secrets_.
-->

Memorized Secret は, 長さが少なくとも8文字となる(**SHALL**). Memorized Secret は, Subscriber によって選択されるか, CSP によってランダムに割り当てられることとなる(**SHALL**). 

CSP が, 頻繁に使用される, 予期される, または侵害されている値のブロックリストにあるために, 選択された Memorized Secret を許可しない場合 ([Sec. 5.1.1.2](sec5_authenticators.md#memsecretver) を参照), Subscriber は別の Memorized Secret を選択することになる(**SHALL**). Memorized Secret に他の複雑さの要件が課されることはない(**SHALL**). この根拠は, [Appendix A](appA_memorized.md#appA) _Strength of Memorized Secrets_ に示される. 

#### Memorized Secret Verifiers {#memsecretver}

<!--
Verifiers **SHALL** require memorized secrets to be at least 8 characters in length. Verifiers **SHOULD** permit memorized secrets to be at least 64 characters in length. All printing ASCII [[RFC20]](references.md#ref-RFC20) characters as well as the space character **SHOULD** be acceptable in memorized secrets. Unicode [[ISO/ISC 10646]](references.md#ref-ISOIEC10646) characters **SHOULD** be accepted as well. Verifiers **MAY** make allowances for likely mistyping, such as removing leading and trailing whitespace characters prior to verification or allowing verification of memorized secrets with differing case for the leading character, provided memorized secrets remain at least 8 characters in length after such processing.
-->

Verifier は, 長さが少なくとも8文字の Memorized Secret を要求することとする(**SHALL**). Verifier は, Memorized Secret の長さが少なくとも64文字であることを許可する必要がある(**SHOULD**). すべての Printing ASCII 文字 [[RFC20]](references.md#ref-RFC20) と空白文字は Memorized Secret に受け入れられる必要がある(**SHOULD**). Unicode 文字 [[ISO/ISC 10646]](references.md#ref-ISOIEC10646) も同様に受け入れられる必要がある(**SHOULD**). Verifier は, Verification の前に先頭と末尾の空白文字を削除したり, 先頭の文字の大文字と小文字が異なる Memorized Secret の Verification を許可したり, 残りの文字数が8文字以上ある場合に先頭の文字の大文字・小文字が異なっていることを許したりなど, タイプミスの可能性を許容してもよい(**MAY**).

<!--
Verifiers **SHALL** verify the entire submitted memorized secret (i.e., not truncate the secret). For purposes of the above length requirements, each Unicode code point **SHALL** be counted as a single character.
-->

Verifier は, 提出された Memorized Secret 全体を検証することになる(**SHALL**)(つまり, Secret を切り詰めない). 前述の長さの要件に関して, 各 Unicode コードポイントは1文字としてカウントされることになる(**SHALL**).

<!--
If Unicode characters are accepted in memorized secrets, the verifier **SHOULD** apply the normalization process for stabilized strings using either the NFKC or NFKD normalization defined in Sec. 12.1 of *Unicode Normalization Forms* [[UAX15]](references.md#ref-UAX15). This process is applied before hashing the byte string representing the memorized secret. Subscribers choosing memorized secrets containing Unicode characters **SHOULD** be advised that some characters may be represented differently by some endpoints, which can affect their ability to authenticate successfully.
-->

 Memorized Secret でUnicode文字が受け入れられる場合, Verifier は Sec. 12.1 of *Unicode Normalization Forms* [[UAX15]](references.md#ref-UAX15) で定義された NFKC または NFKD 正規化を使用して, スタビライズされた文字列の正規化プロセスを適用する必要がある(**SHOULD**). このプロセスは, Memorized Secret を表すバイト文字列をHash する前に適用される. Unicode 文字を含む Memorized Secret を選択する Subscriber は, 一部の文字が一部のエンドポイントによって異なる方法で表現される可能性があることを通知される必要がある(**SHOULD**). これは, 正常に Authenticate する能力に影響を与える可能性がある.

<!--
Memorized secret verifiers **SHALL NOT** permit the subscriber to store a hint that is accessible to an unauthenticated claimant. Verifiers **SHALL NOT** prompt subscribers to use specific types of information (e.g., "What was the name of your first pet?", a technique known as knowledge-based authentication (KBA) or security questions) when choosing memorized secrets.
-->

 Memorized Secret の Verifier は, Subscriber に対して, 認証されていない Claimant がアクセスできるヒントを保存することを許可することはない(**SHALL NOT**). Verifier は, Memorized Secret を選択する際に, Subscriber に特定の種類の情報 (例えば, 「あなたの最初のペットの名前は何ですか?」といった Knowledge-Based Authentication (KBA) または秘密の質問として知られる手法) を使用するように促すことはない(**SHALL NOT**).

<!--
When processing requests to establish and change memorized secrets, verifiers **SHALL** compare the prospective secrets against a blocklist that contains values known to be commonly used, expected, or compromised. For example, the list **MAY** include, but is not limited to:
-->

 Memorized Secret を確立および変更するリクエストを処理するとき, Verifier は, 頻繁に使用される, 予期される, または侵害されていることが知られている値を含む Blocklist と, リクエストされた Secret を比較することになる(**SHALL**). 例えば, リストには以下を含んでもよい(**MAY**) が, これらに限定されない:

<!--
* Passwords obtained from previous breach corpuses.
* Dictionary words.
* Repetitive or sequential characters (e.g. 'aaaaaa', '1234abcd').
* Context-specific words, such as the name of the service, the username, and derivatives thereof.
-->

* 以前の侵害事例から得られた Password.
* 辞書の単語.
* 反復または連続した文字 (例: 'aaaaaa', '1234abcd').
* サービスの名前, ユーザ名, およびその派生語など, コンテキスト特有の単語.

<!--
If the chosen secret is found in the blocklist, the CSP or verifier **SHALL** advise the subscriber that they need to select a different secret, **SHALL** provide the reason for rejection, and **SHALL** require the subscriber to choose a different value. Since the blocklist is used to defend against brute-force attacks and unsuccessful attempts are rate limited as described below, the blocklist **SHOULD** be of a size sufficient to prevent subscribers from choosing memorized secrets that attackers are likely to guess before reaching the attempt limit. Excessively large blocklists **SHOULD NOT** be used because they frustrate subscribers' attempts to establish an acceptable memorized secret and do not provide significantly improved security.
-->

選択された Secret が Blocklist の中にある場合, CSP または Verifier は Subscriber に別の Secret を選択する必要があることを通知することとなり(**SHALL**), 拒否の理由を提供することになり(**SHALL**), Subscriber に別の値を選択することを要求することになる(**SHALL**). Blocklist はブルートフォース Attack を防御するために使用され, 試行の失敗は以下で説明するようにレート制限されるため, Blocklist は Subscriber が Attacker が試行リミットに到達する前に推測する可能性のある Memorized Secret を選択することを防ぐのに十分なサイズにする必要がある(**SHOULD**). 過度に大きな Blocklist は使用しないほうがよい(**SHOULD NOT**). これは, Subscriber が許容される Memorized Secret を確立しようとする試みを妨げ, 大幅に改善されたセキュリティを提供しないためである.

<!--
Verifiers **SHALL** offer guidance to the subscriber to assist the user in choosing a strong memorized secret. This is particularly important following the rejection of a memorized secret on the above list as it discourages trivial modification of listed (and likely very weak) memorized secrets [[Blocklists]](references.md#ref-blocklists).
-->

Verifierは, 強力な Memorized Secret を選択する際にユーザーを支援するために, Subscriber にガイダンスを提供することとなる(**SHALL**). これは, リストされた (そしておそらく非常に弱い) Memorized Secret への浅はかな変更を思いとどまらせるため, 上記のリストにある Memorized Secret の拒否に続いて特に重要である. [[Blocklists]](references.md#ref-blocklists)

<!--
Verifiers **SHALL** implement a rate-limiting mechanism that effectively limits the number of failed authentication attempts that can be made on the subscriber account as described in [Sec. 5.2.2](sec5_authenticators.md#throttle).
-->

Verifier は, [Sec. 5.2.2](sec5_authenticators.md#throttle) で説明されている通り, Subscriber Account で試行できる Authentication の失敗回数を効果的に制限するレート制限メカニズムを実装することとなる(**SHALL**). 

<!--
Verifiers **SHALL NOT** impose other composition rules (e.g., requiring mixtures of different character types or prohibiting consecutively repeated characters) for memorized secrets. Verifiers **SHALL NOT** require users to periodically change memorized secrets. However, verifiers **SHALL** force a change if there is evidence of compromise of the authenticator.
-->

Verifier は,  Memorized Secret に他の構成ルールを課すことはない(**SHALL NOT**) (例: 異なる文字タイプの混合の要求, 連続して繰り返される文字の禁止). Verifier は, Memorized Secret を定期的に変更することをユーザーに要求することはない(**SHALL NOT**). ただし, Authenticator の侵害の証拠がある場合, Verifier は変更を強制することとなる(**SHALL**).

<!--
Verifiers **SHALL** allow the use of password managers. To facilitate their use, verifiers **SHOULD** permit claimants to use "paste" functionality when entering a memorized secret. Password manangers may increase the likelihood that users will choose stronger memorized secrets.
-->

Verifier は, Passwordマネージャーの使用を許可することになる(**SHALL**). それらを使用しやすくするために, Verifier は, Memorized Secret を入力するときに, Claimant が「貼り付け」機能の使用を許可ことになる(**SHALL**). Passwordマネージャーは, ユーザーがより強力な Memorized Secret を選択する可能性を高める場合がある.

<!--
In order to assist the claimant in successfully entering a memorized secret, the verifier **SHOULD** offer an option to display the secret — rather than a series of dots or asterisks — while it is entered and until it is submitted to the verifier. This allows the claimant to confirm their entry if they are in a location where their screen is unlikely to be observed. The verifier **MAY** also permit the claimant's device to display individual entered characters for a short time after each character is typed to verify correct entry. This is common on mobile devices.
-->

Claimant が Memorized Secret を正常に入力することを支援するために, Verifier は, 入力されている間および 
Verifier に送信されるまで, 一連のドットやアスタリスクではなく, Secret を表示するオプションを提供する必要がある(**SHOULD**). これにより Claimant は, 自分の画面が観察される可能性が低い場所にいる場合, 自分の入力を確認できる. Verifier は, 各文字が入力された後, 正しく入力したかを確認するために入力された個々の文字を短時間表示することを Claimant のデバイスに許可してもよい(**MAY**). これは, モバイルデバイスでは一般的である.

<!--
The verifier **SHALL** use approved encryption and an authenticated protected channel when requesting memorized secrets in order to provide resistance to eavesdropping and adversary-in-the-middle attacks.
-->

Verifier は, Memorized Secret を要求するときには, 盗聴や Adversary-in-the-Middle Attack に対する耐性を提供するために, Approved な暗号による暗号化と Authenticated Protected Channel を使用することになる(**SHALL**).

<!--
Verifiers **SHALL** store memorized secrets in a form that is resistant to offline attacks. Memorized secrets **SHALL** be salted and hashed using a suitable password hashing scheme. Password hashing schemes take a password, a salt, and a cost factor as inputs and generate a password hash. Their purpose is to make each password guess more expensive for an attacker who has obtained a hashed password file and thereby make the cost of a guessing attack high or prohibitive. A function that is both memory-hard and compute-hard **SHOULD** be used because it increases the cost of an attack. While NIST has not published guidelines on specific password hashing schemes, examples of such functions include Argon2 [[Argon2]](references.md#ref-argon2) and scrypt [[Scrypt]](references.md#ref-scrypt). Examples of approved one-way functions include Keyed Hash Message Authentication Code (HMAC) [[FIPS198-1]](references.md#ref-FIPS198-1), any approved hash function in [[SP800-107]](references.md#ref-SP800-107), Secure Hash Algorithm 3 (SHA-3) [[FIPS202]](references.md#ref-FIPS202), CMAC [[SP800-38B]](references.md#ref-SP800-38B), Keccak Message Authentication Code (KMAC), Customizable SHAKE (cSHAKE), and ParallelHash [[SP800-185]](references.md#ref-SP800-185). The chosen output length of the password hashing scheme **SHOULD** be the same as the length of the underlying one-way function output.
-->

Verifier は, Memorized Secret を Offline Attack に耐性のある形式で保存することになる(**SHALL**).  Memorized Secret は, 適切な Password Hash スキームを使用して Salt および Hash されることになる(**SHALL**). Password Hash スキームは, Password, Salt, およびコストファクターを入力として受け取り, Password Hash を生成する. それらの目的は, Hash された Password ファイルを取得した Attacker に対して, 各 Password の推測をより高価なものにし, それによって推測攻撃のコストを高くしたり法外なものにしたりすることである. Attack のコストを増加させるため, Memory-Hard と Compute-Hard の両方の性質を持つ関数を使用する必要がある(**SHOULD**). NIST は特定の Password Hash スキームに関するガイドラインを公開していないが, そのような関数の例には Argon2 [[Argon2]](references.md#ref-argon2) や scrypt [[Scrypt]](references.md#ref-scrypt) などがある. 承認された一方向関数の例には, Keyed Hash Message Authentication Code (HMAC) [[FIPS198-1]](references.md#ref-FIPS198-1), [[SP800-107]](references.md#ref-SP800-107) で承認されたいずれかの Hash 関数, Secure Hash Algorithm 3 (SHA-3) [[FIPS202]](references.md#ref-FIPS202), CMAC [[SP800-38B]](references.md#ref-SP800-38B), Keccak Message Authentication Code (KMAC), Customizable SHAKE (cSHAKE), および ParallelHash [[SP800-185]](references.md#ref-SP800-185) が含まれる.  Password Hash スキームが処理した出力の長さは, 基になる一方向関数の出力の長さと同じである必要がある(**SHOULD**).

<!--
The salt **SHALL** be at least 32 bits in length and be chosen arbitrarily so as to minimize salt value collisions among stored hashes. Both the salt value and the resulting hash **SHALL** be stored for each memorized secret authenticator.
-->

Salt は長さが少なくとも 32 ビットとなり, 保存された Hash 間の Salt 値の衝突を最小限に抑えるためにばらついて選択されることとなる(**SHALL**).  Salt 値と結果の Hash の両方が, Memorized Secret Authenticator ごとに保存されることとなる(**SHALL**).

<!--
For the Password-based Key Derivation Function 2 (PBKDF2) [[SP800-132]](references.md#ref-SP800-132), the cost factor is an iteration count: the more times the PBKDF2 function is iterated, the longer it takes to compute the password hash. Therefore, the iteration count **SHOULD** be as large as verification server performance will allow, typically at least 10,000 iterations.
-->

Password-based Key Derivation Function 2 (PBKDF2) [[SP800-132]](references.md#ref-SP800-132) の場合, コストファクターは反復回数である. PBKDF2 関数が反復される回数が多いほど, Password Hash の計算に時間がかかる. したがって, 反復回数は, Verification サーバのパフォーマンスが許す限り大きくする必要がある(通常, 少なくとも10,000回の反復)(**SHOULD**). 

<!--
In addition, verifiers **SHOULD** perform an additional iteration of a keyed hashing or encryption operation using a secret key known only to the verifier. This key value, if used, **SHALL** be generated by an approved random bit generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1) and provide at least the minimum security strength specified in the latest revision of NIST SP 800-131A, *Transitioning the Use of Cryptographic Algorithms and Key Lengths* [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication). The secret key value **SHALL** be stored separately from the hashed memorized secrets (e.g., in a specialized device like a hardware security module). With this additional iteration, brute-force attacks on the hashed memorized secrets are impractical as long as the secret key value remains secret.
-->

さらに, Verifier は, Verifier のみが知っている Secret Key を使用して, 鍵付き Hash または暗号化オペレーションの追加の反復を実行する必要がある(**SHOULD**). この Key 値を使用する場合, Approved Random Bit Generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1) によって生成され, 少なくとも NIST SP 800-131A *Transitioning the Use of Cryptographic Algorithms and Key Lengths* [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティ強度を提供することとなる(この発行日時点で112ビット)(**SHALL**).  Secret Key の値は, Hash された Memorized Secret とは別に保存されることとなる(例えば, Hardware Security Moduleのような特別なデバイスに)(**SHALL**). この追加の反復により, Secret Key の値が秘密のままである限り, Hash された Memorized Secret に対するブルートフォース Attack は非現実的である.

### Look-Up Secrets {#lookupsecrets}

<!--
A look-up secret authenticator is a physical or electronic record that stores a set of secrets shared between the claimant and the CSP. The claimant uses the authenticator to look up the appropriate secrets needed to respond to a prompt from the verifier. For example, the verifier could ask a claimant to provide a specific subset of the numeric or character strings printed on a card in table format. A common application of look-up secrets is the use of one-time "recovery keys" stored by the subscriber for use in the event another authenticator is lost or malfunctions. A look-up secret is _something you have_.
{:.authenticator-image}
-->

Look-up Secret Authenticator は, Claimant と CSP の間で共有される一連の Secret を格納する物理的または電子的な記録である. Claimant は, Verifier からのプロンプトに応答するために必要な, 適切な Secret を見つけるために Authenticator を使用する. 例えば, Verifier は, 表形式でカードに印刷された数値または文字列の特定のサブセットを提供するように Claimant に尋ねることができる. Look-up Secret の一般的な用途は, 別の Authenticator が紛失されたり故障した場合に使用するために, Subscriber によって保管された1回限りの"回復キー"としての使用である. Look-up Secret は _something you have_ である.
{:.authenticator-image}

#### Look-Up Secret Authenticators {#lusa}
<!--
CSPs creating look-up secret authenticators **SHALL** use an approved random bit generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1) to generate the list of secrets and **SHALL** deliver the authenticator securely to the subscriber. Look-up secrets **SHALL** have at least 20 bits of entropy.
-->

Look-up Secret Authenticator を作成する CSP は, Approved Random Bit Generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1) を使用して Secret のリストを生成することとなり(**SHALL**), Authenticator を Subscriber に安全に配布することとなる(**SHALL**). Look-up Secret は, 少なくとも20ビットの Entropy を持つこととなる(**SHALL**).

<!--
Look-up secrets **MAY** be distributed by the CSP in person, by postal mail to the subscriber's address of record, or by online distribution. If distributed online, look-up secrets **SHALL** be distributed over a secure channel in accordance with the post-enrollment binding requirements in [Sec. 6.1.2](sec6_lifecycle.md#post-enroll-bind).
-->

Look-up Secret Authenticator は, CSP が対面で, Subscriber の Address of Record へ郵便で, またはオンラインで配布してもよい(**MAY**). オンラインで配布される場合, Look-up Secret は [Sec. 6.1.2](sec6_lifecycle.md#post-enroll-bind) にある Post-Enrollment Binding の要件に従って, セキュアなチャネルを介して配布されることとなる(**SHALL**).

<!--
If the authenticator uses look-up secrets sequentially from a list, the subscriber **MAY** dispose of used secrets, but only after a successful authentication.
-->

Authenticator がリストからシーケンシャルに Look-up Secret を使用する場合, Authentication が成功した後に限り, Subscriber は使用済みの Secret を破棄してもよい(**MAY**). 

#### Look-Up Secret Verifiers

<!--
Verifiers of look-up secrets **SHALL** prompt the claimant for the next secret from their authenticator or for a specific (e.g., numbered) secret. A given secret from an authenticator **SHALL** be used successfully only once. If the look-up secret is derived from a grid card, each cell of the grid **SHALL** be used only once.
-->

 Look-up Secret の Verifier は, Claimant に, 彼らの Authenticator からの次の Secret, または特定の (例えば, 番号が振られた) Secret を要求することとなる(**SHALL**). Authenticator から与えられた Secret は, 一度だけ成功として使用されることとなる(**SHALL**).  Look-up Secret がグリッド カードから得られたものである場合, グリッドの各セルは一度だけ使用されることとなる(**SHALL**).

<!--
Verifiers **SHALL** store look-up secrets in a form that is resistant to offline attacks. Look-up secrets having at least 112 bits of entropy **SHALL** be hashed with an approved one-way function as described in [Sec. 5.1.1.2](sec5_authenticators.md#memsecretver). Look-up secrets with fewer than 112 bits of entropy **SHALL** be salted and hashed using a suitable password hashing scheme, also described in [Sec. 5.1.1.2](sec5_authenticators.md#memsecretver). The salt value **SHALL** be at least 32 bits in length and arbitrarily chosen so as to minimize salt value collisions among stored hashes. Both the salt value and the resulting hash **SHALL** be stored for each look-up secret.
-->

Verifier は, Offline Attack に耐性のある形式で Look-up Secret を保存することとなる(**SHALL**). 少なくとも 112 ビットの Entropy を持つ Look-up Secret は, [Sec. 5.1.1.2](sec5_authenticators.md#memsecretver) で述べられた通り, Approved な一方向関数で Hash されることとなる(**SHALL**). Entropy が 112 ビット未満の Look-up Secret は, 同様に[Sec. 5.1.1.2](sec5_authenticators.md#memsecretver)で述べられた通り, Salt 化され適切な Password Hash スキームを使用して Hash されることとなる(**SHALL**). 
Salt 値は長さが少なくとも 32 ビット となり, 保存された Hash 間の Salt 値の衝突を最小限に抑えるためにばらついて選択されることとなる(**SHALL**).  Salt 値と結果の Hash の両方が,  Look-up Secret ごとに保存されることとなる(**SHALL**).

<!--
For look-up secrets that have less than 64 bits of entropy, the verifier **SHALL** implement a rate-limiting mechanism that effectively limits the number of failed authentication attempts that can be made on the subscriber account as described in [Sec. 5.2.2](sec5_authenticators.md#throttle).
-->

Entropy が 64 ビット未満の Look-up Secret の場合, Verifier は, [Sec. 5.2.2](sec5_authenticators.md#throttle) で説明されている通り, Subscriber Account で試行できる Authentication の失敗回数を効果的に制限するレート制限メカニズムを実装することとなる(**SHALL**).

<!--
The verifier **SHALL** use approved encryption and an authenticated protected channel when requesting look-up secrets in order to provide resistance to eavesdropping and AitM attacks.
-->

Verifier は, Look-up Secret を要求するときには, 盗聴や AitM Attack に対する耐性を提供するために, Approved な暗号による暗号化と Authenticated Protected Channel を使用することになる(**SHALL**).

### Out-of-Band Devices {#out-of-band}

<!--
An out-of-band authenticator is a physical device that is uniquely addressable and can communicate securely with the verifier over a distinct communications channel, referred to as the secondary channel. The device is possessed and controlled by the claimant and supports private communication over this secondary channel, separate from the primary channel for authentication. An out-of-band authenticator is _something you have_.
{:.authenticator-image}
-->

Out-of-band Authenticator は, 一意にアドレス指定が可能で, セカンダリチャネルと呼ばれる個別の通信チャネルを介して Verifier と安全に通信できる物理デバイスである. デバイスは Claimant によって所有および制御され, Authentication のためのプライマリチャネルとは別に, このセカンダリチャネルを介したプライベート通信をサポートする. Out-of-band Authenticator は _something you have_ である.
{:.authenticator-image}

<!--
Out-of-band authentiction uses a short-term secret generated by the verifier. The secret's purpose is to securely bind the authentication operation on the primary and secondary channel and establishes the claimant's control of the out-of-band device.
-->

Out-of-band Athentiction は, Verifier によって生成された短期的な Secret を使用する. Secret の目的は, プライマリとセカンダリチャネルでの Athentiction 操作を安全にバインドし, Claimant による Out-of-band デバイスの制御を確立することである.

<!--
The out-of-band authenticator can operate in one of the following ways:
-->

Out-of-band Authenticator は以下のいずれかの方法で動作できる:

<!--
- The claimant transfers a secret received by the out-of-band device via the secondary channel to the verifier using the primary channel. For example, the claimant may receive the secret (typically a 6-digit code) on their mobile device and type it into their authentication session. This method is shown in [Figure 1](sec5_authenticators.md#fig-1).
-->

- Claimant は, Out-of-band デバイスによってセカンダリチャネルを介して受信した Secret を, プライマリチャネルを使用して Verifier に転送する. 例えば, Claimant はモバイルデバイスで Secret (通常は6桁のコード) を受信し, それを Authentication Session に入力してもよい. この方法は [Figure 1](sec5_authenticators.md#fig-1) に示される.

[Figure 1. Transfer of Secret to Primary Device](sec5_authenticators.md#fig-1){:name="fig-1"}
{:latex-ignore="true"}

![Diagram showing authentication secret being transferred from out-of-band device to session being authenticated]({{site.baseurl}}/{{page.collection}}/media/OOB-example1.png 'Transfer of Secret to Primary Device'){:latex-src="OOB-example1.png" latex-fig="1" latex-place="pt"}

<!--
- The claimant transfers a secret received via the primary channel to the out-of-band device for transmission to the verifier via the secondary channel. For example, the claimant may view the secret on their authentication session and either type it into an app on their mobile device or use a technology such as a barcode or QR code to effect the transfer. This method is shown in [Figure 2](sec5_authenticators.md#fig-2).
-->

- Claimant は, セカンダリチャネルを介して Verifier に送信するために, プライマリチャネルを介して受信した Secret を Out-of-band デバイスに転送する. 例えば, Claimant は Authentication Session 上で Secret を表示し, モバイルデバイスのアプリにそれを入力するか, バーコードやQRコードなどのテクノロジーを使用して転送を行ってもよい. この方法は [Figure 2](sec5_authenticators.md#fig-2) に示される.

[Figure 2. Transfer of Secret to Out-of-band Device](sec5_authenticators.md#fig-2){:name="fig-2"}
{:latex-ignore="true"}

![Diagram showing authentication secret being transferred from session being authenticated to out-of-band device]({{site.baseurl}}/{{page.collection}}/media/OOB-example2.png 'Transfer of Secret to Out-of-band Device'){:latex-src="OOB-example2.png" latex-fig="2" latex-place="pb"}

<!--
> Note: A third method of out-of-band authentication involving the comparison of secrets received from the primary and secondary channels and approving on the secondary channel is no longer considered acceptable because it was rarely implemented as described. It raised the likelihood that the claimant would just approve without actually comparing the secrets. For example, an authenticator that receives a push notification from the verifier and simply asks the claimant to approve the transaction (even if providing some additional information about the authentication) does not meet the requirements of this section.
-->

> 注: 三番目の方法であった, プライマリとセカンダリチャネルから受信した Secret の比較とセカンダリチャネルでの承認による Out-of-band Authentication は, 説明された通りに実装されることは稀であったため, もはや受け入れられないと見なされる. これは Claimant が Secret を実際に比較せず単に承認する可能性を高くしていた. 例えば, Verifier からプッシュ通知を受け取り, 単に Claimant に Transaction の承認を求めるだけの Authenticator は (たとえ Authentication に関する追加情報を提供したとしても), このセクションの要件を満たさない.

#### Out-of-Band Authenticators {#ooba}
<!--
The out-of-band authenticator **SHALL** establish a separate channel with the verifier in order to retrieve the out-of-band secret or authentication request. This channel is considered to be out-of-band with respect to the primary communication channel (even if it terminates on the same device) provided the device does not leak information from one channel to the other without the authorization of the claimant.
-->

Out-of-band Authenticator は, Out-of-band Secret または Authentication 要求を取得するために, Verifier と別のチャネルを確立することとなる(**SHALL**). このチャネルは, デバイスが Claimant の許可なしにひとつのチャネルから別のチャネルに情報を漏らさないという条件であれば, (たとえ同じデバイス上で完了する場合でも) プライマリ通信チャネルに関して Out-of-band であると見なされる.

<!--
The out-of-band device **SHOULD** be uniquely addressable by the verifier. Communication over the secondary channel **SHALL** be encrypted unless sent via the public switched telephone network (PSTN). For additional authenticator requirements specific to use of the PSTN for out-of-band authentication, see [Sec. 5.1.3.3](sec5_authenticators.md#pstnOOB). Channels or addresses that do not prove possession of a specific device, such as voice-over-IP (VOIP) telephone numbers, **SHALL NOT** be used for out-of-band authentication.
-->

Out-of-band デバイスは, Verifier によって一意にアドレス指定が可能である必要がある(**SHOULD**). セカンダリチャネルを介した通信は, 公衆交換電話網 (Public Switched Telephone Network, PSTN) 経由で送信されない限り, 暗号化されることとなる(**SHALL**). Out-of-band Authentication のために PSTN を使用する場合の追加の Authenticator 要件については, [Sec. 5.1.3.3](sec5_authenticators.md#pstnOOB) を参照のこと. Voice-Over-IP (VOIP) 電話番号など, 特定のデバイスの所有を証明しないチャネルまたはアドレスは, Out-of-band Authentication に使用されることはない(**SHALL NOT**).

<!--
Email **SHALL NOT** be used for out-of-band authentication because it also does not prove possession of a specific device and is typically accessed using only a memorized secret.
-->

電子メールは特定のデバイスの所有を証明するものではなく, 通常は Memorized Secret のみを使用してアクセスされるため, Out-of-band Authentication に使用されることはない(**SHALL NOT**).

<!--
The out-of-band authenticator **SHALL** uniquely authenticate itself in one of the following ways when communicating with the verifier:
-->

Out-of-band Authenticator は, Verifier と通信するときに, 以下のいずれかの方法で自身を一意に Authentication することとなる(**SHALL**). 

<!--
- Establish an authenticated protected channel to the verifier using approved cryptography. The key used **SHALL** be stored in suitably secure storage available to the authenticator application (e.g., keychain storage, TPM, TEE, secure element).
-->

- Approved Cryptography を使用して, Verifier への Authenticated Protected Channel を確立する. 使用されるキーは, Authenticator アプリケーションが利用可能な, 適切に安全なストレージ (例: キーチェーンストレージ, TPM, TEE, セキュアエレメントなど) に格納することとなる(**SHALL**). 

<!--
- Authenticate to a public mobile telephone network using a SIM card or equivalent that uniquely identifies the device. This method **SHALL** only be used if a secret is being sent from the verifier to the out-of-band device via the PSTN (SMS or voice).
-->

- デバイスを一意に識別する SIM カードまたは同等のものを使用して, 公衆携帯電話ネットワークに対して Authentication する. このメソッドは, Secret が Verifier から PSTN (SMS または音声) 経由で Out-of-band デバイスに送信される場合にのみ使用されることとなる(**SHALL**).

<!--
If a secret is sent by the verifier to the out-of-band device, the device **SHOULD NOT** display the authentication secret while it is locked by the owner (i.e., **SHOULD** require the presentation and verification of a PIN, passcode, or biometric characteristic to view). However, authenticators **SHOULD** indicate the receipt of an authentication secret on a locked device.
-->

Verifier によって Out-of-band デバイスに Secret が送信される場合, デバイスは, 所有者によってロックされている間, Authentication Secret を表示しないほうがよい(**SHOULD NOT**)(つまり, 表示のために PIN, パスコード, または Biometric Characteristic の提示と Verification を要求する必要がある(**SHOULD**). ただし, Authenticator は, ロックされたデバイス上で Authentication Secret の受信を示す必要がある(**SHOULD**).

<!--
If the out-of-band authenticator requests approval over the secondary communication channel — rather than by the presenting a secret that the claimant transfers to the primary communication channel — it **SHALL** accept transfer of the secret from the primary channel and send it to the verifier over the secondary channel to associate the approval with the authentication transaction. The claimant **MAY** perform the transfer manually or use a technology such as a barcode or QR code to effect the transfer.
-->

Out-of-band Authenticator が, (Claimant がプライマリ通信チャネルに転送する Secret を提示するのではなく) セカンダリ通信チャネルで承認を要求する場合, プライマリチャネルからの Secret の転送を受け入れることとなり(**SHALL**), 承認を Authentication Transaction に関連付けるために, それをセカンダリチャネルを介して Verifier に送信することとなる. Claimant は, 転送を手動で行うか, バーコードやQRコードなどのテクノロジーを使用して転送を行ってもよい(**MAY**).

#### Out-of-Band Verifiers

<!--
For additional verification requirements specific to the PSTN, see [Sec. 5.1.3.3](sec5_authenticators.md#pstnOOB).
-->

PSTN に固有の追加の Verification 要件については, [Sec. 5.1.3.3](sec5_authenticators.md#pstnOOB) を参照のこと.

<!--
When the out-of-band authenticator is a secure application, such as on a smart phone, the verifier **MAY** send a push notification to that device. The verifier waits for the establishment of an authenticated protected channel with the out-of-band authenticator and verifies its identifying key. The verifier **SHALL NOT** store the identifying key itself, but **SHALL** use a verification method (e.g., an approved hash function or proof of possession of the identifying key) to uniquely identify the authenticator. Once authenticated, the verifier transmits the authentication secret to the authenticator.
-->

Out-of-band Authenticator がスマートフォン上などの安全なアプリケーションである場合, Verifier はそのデバイスにプッシュ通知を送信してもよい(**MAY**).  Verifier は, Out-of-band Authenticator との Authenticated Protected Channel の確立を待ち, その識別キーを Verifiy する. Verifier は識別キー自体を保管することはない(**SHALL NOT**)が, Verification 方法 (例えば, Approved なハッシュ関数または識別キーの所有の証明) を使用して, Authenticator を一意に識別することとなる(**SHALL**). ひとたび Authenticate されると, Verifier は Authentication Secret を Authenticator に送信する.

<!--
Depending on the type of out-of-band authenticator, one of the following **SHALL** take place:
-->

Out-of-band Authenticator のタイプに応じて, 以下のいずれかが行われることとなる(**SHALL**):

<!--
* Transfer of secret from the secondary to the primary channel: The verifier **MAY** signal the device containing the subscriber's authenticator to indicate readiness to authenticate. It **SHALL** then transmit a random secret to the out-of-band authenticator. The verifier **SHALL** then wait for the secret to be returned on the primary communication channel.
-->

* セカンダリからプライマリチャネルへの Secret の転送: Verifier は, Authentication の準備ができていることを示すために, Subscriber の Authenticator を含むデバイスにシグナルを送ってもよい(**MAY**). そして, Random Secret を Out-of-band Authenticator に送信することとなる(**SHALL**). 続いて, Verifier は, プライマリ通信チャネル上で Secret が返却されるのを待つこととなる(**SHALL**).

<!--
* Transfer of secret from the primary to the secondary channel: The verifier **SHALL** display a random authentication secret to the claimant via the primary channel. It **SHALL** then wait for the secret to be returned on the secondary channel from the claimant's out-of-band authenticator.
-->

* プライマリからセカンダリチャネルへの Secret の転送: Verifier は, プライマリチャネルを介して Claimant に Random Authentication Secret を表示することとなる(**SHALL**). そして,  Claimant の Out-of-band Authenticator からセカンダリチャネル上で Secret が返却されるのを待つこととなる(**SHALL**).

<!--
In all cases, the authentication **SHALL** be considered invalid if not completed within 10 minutes. In order to provide replay resistance as described in [Sec. 5.2.8](sec5_authenticators.md#replay), verifiers **SHALL** accept a given authentication secret only once during the validity period.
-->

すべてのケースで, 10分以内に完了しない場合, Authentication は無効と見なされることとなる(**SHALL**). [Sec. 5.2.8](sec5_authenticators.md#replay)で述べられた通りに Replay Resistance を提供するため, Verifier は, 与えられた Authentication Secret の受け入れを有効期間中に一度のみとすることとなる(**SHALL**). 

<!--
The verifier **SHALL** generate random authentication secrets with at least 20 bits of entropy using an approved random bit generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1). If the authentication secret has less than 64 bits of entropy, the verifier **SHALL** implement a rate-limiting mechanism that effectively limits the number of failed authentication attempts that can be made on the subscriber account as described in [Sec. 5.2.2](sec5_authenticators.md#throttle).
-->

Verifier は, Approved Random Bit Generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1) を使用して, 少なくとも 20 ビットの Entropy を持つ Random Authentication Secret を生成することとなる(**SHALL**). Authentication Secret の Entropy が 64 ビット未満の場合, Verifier は, [Sec. 5.2.2](sec5_authenticators.md#throttle) で説明されている通り, Subscriber Account で試行できる Authentication の失敗回数を効果的に制限するレート制限メカニズムを実装することとなる(**SHALL**).

<!--
Out-of-band verifiers **SHALL** consider all authentication operations to be single-factor unless the CSP has confirmed that the out-of-band authentication meets the requirements of [Sec. 5.1.3.4](sec5_authenticators.md#mfooba). This requirement **MAY** be satisfied by issuance of the authenticator by the CSP or a trusted third party or by use of an authentication application known by the CSP to meet these requirements.
-->

CSP が, Out-of-band Authentication が [Sec. 5.1.3.4](sec5_authenticators.md#mfooba) の要件を満たしていることを確認しない限り, Out-of-band Verifier はすべての Authentication 操作を Single-Factor と見なすこととなる(**SHALL**). この要件は CSP または信頼されたサードパーティによる Authenticator の発行, またはこれらの要件を満たすことが CSP によって認識されている Authentication アプリケーションの使用によって満たされてもよい(**MAY**).

<!--
Out-of-band verifiers that send a push notification to a subscriber device **SHOULD** implement a reasonable limit on the rate or total number of push notifications that will be sent since the last successful authentication.
-->

Subscriber のデバイスにプッシュ通知を送信する Out-of-band Verifier は, 成功した最後の Authentication 以降に送信されるプッシュ通知のレートまたは総数に合理的な制限を実装する必要がある(**SHOULD**).

#### Authentication using the Public Switched Telephone Network {#pstnOOB}

<!--
Use of the PSTN for out-of-band verification is restricted as described in this section and in [Sec. 5.2.10](sec5_authenticators.md#restricted). If out-of-band verification is to be made using the PSTN, the verifier **SHALL** verify that the pre-registered telephone number being used is associated with a specific physical device. Changing the pre-registered telephone number is considered to be the binding of a new authenticator and **SHALL** only occur as described in [Sec. 6.1.2](sec6_lifecycle.md#post-enroll-bind).
-->

Out-of-band Verification のための PSTN の使用は, このセクションと [Sec. 5.2.10](sec5_authenticators.md#restricted) で説明されているように制限されている. PSTN を使用して Out-of-band Verification を行う場合, Verifier は, 使用されている事前登録済みの電話番号が特定の物理デバイスに関連付けられていることを Verification することとなる(**SHALL**). 事前登録された電話番号の変更は, 新しい Authenticator のバインドであると見なされ, [Sec. 6.1.2](sec6_lifecycle.md#post-enroll-bind) で説明されている場合にのみ発生することとなる(**SHALL**).

<!--
Use of the PSTN to deliver out-of-band authentication secrets is potentially not available to some subscribers in areas with limited telephone coverage (particularly in areas without mobile phone service). Accordingly, verifiers **SHALL** ensure that alternative authenticator types are available to all subscribers and **SHOULD** remind subscribers of this limitation of PSTN out-of-band authenticators prior to binding.
-->

PSTN を使用して Out-of-band Authentication Secret を配信することは, 限定された電話のカバレッジを持つ地域 (特に携帯電話サービスがない地域) では, 一部の Subscriber が利用できない可能性がある. したがって, Verifier は, すべての Subscriber が代替の Authenticator タイプを利用できるようにすることとなり(**SHALL**), バインドする前に, PSTN を使用した Out-of-band Authenticator のこの制限を Subscriber に通知する必要がある(**SHOULD**).

<!--
Verifiers **SHOULD** consider risk indicators such as device swap, SIM change, number porting, or other abnormal behavior before using the PSTN to deliver an out-of-band authentication secret.
-->

Verifier は, PSTN を使用して Out-of-band Authentication Secret を配信する前に, デバイスの交換, SIM の変更, 番号の移植, またはその他の異常な動作などのリスク指標を考慮する必要がある(**SHOULD**).

<!--
> NOTE: Consistent with the restriction of authenticators in [Sec. 5.2.10](sec5_authenticators.md#restricted), NIST may adjust the restricted status of the PSTN over time based on the evolution of the threat landscape and the technical operation of the PSTN.
-->

> 注意: [Sec. 5.2.10](sec5_authenticators.md#restricted) の Authenticator の制限と整合性を取り, NIST は, 脅威をとりまく状況の進化と PSTN の技術的なオペレーションに基づいて, 時間の経過とともに, PSTN の制限付きステータスを調整してもよい.

#### Multi-Factor Out-of-Band Authenticators {#mfooba}

<!--
Multi-factor out-of-band authenticators operate in a similar manner to single-factor out-of-band authenticators (see [Sec. 5.1.3.1](sec5_authenticators.md#ooba)) except that they require the presentation and verification of an additional factor, either a memorized secret or a biometric characteristic, prior to allowing the claimant to complete the authentication transaction (i.e., prior to accessing the authentication secret, entering the authentication secret, or confirming the transaction as appropriate for the authentication flow being used). Each use of the authenticator **SHALL** require the presentation of the activation factor.
-->

Multi-Factor Out-of-band Authenticator は, Claimant が Authentication Transaction を完了できるようにする前(つまり, Authentication Secret にアクセスする前, Authentication Secret を入力する前, または使用されている Authentication フローに適した Transaction を確認する前)に Memorized Secret または Biometric Characteristic のいずれかの追加要素の提示と Verification を必要とすることを除いて, Single-Factor Out-of-band Authenticator ([Sec. 5.1.3.1](sec5_authenticators.md#ooba)を参照) と同様の方法で動作する. Authenticator の使用ごとに, Activation Factor の提示を要求することとなる(**SHALL**).

<!--
The use of an activation secret by the authenticator **SHALL** meet the requirements of [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11). A biometric activation factor **SHALL** meet the requirements of [Sec. 5.2.3](sec5_authenticators.md#biometric_use), including limits on the number of consecutive authentication failures. Submission of the activation factor **SHALL** be a separate operation from unlocking of the host device (e.g., smartphone), although the same activation factor used to unlock the host device **MAY** be used in the authentication operation. The memorized secret or biometric sample used for activation — and any biometric data derived from the biometric sample such as a probe produced through signal processing — **SHALL** be zeroized immediately after the authentication operation.
-->

Authenticator による Activation Secret の使用は, [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11) の要件を満たすこととなる(**SHALL**). Biometric Activation Factor は, Authentication の連続失敗回数の制限を含め, [Sec. 5.2.3](sec5_authenticators.md#biometric_use) の要件を満たすこととなる(**SHALL**). Activation Factor の提出は, ホストデバイス (スマートフォンなど) のロック解除とは別の操作となる(**SHALL**)が, ホストデバイスのロック解除に使用されたものと同じ Activation Factor が Authentication 操作で使用されてもよい(**MAY**). Activation に使用される Memorized Secret または Biometric Sample -および信号処理によって生成された Probe などの Biometric Sample から得られたすべての Biometric データ- は, Authentication 操作の直後に Zeroize されることとなる(**SHALL**). 

### Single-Factor OTP Device {#singlefactorOTP}

<!--
A single-factor OTP device generates one-time passwords (OTPs). This category includes hardware devices and software-based OTP generators installed on devices such as mobile phones. These devices have an embedded secret that is used as the seed for generation of OTPs and does not require activation through a second factor. The OTP is displayed on the device and manually input for transmission to the verifier, thereby proving possession and control of the device. An OTP device may, for example, display 6 characters at a time. A single-factor OTP device is _something you have_.
{:.authenticator-image}
-->

Single-Factor OTP デバイスは, ワンタイムパスワード(OTP)を生成する. このカテゴリには, ハードウェアデバイスと携帯電話などのデバイス上にインストールされた Software-Based OTP Generator が含まれる. これらのデバイスは, OTP 生成のシードとして使用される組み込みの Secret を持ち, 二番目の要素による Activation を必要としない. OTP はデバイス上に表示され Verifier に送信するために手動で入力される, これによりデバイスの所有と制御が証明される. OTP デバイスは, 例えば, 一度に6文字を表示してもよい. Single-Factor OTP デバイスは _something you have_ である.
{:.authenticator-image}

<!--
Single-factor OTP devices are similar to look-up secret authenticators with the exception that the secrets are cryptographically and independently generated by the authenticator and verifier and compared by the verifier. The secret is computed based on a nonce that may be time-based or from a counter on the authenticator and verifier.
-->

Single-Factor OTP デバイスは, Secret が Authenticator と Verifier によって暗号論的にかつ独立して生成され, Verifier によって比較されることを除いて, Look-up Secret Authenticator と同様である. Secret は, 時間ベースの Nonce に基づいて, または Authenticator と Verifier の数値カウンターから計算されてもよい.

#### Single-Factor OTP Authenticators {#sfotpa}

<!--
Single-factor OTP authenticators contain two persistent values. The first is a symmetric key that persists for the device's lifetime. The second is a nonce that is either changed each time the authenticator is used or is based on a real-time clock.
-->

Single-Factor OTP Authenticator は, 2つの永続的な値を含む. 1つ目は, デバイスのライフタイムの間保持される Symmetric Key である. 2つ目は, Authenticator が使用されるたびに変更されるか, リアルタイムクロックに基づく Nonce である.

<!--
The secret key and its algorithm **SHALL** provide at least the minimum security strength specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication). The nonce **SHALL** be of sufficient length to ensure that it is unique for each operation of the device over its lifetime. If a subscriber needs to change the device used for a software-based OTP authenticator, they **SHOULD** bind the authenticator application on the new device to their subscriber account as described in [Sec. 6.1.2.1](sec6_lifecycle.md#post-enroll-bind) and invalidate the authenticator application that will no longer be used.
-->

Secret Key とそのアルゴリズムは, 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティ強度を提供することとなる(**SHALL**)(発行日現在で 112 ビット). Nonce は, デバイスのライフタイム全体にわたってデバイスの各操作ごとに一意であることを確保するのに十分な長さとなる(**SHALL**). Subscriber が Software-Based OTP Authenticator に使用されるデバイスを変更する必要がある場合, 彼らは [Sec. 6.1.2.1](sec6_lifecycle.md#post-enroll-bind) で説明されている通りに新しいデバイス上の Authenticator を Subscriber Account へバインドする必要があり(**SHOULD**), 使用されなくなった Authenticator アプリケーションを無効にする必要がある.

<!--
The authenticator output is obtained by using an approved block cipher or hash function to combine the key and nonce in a secure manner. The authenticator output **MAY** be truncated to as few as 6 decimal digits (approximately 20 bits of entropy).
-->

Authenticator の出力は, Key と Nonce を安全な方法で結合するために Approved なブロック暗号または Hash 関数を使用すること取得される. Authenticator の出力は, わずか6桁の10進数 (約20ビットのEntropy) に切り詰められられてもよい(**MAY**).

<!--
If the nonce used to generate the authenticator output is based on a real-time clock, the nonce **SHALL** be changed at least once every 2 minutes.
-->

Authenticator の出力を生成するために使用される Nonce がリアルタイムクロックに基づいている場合, Nonce は少なくとも2分ごとに変更されることとなる(**SHALL**).

#### Single-Factor OTP Verifiers

<!--
Single-factor OTP verifiers effectively duplicate the process of generating the OTP used by the authenticator. As such, the symmetric keys used by authenticators are also present in the verifier, and **SHALL** be strongly protected against unauthorized disclosure by the use of access controls that limit access to the keys to only those software components on the device requiring access.
-->

Single-Factor OTP Verifier は, Authenticator に使用される OTP 生成プロセスを効果的に複製する. そのため, Authenticator に使用される Symmetric Key は Verifier にもまた存在し, アクセスを必要とするデバイス上のそれらのソフトウェアコンポーネントのみに Key へのアクセスを制限するアクセスコントロールを使用して, 無許可の開示から強力に保護されることとなる(**SHALL**).

<!--
When a single-factor OTP authenticator is being associated with a subscriber account, the verifier or associated CSP **SHALL** use approved cryptography to either generate and exchange or to obtain the secrets required to duplicate the authenticator output.
-->

Single-Factor OTP Authenticator が Subscriber Account に関連付けられている場合, Verifier または関連付けられた CSP は, Authenticator の出力を複製するために必要な Secret を生成および交換, または取得するために, Approved Cryptography を使用することとなる(**SHALL**).

<!--
The verifier **SHALL** use approved encryption and an authenticated protected channel when collecting the OTP in order to provide resistance to eavesdropping and AitM attacks. In order to provide replay resistance as described in [Sec. 5.2.8](sec5_authenticators.md#replay), verifiers **SHALL** accept a given OTP only once while it is valid. In the event a claimant's authentication is denied due to duplicate use of an OTP, verifiers **MAY** warn the claimant in case an attacker has been able to authenticate in advance. Verifiers **MAY** also warn a subscriber in an existing session of the attempted duplicate use of an OTP.
-->

Verifier は, OTP を収集するときに, 盗聴や AitM Attack への耐性を提供するために, Approved Encryption と Authenticated Protected Channel を使用することとなる(**SHALL**). [Sec. 5.2.8](sec5_authenticators.md#replay) で説明されている通りに Replay Resistance を提供するために, Verifier は, 有効な OTP の受け入れを一度のみとすることとなる(**SHALL**). OTP の重複使用が原因で Claimant の Authentication が拒否された場合, Verifier は, Attacker が事前に Authenticate できた場合に備えて Claimant に警告してもよい(**MAY**). また, Verifier は, OTP の重複使用の試行について, 既存セッションの中にいる Subscriber に警告してもよい(**MAY**).

<!--
Time-based OTPs [[TOTP]](references.md#ref-totp) **SHALL** have a defined lifetime that is determined by the expected clock drift — in either direction — of the authenticator over its lifetime, plus allowance for network delay and user entry of the OTP.
-->

時間ベースの OTP [[TOTP]](references.md#ref-totp) は, ネットワーク遅延と OTP のユーザ入力のための許容値, それに加え Authenticator が寿命の間に持つはずの両方向のクロックのずれを考慮した上で決定される, 定義されたライフタイムを持つこととなる(**SHALL**).

<!--
If the authenticator output has less than 64 bits of entropy, the verifier **SHALL** implement a rate-limiting mechanism that effectively limits the number of failed authentication attempts that can be made on the subscriber account as described in [Sec. 5.2.2](sec5_authenticators.md#throttle).
-->

Authenticator の出力の Entropy が 64 ビット未満の場合, Verifier は, [Sec. 5.2.2](sec5_authenticators.md#throttle) で説明されている通り, Subscriber Account で試行できる Authentication の失敗回数を効果的に制限するレート制限メカニズムを実装することとなる(**SHALL**).

### Multi-Factor OTP Devices {#multifactorOTP}

<!--
A multi-factor OTP device generates OTPs for use in authentication after activation through input of an activation factor. This includes hardware devices and software-based OTP generators installed on devices such as mobile phones. The second factor of authentication may be achieved through some kind of integral entry pad, an integral biometric (e.g., fingerprint) reader, or a direct computer interface (e.g., USB port). The OTP is displayed on the device and manually input for transmission to the verifier. For example, an OTP device may display 6 characters at a time, thereby proving possession and control of the device. The multi-factor OTP device is _something you have_, and it **SHALL** be activated by either _something you know_ or _something you are_.
{:.authenticator-image}
-->

Multi-Factor OTP デバイスは, Activation Factor の入力による Activation 後に Authentication に使用する OTP を生成する. これには, ハードウェアデバイスと携帯電話などのデバイス上にインストールされた Software-Based OTP Generator が含まれる. Authentication の二番目の要素は, 一体型入力パッドのようなもの, 一体型Biometric (例: 指紋) リーダー, または直接的なコンピュータインターフェース (例: USB ポート) によって実現されてもよい. OTP はデバイス上に表示され Verifier に送信するために手動で入力される. 例えば, OTP デバイスは一度に6文字を表示することができ, それによってデバイスの所有と制御を証明する. Multi-Factor OTP デバイスは _something you have_ であり, かつ, _something you know_ または _something you are_ のいずれかによって Activation されることとなる(**SHALL**).
{:.authenticator-image}


#### Multi-Factor OTP Authenticators {#mfotpa}

<!--
Multi-factor OTP authenticators operate in a similar manner to single-factor OTP authenticators (see [Sec. 5.1.4.1](sec5_authenticators.md#sfotpa)), except that they require the presentation and verification of either a memorized secret or a biometric characteristic to obtain the OTP from the authenticator. Each use of the authenticator **SHALL** require the input of the activation factor.
-->

Multi-Factor OTP Authenticator は, Authenticator から OTP を取得するために Memorized Secret または Biometric Characteristic のいずれかの提示と Verification を必要とすることを除いて, Single-Factor OTP Authenticator ([Sec. 5.1.4.1](sec5_authenticators.md#sfotpa)を参照) と同様の方法で動作する. Authenticator の使用ごとに, Activation Factor の入力を要求することとなる(**SHALL**).

<!--
In addition to activation information, multi-factor OTP authenticators contain two persistent values. The first is a symmetric key that persists for the device's lifetime. The second is a nonce that is either changed each time the authenticator is used or is based on a real-time clock.
-->

Activation 情報に加えて, Multi-Factor OTP Authenticator は, 2つの永続的な値を含む. 1つ目は, デバイスのライフタイムの間保持される Symmetric Key である. 2つ目は, Authenticator が使用されるたびに変更されるか, リアルタイムクロックに基づく Nonce である.

<!--
The secret key and its algorithm **SHALL** provide at least the minimum security strength specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication). The nonce **SHALL** be of sufficient length to ensure that it is unique for each operation of the device over its lifetime. If a subscriber needs to change the device used for a software-based OTP authenticator, they **SHOULD** bind the authenticator application on the new device to their subscriber account as described in [Sec. 6.1.2.1](sec6_lifecycle.md#post-enroll-bind) and invalidate the authenticator application that will no longer be used.
-->

Secret Key とそのアルゴリズムは, 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティ強度を提供することとなる(**SHALL**)(発行日現在で 112 ビット). Nonce は, デバイスのライフタイム全体にわたってデバイスの各操作ごとに一意であることを確保するのに十分な長さとなる(**SHALL**). Subscriber が Software-Based OTP Authenticator に使用されるデバイスを変更する必要がある場合, 彼らは [Sec. 6.1.2.1](sec6_lifecycle.md#post-enroll-bind) で説明されている通りに新しいデバイス上の Authenticator を Subscriber Account へバインドする必要があり(**SHOULD**), 使用されなくなった Authenticator アプリケーションを無効にする必要がある.

<!--
The authenticator output is obtained by using an approved block cipher or hash function to combine the key and nonce in a secure manner. The authenticator output **MAY** be truncated to as few as 6 decimal digits (approximately 20 bits of entropy).
-->

Authenticator の出力は, Key と Nonce を安全な方法で結合するために Approved なブロック暗号または Hash 関数を使用すること取得される. Authenticator の出力は, わずか6桁の10進数 (約20ビットのEntropy) に切り詰められられてもよい(**MAY**).

<!--
If the nonce used to generate the authenticator output is based on a real-time clock, the nonce **SHALL** be changed at least once every 2 minutes.
-->

Authenticator の出力を生成するために使用される Nonce がリアルタイムクロックに基づいている場合, Nonce は少なくとも2分ごとに変更されることとなる(**SHALL**).

<!--
The use of an activation secret by the authenticator **SHALL** meet the requirements of [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11). A biometric activation factor **SHALL** meet the requirements of [Sec. 5.2.3](sec5_authenticators.md#biometric_use), including limits on the number of consecutive authentication failures. Submission of the activation factor **SHALL** be a separate operation from unlocking of the host device (e.g., smartphone), although the same activation factor used to unlock the host device **MAY** be used in the authentication operation. The unencrypted key and activation secret or biometric sample — and any biometric data derived from the biometric sample such as a probe produced through signal processing — **SHALL** be zeroized immediately after an OTP has been generated.
-->

Authenticator による Activation Secret の使用は, [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11) の要件を満たすこととなる(**SHALL**). Biometric Activation Factor は, Authentication の連続失敗回数の制限を含め, [Sec. 5.2.3](sec5_authenticators.md#biometric_use) の要件を満たすこととなる(**SHALL**). Activation Factor の提出は, ホストデバイス (スマートフォンなど) のロック解除とは別の操作となる(**SHALL**)が, ホストデバイスのロック解除に使用されたものと同じ Activation Factor が Authentication 操作で使用されてもよい(**MAY**). Unencrypted Key と Activation Secret, または Biometric Sample -および信号処理によって生成された Probe などの Biometric Sample から得られたすべての Biometric データ- は, Authentication 操作の直後に Zeroize されることとなる(**SHALL**). 

#### Multi-Factor OTP Verifiers

<!--
Multi-factor OTP verifiers effectively duplicate the process of generating the OTP used by the authenticator, but without the requirement that a second factor be provided. As such, the symmetric keys used by authenticators **SHALL** be strongly protected against unauthorized disclosure by the use of access controls that limit access to the keys to only those software components on the device requiring access.
-->

Multi-Factor OTP Verifier は, 二番目の要素を提供を受ける要件なしに Authenticator に使用される OTP 生成プロセスを効果的に複製する. そして, Authenticator に使用される Symmetric Key はアクセスを必要とするデバイス上のそれらのソフトウェアコンポーネントのみに Key へのアクセスを制限するアクセスコントロールを使用して, 無許可の開示から強力に保護されることとなる(**SHALL**).

<!--
When a multi-factor OTP authenticator is being associated with a subscriber account, the verifier or associated CSP **SHALL** use approved cryptography to either generate and exchange or to obtain the secrets required to duplicate the authenticator output. The verifier or CSP **SHALL** also establish, by issuance of the authentictor, that the authenticator is a multi-factor device. Otherwise, the verifier **SHALL** treat the authenticator as single-factor, in accordance with [Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP).
-->

Multi-Factor OTP Authenticator が Subscriber Account に関連付けられている場合, Verifier または関連付けられた CSP は, Authenticator の出力を複製するために必要な Secret を生成および交換, または取得するために, Approved Cryptography を使用することとなる(**SHALL**). Verifier または CSP は, Authenticator の発行によって, Authenticator が Multi-Factor デバイスであることを確立することとなる(**SHALL**). それ以外の場合, Verifier は, [Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP) に従って, Authenticator を Single-Factor として扱うこととなる(**SHALL**).

<!--
The verifier **SHALL** use approved encryption and an authenticated protected channel when collecting the OTP in order to provide resistance to eavesdropping and AitM attacks. In order to provide replay resistance as described in [Sec. 5.2.8](sec5_authenticators.md#replay), verifiers **SHALL** accept a given OTP only once while it is valid. In the event a claimant's authentication is denied due to duplicate use of an OTP, verifiers **MAY** warn the claimant in case an attacker has been able to authenticate in advance. Verifiers **MAY** also warn a subscriber in an existing session of the attempted duplicate use of an OTP.
-->

Verifier は, OTP を収集するときに, 盗聴や AitM Attack への耐性を提供するために, Approved Encryption と Authenticated Protected Channel を使用することとなる(**SHALL**). [Sec. 5.2.8](sec5_authenticators.md#replay) で説明されている通りに Replay Resistance を提供するために, Verifier は, 有効な OTP の受け入れを一度のみとすることとなる(**SHALL**). OTP の重複使用が原因で Claimant の Authentication が拒否された場合, Verifier は, Attacker が事前に Authenticate できた場合に備えて Claimant に警告してもよい(**MAY**). また, Verifier は, OTP の重複使用の試行について, 既存セッションの中にいる Subscriber に警告してもよい(**MAY**).

<!--
Time-based OTPs [[TOTP]](references.md#ref-totp) **SHALL** have a defined lifetime that is determined by the expected clock drift — in either direction — of the authenticator over its lifetime, plus allowance for network delay and user entry of the OTP.
-->

時間ベースの OTP [[TOTP]](references.md#ref-totp) は, ネットワーク遅延と OTP のユーザ入力のための許容値, それに加え Authenticator が寿命の間に持つはずの両方向のクロックのずれを考慮した上で決定される, 定義されたライフタイムを持つこととなる(**SHALL**).

<!--
If the authenticator output or activation secret has less than 64 bits of entropy, the verifier **SHALL** implement a rate-limiting mechanism that effectively limits the number of failed authentication attempts that can be made on the subscriber account as described in [Sec. 5.2.2](sec5_authenticators.md#throttle).
-->

Authenticator の出力または Activation Secret の Entropy が 64 ビット未満の場合, Verifier は, [Sec. 5.2.2](sec5_authenticators.md#throttle) で説明されている通り, Subscriber Account で試行できる Authentication の失敗回数を効果的に制限するレート制限メカニズムを実装することとなる(**SHALL**).

### Single-Factor Cryptographic Software {#sfcs}

<!--
A single-factor cryptographic software authenticator is a cryptographic key stored on disk or some other "soft" media. Authentication is accomplished by proving possession and control of the key. The authenticator output is highly dependent on the specific cryptographic protocol, but it is generally some type of signed message. The single-factor cryptographic software authenticator is _something you have_.
{:.authenticator-image}
-->

Single-Factor Cryptographic Software Authenticator は, ディスク上またはその他の "ソフト" メディアに格納された Cryptographic Key である. Authentication は, Key の所有と制御を証明することによって成し遂げられる. Authenticator の出力は, 特定の暗号プロトコルに大きく依存するが, 通常は何らかのタイプの署名付きメッセージである. Single-Factor Cryptographic Software Authenticator は _something you have_ である.
{:.authenticator-image}

#### Single-Factor Cryptographic Software Authenticators {#sfcsa}

<!--
Single-factor cryptographic software authenticators encapsulate one or more secret keys unique to the authenticator. The key **SHALL** be stored in suitably secure storage available to the authenticator application (e.g., keychain storage, TPM, or TEE if available). The key **SHALL** be strongly protected against unauthorized disclosure by the use of access controls that limit access to the key to only those software components on the device requiring access.
-->

Single-Factor Cryptographic Software Authenticator は, 1つかそれ以上の一意の Secret Key を Authenticator にカプセル化する. Key は, Authenticator アプリケーションが利用可能な, 適切に安全なストレージ (例: キーチェーンストレージ, TPM, または可能であれば TEE) に格納することとなる(**SHALL**). Key は, アクセスを必要とするデバイス上のそれらのソフトウェアコンポーネントのみに Key へのアクセスを制限するアクセスコントロールを使用して, 無許可の開示から強力に保護されることとなる(**SHALL**).

<!--
External cryptographic authenticators that do not meet the requirements of cryptographic hardware authenticators (e.g., that have a mechanism to allow private keys to be exported) are also considered to be cryptographic software authenticators. They **SHALL** meet the requirements for connected authenticators in [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12).
-->

Cryptographic Hardware Authenticator の要件を満たさない, 外付けの Cryptographic Authenticator (例: Private Key のエクスポートを許可するメカニズムを持つもの) も, Cryptographic Software Authenticator と見なされる. それらは [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12) の Connected Authenticator の要件を満たすこととなる(**SHALL**).

#### Single-Factor Cryptographic Software Verifiers

<!--
The requirements for a single-factor cryptographic software verifier are identical to those for a single-factor cryptographic device verifier, described in [Sec. 5.1.7.2](sec5_authenticators.md#sfcdv).
-->

Single-Factor Cryptographic Software Verifier の要件は, [Sec. 5.1.7.2](sec5_authenticators.md#sfcdv) で述べられる Single-Factor Cryptographic Device Verifier と同様である.

### Single-Factor Cryptographic Devices {#sfcd}

<!--
A single-factor cryptographic device is a hardware device that performs cryptographic operations using protected cryptographic keys and provides the authenticator output via direct connection to the user endpoint. The device uses embedded symmetric or asymmetric cryptographic keys, and does not require activation through a second factor of authentication. Authentication is accomplished by proving possession of the device via the authentication protocol. The authenticator output is provided by direct connection to the user endpoint and is highly dependent on the specific cryptographic device and protocol, but it is typically some type of signed message. A single-factor cryptographic device is _something you have_.
{:.authenticator-image}
-->

Single-Factor Cryptographic デバイスは, 保護された Cryptographic Key を使用して暗号的操作を実行し, ユーザーエンドポイントへの直接接続を介して Authenticator の出力を提供するハードウェアデバイスである. デバイスは, 組み込みの Symmetric または Asymmetric Cryptographic Key を使用し, 二番目の要素による Activation を必要としない. Authentication は, Authentication Protocol を介してデバイスの所有を証明することによって成し遂げられる. Authenticator の出力は, ユーザーエンドポイントへの直接接続によって提供され, また特定の暗号デバイスとプロトコルに大きく依存するが, 通常は何らかのタイプの署名付きメッセージである. Single-Factor Cryptographic デバイスは _something you have_ である.

#### Single-Factor Cryptographic Device Authenticators {#sfcda}

<!--
Single-factor cryptographic device authenticators use tamper-resistant hardware to encapsulate one or more secret keys unique to the authenticator that **SHALL NOT** be exportable (i.e., cannot be removed from the device). The authenticator operates using a secret key to sign a challenge nonce presented through a direct interface between the authenticator and endpoint (e.g., a USB port or secured wireless connection) as specified in [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12). Alternatively, the authenticator could be a suitably secure processor integrated with the user endpoint itself.
-->

Single-Factor Cryptographic Device Authenticator は, 1つかそれ以上の一意の Secret Key を, エクスポート機能を持つことはない(**SHALL NOT**)(つまり,デバイスから削除できない) Authenticator にカプセル化するために耐タンパー性ハードウェアを使用する. この Authenticator は, [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12) に指定された通り, Authenticator とエンドポイントの間の直接的なインターフェース(例: USB ポートや保護されたワイヤレス接続)を通じて提示された Challenge Nonce に署名するために Secret Key を使用することで動作する. あるいは, Authenticator は, ユーザエンドポイントそれ自体に統合された適切に安全なプロセッサであってもよい.

<!--
The secret key and its algorithm **SHALL** provide at least the minimum security length specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication). The challenge nonce **SHALL** be at least 64 bits in length. Approved cryptography **SHALL** be used.
-->

Secret Key とそのアルゴリズムは, 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティの長さを提供することとなる(**SHALL**)(発行日現在で 112 ビット). Challenge Nonce は, 少なくとも 64 ビットの長さとなる(**SHALL**). Approved Cryptography を使用することとなる(**SHALL**).

<!--
Cryptographic device authenticators differ from cryptographic software authenticators because of the greater protection afforded to the embedded authentication secrets by cryptographic devices. In order to be considered a cryptographic device, an authenticator **SHALL** either be a separate piece of hardware or an embedded processor or execution environment, e.g., secure element, trusted execution environment (TEE), trusted platform module (TPM). These hardware authenticators or embedded processors are separate from a host processor such as the CPU on a laptop or mobile device. A cryptographic device authenticator **SHALL** be designed so as to prohibit the export of the authentication secret to the host processor and **SHALL NOT** be capable of being reprogrammed by the host processor so as to allow the secret to be extracted. The authenticator is subject to applicable [[FIPS140]](references.md#ref-FIPS140-2) requirements of the AAL at which the authenticator is being used.
-->

Cryptographic Device Authenticator は, 暗号デバイスによる組み込みの Authentication Secret によって, より大きな保護がもたらされるため, Cryptographic Software Authenticator とは異なる. 暗号デバイスと見なされるために, Authenticator は, ハードウェアの別の部分または組み込みプロセッサ, または実行環境 (例: セキュア エレメント, Trusted Execution Environment (TEE), Trusted Platform Module (TPM))のいずれかとなる(**SHALL**). これらのハードウェア Authenticator または組み込みプロセッサは, ラップトップやモバイルデバイス上の CPU などのホストプロセッサからは分離される. Cryptographic Device Authenticator は, ホストプロセッサへの Authentication Secret のエクスポートを禁止するように設計されることとなり(**SHALL**), Secret の抽出が許されるようにホストプロセッサによって再プログラムを行えるようになることはない(**SHALL NOT**). Authenticator は, Authenticator が使用されている AAL に適合する [[FIPS140]](references.md#ref-FIPS140-2) の要件の対象となる.

<!--
Single-factor cryptographic device authenticators **SHOULD** require a physical input (e.g., the pressing of a button) in order to operate. This provides defense against unintended operation of the device, which might occur if the endpoint to which it is connected is compromised.
-->

Single-Factor Cryptographic Device Authenticator は, 動作するために物理的な入力 (例: ボタンを押す) を要求する必要がある(**SHOULD**). これは, デバイスが接続されているエンドポイントが侵害された場合に発生する可能性がある, デバイスの意図しない動作に対する防御を提供する.

#### Single-Factor Cryptographic Device Verifiers {#sfcdv}

<!--
Single-factor cryptographic device verifiers generate a challenge nonce, send it to the corresponding authenticator, and use the authenticator output to verify possession of the device. The authenticator output is highly dependent on the specific cryptographic device and protocol, but it is generally some type of signed message.
-->

Single-Factor Cryptographic Device Verifier は, Challenge Nonce を生成し, それを対象の Authenticator に送信し, デバイスの所有を検証するために Authenticator の出力を使用する. Authenticator の出力は, 特定の暗号デバイスとプロトコルに大きく依存するが, 通常は何らかのタイプの署名付きメッセージである. 

<!--
The verifier has either symmetric or asymmetric cryptographic keys corresponding to each authenticator. While both types of keys **SHALL** be protected against modification, symmetric keys **SHALL** additionally be protected against unauthorized disclosure by the use of access controls that limit access to the key to only those software components on the device requiring access.
-->

Verifier は, それぞれの Authenticator に対応する Symmetric または Asymmetric Cryptographic Key のいずれかを持つ. 両タイプの鍵は変更から保護されることとなる(**SHALL**)が, Symmetric Key はさらに, アクセスを必要とするデバイス上のそれらのソフトウェアコンポーネントのみに Key へのアクセスを制限するアクセスコントロールを使用して, 無許可の開示から強力に保護されることとなる(**SHALL**).

<!--
The challenge nonce **SHALL** be at least 64 bits in length, and **SHALL** either be unique over the authenticator's lifetime or statistically unique (i.e., generated using an approved random bit generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1)). The verification operation **SHALL** use approved cryptography.
-->

 Challenge Nonce は, 長さが少なくとも 64 ビットとなり(**SHALL**), Authenticator のライフタイムにわたって, または統計的に一意となる(**SHALL**)(つまり, Approved Random Bit Generator [[SP800-90Ar1]](references.md#ref-SP800-90Ar1) を使用して生成される). Verification 操作は, Approved Cryptography を使用することとなる(**SHALL**).

### Multi-Factor Cryptographic Software {#mfcs}

<!--
A multi-factor cryptographic software authenticator is a cryptographic key stored on disk or some other "soft" media that requires activation through a second factor of authentication. Authentication is accomplished by proving possession and control of the key. The authenticator output is highly dependent on the specific cryptographic protocol, but it is generally some type of signed message. The multi-factor cryptographic software authenticator is _something you have_, and it **SHALL** be activated by either _something you know_ or _something you are_.
{:.authenticator-image}
-->

Multi-Factor Cryptographic Software Authenticator は, Authentication の二番目の要素での Activation を必要とする, ディスク上またはその他の "ソフト" メディアに格納された Cryptographic Key である. Authentication は, Key の所有と制御を証明することによって成し遂げられる. Authenticator の出力は, 特定の暗号プロトコルに大きく依存するが, 通常は何らかのタイプの署名付きメッセージである. Multi-Factor Cryptographic Software Authenticator は _something you have_ であり, _something you know_ または _something you are_ のいずれかによって Activation されることとなる(**SHALL**).
{:.authenticator-image}

#### Multi-Factor Cryptographic Software Authenticators {#mfcsa}

<!--
Multi-factor cryptographic software authenticators encapsulate one or more secret keys unique to the authenticator and accessible only through the presentation and verification of an activation factor, either a memorized secret or a biometric characteristic. The key **SHOULD** be stored in suitably secure storage available to the authenticator application (e.g., keychain storage, TPM, TEE). The key **SHALL** be strongly protected against unauthorized disclosure by the use of access controls that limit access to the key to only those software components on the device requiring access.
-->

Multi-Factor Cryptographic Software Authenticator は, 1つかそれ以上の一意の Secret Key を Authenticator にカプセル化し, Memorized Secret または Biometric Characteristic のいずれかの Activation Factor の提示と Verification によってのみアクセス可能となる. Key は, Authenticator アプリケーションが利用可能な, 適切に安全なストレージ (例: キーチェーンストレージ, TPM, TEE) に格納する必要がある(**SHOULD**). Key は, アクセスを必要とするデバイス上のそれらのソフトウェアコンポーネントのみに Key へのアクセスを制限するアクセスコントロールを使用して, 無許可の開示から強力に保護されることとなる(**SHALL**).

<!--
External cryptographic authenticators that do not meet the requirements of cryptographic hardware authenticators (e.g., that have a mechanism to allow private keys to be exported) are also considered to be cryptographic software authenticators. They **SHALL** meet the requirementss for connected authenticators in [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12).
-->

Cryptographic Hardware Authenticator の要件を満たさない, 外付けの Cryptographic Authenticator (例: Private Key のエクスポートを許可するメカニズムを持つもの) も, Cryptographic Software Authenticator と見なされる. それらは [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12) の Connected Authenticator の要件を満たすこととなる(**SHALL**).

<!--
Each authentication operation using the authenticator **SHALL** require the input of the activation factor.
-->

Authenticator を使用する各 Authentication 操作は, Activation Factor の入力を必要とすることとなる(**SHALL**).

<!--
The use of an activation secret by the authenticator **SHALL** meet the requirements of [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11). A biometric activation factor **SHALL** meet the requirements of [Sec. 5.2.3](sec5_authenticators.md#biometric_use), including limits on the number of consecutive authentication failures. Submission of the activation factor **SHALL** be a separate operation from unlocking of the host device (e.g., smartphone), although the same activation factor used to unlock the host device **MAY** be used in the authentication operation. The activation secret or biometric sample — and any biometric data derived from the biometric sample such as a probe produced through signal processing — **SHALL** be zeroized immediately after an authentication transaction has taken place.
-->

Authenticator による Activation Secret の使用は, [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11) の要件を満たすこととなる(**SHALL**). Biometric Activation Factor は, Authentication の連続失敗回数の制限を含め, [Sec. 5.2.3](sec5_authenticators.md#biometric_use) の要件を満たすこととなる(**SHALL**). Activation Factor の提出は, ホストデバイス (スマートフォンなど) のロック解除とは別の操作となる(**SHALL**)が, ホストデバイスのロック解除に使用されたものと同じ Activation Factor が Authentication 操作で使用されてもよい(**MAY**). Activation Secret または Biometric Sample -および信号処理によって生成された Probe などの Biometric Sample から得られたすべての Biometric データ- は, Authentication 操作の直後に Zeroize されることとなる(**SHALL**). 

#### Multi-Factor Cryptographic Software Verifiers

<!--
The requirements for a multi-factor cryptographic software verifier are identical to those for a single-factor cryptographic device verifier, described in [Sec. 5.1.7.2](sec5_authenticators.md#sfcdv). Verification of the output from a multi-factor cryptographic software authenticator proves use of the activation factor.
-->

Multi-Factor Cryptographic Software Verifier の要件は, [Sec. 5.1.7.2](sec5_authenticators.md#sfcdv) で述べられる Single-Factor Cryptographic Device Verifier と同様である. Multi-Factor Cryptographic Software Authenticator からの出力の Verification は,  Activation Factor の使用を証明する.

### Multi-Factor Cryptographic Devices {#mfcd}

<!--
A multi-factor cryptographic device is a hardware device that performs cryptographic operations using one or more protected cryptographic keys and requires activation through a second authentication factor. Authentication is accomplished by proving possession of the device and control of the key. The authenticator output is provided by direct connection to the user endpoint and is highly dependent on the specific cryptographic device and protocol, but it is typically some type of signed message. The multi-factor cryptographic device is _something you have_, and it **SHALL** be activated by either _something you know_ or _something you are_.
{:.authenticator-image}
-->

Multi-Factor Cryptographic デバイスは, 1つかそれ以上の保護された Cryptographic Key を使用して暗号的操作を実行し, 二番目の Authentication Factor による Activation を必要とするハードウェアデバイスである. Authentication は, デバイスの所有および Key の制御を証明することによって成し遂げられる. Authenticator の出力は, ユーザーエンドポイントへの直接接続によって提供され, また特定の暗号デバイスとプロトコルに大きく依存するが, 通常は何らかのタイプの署名付きメッセージである. Multi-Factor Cryptographic デバイスは, _something you have_ であり, かつ, _something you know_ または _something you are_ のいずれかによって Activation されることとなる(**SHALL**).
{:.authenticator-image}

#### Multi-Factor Cryptographic Device Authenticators {#mfcda}

<!--
Multi-factor cryptographic device authenticators use tamper-resistant hardware to encapsulate one or more secret keys unique to the authenticator that **SHALL NOT** be exportable (i.e., cannot be removed from the device). The secret key **SHALL** be accessible only through the presentation and verification of an activation factor, either a biometric characteristic or an activation secret as described in [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11). The authenticator operates by using a secret key that was unlocked by the activation factor to sign a challenge nonce presented through a direct interface between the authenticator and endpoint (e.g., a USB port or secured wireless connection) as specified in [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12). Alternatively, the authenticator could be a suitably secure processor integrated with the user endpoint itself (e.g., a hardware TPM).
-->

Multi-Factor Cryptographic Device Authenticator は, 1つかそれ以上の一意の Secret Key を, エクスポート機能を持つことはない(**SHALL NOT**)(つまり,デバイスから削除できない) Authenticator にカプセル化するために耐タンパー性ハードウェアを使用する. Secret Key は, [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11) で述べられている通り, Biometric Characteristic または Activation Secret のいずれかの Activation Factor の提示と Verification によってのみアクセス可能となる(**SHALL**). この Authenticator は, [Sec. 5.2.12](sec5_authenticators.md#s-5-2-12) に指定された通り, Authenticator とエンドポイントの間の直接的なインターフェース(例: USB ポートや保護されたワイヤレス接続)を通じて提示された Challenge Nonce に署名するために Activation Factor によってアンロックされた Secret Key を使用することで動作する. あるいは, Authenticator は, ユーザエンドポイントそれ自体に統合された適切に安全なプロセッサであってもよい(例: ハードウェア TPM).

<!--
The secret key and its algorithm **SHALL** provide at least the minimum security length specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication). The challenge nonce **SHALL** be at least 64 bits in length. Approved cryptography **SHALL** be used.
-->

Secret Key とそのアルゴリズムは, 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティの長さを提供することとなる(**SHALL**)(発行日現在で 112 ビット). Challenge Nonce は, 少なくとも 64 ビットの長さとなる(**SHALL**). Approved Cryptography を使用することとなる(**SHALL**).

<!--
Cryptographic device authenticators differ from cryptographic software authenticators because of the greater protection afforded to the embedded authentication secrets by cryptographic devices. In order to be considered a cryptographic device, an authenticator **SHALL** either be a separate piece of hardware or an embedded processor or execution environment, e.g., secure element, trusted execution environment (TEE), trusted platform module (TPM). A cryptographic device authenticator **SHALL** be designed so as to prohibit the export of the authentication secret to the host processor and **SHALL NOT** be capable of being reprogrammed by the host processor so as to allow the secret to be extracted. The authenticator is subject to applicable [[FIPS140]](references.md#ref-FIPS140-2) requirements of the AAL at which the authenticator is being used.
-->

Cryptographic Device Authenticator は, 暗号デバイスによる組み込みの Authentication Secret によって, より大きな保護がもたらされるため, Cryptographic Software Authenticator とは異なる. 暗号デバイスと見なされるために, Authenticator は, ハードウェアの別の部分または組み込みプロセッサ, または実行環境 (例: セキュア エレメント, Trusted Execution Environment (TEE), Trusted Platform Module (TPM))のいずれかとなる(**SHALL**). Cryptographic Device Authenticator は, ホストプロセッサへの Authentication Secret のエクスポートを禁止するように設計されることとなり(**SHALL**), Secret の抽出が許されるようにホストプロセッサによって再プログラムを行えるようになることはない(**SHALL NOT**). Authenticator は, Authenticator が使用されている AAL に適合する [[FIPS140]](references.md#ref-FIPS140-2) の要件の対象となる.

<!--
Each authentication operation using the authenticator **SHOULD** require the input of the activation factor. Input of the activation factor **MAY** be accomplished via either direct input on the device or via a hardware connection (e.g., USB, smartcard).
-->

Authenticator を使用する各 Authentication 操作は, Activation Factor の入力が必要である(**SHOULD**). Activation Factor の入力は, デバイス上の直接入力か, ハードウェア接続(例: USB, スマートカード)を介してのいずれかで行われてもよい(**MAY**).

<!--
The use of an activation secret by the authenticator **SHALL** meet the requirements of [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11). A biometric activation factor **SHALL** meet the requirements of [Sec. 5.2.3](sec5_authenticators.md#biometric_use), including limits on the number of consecutive authentication failures. Submission of the activation factor **SHALL** be a separate operation from unlocking of the host device (e.g., smartphone), although the same activation factor used to unlock the host device **MAY** be used in the authentication operation. The activation secret or biometric sample — and any biometric data derived from the biometric sample such as a probe produced through signal processing — **SHALL** be zeroized immediately after an authentication transaction has taken place.
-->

Authenticator による Activation Secret の使用は, [Sec. 5.2.11](sec5_authenticators.md#s-5-2-11) の要件を満たすこととなる(**SHALL**). Biometric Activation Factor は, Authentication の連続失敗回数の制限を含め, [Sec. 5.2.3](sec5_authenticators.md#biometric_use) の要件を満たすこととなる(**SHALL**). Activation Factor の提出は, ホストデバイス (スマートフォンなど) のロック解除とは別の操作となる(**SHALL**)が, ホストデバイスのロック解除に使用されたものと同じ Activation Factor が Authentication 操作で使用されてもよい(**MAY**). Activation Secret または Biometric Sample -および信号処理によって生成された Probe などの Biometric Sample から得られたすべての Biometric データ- は, Authentication 操作の直後に Zeroize されることとなる(**SHALL**). 

#### Multi-Factor Cryptographic Device Verifiers {#mfcdv}

<!--
The requirements for a multi-factor cryptographic device verifier are identical to those for a single-factor cryptographic device verifier, described in [Sec. 5.1.7.2](sec5_authenticators.md#sfcdv). Verification of the authenticator output from a multi-factor cryptographic device proves use of the activation factor.
-->

Multi-Factor Cryptographic Device Verifier の要件は, [Sec. 5.1.7.2](sec5_authenticators.md#sfcdv) で述べられる Single-Factor Cryptographic Device Verifier と同様である. Multi-Factor Cryptographic Device からの Authenticator 出力の Verification は, Activation Factor の使用を証明する.

## General Authenticator Requirements

### Physical Authenticators

<!--
CSPs **SHALL** provide subscriber instructions on how to appropriately protect the authenticator against theft or loss. The CSP **SHALL** provide a mechanism to invalidate the authenticator immediately upon notification from subscriber that loss or theft of the authenticator is suspected.
-->

CSP は, Authenticator を盗難や紛失から適切に保護する方法について, Subscriber にインストラクションを提供することとなる(**SHALL**). CSP は, Subscriber からの Authenticator の紛失または盗難が疑われる通知に対して, 即時に Authenticator を無効にするメカニズムを提供することとなる(**SHALL**).

### Rate Limiting (Throttling) {#throttle}

<!--
When required by the authenticator type descriptions in [Sec. 5.1](sec5_authenticators.md#reqauthtype), the verifier **SHALL** implement controls to protect against online guessing attacks. Unless otherwise specified in the description of a given authenticator, the verifier **SHALL** limit consecutive failed authentication attempts on a single subscriber account to no more than 100.
-->

[Sec. 5.1](sec5_authenticators.md#reqauthtype) の Authenticator Type の説明で必要とされる場合, Verifier は, Online Guessing Attack から保護するための制御を実装することとなる(**SHALL**). その Authenticator の説明で特に指定されていない限り, Verifier は, 単一の Subscriber Account での Authentication の連続失敗の試行を 100回 以下に制限することとなる(**SHALL**).

<!--
Additional techniques **MAY** be used to reduce the likelihood that an attacker will lock the legitimate claimant out as a result of rate limiting. These include:
-->

レート制限の結果として Attacker が正当な Claimant をロックアウトする可能性を減らすために, 以下を含む追加のテクニックが使用されてもよい(**MAY**)：

<!--
- Requiring the claimant to complete a bot-detection and mitigation challenge before attempting authentication.
-->

- Authentication を試みる前に, Claimant にボットの検出と緩和のための課題を完了するように要求する.

<!--
- Requiring the claimant to wait following a failed attempt for a period of time that increases as the subscriber account approaches its maximum allowance for consecutive failed attempts (e.g., 30 seconds up to an hour).
-->

- 失敗した試行の後に, Subscriber Account がその連続失敗試行回数の最大許容値に近づくにつれて増加する時間(例: 30秒から1時間まで)の間, Claimant に待つことを要求する.

<!--
- Accepting only authentication requests that come from an allowlist of IP addresses from which the subscriber has been successfully authenticated before.
-->

- Subscriber が以前, Authentication に成功した IP アドレスの Allowlist からの Authentication 要求のみを受け入れる.

<!--
- Leveraging other risk-based or adaptive authentication techniques to identify user behavior that falls within, or out of, typical norms. These might, for example, include use of IP address, geolocation, timing of request patterns, or browser metadata.
-->

- 他のリスクベースまたは適応できる Authentication テクニックを活用して, 一般的な基準の範囲内または範囲外となるユーザーの行動を識別する. これらには, 例えば, IP アドレス, 位置情報, リクエストのタイミングのパターン, またはブラウザのメタデータの使用が含まれることがある.

<!--
When the subscriber successfully authenticates, the verifier **SHOULD** disregard any previous failed attempts for that user from the same IP address.
-->

Subscriber が Authentication に成功すると, Verifierは, 同じ IP アドレスからのそのユーザーのそれ以前の失敗試行をすべて考慮しないようにする必要がある(**SHOULD**).

### Use of Biometrics {#biometric_use}

<!--
The use of biometrics (*something you are*) in authentication includes both measurement of physical characteristics (e.g., fingerprint, iris, facial characteristics) and behavioral characteristics (e.g., typing cadence). Both classes are considered biometric modalities, although different modalities may differ in the extent to which they establish authentication intent as described in [Sec. 5.2.9](sec5_authenticators.md#intent).
-->

Authentication における Biometrics (*something you are*) の使用は, 身体的特徴 (例: 指紋, 虹彩, 顔の特徴) と行動的特徴 (例: タイピングのリズム) の両方の測定を含む. どちらのクラスも Biometric Modalitiy と見なされるが, [Sec. 5.2.9](sec5_authenticators.md#intent) で説明されているように, それぞれの Modalitiy によってどの程度 Authentication の確立を意図しているかが異なる場合がある.

<!--
For a variety of reasons, this document supports only limited use of biometrics for authentication. These reasons include:
-->

さまざまな理由から, このドキュメントでは, Authentication のための Biometrics の限定的な使用のみをサポートしている. 理由は以下を含む:

<!--
- The biometric False Match Rate (FMR) does not provide confidence in the authentication of the subscriber by itself. In addition, FMR does not account for spoofing attacks.
- Biometric comparison is probabilistic, whereas the other authentication factors are deterministic.
- Biometric template protection schemes provide a method for revoking biometric credentials that is comparable to other authentication factors (e.g., PKI certificates and passwords). However, the availability of such solutions is limited, and standards for testing these methods are under development.
- Biometric characteristics do not constitute secrets. They can often be obtained online or, in the case of a facial image, by taking a picture of someone with or without their knowledge. Latent fingerprints can be lifted from objects someone touches, and iris patterns can be captured with high resolution images. While presentation attack detection (PAD) technologies can mitigate the risk of these types of attacks, additional trust in the sensor or biometric processing is required to ensure that PAD is operating in accordance with the needs of the CSP and the subscriber.
-->

- Biometric False Match Rate (FMR) は, Subscriber の Authentication が Subscriber 自身 によってなされたものであるという信頼を提供しない. さらに, FMR はスプーフィング Attack を考慮して計算されない.
- Biometric の比較は確率的だが, 他の Authentication Factor は決定的である.
- Biometric Template Protection スキームは, 他の Authentication Factor (例: PKIの証明書およびパスワード) と同等の Biometric Credential を失効する方法を提供する. しかし, そのようなソリューションの有効性は限られており, これらの方法をテストするための標準は開発中である.
- Biometric Characteristics は Secret の構成要素とはならない. それらはオンラインでたびたび入手でき, また人々の顔写真は相手の認識の有無を問わず写真を撮ることで入手できる. 隠れた指紋は人々が触れた物から取得することができ, 虹彩パターンは高解像度の画像で捉えられる. Presentation Attack Detection (PAD) テクノロジーはこれらのタイプの Attack のリスクを軽減できるが, PAD が CSP と Subscriber のニーズに従って動作していることを確実にするには, センサーまたは Biometric Processing への追加の信頼が必要とされる.

<!--
Therefore, the limited use of biometrics for authentication is supported with the following requirements and guidelines:
-->

このため, Authentication のための Biometrics の限定的な使用は, 次の要件とガイドラインでサポートされる:

<!--
Biometrics **SHALL** be used only as part of multi-factor authentication with a physical authenticator (*something you have*).
-->

Biometrics は, 物理的な Authenticator (*something you have*) を使用した Multi-Factor Authentication の一部としてのみ使用されることとなる(**SHALL**).

<!--
The biometric system **SHALL** operate with a false-match rate (FMR) [[ISO/IEC2382-37]](references.md#ref-ISOIEC2382-37) of 1 in 10000 or better. This FMR **SHALL** be achieved under conditions of a conformant attack (i.e., zero-effort impostor attempt) as defined in [[ISO/IEC30107-1]](references.md#ref-ISOIEC30107-1).
-->

Biometric システムは, 1/10000 またはそれよりも望ましい False-Match Rate (FMR) [[ISO/IEC2382-37]](references.md#ref-ISOIEC2382-37) で動作することとなる(**SHALL**). この FMR は, [[ISO/IEC30107-1]](references.md#ref-ISOIEC30107-1) で定義されている Conformant Attack  (つまり, Zero-Effort Impostor Attempt) の条件のもとで達成されることとなる(**SHALL**).

<!--
The biometric system **SHOULD** implement presentation attack detection (PAD). Testing of the biometric system to be deployed **SHOULD** demonstrate at least 90% resistance to presentation attacks for each relevant attack type (i.e., species), where resistance is defined as the number of thwarted presentation attacks divided by the number of trial presentation attacks. Testing of presentation attack resistance **SHALL** be in accordance with Clause 12 of [[ISO/IEC30107-3]](references.md#ref-ISOIEC30107-3). The PAD decision **MAY** be made either locally on the claimant's device or by a central verifier.
-->

Biometric システムは, Presentation Attack Detection (PAD) を実装する必要がある(**SHOULD**). 展開される Biometric システムのテストでは, 関連する Attack タイプ (つまり, Species) ごとに, Presentation Attack に対して少なくとも 90% の耐性があることを示す必要がある(**SHOULD**). 耐性は, 阻止された Presentation Attack の数を試行したPresentation Attack の数で割った値として定義される. Presentation Attack 耐性のテストは, [[ISO/IEC30107-3]](references.md#ref-ISOIEC30107-3) の第12条に従うこととなる(**SHALL**). PAD の決定は, Claimant のデバイス上でローカルに行われるか, 中央の Verifier によって行われてもよい(**MAY**).

<!--
The biometric system **SHALL** allow no more than 5 consecutive failed authentication attempts or 10 consecutive failed attempts if PAD, meeting the above requirements, is implemented. Once that limit has been reached, the biometric authenticator **SHALL** impose a delay of at least 30 seconds before each subsequent attempt, with an overall limit of no more than 50 consecutive failed authentication attempts (100 if PAD is implemented). Once the overall limit is reached, the biometric system **SHALL** disable biometric user authentication and offer another factor (e.g., a different biometric modality or an activation secret if it is not already a required factor) if such an alternative method is already available.
-->

Biometric システムは, 認証の試行の連続失敗を5回まで, または, 上記の要件を満たす PAD が実装されている場合においては試行の連続失敗を 10 回まで許容することとなる(**SHALL**). ひとたびその制限に達すると, Biometric Authenticator は, 全体的な制限として認証の試行の連続失敗が 50 回 (PAD が実装されている場合は 100 回) を超えないとともに, その後の各試行の前に少なくとも 30 秒の遅延を課すこととなる(**SHALL**). ひとたび全体的な制限に達すると, Biometric システムは, Biometric User Authentication を無効にすることとなり(**SHALL**), 利用可能な代替方法がすでにある場合は, 他の要素 (例: 別の Biometric Modality, または, まだ要求された要素でない場合は Activation Secret) を提案することとなる.

<!--
The verifier **SHALL** make a determination of sensor and endpoint performance, integrity, and authenticity. Acceptable methods for making this determination include, but are not limited to:
-->

Verifier は, センサーとエンドポイントのパフォーマンス, 完全性, および 真正性を判断することとなる(**SHALL**). この決定を行うための許容される方法は, 以下を含むがこれらに限定されない:

<!--
* Authentication of the sensor or endpoint
* Certification by an approved accreditation authority
* Runtime interrogation of signed metadata (e.g., attestation) as described in [Sec. 5.2.4](sec5_authenticators.md#attestation).
-->

* センサーまたはエンドポイントの Authentication
* Approvedな 公認機関による Certification
* [Sec. 5.2.4](sec5_authenticators.md#attestation) で説明されている通りの, 署名されたメタデータ (例: Attestation) の実行時の問い合わせ.

<!--
Biometric comparison can be performed locally on the claimant's device or at a central verifier. Since the potential for attacks on a larger scale is greater at central verifiers, comparison **SHOULD** be performed locally.
-->

Biometric の比較は, Claimant のデバイス上でローカルでも, 中央の Verifier でも実行可能である. しかし, 大規模な Attack の可能性は中央の Verifier の方が大きいため, 比較はローカルで実行される必要がある(**SHOULD**).

<!--
If comparison is performed centrally:
-->

比較が中央で実行される場合:

<!--
* Use of the biometric as an authentication factor **SHALL** be limited to one or more specific devices that are identified using approved cryptography. Since the biometric has not yet unlocked the main authentication key, a separate key **SHALL** be used for identifying the device.
* Biometric revocation, referred to as biometric template protection in [[ISO/IEC24745]](references.md#ref-ISOIEC24745), **SHALL** be implemented.
* An authenticated protected channel between sensor (or an endpoint containing a sensor that resists sensor replacement) and verifier **SHALL** be established and the sensor or endpoint **SHALL** be authenticated prior to capturing the biometric sample from the claimant.
* All transmission of biometrics **SHALL** be over an authenticated protected channel.
-->

* Authentication Factor としての Biometric の使用は, Approved Cryptography を使用して識別される1つかそれ以上の特定のデバイスに限定されることとなる(**SHALL**). Biometric はメインの Authentication Key をまだアンロックしていないため, デバイスの識別には別の Key が使用されることとなる(**SHALL**).
* [[ISO/IEC24745]](references.md#ref-ISOIEC24745) で Biometric Template Protection と呼ばれるBiometric Revocation が実装されることとなる(**SHALL**).
* Authenticated Protected Channel は, センサー (またはセンサー交換耐性があるセンサーを含むエンドポイント) と Verifier の間に確立されることとなり(**SHALL**), また, センサーまたはエンドポイントは, Claimant から Biometric Sample を取得する前に Authenticate されることとなる(**SHALL**).
* Biometrics のすべての送信は, Authenticated Protected Channel を介することとなる(**SHALL**).

<!--
Biometric samples collected in the authentication process **MAY** be used to train comparison algorithms or — with user consent — for other research purposes. Biometric samples and any biometric data derived from the biometric sample such as a probe produced through signal processing **SHALL** be zeroized immediately after any training or research data has been derived.
-->

Authentication プロセスの中で収集された Biometric Sampleは, 比較アルゴリズムのトレーニングに使用するか, または -ユーザーの同意のもとで- 他の研究目的に使用されてもよい(**MAY**). Biometric Sample, および信号処理によって生成された Probe などの Biometric Sample から得られたすべての Biometric データは, すべてのトレーニングまたは研究データが得られた直後に Zeroize されることとなる(**SHALL**). 

<!--
Biometric authentication technologies **SHALL** provide similar performance for subscribers of different demographic types (racial background, gender, ethnicity, etc.).
-->

Biometric Authentication 技術は, さまざまな人口統計的タイプ (人種的背景, 性別, 民族など) の Subscriber に対して同様のパフォーマンスを提供することとなる(**SHALL**). 

### Attestation {#attestation}

<!--
An attestation is information conveyed to the verifier regarding a connected authenticator or the endpoint involved in an authentication operation. Information conveyed by attestation **MAY** include, but is not limited to:
-->

Attestation は, 接続された Authenticator, または Authentication 操作に関わるエンドポイントに関して Verifier に伝達される情報である. Attestation によって伝達される情報には以下を含んでもよい(**MAY**) が, これらに限定されない:

<!--
* The provenance (e.g., manufacturer or supplier certification), health, and integrity of the authenticator and endpoint
* Security features of the authenticator
* Security and performance characteristics of biometric sensors
* Sensor modality
-->

* Authenticator とエンドポイントの起源 (例: メーカーまたはサプライヤーの認定), 健全性, および完全性
* Authenticator のセキュリティ機能
* Biometric センサーのセキュリティとパフォーマンスの特性
* センサーモダリティ

<!--
If this attestation is signed, it **SHALL** be signed using a digital signature that provides at least the minimum security strength specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication).
-->

この Attestation が署名されている場合は, 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティ強度(発行日現在で 112 ビット)を提供するデジタル署名を使用して署名されることとなる(**SHALL**).

<!--
Attestation information **MAY** be used as part of a verifier's risk-based authentication decision.
-->

Attestation 情報は, Verifier のリスクベース Authentication の決断の一部として使用されてもよい(**MAY**).

### Phishing (Verifier Impersonation) Resistance {#verifimpers}

<!--
Phishing attacks, previously referred to in SP 800-63B as "verifier impersonation," are attempts by fraudulent verifiers and RPs to fool an unwary claimant into presenting an authenticator to an impostor. In some prior versions of SP 800-63, protocols resistant to phishing attacks were also referred to as "strongly MitM resistant."
-->

以前 SP 800-63B で "Verifier Impersonation" と呼ばれていた Phishing Attack は, 悪意のある偽物の Verifier と RP が, 不注意な Claimant をだまして Authenticator を Impostor に提示させようとする試みである. いくつかの SP 800-63 の以前のバージョンでは, Phishing Attack に耐性のあるプロトコルは, "Strongly MitM Resistant" とも呼ばれていた.

<!--
The term _phishing_ is widely used to describe a variety of similar attacks. For the purposes of this document, phishing resistance is the ability of the authentication protocol to detect and prevent disclosure of authentication secrets and valid authenticator outputs to an impostor relying party without reliance on the vigilance of the subscriber. The means by which the subscriber was directed to the impostor relying party are not relevant. For example, regardless of whether the subscriber was directed there via search engine optimization or prompted by email, it is considered to be a phishing attack.
-->

Phishing という用語は, さまざまな同様の Attack を説明するために広く使用されている. このドキュメントの目的上, Phishing 耐性とは, Subscriber の警戒に頼ることなく, Authentication Secret と有効な Authenticator 出力を Impostor が偽装する Relying Party へ開示することを検出し防止する Authentication Protocol の機能である. Subscriber が Impostor が偽装する Relying Party に向けられた手段は関係しない. 例えば, Subscriber が検索エンジンの最適化によってそこに案内されたのか, 電子メールで促されたのかに関係なく, Phishing Attack であると見なされる.

<!--
Approved cryptographic algorithms **SHALL** be used to establish phishing resistance where it is required. Keys used for this purpose **SHALL** provide at least the minimum security strength specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication).
-->

Approved な暗号アルゴリズムは, 必要とされる場所で Phishing 耐性を確立するために使用されることとなる(**SHALL**). この目的のための Key は, 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティ強度(発行日現在で 112 ビット)を提供することとなる(**SHALL**).

<!--
Authenticators that involve the manual entry of an authenticator output, such as out-of-band and OTP authenticators, **SHALL NOT** be considered phishing resistant because the manual entry does not bind the authenticator output to the specific session being authenticated. In an AitM attack, an impostor verifier could replay the OTP authenticator output to the verifier and successfully authenticate.
-->

Out-of-band や OTP Authenticator のような, Authenticator 出力の手動入力を伴う Authenticator は, Phishing 耐性があると見なされることはない(**SHALL NOT**), なぜならば, 手動入力は Authenticator 出力を特定の Authenticated session に Bind しないためである. AitM Attack では, Impostor が偽装する Verifier が OTP Authenticator の出力を Verifier に Replay し, 認証に成功する可能性がある.

<!--
While an individual authenticator may be phishing resistant, phishing resistance for a given subscriber account is only achieved when all methods of authentication are phishing resistant.
-->

個々の Authenticator には Phishing 耐性があるとしても, 特定の Subscriber Account の Phishing 耐性はすべての Authentication の方法に Phishing 耐性がある場合にのみ達成される.

<!--
Two methods of phishing resistance are recognized: channel binding and verifier name binding. Channel binding is considered more secure than verifier name binding because it is not vulnerable to mis-issuance or misappropriation of relying party certificates, but either method satisfies the requirements for phishing resistance.
-->

Phishing 耐性の2つの方法が知られている: Channel Binding と Verifier Name Binding である. Channel Binding は Relying Party 証明書の誤発行や不正使用に対して脆弱ではないため, Verifier Name Binding よりも安全であるとみなされるが, どちらの方法も Phishing 耐性の要件を満たす.

#### Channel Binding

<!--
An authentication protocol with channel binding **SHALL** establish an authenticated protected channel with the verifier. It **SHALL** then strongly and irreversibly bind a channel identifier that was negotiated in establishing the authenticated protected channel to the authenticator output (e.g., by signing the two values together using a private key controlled by the claimant for which the public key is known to the verifier). The verifier **SHALL** validate the signature or other information used to prove phishing resistance. This prevents an impostor verifier, even one that has obtained a certificate representing the actual verifier, from successfully relaying that authentication on a different authenticated protected channel.
-->

Channel Binding を伴う Authentication Protocol は, Authenticated Protected Channel を Verifier と確立することとなる(**SHALL**). 次に, Authenticated Protected Channel を確立する際にネゴシエートされた Channel identifier を, Authenticator 出力に強力かつ不可逆的に Bind することとなる(**SHALL**)(例: Public Key が Verifier に知られている Claimant によって制御される Private Key を使用して, 2つの値を一緒に署名することによって). Verifier は, Phishing 耐性を証明するために, 使用される署名またはその他の情報を検証することとなる(**SHALL**).  これにより, Impostor が偽装する Verifier が実際の Verifier を表す証明書を取得したとしても, 異なる Authenticated Protected Channel でその Authentication の中継に成功することを防ぐ.

<!--
An example of a phishing resistant authentication protocol that uses channel binding is client-authenticated TLS, because the client signs the authenticator output along with earlier messages from the protocol that are unique to the particular TLS connection being negotiated.
-->

Channel Binding を使用する Phishing 耐性のある Authentication Protocol の例は, クライアント認証 TLS である. なぜならば, ネゴシエートされた特定の TLS 接続に一意の, Protocol からの以前のメッセージと共に Authenticator の出力にクライアントが署名するためである.

#### Verifier Name Binding

<!--
An authentication protocol with authenticator name binding **SHALL** establish an authenticated protected channel with the verifier. It **SHALL** then generate an authenticator output that is cryptographically bound to a verifier identifier that is authenticated as part of the protocol.  In the case of domain name system (DNS) identifiers, the verifier identifier **SHALL** be either the authenticated hostname of the verifier or a parent domain that is at least one level below the public suffix [[PSL]](references.md#ref-psl) associated with that hostname. The binding **MAY** be established by choosing an associated authenticator secret, by deriving an authenticator secret using the verifier identifier, by cryptographically signing the authenticator output with the verifier identifier, or similar cryptographically secure means.
-->

Authenticator Name Binding を伴う Authentication Protocol は, Authenticated Protected Channel をVerifier と確立することとなる(**SHALL**). 次に, Protocol の一部として Authenticate された Verifier Identifier に対して暗号的に Bind された Authenticator 出力を生成することとなる(**SHALL**). Domain Name System (DNS) Identifier の場合, Verifier Identifier は, Verifier の Authenticate されたホスト名, またはホスト名に関連付けられた Public Suffix [[PSL]](references.md#ref-psl) の少なくとも 1 レベル遡った親ドメインのいずれかとなる(**SHALL**). Binding は, 関連付けられた Authenticator Secret を選択するか, Verifier Identifier を使用して Authenticator Secret を導出するか, Verifier Identifier と供に Authenticator 出力に暗号的に署名するか, または同様の暗号的に安全な手段によって確立されてもよい(**MAY**).

### Verifier-CSP Communications {#csp-verifier}

<!--
In situations where the verifier and CSP are separate entities (as shown by the dotted line in [[SP800-63]](../_sp800-63/sec4_model.md#fig-1){:latex-href="#ref-SP800-63"} Figure 1), communications between the verifier and CSP **SHALL** occur through a mutually authenticated secure channel (such as a client-authenticated TLS connection) using approved cryptography.
-->

Verifier と CSP が別々のエンティティである状況では ([[SP800-63]](../_sp800-63/sec4_model.md#fig-1){:latex-href="#ref-SP800-63"} の点線で示されているように, Verifier と CSP 間の通信は, Approved Cryptography を使用して, (クライアント認証 TLS 接続のような) 相互に Authenticate された安全なチャネルを介して行われることとなる(**SHALL**). 

### Verifier Compromise Resistance {#verifier-secrets}

<!--
Use of some types of authenticators requires that the verifier store a copy of the authenticator secret. For example, an OTP authenticator (described in [Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP)) requires that the verifier independently generate the authenticator output for comparison against the value sent by the claimant. Because of the potential for the verifier to be compromised and stored secrets stolen, authentication protocols that do not require the verifier to persistently store secrets that could be used for authentication are considered stronger, and are described herein as being *verifier compromise resistant*. Note that such verifiers are not resistant to all attacks. A verifier could be compromised in a different way, such as being manipulated into always accepting a particular authenticator output.
-->

いくつかのタイプの Authenticator を使用するには, Verifier が Authenticator Secret のコピーを保管する必要がある. 例えば, OTP Authenticator ([Sec. 5.1.4](sec5_authenticators.md#singlefactorOTP) で説明) では, Claimant によって送信された値と比較するための Authenticator 出力を, Verifier が独立して生成することが求められる. Verifier が侵害され, 保管された Secret が盗まれる可能性のため, Verifier が Authentication に使用できる Secret を永続的に保管する必要のない Authentication Protocol はより強力であると見なされ, *Verifier Compromise Resistant(Verifierが侵害耐性を持つ状態)* である旨がここで説明されている. このような Verifier もすべての Attack に耐性があるわけではないことに注意が必要である. Verifier は, 特定の Authenticator 出力を常に受け入れるようにのっとられるなど, 別の方法で侵害されるかもしれない.

<!--
Verifier compromise resistance can be achieved in different ways, for example:
-->

Verifier Compromise Resistant は様々な方法で達成できる, 例えば:

<!--
- Use a cryptographic authenticator that requires the verifier store a public key corresponding to a private key held by the authenticator.
-->

- Verifier は, Authenticator 保持する Private Key に対応する Public key を保管することを要求する Cryptographic Authenticator を使用する.

<!--
- Store the expected authenticator output in hashed form. This method can be used with some look-up secret authenticators (described in [Sec. 5.1.2](sec5_authenticators.md#lookupsecrets)), for example.
-->

- 予想される Authenticator 出力を Hash 形式で保管する. このメソッドは, 例えば一部の Look-Up Secret 
Authenticator ([Sec. 5.1.2](sec5_authenticators.md#lookupsecrets) で説明) で使用できる.

<!--
To be considered verifier compromise resistant, public keys stored by the verifier **SHALL** be associated with the use of approved cryptographic algorithms and **SHALL** provide at least the minimum security strength specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication).
-->

Verifier Compromise Resistant であると見なされるために, Verifier によって保管される Public key は, Approved な暗号アルゴリズムの使用によるものとなり(**SHALL**), 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティ強度(発行日現在で 112 ビット)を提供することとなる(**SHALL**).

<!--
Other verifier compromise resistant secrets **SHALL** use approved hash algorithms and the underlying secrets **SHALL** have at least the minimum security strength specified in the latest revision of [[SP800-131A]](references.md#ref-SP800-131A) (112 bits as of the date of this publication). Secrets (e.g., memorized secrets) having lower complexity **SHALL NOT** be considered verifier compromise resistant when hashed because of the potential to defeat the hashing process through dictionary lookup or exhaustive search.
-->

その他の Verifier Compromise Resistant Secret は, Approved な Hash アルゴリズムを使用することとなり(**SHALL**), 基となる Secret は, 少なくとも [[SP800-131A]](references.md#ref-SP800-131A) の最新リビジョンで指定されている最小のセキュリティ強度(発行日現在で 112 ビット)を持つすることとなる(**SHALL**). 低い複雑度を持つ Secret (例: Memorized Secret) は, 辞書検索または網羅的探索によって Hash プロセスを破る可能性があるため, Hash された場合でも Verifier Compromise Resistant と見なされることはない(**SHALL NOT**).

### Replay Resistance {#replay}

<!--
An authentication process resists replay attacks if it is impractical to achieve a successful authentication by recording and replaying a previous authentication message. Replay resistance is in addition to the replay-resistant nature of authenticated protected channel protocols, since the output could be stolen prior to entry into the protected channel. Protocols that use nonces or challenges to prove the "freshness" of the transaction are resistant to replay attacks since the verifier will easily detect when old protocol messages are replayed since they will not contain the appropriate nonces or timeliness data.
-->

Authentication Process は, 過去の Authentication のメッセージを記録して Replay することによって Authentication を成功させることが現実的でない場合, Replay Attack に耐性がある. Protected Channel に入る前に出力が盗まれる可能性があるため, Replay Resistance は Authenticated Protected Channel Protocol の Replay-Resistant 特性には含まれていない. Nonce または Challenge を使用して Transaction の "真新しさ" を証明するプロトコルは, Replay Attack に耐性がある. Verifier は, 古いプロトコルメッセージが適切な Nonce または適時性のあるデータを含んでいないため, 古いプロトコルメッセージが Replay されることを簡単に検出できるからである.

<!--
Examples of replay-resistant authenticators are OTP devices, cryptographic authenticators, and look-up secrets.
-->

Replay 耐性のある Authenticator の例は, OTP デバイス, Cryptographic Authenticator, および Look-Up Secret である.

<!--
In contrast, memorized secrets are not considered replay resistant because the authenticator output — the secret itself — is provided for each authentication.
-->

反対に, Memorized Secret は Replay 耐性があるとは見なされない. Authenticator の出力 —つまり, Secret そのもの— が Authentication ごとに提供されるためである.

### Authentication Intent {#intent}

<!--
An authentication process demonstrates intent if it requires the subject to explicitly respond to each authentication or reauthentication request. The goal of authentication intent is to make it more difficult for authenticators (e.g., multi-factor cryptographic devices) to be used without the subject's knowledge, such as by malware on the endpoint. Authentication intent **SHALL** be established by the authenticator itself, although multi-factor cryptographic devices **MAY** establish intent by reentry of the activation factor for the authenticator.
-->

Subject がそれぞれの Authentication または Reauthentication の要求に明示的に応答する必要がある場合, Authentication Process は Intent (意図)を実証する. Authentication Intent のゴールは, エンドポイント上のマルウェアなどによって, Subject の知らないうちに Authenticator (例: Multi-Factor Cryptographic Device) が使用されるのをより困難にすることである. Authentication Intent は, Authenticator 自体によって確立されることとなる(**SHALL**)が, Multi-Factor Cryptographic Device は, Authenticator の Activation Factor の再入力によって Intent を確立してもよい(**MAY**).

<!--
Authentication intent **MAY** be established in a number of ways. Authentication processes that require the subject's intervention establish intent (e.g., a claimant entering an authenticator output from an OTP device). Cryptographic devices that require user action for each authentication or reauthentication operation also establish intent (e.g., pushing a button or reinsertion).
-->

Authentication Intent は, いろいろな方法で確立されてもよい(**MAY**). Subject の介入を必要とする Authentication Process は, Intent を確立する (例: OTP デバイスからの Authenticator 出力を入力するClaimant). それぞれの Authentication または Reauthentication 操作ごとにユーザーアクションを必要とする暗号デバイスも, Intent を確立する (例: ボタンを押す, 再挿入する).

<!--
Depending on the modality, presentation of a biometric characteristic may or may not establish authentication intent. Behavioral biometrics similarly may or may not establish authentication intent because they do not always require a specific action on the claimant's part.
-->

Modality に応じて, Biometric Characteristic の提示は Authentication Intent を確立する場合と確立しない場合がある. Behavioral Biometrics も, Claimant 側での特定のアクションを必ずしも必要としないため, 同様に Authentication Intent を確立する場合と確立しない場合がある,

### Restricted Authenticators {#restricted}

<!--
As threats evolve, authenticators' capability to resist attacks typically degrades. Conversely, some authenticators' performance may improve, for example, when changes to their underlying standards increases their ability to resist particular attacks.
-->

脅威の進化により, Authenticator の Attack 耐性の性能は通常は低下する. 反対に, 一部の Authenticator のパフォーマンスは, 例えば基となる標準の変更によって特定の Attack 耐性の能力が向上した場合に改善することがある.

<!--
To account for these changes in authenticator performance, NIST places additional restrictions on authenticator types or specific classes or instantiations of an authenticator type.
-->

Authenticator のパフォーマンスのこれらの変化に責任を持つために, NIST は, Authenticator Type, または Authenticator Type の特定のクラスやインスタンス化に追加の制約を課す:

<!--
The use of a *restricted authenticator* requires that the implementing organization assess, understand, and accept the risks associated with that authenticator and acknowledge that risk will likely increase over time. It is the responsibility of the organization to determine the level of acceptable risk for their systems and associated data and to define any methods for mitigating excessive risks. If at any time the organization determines that the risk to any party is unacceptable, then that authenticator **SHALL NOT** be used.
-->

*Restricted Authenticator* の使用は, 実装組織がその Authenticator に関連するリスクを評価, 理解, および受け入れ, リスクが時間の経過とともに増加する可能性があることを認識することを求める. システムと関連データについて許容可能なリスクのレベルを決定し, それを超えるリスクを軽減する方法を定義することは組織の責任である. いずれかの関係者へのリスクが許容できないと組織が判断した場合はいつでも, それ以降その Authenticator が使用されることはない(**SHALL NOT**).

<!--
Further, the risk of an authentication error is typically borne by multiple parties, including the implementing organization, organizations that rely on the authentication decision, and the subscriber. Because the subscriber may be exposed to additional risk when an organization accepts a restricted authenticator and that the subscriber may have a limited understanding of and ability to control that risk, the CSP **SHALL**:
-->

さらに, Authentication エラーのリスクは通常, 実装組織, Authentication の決定に依存する組織, および Subscriber を含む複数の関係者によって負担される. 組織が Restricted Authenticator を受け入れると, Subscriber は追加のリスクにさらされる可能性があり, また Subscriber が持つ理解と制御能力が限られている可能性があるため, CSP は以下を行うこととなる(**SHALL**):

<!--
1. Offer subscribers at least one alternate authenticator that is not restricted and can be used to authenticate at the required AAL.
-->

1. 必要とされる AAL で使用できる少なくとも1つの Restricted でない 代替の Authenticator を Subscriber に提供する.

<!--
2. Provide meaningful notice to subscribers regarding the security risks of the restricted authenticator and availability of alternatives that are not restricted.
-->

2. Restricted Authenticator のセキュリティリスクと Restricted でない代替について, Subscriber に意味のある通知を提供する.

<!--
3. Address any additional risk to subscribers in its risk assessment.
-->

3. Risk Assessment で Subscriber への追加のリスクに取り組む.

<!--
4. Develop a migration plan for the possibility that the restricted authenticator is no longer acceptable at some point in the future and include this migration plan in its [digital identity acceptance statement](../_sp800-63/sec5_DIRM.md#daps){:latex-href="#ref-SP800-63"}.
-->

4. Restricted Authenticator が未来のある時点で受け入れられなくなる可能性について移行計画を作成し, この移行計画をその [digital identity acceptance statement](../_sp800-63/sec5_DIRM.md#daps){:latex-href="#ref-SP800-63"} に含む.

### Activation Secrets {#s-5-2-11}

<!--
Memorized secrets that are used as an activation factor for a multi-factor authenticator are referred to as _activation secrets_. An activation secret is used to decrypt a stored secret key used for authentication or is compared against a locally held stored verifier to provide access to the authentication key. In either of these cases, the activation secret **SHALL** remain within the authenticator and its associated user endpoint.
-->

Multi-Factor Authenticator の Activation Factor として使用される Memorized Secret は, _Activation Secret_ と呼ばれる. Activation Secret は, Authentication に使用される Stored Secret Key を復号するために使用されるか, Authentication Key へのアクセスを提供するためにローカルに保持されている Stored Verifier と比較される. これらのいずれの場合でも, Activation Secret は Authenticator とそれに関連付けられたユーザーエンドポイント内にとどまることとなる(**SHALL**).

<!--
Authenticators making use of activation secrets **SHALL** require the secrets to be at least 6 characters in length. Activation secrets **MAY** be entirely numeric (i.e., a PIN). If alphanumeric (rather than only numeric) values are permitted, all printing ASCII [[RFC20]](references.md#ref-RFC20) characters as well as the space character **SHOULD** be accepted. Unicode [[ISO/ISC 10646]](references.md#ref-ISOIEC10646) characters **SHOULD** be accepted as well in alphanumeric secrets. The authenticator **SHALL** contain a blocklist (either specified by specific values or by an algorithm) of at least 10 commonly used activation values and **SHALL** prevent their use as activation secrets.
-->

Activation Secret を利用する Authenticator は, Secret の長さに少なくとも 6 文字を要求することとなる(**SHALL**). Activation Secret は, すべて数字 (つまり PIN) であってもよい(**MAY**). (数字だけではなく)英数字の値が許可されている場合は, すべての Printing ASCII [[RFC20]](references.md#ref-RFC20) 文字と空白文字が受け入れられる必要がある(**SHOULD**). Unicode [[ISO/ISC 10646]](references.md#ref-ISOIEC10646) 文字もまた, 英数字の Secret に受け入れられる必要がある(**SHOULD**). Authenticator は, (特定の値またはアルゴリズムによって指定された) 少なくとも 10 個のよく使用される Activation 値の Blocklist を含むこととなり(**SHALL**), それらの Activation Secret としての使用を防ぐこととなる(**SHALL**).

<!--
The authenticator or verifier **SHALL** implement a retry-limiting mechanism that effectively limits the number of consecutive failed activation attempts using the authenticator to ten (10). If the entry of an incorrect activation secret causes the authenticator to generate an invalid output that is sent to the central verifier, rate limiting **MAY** be implemented by the verifier. In all other cases, rate limiting **SHALL** be implemented in the authenticator. Once the limit of 10 attempts is reached, the authenticator **SHALL** be disabled and a different authenticator **SHALL** be required for authentication.
-->

Authenticator または Verifier は, Authenticator を使用した Activation の連続失敗の試行を効果的に 10回 に制限する再試行制限メカニズムを実装することとなる(**SHALL**). 正しくない Activation Secret の入力によって Authenticator が中央の Verifier に送信される無効な出力を生成する場合, Verifier によってレート制限が実装されてもよい(**MAY**). すべての他のケースでは, レート制限は Authenticator に実装されることとなる(**SHALL**). ひとたび 10回 の試行の制限に達すると, Authenticator を無効化されることとなり(**SHALL**), Authentication には別の Authenticator が要求されることとなる(**SHALL**).

<!--
If the authenticator verifies the activation secret locally (rather than using it for decryption of a key), verification **SHALL** be performed within a hardware-based authenticator or in a secure element (e.g., TEE, TPM) that releases the authentication secret only upon presentation of the correct activation secret. In other circumstances (i.e., software-based multi-factor authenticators), the authenticator **SHALL** use the memorized secret as a key to decrypt its stored authentication secret. Approved cryptography **SHALL** be used.
-->

Authenticator が Activation Secret を (Key の復号に使用するのではなく) ローカルで Verifiy する場合, Verification は, ハードウェアベースの Authenticator 内, または正しい Activation Secret の提示時にのみ Authentication Secret を解放するセキュアエレメント内 (例: TEE, TPM) で実行されることとなる(**SHALL**). 他の状況 (つまり, Software-Based Multi-Factor Authenticators) では, Authenticator は, 保管された Authentication Secret の復号のために Memorized Secret を Key として使用することとなる(**SHALL**). Approved Cryptography が使用されることとなる(**SHALL**). 

### Connected Authenticators {#s-5-2-12}

<!--
Cryptographic authenticators require a direct connection between the authenticator and the endpoint being authenticated. This connection **MAY** be wired (e.g., USB or direct connection with a smartcard) or wireless (e.g., NFC, Bluetooth). While in most cases wired connections can be presumed to be secure from eavesdropping and adversary-in-the-middle attacks, additional precautions are required for authenticators that are connected via wireless technologies.
-->

Cryptographic Authenticator は, Authenticator と Authenticate されるエンドポイントとの間の直接接続を必要とする. この接続は, 有線 (例: USB またはスマートカードとの直接接続) またはワイヤレス (例: NFC, Bluetooth) でもよい(**MAY**). ほとんどの場合, 有線接続は盗聴や Adversary-in-the-Middle Attack から安全であると推定できるが, ワイヤレス技術を介して接続されている Authenticator には追加の予防措置が必要とされる.

<!--
Wired authenticator connections include both authenticators that are embedded in endpoints (e.g., in a TPM) and those that are connected via an external interface, such as USB. Claimants **SHOULD** be advised to use trusted hardware (cables, etc.) for external connections for additional assurance that they have not been compromised.
-->

有線の Authenticator 接続は, エンドポイントに組み込まれている Authenticator (例: TPMの中) と, USB などの外部インターフェースを介して接続される Authenticator の両方を含む. Claimant は, 彼らが侵害されていないことのさらなる保証のため, 外部接続に信頼されたハードウェア (ケーブルなど) を使用することについてアドバイスを受ける必要がある(**SHOULD**).

<!--
Wireless authenticator connections are potentially vulnerable to threats including eavesdropping, injection, and relay attacks. The potential for such attacks depends on the effective range of the wireless technology being used.
-->

ワイヤレスの Authenticator 接続は, 盗聴, インジェクション, リレー Attack などの脅威に対して潜在的に脆弱である. このような Attack の可能性は, 使用されているワイヤレス技術の有効範囲に依存する.

<!--
Wireless technologies having an effective range of 1 meter or more (e.g., Bluetooth LE) **SHALL** use an authenticated encrypted connection between the authenticator and endpoint. A pairing process **SHALL** be used to establish a key for encrypted communication between the authenticator and endpoint. A temporary wired connection between the devices **MAY** also be used to establish the key in lieu of the pairing process. The pairing process **SHALL** be authenticated through the use of a pairing code. The pairing code **SHALL** be associated with either the authenticator or endpoint and **SHALL** have at least 20 bits or 6 decimal digits of entropy. The pairing code **MAY** be printed on the associated device and **SHALL** be conveyed between the devices by manual entry or by using a QR code or similar representation that is optically communicated. An example of this is the pairing code used with the virtual contact interface specified in [[SP800-73]](references.md#ref-SP800-73). The entire authentication transaction **SHALL** be encrypted using a key established by the pairing process.
-->

 1 メートル以上の有効範囲を持つワイヤレス技術 (例: Bluetooth LE) は, Authenticator とエンドポイントの間で Authenticate された暗号化接続を使用することとなる(**SHALL**). ペアリングプロセスは,  Authenticator とエンドポイント間の暗号化通信用の Key を確立するために使用される. ペアリングプロセスの代わりに, デバイス間の一時的な有線接続が Key を確立するために使用されてもよい(**MAY**). ペアリングプロセスは, ペアリングコードを使用することで Authenticate されることとなる(**SHALL**). ペアリングコードは, Authenticator またはエンドポイントのいずれかに関連付けられることとなり(**SHALL**), 少なくとも 20 ビットまたは 10 進数 6 桁の Entropy を持つこととなる(**SHALL**). ペアリングコードは, 関連付けられたデバイスに印刷してもよく(**MAY**), 手動入力, または光学的に伝達される QR コードか同様の提示方法を使用して, デバイス間で伝達することとなる(**SHALL**). この例は, [[SP800-73]](references.md#ref-SP800-73) で指定された仮想コンタクトインターフェースで使用されるペアリングコードである. Authentication Transaction 全体は, ペアリングプロセスによって確立された Key を使用して暗号化されることとなる(**SHALL**).

<!--
When a wireless technology with an effective range of less than 1 meter is in use (e.g., NFC), the activation secret, if any, transmitted from the endpoint to authenticator **SHALL** be encrypted using a key established through a pairing process between the devices or through a temporary wired connection. An authenticated connection using a pairing code meeting the above requirements **SHOULD** be used. If the authenticator is configured to require authenticated pairing, pairing code **SHALL** be used.
-->

1 メートル未満の有効範囲を持つワイヤレス技術 (例: NFC) が使用されている場合, エンドポイントから Authenticator に送信される Activation Secret がもしあれば, デバイス間のペアリングプロセスまたは一時的な有線接続を介して確立された Key を使用して暗号化されることとなる(**SHALL**). 上記の要件を満たすペアリング コードを使用した Authenticate された接続を使用する必要がある(**SHOULD**). Authenticator が Authenticate されたペアリングを要求するように構成されている場合, ペアリングコードが使用されることとなる(**SHALL**).

<!--
> Note: Encryption of only the activation secret, and not the entire authentication transaction, may expose sensitive information such as the identity of the relying party, although this would require the attacker to be very close to the subscriber. Special care should be taken with authenticators containing personally identifiable information that do not require authenticated pairing to protect that information against "skimming" and eavesdropping attacks.
-->

> 注: Authentication Transaction 全体ではなく Activation Secret のみの暗号化は, Relying Party の Identity などのセンシティブ情報を晒してしまう可能性があるが, これには Attacker が Subscriber の非常に近くにいる必要がある. "スキミング" や Eavesdropping Attack から情報を保護するために, Authenticate されたペアリングを必要としない, 個人を特定できる情報を含む Authenticator には, 特別な注意を払う必要がある.

<!--
The key established as a result of the pairing process **MAY** be either temporary (valid for a limited number of transactions or time) or persistent. A mechanism for endpoints to remove persistent keys **SHALL** be provided.
-->

ペアリングプロセスの結果として確立された Key は, 一時的 (限られた数のトランザクションまたは時間に対して有効) または永続的のどちらであってもよい(**MAY**). 永続 Key を削除するエンドポイントのメカニズムが提供されることとなる(**SHALL**).

<!--
Where cryptographic operations are required, approved cryptography **SHALL** be used. All communication of authentication data between authenticators and endpoints **SHALL** occur directly between those devices or through an authenticated protected channel between the authenticator and endpoint.
-->

暗号操作が必要なところでは, Approved Cryptography を使用することとなる(**SHALL**). Authenticator とエンドポイント間の Authentication データのすべての通信は, これらのデバイス間で直接行われるか, Authenticator とエンドポイント間の Authenticated Protected Channel を介して行われることとなる(**SHALL**).