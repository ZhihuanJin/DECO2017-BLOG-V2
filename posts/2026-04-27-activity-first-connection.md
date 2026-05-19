---
title: From Neighbourhood Platform to Activity-First Connection
date: 2026-04-27
author: Zhihuan Jin
summary: Refining the project direction into a clearer set of functional requirements for a 55+ trust-aware community connection platform.
tags:
  - requirements
  - scope
  - community
  - older adults
  - design decisions
---

After settling on a neighbourhood-based community platform, the next question was not simply “what features should it have?”, but what kind of connection it should make possible. My initial reference point was Nextdoor: a local platform where people interact through neighbourhood identity rather than broad social networking. However, for our project, directly copying a neighbourhood noticeboard would not be enough. It would risk becoming another general-purpose community feed, which is both technically ordinary and weakly connected to a specific user need.

The clearer direction is now a community hub for adults aged 55 and above, focused on companionship, social connection, and activity-first matching. This is an important distinction from a dating platform. The problem I want to address is not romance, but the difficulty of finding low-pressure, trusted, local social opportunities. For this user group, the application should reduce the awkwardness of making first contact and provide structured reasons to meet, such as walking groups, coffee meetups, hobby circles, library visits, or local events.

This changed how I understood the core functional requirements. Instead of making “profiles” or “chat” the centre of the application, the core should be a guided pathway from local identity to shared activity to safe introduction. I am therefore treating the standard social media features as supporting infrastructure, not the unique value of the prototype.

| Priority | Requirement | Reasoning |
|---|---|---|
| Must have | Choose or enter a local community area | The platform only makes sense if connection is geographically meaningful. |
| Must have | Browse activity-based social opportunities | Activities give users a concrete, low-pressure reason to connect. |
| Must have | Guided introduction flow | Older users may need clearer interaction support than an open-ended messaging system. |
| Should have | Trust signals, such as shared area or verified group context | Trust is central if the app encourages offline social contact. |
| Could have | Personal interest matching | Useful, but risky if it makes the platform feel too much like dating. |
| Not now | Full open chat or complex recommendation algorithm | These are technically larger and not necessary for the prototype’s unique value. |

The main design trade-off is between openness and guidance. An open feed gives users flexibility, but it may also create noise, uncertainty, or safety concerns. A highly guided system is more limited, but it better supports the specific goal of helping older adults move from isolation toward real-world social participation. For this reason, I am leaning toward a structured interaction model: users first select a neighbourhood, then choose an activity category, then view small group opportunities, and only then enter an introduction or RSVP flow.

This decision also affects technical feasibility. The prototype does not need to implement every possible community function. A smaller database structure could focus on users, communities, activities, and participation records. This would be more achievable than building a complete social network, while still demonstrating meaningful full-stack behaviour. It also gives the interface a clearer structure: community selection, activity discovery, activity detail, and guided response.

There are still unresolved risks. First, we need to avoid stereotyping older adults as passive or technologically incapable. The interface should be clear and supportive without being patronising. Second, privacy and safety need to be considered carefully, especially because the app may encourage offline meetings. Third, the idea of “trust” must be represented through realistic prototype features rather than vague language. In the next stage, I need to translate this scope into a sitemap or user flow so that the relationship between user need, interface structure, and technical implementation becomes clearer.