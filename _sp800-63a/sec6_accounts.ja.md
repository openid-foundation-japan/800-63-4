---
layout: default.ja
title: Subscriber Accounts
navOrder: 6
navTitle: accounts
permalink: /sp800-63a/accounts/
anchor: accounts
section: 6
---

# Subscriber Accounts {#accounts}

_This section is normative._

## Subscriber Accounts

オンラインサービスへの 1 回限りのアクセスを提供する目的の Identity Proofing、または Applicant がアカウントへの Enrollment を拒否した場合を除き、CSP は Applicant をその Identity サービスの Subscriber として Enroll し、 Applicant の Identity Proofing の成功後にその Subscriber 用の固有の _subscriber account_ を確立するものとする（**SHALL**）。

{% comment %}
With the exception of identity proofing for the purposes of providing one-time access to an online service, or when an applicant declines enrollment into an account, the CSP **SHALL** enroll the applicant as a subscriber into its identity service and establish a unique _subscriber account_ for that subscriber following the successful identity proofing of an applicant. 
{% endcomment %}

CSP は、各 Subscriber Account に一意の識別子を割り当てるものとする（**SHALL**）。

少なくとも、CSP は各 Subscriber Account に以下の情報を含めるものとする。（**SHALL**）。

* Subscriberのために確立された一意の識別子。
* [Sec. 5.1.1](sec5_ial.ja.md#DocRecReqs) に従って Subscriber のために完了した Identity Proofing ステップの記録
* Subscriber の Identity Proofing が無事に達成された際の最大 IAL
* Subscriber Account に保持されている個人情報または機微情報の処理、保持、または開示に対して提供された Subscriber の同意。
* Subscriber Account に現在バインドされているすべてのAuthenticator。それが Enrollment時に登録されたか、Enrollment後に登録されたかに関わらない。
* RP アクセスをサポートするために、Identity Proofing プロセス中またはその後のトランザクションでValidateされたすべてのAttribute。

{% comment %}
The CSP **SHALL** assign a unique identifier to each subscriber account. 

At a minimum the CSP **SHALL** include the following information in each subscriber account:

* Unique identifier established for the subscriber
* A record of the identity proofing steps completed for the subscriber in accordance with [Sec. 5.1.1](sec5_ial.md#DocRecReqs)
* Maximum IAL successfully achieved for the identity proofing of the subscriber
* Subscriber consent provided for the processing, retention, or disclosure of any personal or sensitive information maintained in the subscriber account
* All authenticators currently bound to the subscriber account, whether registered at enrollment or subsequent to enrollment
* All attributes that were validated during the identity proofing process or in subsequent transactions to support RP access 
{% endcomment %}

CSP は、各 Subscriber の Identity Proofing プロセス中に収集された、またはその後更新された、以下を含む情報を Subscriber Account に記録するものとする:

* Validate された Identity Evidence 
* Validate された Attribute情報
* CSP の Identity サービスへの Enrollment のために収集された Attribute 情報（Identity Proofing の目的では Validate されていない）

CSP は、[Sec. 5.1.2](sec5_ial.ja.md#PrivacyReqs) に従って、Subscriber Account に保持されるあらゆる個人情報の処理、保持、または開示についてプライバシーリスク評価を実施するものとする（**SHALL**）。

{% comment %}
The CSP **SHALL** record information in the subscriber account that was collected during the identity proofing process or subsequently updated for each subscriber, including:

* Validated identity evidence
* Validated attribute information
* Attribute information that was collected for enrollment in the CSP identity service that was not validated for identity proofing purposes

The CSP **SHALL** perform a privacy risk assessment for the processing, retention, or disclosure of any personal information maintained in the subscriber account in accordance with [Sec. 5.1.2](sec5_ial.md#PrivacyReqs).
{% endcomment %}

## Subscriber Account Access

PII を含むアカウントを多要素認証（MFA）で保護するという要件を満たすために、CSP は、Subscriber Account に登録されたAuthenticatorを使用して、AAL2 または AAL3 認証プロセスにより Subscriber Accountの 情報にアクセスする方法を提供するものとする(**SHALL**)。

CSP は、Subscriber が Subscriber Account に含まれる個人情報を変更または更新するための機能を提供するものとする（**SHALL**）。

{% comment %}
In order to meet the requirement that accounts containing PII be protected by multi-factor authentication (MFA), the CSP **SHALL** provide a way for subscribers to access the information in their subscriber account through AAL2 or AAL3 authentication processes using authenticators registered to the subscriber account. 

The CSP **SHALL** provide the capability for subscribers to change or update the personal information contained in their subscriber account.
{% endcomment %}

## Subscriber Account Lifecycle

### Subscriber Account Activity

CSP は、以下で説明するように、Enrollment 時からアカウント閉鎖時まで、CSP Identity システム内のアクティブな各 Subscriber について一意の Subscriber Account を設け、維持するものとする(**SHALL**)。 アカウントが閉鎖されるまで、CSP は、Subscriber Account、アカウントに含まれる情報、および 登録された Authenticator の使用を提供するものとする(**SHALL**)。

{% comment %}
The CSP **SHALL** establish and maintain a unique subscriber account for each active subscriber in the CSP identity system from the time of enrollment to the time of account closure, as described below.  Until the account is closed, the CSP **SHALL** provide for the use of the subscriber account, information contained in the account, and registered authenticators. 
{% endcomment %}

### Subscriber Account Termination

CSP は、以下のいずれかが発生した場合、Subscriber Account を終了させ、その使用を中止するものとする。

* Subscriber が CSP の Subscriber Account の終了を選択した場合 
* CSP は、CSP が定める任意の期限付き通知期間および要件に従って、Subscriber Account が侵害されたと判断した場合
* CSP は、CSP が定める任意の期限付き通知期間および要件に従って、Subscriber が CSP Identity サービスへの参加に関するポリシーまたは規則に違反したと判断する。
* CSP は、CSP が定める任意の期限付き通知期間および要件に従って、Subscriber Account が非アクティブであることを、CSP が定めるポリシーまたは規則に従って判断する。
* CSP は、Identity システムおよびサービスの運用を停止する。

CSP は、アカウント終了後に、Subscriber Account の記録から個人情報または機微情報を、記録保持と廃棄の要件に従ってすべて削除するものとする(**SHALL**)

{% comment %}
The CSP **SHALL** terminate the subscriber account and discontinue its use when one of the following occur:

* The subscriber elects to terminate their subscriber account with the CSP.
* The CSP determines, following any due notice period and requirements established by the CSP, that the subscriber account has been compromised.
* The CSP determines, following any due notice period and requirements established by the CSP, that the subscriber has violated the policies or rules for participation in the CSP identity service.
* The CSP determines, following any due notice period and requirements established by the CSP, that the subscriber account is inactive in accordance with the policies or rules established by the CSP.
* The CSP ceases identity system and services operations.

The CSP **SHALL** delete any personal or sensitive information from the subscriber account records following account termination in accordance with the record retention and disposal requirements.

{% endcomment %}