---

title: Evaluating Nearby Together as a Low-Pressure Community Hub
date: 2026-06-14
author: Zhihuan Jin
summary: A final reflection evaluating the performance, accessibility, usability, and functional scope of the completed Nearby Together prototype.
tags:

- A3 reflection
- evaluation
- accessibility
- usability testing
- performance
- Nearby Together

---

<div style="border-left: 4px solid #d8b46a; background: rgba(216,180,106,0.12); padding: 1rem 1.2rem; margin: 1.5rem 0 2rem 0; border-radius: 8px;">
  <strong>Evidence note:</strong> The evidence blocks below are supporting material and are not included in the 1250-word reflective writing count. Full supporting notes are stored in the repository as <a href="assets/a3-reflection/lighthouse-performance-evidence.md">Lighthouse performance evidence</a>, <a href="assets/a3-reflection/aa-checklist-status.md">AA checklist status</a>, and <a href="assets/a3-reflection/usability-test-form-1.md">usability test notes</a>.
</div>

When I first narrowed Nearby Together, I treated the prototype as a test of one main uncertainty: can an older neighbour move from local curiosity to a safe first step without being pushed into a public feed or a final commitment? The finished build does not answer every possible community need, but it gives me enough evidence to evaluate that question. The prototype supports choosing a local community, browsing activities, selecting interests, joining circles, answering a daily question, saving personal community state, and sending a private interest message to an organiser. My reflection is therefore not simply that the site “works”. It is about where this narrow, low-pressure model worked well, and where the evidence shows it still needs clearer language, richer content, and stronger local context.

## Evidence block 1: Lighthouse performance audit

<div style="border: 1px solid #d8b46a; background: rgba(216,180,106,0.08); padding: 1.2rem; margin: 2rem 0; border-radius: 10px;">

<p style="margin-top: 0; font-weight: 700; color: #d8b46a;">Supporting evidence — performance</p>

<figure style="margin: 0;">
  <img src="assets/a3-reflection/a3-lighthouse-summary.png" alt="Figure 1. Lighthouse audit summary for the Nearby Together prototype." style="width:100%; max-width:760px; height:auto; display:block; margin: 0 auto;">
  <figcaption style="font-size: 0.9rem; opacity: 0.85; margin-top: 0.75rem;">
    Figure 1. Lighthouse audit summary for the Nearby Together prototype.
  </figcaption>
</figure>

<p style="font-size: 0.95rem; margin-bottom: 0;">
  The Lighthouse audit was run across the main prototype routes. Most tested pages scored 100 for Performance, Accessibility, and Best Practices, while the mobile home page scored 98 for Performance. SEO remained at 90 because of one repeated issue: no meta description.
</p>

</div>

The prototype performed better than I expected. The Lighthouse audit across the main routes showed high scores: most pages received 100 for Performance, Accessibility, and Best Practices, while the mobile home page still reached 98 for Performance. The Core Web Vitals were also within the brief target: First Contentful Paint was 0.2 seconds, Largest Contentful Paint was 0.3 seconds, Speed Index was 0.2 seconds, Total Blocking Time was normally 0 ms, and Cumulative Layout Shift was 0. This suggests that the current implementation provides a fast, stable first experience. The main reason is clear: the prototype is server-rendered, uses local assets, has no heavy image content, and keeps the interaction model simple. However, the audit still identified missing meta descriptions, unused JavaScript, render-blocking resources, and unminified or unused CSS. These did not seriously affect the small prototype, but they would matter more if the site grew into a public service with images, maps, posts, or marketplace listings.

Technically, the strongest part of the build is that the important screens are not just static mock-ups. The routes, templates, SQLite database, and user session logic work together to hold simple state. Interests affect recommended circles, the Daily Question can be saved and then found again in My Circle, activities can be filtered, and the private interest form leads to a confirmation page that reflects the action taken. This means the prototype demonstrates the behaviour I planned rather than only showing its appearance. The use of normal forms and server-rendered templates also helped reliability because interactions remained understandable without complex client-side logic. I should not overstate the technical depth. The data set is small, the organiser side is not implemented, and repeated local testing can make prototype data feel less clean. A future version would need clearer seed/reset processes, stronger content management, and a more realistic organiser workflow.

## Evidence block 2: Usability test summary

<div style="border: 1px solid #d8b46a; background: rgba(216,180,106,0.08); padding: 1.2rem; margin: 2rem 0; border-radius: 10px;">

<p style="margin-top: 0; font-weight: 700; color: #d8b46a;">Supporting evidence — usability testing</p>

<table>
  <thead>
    <tr>
      <th>Finding</th>
      <th>Evidence from test</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Main flow was completed.</td>
      <td>All three participants completed all five tasks.</td>
    </tr>
    <tr>
      <td>Labels still needed interpretation.</td>
      <td>Participants paused around “Daily Question”, “My Circle”, “next prompt”, and “I’m interested”.</td>
    </tr>
    <tr>
      <td>Feedback was mostly visible.</td>
      <td>Participants knew actions had succeeded after saved content or confirmation pages appeared.</td>
    </tr>
    <tr>
      <td>Private interest was understood after confirmation.</td>
      <td>Two participants clearly understood that the organiser could see the message and nothing was posted publicly.</td>
    </tr>
    <tr>
      <td>Richer content was requested.</td>
      <td>Participants wanted more activities, more communities, images, visual cues, or location-based recommendations.</td>
    </tr>
  </tbody>
