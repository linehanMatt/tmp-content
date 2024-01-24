---
title: 'What is Unix time?'
description: 'Unix time is a system for representing a point in time.  It is the number of seconds that have elapsed since January 1st, 1970 00:00:00 UTC.'
lastUpdated: '2022-05-31T13:14:33.015Z'
tags: ['Data Types', 'General Attributes']
---
### Overview

Unix is an operating system originally developed in the 1960s.  Unix time is a way of representing a timestamp by representing the time as the number of seconds since January 1st, 1970 at 00:00:00 UTC.  One of the primary benefits of using Unix time is that it can be represented as an integer making it easier to parse and use across different systems. 

Narrative's Data Streaming Platform defaults to using Unix time (in milliseconds) for all timestamp fields.  

### Unix Epoch

January 1st, 1970 at 00:00:00 UTC is referred to as the Unix epoch.   Early Unix engineers picked that date arbitrarily because they needed to set a uniform date for the start of time, and New Year's Day, 1970, seemed most convenient.

### Examples

**Date / Time**

**Unix Time**

January 1st, 1970 00:00:00

0

June 6th, 1983 00:00:00

423705600

June 6th, 1983 16:00:00

423763200

September 9, 2001 1:46:40

1000000000

July 20th, 1969 20:17:40

\-14182940

### Limitations

#### Year 2038 Problem

The year 2038 problem is related to Unix time because times after 03:14:07 UTC on 19 January 2038 will require computers to store the value as greater than 32-bits.  Systems built assuming that the time would always fit withing 32-bits will result in undefined behavior potentially causing those systems to crash, become unusable, or create other undesired effects. The problem is similar to the Y2K problem which arose when developers assumed that years could be stored in two digits instead of four. 

#### Leap Seconds

Leap seconds are ignored in Unix time.  Leap seconds have the same Unix time as the second before it.  The underlying assumption is that each day has exactly 86,400 seconds.  Because of this Unix time is not a true representation of UTC.

#### Pre-1970 Timestamps

The Unix epoch is at the beginning of 1970 meaning that any timestamp prior to 1970 needs to be represented as a negative number representing the number of seconds until January 1st, 1970 00:00:00 UTC.

### Variations

If the timestamp needs to represent a time that is smaller than one second a variation of Unix time needs to be employed.

#### Unix Time w/Decimals

One way to represent timestamps with greater precision than a single second is instead of representing time using whole numbers, instead use decimals to represent fractions of a second.

#### Unix Time in Milliseconds

Another option is to represent timestamps using the number of milliseconds since the Unix epoch instead of the number of seconds.  This is the methodology adopted by Narrative.

### Additional Resources

*   Wikipedia: [Year 2038 Problem](https://en.wikipedia.org/wiki/Year_2038_problem)
*   Wikipedia: [Unix time](https://en.wikipedia.org/wiki/Unix_time)
*   [Epoch Converter](https://www.epochconverter.com/)
