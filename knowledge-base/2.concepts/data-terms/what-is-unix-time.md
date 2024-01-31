---
title: 'What is Unix Time?'
description: 'An introduction to Unix time, its significance, examples, limitations, and how it is utilized within Narrative’s Data Streaming Platform.'
lastUpdated: '2024-01-31'
tags: ['Data Types', 'General Attributes']
---

### Overview

Unix time, a concept originating from the Unix operating system developed in the 1960s, represents timestamps as the number of seconds elapsed since January 1st, 1970 at 00:00:00 UTC, known as the Unix epoch. This method simplifies parsing and utilizing time across various systems by representing it as an integer. Narrative’s Data Streaming Platform, for instance, defaults to using Unix time in milliseconds for all timestamp fields.

### Unix Epoch

The Unix epoch, January 1st, 1970 at 00:00:00 UTC, was chosen by early Unix engineers as a convenient and uniform start point for representing time.

### Examples

Below are some examples of dates and their corresponding Unix time representation:

| Date / Time             | Unix Time  |
|-------------------------|------------|
| January 1st, 1970 00:00:00 | 0          |
| June 6th, 1983 00:00:00    | 423705600  |
| June 6th, 1983 16:00:00    | 423763200  |
| September 9, 2001 1:46:40  | 1000000000 |
| July 20th, 1969 20:17:40   | -14182940  |

### Limitations

#### Year 2038 Problem

Unix time faces the Year 2038 problem, akin to the Y2K issue, where systems assuming a 32-bit storage for Unix time will encounter errors or crashes after 03:14:07 UTC on January 19, 2038, as times then exceed 32-bit storage capacity.

#### Leap Seconds

Leap seconds are not accounted for in Unix time, assuming each day has exactly 86,400 seconds, leading to discrepancies with true UTC time.

#### Pre-1970 Timestamps

Dates before 1970 are represented as negative numbers in Unix time, counting seconds back to the Unix epoch.

### Variations

For more precise time representation, Unix time can be adapted:

#### Unix Time with Decimals

Fractions of a second are represented using decimals to provide greater precision.

#### Unix Time in Milliseconds

Narrative adopts this method, representing time as the number of milliseconds since the Unix epoch, allowing for more detailed timestamp data.

### Additional Resources

- Wikipedia on the [Year 2038 Problem](https://en.wikipedia.org/wiki/Year_2038_problem)
- Wikipedia on [Unix time](https://en.wikipedia.org/wiki/Unix_time)
- [Epoch Converter](https://www.epochconverter.com/) for practical conversions between Unix time and standard dates.

This article serves as an introduction to Unix time, offering insights into its application, examples, and addressing its inherent limitations and variations.