</table>

<p style="font-size: 0.95rem; margin-bottom: 0;">
  Full notes are stored as <a href="assets/a3-reflection/usability-test-form-1.md">usability test notes</a>.
</p>

</div>

The usability test gave the clearest evidence about the experience. All three participants completed all five tasks: choosing interests, joining a circle, answering the Daily Question and finding it again, showing interest in an activity, and changing community. This suggests that the overall structure is understandable across different digital confidence levels. The most successful flow was the activity-interest path. Users could open an activity, read practical details, reach the interest form, and understand the confirmation page. This supports the original decision to make the activity detail page a trust-aware decision point rather than a decorative event card. However, completion did not mean the interface was always self-explanatory. All three participants paused at least once because a label or concept needed interpretation. The main examples were “Daily Question”, “My Circle”, “next prompt”, and “I’m interested”. Two users expected “I’m interested” to behave like RSVP or booking, even though the system treats it as a private first step. This matters because emotional safety depends on that distinction.

The Daily Question flow also worked, but only after users saw where the answer ended up. All participants knew their answer had been saved once the saved content appeared, but two suggested that a stronger immediate success message would make the feedback clearer. This tells me the problem is not database behaviour; the system saves and displays the answer. The problem is feedback timing. A small confirmation banner, for example “Saved to My Circle”, would close the loop before the user has to search for evidence. I also learned that the feature’s value is uneven. One participant found the “How are you feeling?” prompt interesting, while another saw Daily Question as a light check-in rather than a main reason to use the app. I still think the feature belongs because it offers a low-pressure alternative to posting, but it needs clearer connection to community belonging.

## Evidence block 3: AA accessibility and contrast review

<div style="border: 1px solid #d8b46a; background: rgba(216,180,106,0.08); padding: 1.2rem; margin: 2rem 0; border-radius: 10px;">

<p style="margin-top: 0; font-weight: 700; color: #d8b46a;">Supporting evidence — accessibility</p>

<figure style="margin: 0;">
  <img src="assets/a3-reflection/a3-aa-contrast-review.png" alt="Figure 2. Text contrast review against WCAG AA and AAA thresholds." style="width:100%; max-width:760px; height:auto; display:block; margin: 0 auto;">
  <figcaption style="font-size: 0.9rem; opacity: 0.85; margin-top: 0.75rem;">
    Figure 2. Text contrast review against WCAG AA and AAA thresholds.
  </figcaption>
</figure>

<p style="font-size: 0.95rem; margin-bottom: 0;">
  The AA checklist recorded large body text, generous line height, visible form labels, native controls, skip link support, visible focus outlines, semantic landmarks, responsive layouts, and privacy text that does not rely on colour alone. The contrast review shows that all measured text pairs cleared AA, with most clearing AAA.
</p>

</div>

Accessibility was one of the better outcomes of the project. The AA checklist showed that the interface uses large body text, generous line height, visible form labels, text-based actions, privacy explanations that do not rely on colour alone, native buttons and links, a skip link, visible focus outlines, semantic landmarks, and responsive layouts. The contrast review was also strong: every measured text pair cleared AA, and most cleared AAA except secondary text. Niko, the participant closest to the target age range, said the text was large, calm, and easy to read compared with busier social media apps. Still, this is not a complete accessibility claim. Axe testing and a screen reader pass were not completed, and only one participant was within the older adult target range. A stronger evaluation would include VoiceOver or NVDA testing and more users aged 55 and above.

Looking back at the functional requirements, I think the original scope was mostly realistic. The prototype covers the must-have path: choose a community, browse local activities, review trust and access details, express interest privately, and maintain a simple personal community space. It also implements supporting requirements such as interest matching, recommended circles, and a low-pressure daily prompt. The features that were cut or left shallow were understandable cuts: full public posting, open chat, photo sharing, precise location detection, calendar integration, a real organiser dashboard, and a local second-hand market. These would make the platform feel more complete, but they would also introduce moderation, privacy, abuse reporting, data storage, and performance issues. Earlier in the semester I was tempted to think of these as missing features. Now I see them as later layers that should only be added after the core private-interest path is clear.

If I continued the project, I would improve it in stages rather than simply add everything at once. First, I would change “I’m interested” to something like “Send private interest” and add a short helper line explaining that it is not a booking or public RSVP. Second, I would strengthen feedback after Daily Question submissions and after joining circles. Third, I would make the site more visually convincing. The current design is readable, but it is also quite plain. Activity images, community photos, simple icons, and visual cards could help users understand place and activity faster, if images include alt text and preserve load times. Fourth, I would add optional postcode or approximate-location matching instead of forcing precise GPS. A controlled posting feature or local marketplace could be valuable later, but only with clear categories, moderation tools, and safety rules.

The main lesson is that evaluation changed what “finished” means to me. The prototype is successful as a small full-stack slice: fast, readable, accessible in many measured ways, and usable enough for participants to complete the core flow. But the evidence also shows that a working route is not the same as a fully understood interaction. The next iteration should not chase scale first. It should make the low-pressure model more explicit, more visual, and more locally meaningful.
