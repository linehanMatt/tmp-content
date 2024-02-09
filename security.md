---
title: 'Security Practices at Narrative'
description: 'An overview of Narrative’s commitment to security, including SOC 2 compliance, security policies, data encryption, and vulnerability management.'
lastUpdated: '2024-02-09T23:05:19.054Z'
tags: ['security', 'SOC 2', 'data encryption', 'vulnerability management']
layout: 'urban-dawn'
---


**CONTACT: security@narrative.io**

At Narrative, we believe security is critically important. We are committed to maintaining industry-standard security controls and best practices to protect our systems and the data we handle.

## SOC 2

Narrative has been evaluated by a third-party auditor and is SOC 2 compliant. Customers can request a copy of our most recent report [here](https://share.hsforms.com/1TXka85p6S_SdPYOJ5klH2g38eec).

## Security Policies & Procedures

Narrative maintains a comprehensive program of security policies and procedures, and management reviews and updates policies annually or as needed.

## Vulnerability Management & Remediation

Narrative performs regular vulnerability scanning and penetration testing of our applications and systems to identify and address any potential security weaknesses. Vulnerabilities are reported, evaluated, tracked, and resolved according to standardized procedures and time requirements.

## Data Encryption

All customer data is encrypted "At-Rest" using industry-accepted algorithms (e.g., AES-256, RSA-2048) and "In-Transit" using Secure Socket Layer (SSL) or Transport Layer Security (TLS) protocols with a minimum of TLS v1.2. Encryption standards are regularly reviewed and will be updated in accordance with assessed risk and market acceptance of new standards.

## Secure Development Lifecycle

Our Software Development Lifecycle policy covers all stages of development and requires — among other things — separation of duties, code review, approval processes, and change control standards.

## Monitoring

We continuously monitor our security controls and devices to help us immediately detect and respond to any potential security incidents. We also use an integrated compliance platform to make sure our controls and procedures are properly enforced at all times. Our comprehensive Security & Compliance Report is accessible [here](https://app.drata.com/security-report/e8d6f937-57f6-4605-9306-fdcd235bce16/daf052e3-6a37-4986-97bc-18b1e27f0960?region=NA).

## Employee Training & Awareness

All employees complete ongoing security training and awareness programs and are required to regularly review and accept our security policies. Engineers are also required to complete additional training, which includes content provided by OWASP.

## Access Controls

We implement role-based access controls based on the “least-privilege” principle to ensure employees only have access to systems and applications necessary for their role. Narrative management regularly reviews access and can revoke it as needed. All employees are pre-screened and required to sign confidentiality agreements upon hiring. Multi-factor authentication is required for any and all systems that provide the option.

## Third-party Audits and Assessments

Independent third-party audits and assessments are performed at least annually to validate the effectiveness of our controls and procedures.

## Vulnerability Disclosure Program

If you believe you've found a security issue in our product or service, we encourage you to notify us so we can take steps to address it as quickly as possible.

We consider the following vulnerabilities out of scope:

- Clickjacking on pages with no sensitive actions
- Man-in-middle attacks
- Attacks requiring physical access to the victim’s computer
- Social engineering, phishing, or other fraud including but not limited to:
  - Internationalized domain name (IDN) homograph attacks
  - Right-to-left (RTL) Ambiguity
  - RTL Override (RTLO)
  - Tabnabbing
- Any activity that could lead to disruption of our services (DoS)
- Missing DNSSEC, CAA, or CSP headers
- CSRF without any security impact
- Lack of Secure or HTTP only flag on non-sensitive cookies
- Reports about CVEs published on mailing lists, groups etc. without demonstrating an impact on Narrative

*Narrative reserves the right to designate any reported vulnerability as out of scope.*

Please respect the following guidelines:

- Do not run automated scanners on our infrastructure or dashboard.
- Do not exploit the vulnerability or problem you have discovered, for example by downloading more data than necessary to demonstrate the vulnerability or deleting or modifying other people's data.
- Do not reveal the problem to others until it has been resolved.
- Do not use attacks on physical security, social engineering, distributed denial of service, spam or applications of third parties.
- Do provide sufficient information to reproduce the problem, so we will be able to resolve it as quickly as possible. Usually, the IP address or the URL of the affected system and a description of the vulnerability will be sufficient, but complex vulnerabilities may require further explanation.

## How to report a vulnerability

Please e-mail your findings to security@narrative.io and include enough information to reproduce the problem. Usually, the IP address or the URL of the affected system and a description of the vulnerability will be sufficient. We will respond to your report within 3 business days with our evaluation of the report and an expected resolution date.

- If you have followed the instructions above, we will not take any legal action against you in regard to the report.
- We will handle your report with strict confidentiality, and not pass on your personal details to third parties without your permission.
- We will keep you informed of the progress towards resolving the problem.
- In the public information concerning the problem reported, we will give your name as the discoverer of the problem (unless you desire otherwise).
