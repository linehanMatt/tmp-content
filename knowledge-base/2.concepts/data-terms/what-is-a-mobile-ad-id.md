---
title: 'What is a mobile ad ID?'
description: 'A mobile advertising identifier, or MAID, is a unique pseudo-anonymous identifier tied to a mobile phone. '
lastUpdated: '2023-06-14T18:21:21.098Z'
tags: ['Data Types', 'General Attributes']
---
### Overview

Mobile phones offer several APIs to developers that allow them to collect data about the phone itself as well as the phone's usage patterns. Both iOS and Android have created unique identifiers that enable data to be pseudo-anonymously be tied back to the phone where it was collected. Those identifiers are known as mobile advertising identifiers, mobile ad IDs, or simply MAIDs.

### Types

The different mobile operating systems have slightly different implementations of MAIDs. In practice, they work the same way but are sometimes referred to by their vendor-specific names.

#### Apple / iOS / IDFA

Apple's implementation of the MAID on iOS is called the Identifier For Advertisers or [IDFA](https://developer.apple.com/documentation/adsupport/asidentifiermanager). The IDFA consists of 32 hyphen-separated characters.

Example:

918F1D4F-D195-4A8B-AF47-44683FE11DB9

#### Google / Android/ GAID

Google's implementation of the MAID on Android is called the Advertising Identifier or [Ad Id](https://support.google.com/googleplay/android-developer/answer/6048248?hl=en). Like the IDFA, it consists of 32 hyphen-separated characters.

Example:

3f097372-f01e-4b64-984c-395ae5828ee6

### Privacy

MAIDs were initially developed to be privacy-safe identifiers that would allow for data collection, but wouldn't allow the collector to tie it back to an identifiable person. The identifiers are [pseudo-anonymous](https://en.wikipedia.org/wiki/Pseudonymization) because they lack any personally identifiable information.

By design, these identifiers are resettable and Apple and Android both offer mechanisms to opt-out of data collection:

* [iPhone Users Guide: Limit Ad Tracking](https://support.apple.com/guide/iphone/limit-ad-targeting-iphf60a6a256/ios)
* [Google Support: Control the Ads You See](https://support.google.com/ads/answer/2662856?co=GENIE.Platform%3DAndroid&hl=en)

### Recap

The mobile ad ID's creation allowed mobile applications to pseudo-anonymously collect data about the usage patterns of a mobile phone. The mobile operating systems, primarily Android and iOS, control how MAIDs work, including allowing users to opt-out of their usage.
