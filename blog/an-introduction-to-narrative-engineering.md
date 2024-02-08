---
title: 'An Introduction to Narrative Engineering'
description: 'An Introduction to Narrative Engineering'
publishDate: '2019-05-23 17:29:53'
author: 'Alex Kuang'
ogImage: '/img/blog/2019/05/intro-to-engineering.jpg'
image: '/img/blog/2019/05/intro-to-engineering.jpg'
tags: ['engineering']

---
### A look inside Narrative's approach to technical feature development

Every team has their own ideas about how to run technical product development. You can ask ten teams and probably get twelve different answers back. At Narrative we believe in small 3-5 person teams owning entire features, from scoping to implementation to maintenance and operations. The exact makeup of the team depends on the project: a UI-heavy dashboard project might include a frontend dev, a backend dev, and a UI/UX designer; a more infrastructure-focused project might just be three backend devs. But regardless of the team makeup, we adhere to the same high level process for major development.

### Scoping and Design

The first step for meaty features is to decide what we are building and why we are building it. The product and tech leads for the project collaborate on a design document that outlines our basic business assumptions and how those assumptions inform the technical and product decisions that we make. Rather than attempt to define everything up front waterfall-style, this is a living document that serves as a starting point and continues to evolve through the life of the project. Writing everything down is also helpful for new team members who join and wish to dig further into the context around decisions from past projects.

### Implementation and Deployment

Implementation begins once we settle on the basic requirements of what we are building. This often happens in parallel with the development of the design doc, especially if we are using a new technology that requires us to gather more information via prototype work. Implementation covers everything from new application code to infrastructure changes, and everything goes through code review.

We try to avoid "big bang" releases whenever possible, so we deploy code and infrastructure incrementally as we make progress. The exact details of deployment vary depending on the application but we typically use [sbt](https://www.scala-sbt.org/) to build Scala artifacts and [terraform](https://www.terraform.io/) to manage our infrastructure.

### Maintenance and Operations

As every developer knows, nothing is ever 100% done in software. Bugs are discovered, application load increases, and AWS goes down. Therefore, operations is very much a regular part of developer life. We use a combination of [DataDog](https://www.datadoghq.com/), PagerDuty, and AWS SNS to ensure that our systems are running smoothly and someone is alerted when anything looks off.

### Geeking out

We love getting into the weeds and talking about what we're doing on a technical level. If this is your sort of thing, keep an eye out as this will be an ongoing series of blog posts.
