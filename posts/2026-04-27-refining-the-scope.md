---
title: "Refining the Scope: Structuring a Neighbourhood Companionship Web App
date: 2026-04-27
author: Zhihuan Jin
summary: "This post narrows the project from a broad community idea into a structured web application concept for adults aged 55 and above, using a simple sitemap to reason about scope, functionality, and feasibility."
tags:
  - functional requirements
  - sitemap
  - scope
  - older adults
  - community connection
---

After the first stage of ideation, our project direction has become more focused. Earlier ideas included a retro gaming community, an anime fan platform, and a USyd “treehole” style space for anonymous student expression. These ideas were interesting, but they also had clear limitations. The retro gaming and anime ideas already have many existing platforms, while the student treehole concept would depend heavily on moderation and could create difficult safety issues. For this reason, I decided that our A2 prototype needs a more specific community need and a clearer functional purpose.

The current direction is a neighbourhood-based companionship web application for adults aged 55 and above. It is partly inspired by Nextdoor’s local community logic, but it should not simply become another neighbourhood noticeboard. I also do not want to frame it as a dating app. Instead, the focus should be companionship, social connection, activity-first matching, guided introductions, and trust-aware local participation. The main design challenge is to help older adults find nearby people and activities in a way that feels safe, purposeful, and socially comfortable.

To make the concept more concrete, I created a simple sitemap to reason about the possible structure of the web application:

```text
Home / Landing
│
├── Choose Community
│   ├── Use Approximate Location
│   └── Enter Suburb / Postcode Manually
│
├── Community Dashboard
│   ├── Local Activities
│   │   ├── Activity Details
│   │   ├── Join / Express Interest
│   │   └── Create Activity
│   │
│   ├── Companions
│   │   ├── Browse Profiles
│   │   └── Request Guided Introduction
│   │
│   ├── Messages / Introductions
│   └── Safety & Community Guidelines
│
└── User Profile
    ├── Interests
    ├── Availability
    └── Trust / Contact Preferences
```

This sitemap helped me separate essential functions from optional ones. The essential functions are choosing a local community, browsing local activities, viewing activity details, expressing interest in an activity, setting up a basic profile, and requesting a guided introduction. These features directly support the main purpose of the application: helping older adults move from local isolation toward low-pressure social participation.

Other possible features should remain outside the first prototype. For example, real-time chat, complex recommendation algorithms, detailed map browsing, full identity verification, and rating systems could all be useful in a future version. However, including them too early would increase technical complexity and may distract from the core interaction. A full open community feed could also make the platform feel too similar to existing social media or neighbourhood apps. For this prototype, a smaller set of meaningful interactions is more appropriate than a large set of loosely connected features.

One important design decision is that activities should be the main entry point, not individual profiles. If the application begins with browsing people, it may feel too much like dating or profile-based social media. If it begins with activities, the interaction becomes more natural. Users connect because they both want to join a walking group, coffee meet-up, book discussion, gardening activity, or local event. This supports companionship without forcing direct personal matching too early.

There are still risks and unknowns. Location is useful for building a local community, but precise GPS tracking may create privacy concerns. Manual suburb or postcode entry may be safer and easier to prototype. Trust is also difficult to design: too little safety support may make users hesitant, but too much verification may feel intrusive. Accessibility is another key issue, since the interface needs clear navigation, readable text, simple forms, and predictable interactions.

My next step is to move from this sitemap into more specific user flows. In particular, I need to understand how a user would enter a community, join an activity, request an introduction, and manage their profile. This will help test whether the current scope is realistic for the A2 prototype and whether the planned features genuinely support the project’s social goal.
