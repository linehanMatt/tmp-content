---
title: 'What is pseudonymization?'
description: 'Pseudonymization is a technique to replaces personally identifiable information from a data record with artificial identifiers that are privacy safe'
lastUpdated: '2020-01-20T12:46:07.633Z'
tags: ['Legal / Compliance / Privacy', 'Concepts']
---
### Overview

Pseudonymization removes information from a data record that might be [personally identifiable](/knowledge-base/concepts/data-terms/what-is-pii). The technique preserves the uniqueness of the record while ensuring it is privacy-safe.

### Differences From Anonymization

Pseudonymization and anonymization differ in that anonymization irreversibly eliminates the ability to identify the person on whom the data was collected. Pseudonymization is done through substitution of attributes on a data record. A pseudonymous record is not personally identifiable on its own, but when combined with other data, it may allow for re-identification.

### Techniques

A number of different pseudonymization techniques exist. These techniques are typically chosen based on the attributes being pseudonymized, and each has its own pros and cons.

#### Hashing

[Hashing](/knowledge-base/concepts/data-terms/what-is-hashing) is a technique that generates a new value from a string of text using a mathematical function. Hashing is one way, meaning that you can not turn the new value into the original string. This enables security and makes it particularly suited to pseudonymization of identifiers that are considered PII like e-mail addresses.

#### Blurring

Data blurring is a technique that approximates data values to render their meaning obsolete. A typical example is when software replaces the first five digits of a social security number with the letter X: "XXX-XX-1234."

#### Bucketing

Bucketing of data is another common technique to make an attribute less specific and, therefore, less identifying. Data records containing age often use this technique. For example, if a record includes a person's actual age, 42, that age may be bucketed into a range of 40-49.

### Regulations

Many jurisdictions have started regulating the use of consumer data. Those regulations often rely on data processors to use pseudonymization as a technique to preserve consumer privacy.

#### General Data Protection Regulation (GDPR)

GDPR is a European regulatory framework that governs how consumer data is collected and used in regards to European citizens. It defines pseudonymization:

> 'Pseudonymisation' means the processing of personal data in such a manner that the personal data can no longer be attributed to a specific data subject without the use of additional information, provided that such additional information is kept separately and is subject to technical and organisational measures to ensure that the personal data are not attributed to an identified or identifiable natural person.

and further defines _personal data_ and _data subject_:

> 'Personal data' means any information relating to an identified or identifiable natural person ('data subject'); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person.

#### California Consumer Privacy Act (CCPA)

CCPA is a data protection regulation passed in the State of California. Like GDPR it too defines pseudonymization:

> (r) “Pseudonymize” or “Pseudonymization” means the processing of personal information in a manner that renders the personal information no longer attributable to a specific consumer without the use of additional information, provided that the additional information is kept separately and is subject to technical and organizational measures to ensure that the personal information is not attributed to an identified or identifiable consumer.

### Additional Resources

Learn more about pseudonymization:

* Wikipedia: [Pseudonymization](https://en.wikipedia.org/wiki/Pseudonymization)
* Wikipedia: [De-identification](https://en.wikipedia.org/wiki/De-identification)
* Wikipedia: [Hashing function](https://en.wikipedia.org/wiki/Hash_function)
* Wikipedia: [Data re-identification](https://en.wikipedia.org/wiki/Data_re-identification)
* European Commission: [Data protection](https://ec.europa.eu/info/law/law-topic/data-protection_en)
* State of California: [CCPA](https://oag.ca.gov/privacy/ccpa)
