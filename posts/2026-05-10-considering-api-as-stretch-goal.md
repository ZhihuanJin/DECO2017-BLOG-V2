---
title: Considering an API as a Stretch Goal for Activity Decisions
date: 2026-05-10
author: Zhihuan Jin
summary: Exploring whether external API data should support the Activity Detail Page, and how a small weather feature could improve decision-making without becoming a core dependency.
tags:
  - API
  - DDD
  - technical feasibility
  - activity detail
  - stretch goal
---

In the previous post, I used the Activity Detail Page wireframe to clarify what the application needs to communicate before an older adult decides to join a local activity. That process shifted my focus from simply showing an event listing to supporting a more careful decision: Is this activity close enough? Is it suitable for my pace? Who runs it? What happens after I say I am interested? For this post, I am considering whether external API data could add value to that page, especially as a stretch goal rather than a core requirement.

The Week 10 tutorial introduced a useful technical pattern for making HTTP requests to external APIs through the `UserAgent` class, parsing JSON responses, handling errors gracefully, using cached results, and storing API keys in `config.yml` when needed. The important design question for my prototype is not just “can I use an API?”, but whether API data would support the functional requirements of the application. Since my project is centred on activity-first social connection for adults aged 55 and above, the most relevant API idea is a weather or forecast panel on the Activity Detail Page.

This would be especially useful for outdoor activities such as walking groups, gardening meetups, park visits, or community markets. For older users, weather is not a decorative detail. Rain, heat, wind, or poor conditions may affect comfort, mobility, health, transport decisions, and confidence about attending. A simple weather note could therefore support accessibility and care. However, it should not become the centre of the application. The main value of the platform is still trusted local connection, guided introduction, and clear activity information. Weather data should support the decision, not distract from it.

A small Data Definition Document helps clarify what data this feature would actually need:

| attribute | description | example value |
|---|---|---|
| activity_id | The activity this weather panel belongs to | walk_001 |
| activity_location | The meeting location used to estimate weather | Riverside Park, main gate |
| latitude | Generated or stored coordinate for the meeting point | -33.8688 |
| longitude | Generated or stored coordinate for the meeting point | 151.2093 |
| activity_start_time | The scheduled time used to request a relevant forecast | 2026-05-26 10:00 |
| temperature | Forecast temperature near the activity time | 19°C |
| rain_chance | Probability or warning of rain, if available | Light rain possible |
| wind_speed | Wind condition that may affect outdoor comfort | 18 km/h |
| comfort_summary | Human-readable interpretation for the user | Mild weather, bring a light jacket |
| last_updated | When the forecast data was fetched or cached | 2026-05-10 09:30 |

This DDD shows that the API feature is not just “show weather”. It depends on the activity already having structured date, time, and location information. It also reveals a hidden technical decision: location should not only be a display string. If the prototype fetches weather, the system needs either stored coordinates or a geocoding step that converts a place name into latitude and longitude. This creates more complexity, so it should remain a stretch goal unless the core activity and introduction flow is already stable.

The technical approach would follow the tutorial pattern. The server would request forecast data using `UserAgent`, parse the JSON response, and pass a simplified result into the page template. If the API fails, the page should still work. This is important because an external API should not break the user’s ability to view or join an activity. A failed response could simply hide the weather panel or show a message such as “Weather information is currently unavailable.” This graceful failure pattern is particularly suitable for my project because trust depends on reliability and clarity.

Caching is also important. Weather data does not need to be fetched every time a user opens the page. A cached result would reduce redundant API calls and make the page feel faster. If implemented with HTMX, the weather panel could also load or refresh as a small partial section rather than forcing the whole page to reload. This would fit the server-rendered HTML and HTMX stack while keeping the interaction simple.

The main trade-off is between usefulness and scope control. A weather panel could make the Activity Detail Page more supportive and age-friendly, but it also introduces extra development tasks: API calls, data parsing, caching, error states, and possibly geocoding. For the prototype, I would treat it as optional. The must-have requirements remain community selection, activity browsing, activity detail, trust indicators, and guided introduction. The weather API becomes valuable only if it strengthens those flows rather than competing with them.

This also affects how I evaluate the design. I would not judge the feature by whether it looks technically impressive, but by whether users can make a more confident decision about attending. For older adults, the best version of this feature would be plain-language, readable, and practical: not a dense weather widget, but a short comfort note connected to the specific activity. In that sense, the API is most appropriate when it becomes invisible infrastructure behind a more human-centred decision.