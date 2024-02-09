---
title: 'What does the term "hash" mean?'
description: 'To hash something (hashing) is the colloquial term for a cryptographic hash function.  Hashing takes an input and uses mathematical techniques to produce an output of a predetermined length.  Hashing is often used to pseudonymize data.'
lastUpdated: '2020-12-02T15:34:27.505Z'
tags: ['Legal / Compliance / Privacy', 'Concepts']
---

### Overview

_Hashing_ and _hash_ are common terms that are used when discussing data, privacy, and pseudonymization. Hashing has a number of properties that make it particularly well suited for the job of pseudonymization but it isn't without its limitations. Here we'll discuss its important properties, how its used, and talk about some of the shortcomings.

### Properties

Hashes have a number of properties that make them useful for various use cases. We'll focus here on the properties that make them particularly well suited for pseudonymization.

#### Speed / Computational Efficiency

When used for pseudonymization, it isn't uncommon to hash billions of attributes.  The scale involved in this hashing requires that the hashing itself be quick.

#### Consistency / Deterministic

One way hashes will always produce the same output for a given input. This is important in ensuring that regardless of when or on what system a hash has been generated, it is guaranteed that the same input generated at a later time or on a different computer will result in the same output.

#### Collision Resistant

A hash function becomes less useful if different inputs can produce the same output. Ideally, every input would have a unique output. Because the output of hash functions is of fixed length, it is impossible to ensure that input of arbitrary length won't produce identical output, but well-designed hash functions minimize the likelihood of such collisions.

As an example, the likelihood of finding a collision using the SHA-1 hashing function is 2^160.

#### Irreversible

When used for pseudonymization an important property of a hash function is that it is irreversible (referred to as a one-way hash). When using a one-way hash it is not possible to reverse the output of the function into the original input. This ensures that if someone has the hash (the output of the hash function) they can not reverse engineer it back to the original text, which is why one-way hashes provide protections against revealing [personally identifiable information](/knowledge-base/concepts/data-terms/what-is-pii) (PII).

### Example Hash Functions

There exist dozens of different hashing functions. For use in pseudonymization, the three most common are discussed below. For each function, we've hashed the string "Narrative" (no quotes) and you can see the resulting output.

* MD5: The details of the MD5 hash function were first published in 1992. The output of the hash function will always be 32 characters.
  * "Narrative" output: _**0c036b871e3c66c1724f68fd007c4718**_

* SHA-1: SHA-1 was first published in 1995. The output is 40 characters in length.
  * "Narrative" output: _**fafe72dfca878eb2084fb7478a44d279f7895b9b**_

* SHA-2: Published in 2001, SHA-2 has a number of different variants. The most common for pseudonymization is SHA-256 which produces an output of 64 characters.
  * "Narrative" output: **_ed2e59c337d01185f388a4e9334d6f2e5cb29652f222afe4b692582d2e1c3fce_**

When hashing an attribute it is a best practice to create all three variants of the hash to ensure interoperability across different tools / platforms.

### Use in Pseudonymization

Hashing is typically used in pseudonymization to take attributes that are considered personally identifiable (PII) and create a unique yet non-personally identifiable equivalent.  Here is an example of a simple record:

_**Email**_

_**Age**_

_**Gender**_

<foo@bar.com>

36

Female

The record contains an email address that is considered PII along with two demographic traits that are not considered PII.  By using a hashing function (MD5 in this example) we can change the record to remove the PII while preserving the underlying structure and signal:

_**MD5 Email Hash**_

_**Age**_

_**Gender**_

_f3ada405ce890b6f8204094deb12d8a8_

36

Female

#### Considerations

* Case / Whitespace Sensitivity:  Hash functions are sensitive to their input.  Two strings, one capitalized and one lower case, will produce two different outputs.  Because of this, it is important to choose a standard casing for any strings where the input is not case sensitive.  Typically lowercasing the entire string for input like email addresses is recommended.   The input should also be stripped of any whitespace (leading or trailing spaces) as these will also impact the output.  
  * MD5 Hash of "narrative": _**a936fba0061bf85904722500de008e51**_
  * MD5 Hash of "NARRATIVE": _**2402a932631e086f028721943b7350c8**_
* Dictionary Attacks:  While one-way hash functions are irreversible, it is possible to create what are called hash dictionaries for certain types of inputs.  Dictionaries create a mapping between inputs and outputs.  If such a mapping exists, someone can then look at the output generated by the hash and lookup the corresponding input, eliminating the property of irreversibility.  In practice, these attacks are only effective where the full set of possible inputs is known.    As a practical example, it doesn't make sense to use one-way hashes to pseudonymize phone numbers. For a nine-digit phone number, there are only 10 billion possible outputs meaning an attacker with enough resources could create a dictionary of all 10 billion numbers making the hash entirely ineffective in protecting the input. Strings like e-mails are safer from these attacks because they can be much longer and contain many more unique characters than a phone number.

### Additional Resources

* [Cryptographic Hash Functions Explained: A Beginner’s Guide](https://komodoplatform.com/cryptographic-hash-function/)
* [SHA-2 Hash Generator](https://www.browserling.com/tools/sha2-hash)
