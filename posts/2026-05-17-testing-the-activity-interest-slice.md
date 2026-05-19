---
title: Testing the Activity-Interest Slice Before Building More
date: 2026-05-17
author: Zhihuan Jin
summary: Using Week 11 testing and analytics concepts to narrow the Nearby Together prototype into one testable activity-interest flow, focusing on trust, privacy, and older adults’ confidence before expanding the system.
tags:
  - testing
  - analytics
  - user flow
  - DDD
  - prototype
  - older adults
  - activity detail
---

In the previous post, I considered whether an external API could support the Activity Detail Page as a stretch goal. That helped me think about technical extension, but Week 11 shifted my attention back to a more important question: what is the smallest part of the prototype that must work before I build anything extra? For this project, the answer is not the full social platform. It is the activity-interest slice: an older adult finds a nearby activity, understands the key details, judges whether the organiser feels trustworthy, and shows interest without feeling publicly exposed or locked into a commitment.

This is why I created a focused user flow for one test slice rather than mapping every possible feature. The flow begins with browsing nearby activities and ends with a confirmation message after the user sends interest. I deliberately kept account creation, payment, group chat, organiser replies, and calendar syncing out of scope. These features may be useful later, but they would distract from the core uncertainty I need to test first: can a user safely and confidently move from curiosity to a private first step?

![Figure 01. User flow for the activity-interest test slice](assets/user-flow-test-slice-academic.png)

The user flow also helped me notice that the Activity Detail Page is doing more than displaying event information. It needs to support a careful decision. For older adults, especially users who may be cautious about meeting strangers or joining unfamiliar groups, the page has to answer several quiet questions at once: Where is it? How long does it take? Is it accessible? Who is running it? What happens if I tap the button? This made the page less like a simple event listing and more like a trust and reassurance interface.

![Figure 02. Activity Detail Page wireframe for the test slice](assets/blog5-activity-detail-page-wireframe.png)

The wireframe therefore separates the decision into readable sections: activity title, plain-language description, key information, organiser trust indicators, privacy reassurance, and a primary call-to-action. I used the wording “I’m interested” rather than “Sign up” or “RSVP” because the interaction is intentionally low-pressure. The user is not making a public commitment. They are starting a guided introduction. This wording is small, but it matters because the emotional risk of the interaction is part of the design problem.

Week 11’s focus on testing also helped me think more carefully about fidelity. Instead of jumping straight into a complete implementation, I treated the prototype as a sequence of test rungs. At this stage, the cheapest useful test is not a fully coded platform. It is a clickable or static stub that lets someone move through the activity detail path and explain what they think will happen next. If the user misunderstands the CTA, hesitates because of privacy concerns, or cannot find the key information quickly, then a more expensive implementation would only make the wrong design more polished.

To support this scope decision, I created a lightweight DDD map. I did not use it as a full database design. Instead, I used it to clarify the minimum domain objects needed for this slice: User / Neighbour, Activity, Organiser, Trust Indicator, Guided Intro, and Interest. This helped me separate what must exist for the test from what can wait. For example, the prototype needs enough structure to show trust cues and create an interest signal, but it does not yet need payment, recommendation algorithms, full transport routing, or a complete organiser workflow.

![Figure 03. Lightweight DDD map for the activity-interest slice](assets/nearby-together-figure-03-lightweight-ddd-map.png)

This DDD exercise also changed how I think about “technical feasibility”. Before, I sometimes treated feasibility as whether a feature could be built. Now I see it more as whether the technical structure supports the design question being tested. A small, stable activity-interest path is more valuable than a broad but fragile prototype. If the prototype can render the activity detail, show the trust and accessibility details, create a private interest signal, and confirm that nothing has been publicly shared, then it proves the most important behaviour for this stage.

I then turned this into a testing plan with a user story, acceptance criteria, and a clear success signal. The user story is: as an older neighbour, I want to show interest in a local activity without publicly committing, so that I can start a safe guided introduction at my own pace. The acceptance criteria are deliberately practical. The page must show date, time, meeting point, cost, accessibility, and organiser trust cues before the primary CTA. The CTA must explain that “I’m interested” is not a final commitment. The confirmation message must reassure the user that only the organiser receives the guided introduction and that nothing has been posted publicly.

![Figure 04. Testing plan for the activity-interest slice](assets/nearby-together-figure-04-testing-plan.png)

The most useful test would be observational rather than persuasive. I would ask a tester to complete the path without coaching: find the walk, decide whether they would show interest, and explain what they think happens after pressing the button. I would record hesitation, wrong turns, wording confusion, and privacy questions. This is important because the interface should communicate the next step by itself. If I need to verbally explain that the action is private and low-pressure, then the design has not done its job yet.

The Week 11 material also made me think about analytics as a way to support design judgement, not just as a way to collect numbers. For this prototype, useful analytics would be minimal and closely tied to the test question. I would want to know whether users reach the Activity Detail Page, whether they click “I’m interested”, whether they choose “Ask a question first” instead, whether they start the guided introduction, and whether they reach the confirmation screen. These events would not be used to profile users. They would help identify friction in the activity-interest path.

| event | what it indicates | design question |
|---|---|---|
| activity_detail_view | The user opened an activity page | Is the activity card leading users into the decision page? |
| interest_cta_click | The user clicked “I’m interested” | Does the CTA feel clear and safe enough to press? |
| ask_question_click | The user chose to ask before showing interest | Are users still uncertain before committing to the guided intro? |
| guided_intro_start | The user entered the short introduction step | Does the transition after the CTA make sense? |
| guided_intro_submit | The user submitted the private introduction | Are the questions short and comfortable enough to complete? |
| confirmation_view | The user reached the reassurance screen | Does the system clearly close the loop? |

However, analytics must be used carefully in a project about older adults and local trust. It would be contradictory to design a privacy-sensitive social platform and then measure users in a way that feels invasive. For that reason, I would keep analytics aggregated and behaviour-focused. The goal is not to know everything about the user. The goal is to understand whether the interface creates unnecessary anxiety or confusion.

The main reflection from this week is that testing is not something that only happens after the product is finished. It is a way of deciding what the product should become. My earlier instinct was to keep adding useful features: API support, richer activity data, organiser workflows, and more platform logic. Week 11 helped me step back and ask a stricter question: what uncertainty am I testing right now? For Nearby Together, the current uncertainty is whether an older adult can understand and trust one simple activity-interest journey. Until that path works, adding more features would only increase noise.

This gives me a clearer direction for the next stage of the prototype. I should build and evaluate the smallest reliable path first: activity card, activity detail, trust indicators, “I’m interested”, guided introduction, and confirmation. If that path feels calm, private, and understandable, then the project has a strong foundation. If it does not, then the testing will show me exactly where the design needs to change before the platform becomes larger.