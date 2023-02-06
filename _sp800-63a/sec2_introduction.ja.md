---
layout: default.ja
title: Introduction
navOrder: 2
navTitle: Introduction
permalink: /sp800-63a/introduction/
anchor: purpose
section: 2
---

#  Introduction {#intro}

_This section is informative._

オンラインサービスを提供する際の課題の1つは、一連の活動を特定の個人と関連付けることができるようにすることである。匿名またはpseudonymityが望ましい場合など、この必要がない場合もあるが、実存する Subject との関連付けを確実に確立することが重要な場合もある。例えば、行政サービスの利用や金融取引の実行などである。また、実存する Subject との関連付けが、規制（たとえば、金融業界の「Know Your Customer」要件）やハイリスクのアクション（たとえば、ダムからの放水量の変更）に対する説明責任を確立するために必要とされる状況も存在する。

{% comment %}
One of the challenges of providing online services is being able to associate a set of activities with a single, specific individual. While there are situations where this is not necessary - such as when anonymity or pseudonymity is desirable - there are other situations where it is important to reliably establish an association with a real-life subject. Examples of this include accessing some government services or executing financial transactions. There are also situations where association with a real-life subject is required by regulations (e.g., the financial industry's 'Know Your Customer' requirements) or to establish accountability for high-risk actions (e.g., changing the release rate of water from a dam).
{% endcomment %}


このガイダンスは、Identity Proofing を、オンライン・サービスにアクセスする Subject と実存する人物との関係性を、ある程度の確実性または保証をもって確立するプロセスのことであると定義する。本書は、連邦機関、サードパーティのCredential Service Providers(CSP)、そしてIdentity Proofingサービスを提供する他の組織に対するガイダンスを提供する。

{% comment %}
This guidance defines identity proofing as the process of establishing, to some degree of certainty or assurance, a relationship between a subject accessing online services and a real-life person. This document provides guidance for Federal Agencies, third-party Credential Service Providers (CSP), and other organizations that provide identity proofing services.
{% endcomment %}

次のリストは、本書のどのセクションに normative な言語が含まれ、どのセクションにnon-normative、informativeな言語が含まれるかを示している。特定の要件を明確にするために必要な場合、normativeなセクションには多くの場合informativeな説明が含まれている。どの記述がnormativeで、どれがそうでないかを明確にするには、本書の「Requirements Notation and Conventions」のセクションを参照すること。

{% comment %}
The following list states which sections of this document contain normative language and which contain non-normative, informative language.  Where needed to help clarify specific requirements, normative sections often include informative explanations.  See the "Requirements Notation and Conventions" section of this document for clarification on which statements are normative and which are not.  
{% endcomment %}

- 1 Purpose _Informative_
- 2 Introduction _Informative_
- 3 Definitions and Abbreviations _Informative_
- 4 Identity Assurance Level Requirements _Normative_
- 5 Identity Resolution, Validation, and Verification _Normative_
- 6 Subscriber Accounts _Normative_
- 7 Threats and Security Considerations _Informative_
- 8 Privacy Considerations _Informative_
- 9 Usability Considerations _Informative_
- 10 Equity Considerations _Informative_

{% comment %}

- 1 Purpose _Informative_
- 2 Introduction _Informative_
- 3 Definitions and Abbreviations _Informative_
- 4 Identity Assurance Level Requirements _Normative_
- 5 Identity Resolution, Validation, and Verification _Normative_
- 6 Subscriber Accounts _Normative_
- 7 Threats and Security Considerations _Informative_
- 8 Privacy Considerations _Informative_
- 9 Usability Considerations _Informative_
- 10 Equity Considerations _Informative_

{% endcomment %}

## Identity Proofingに期待される結果

{% comment %}

## Expected Outcomes of Identity Proofing

{% endcomment %}

Identity Proofingに期待される成果は: 

* **Identity resolution**: によりClaimされたアイデンティティが、CSPサーバーのユーザー母集団の文脈で単一で一意な個人であると判断し、
* **Evidence validation**: により提出された全てのエビデンスが全て本物で、真正性があり、有効期限が切れていないことを確認し、
* **Attribute validation**: により Core Attributeの正確性を確認し、
* **Identity verification**: Claim されたアイデンティティと、Identity Evidence を提出した実存する人物とが結びついていることを検証し、
* **Fraud Prevention**: 便益、サービス、データあるいはアセットに対する欺瞞的なアクセスの試みを緩和することである。

{% comment %}
The expected outcomes of identity proofing include:

* **Identity resolution**: determine that the claimed identity corresponds to a single, unique individual within the context of the population of users the CSP serves;
* **Evidence validation**: confirm that all supplied evidence is genuine, authentic, and unexpired;
* **Attribute validation**: confirm the accuracy of core attributes;
* **Identity verification**: verify that the claimed identity is associated with the real-life person supplying the identity evidence; and
* **Fraud Prevention**: mitigate attempts to gain fraudulent access to benefits, services, data, or assets.
{% endcomment %}

## Identity Assurance Levels

Subscriberのアイデンティティの保証は、次のIdentity Assurance Levels (IAL)のいずれかを用いて記述される。後続する各 IAL は、より高い保証を達成するために、より低い IAL の要件の上に構築される。  

{% comment %}
Assurance in a subscriber's identity is described using one of the following Identity Assurance Levels (IAL). Each successive IAL builds on the requirements of lower IALs in order to achieve greater assurance.   
{% endcomment %}


**Identity Proofingなし (IAL0)**: Applicantと特定の実在するアイデンティティとをリンクする要件はない。Subjectの活動に伴って提供されるすべてのAttributeは、自己申告または自己申告として扱われる。自己申告のAttributeはIAL0ではValidateもVerifyもされない。

{% comment %}
**No identity proofing (IAL0)**: There is no requirement to link the applicant to a specific, real-life identity. Any attributes provided in conjunction with the Subject's activities are self-asserted and are treated as self-asserted. Self-asserted attributes at IAL0 are neither validated nor verified.
{% endcomment %}

**IAL1**: Identity Proofing プロセスは、Claimされたアイデンティティが現実世界に存在することを裏付ける。Core Attributeは Identity Evidence から得たものや、Applicantから申告されたものである。すべての Core AttributeはAuthoritativeあるいは信用できるソースに対してValidateされ、Identity Proofingプロセス実施下にある個人と、Attributeとを結びつけるための方策を講じる。

{% comment %}
**IAL1**: The identity proofing process supports the real-world existence of the claimed identity. Core attributes are obtained from identity evidence or asserted by the applicant.  All core attributes are validated against authoritative or credible sources and steps are taken to link the attributes to the person undergoing the identity proofing process.   
{% endcomment %} 

**IAL2**: IAL2 は、より強力なタイプのエビデンスの収集と、エビデンスをvalidateしアイデンティティをverifyするためのより厳密なプロセスを要求することにより、Identity Proofingプロセスにさらなる厳密さを追加する。

{% comment %} 
**IAL2**: IAL2 adds additional rigor to the identity proofing process by requiring the collection of stronger types of evidence and a more rigorous process for validating the evidence and verifying the identity. 
{% endcomment %} 

**IAL3**: IAL3 は、訓練を受けた CSP 担当者が、対面または監視下でのリモートIdentity Proofingセッションを介して、 Identity Proofingセッション全体にわたってApplicantと直接やりとりするための要件を追加している。

{% comment %} 
**IAL3**: IAL3 adds the requirement for a trained CSP representative to interact directly with the applicant during the entire identity proofing session, either in person or via a supervised remote identity proofing session.
{% endcomment %} 

