## Evidence: Lighthouse performance audit

**Category scores by route**

| Route | Performance | Accessibility | Best Practices | SEO |
| --- | ---: | ---: | ---: | ---: |
| `/` (home, desktop) | 100 | 100 | 100 | 90 |
| `/` (home, mobile) | 98 | 100 | 100 | 90* |
| `/activities` | 100 | 100 | 100 | 90 |
| `/community` | 100 | 100 | 100 | 90 |
| `/login?next=/interests` | 100 | 100 | 100 | 90 |
| `/interests` | 100 | 100 | 100 | 90 |
| `/circles` | 100 | 100 | 100 | 90 |
| `/daily` | 100 | 100 | 100 | 90 |
| `/my-circle` | 100 | 100 | 100 | 90 |
| `/activities/garden_003` (detail) | 100 | 100 | 100 | 90 |
| `/activities/garden_003/interest` (interest form) | 100 | 100 | 100 | 90 |
| `/confirmation/...` (confirmation) | 100 | 100 | 100 | 90 |

\* Mobile home SEO value was cropped in the capture; inferred as 90 from the other routes.

**Core Web Vitals (consistent across routes)**

| Metric | Value |
| --- | ---: |
| First Contentful Paint (FCP) | 0.2 s |
| Largest Contentful Paint (LCP) | 0.3 s |
| Total Blocking Time (TBT) | 0 ms |
| Cumulative Layout Shift (CLS) | 0 |
| Speed Index | 0.2 s |

Exception: `/activities/garden_003/interest` recorded TBT = 10 ms; all other metrics matched.

**Notes**

- SEO is held at 90 on every route by one repeated item: no meta description.
- Recurring Performance diagnostics (not score-affecting on desktop): efficient cache lifetimes (about 64 KiB), unused JavaScript (about 1,779 KiB), render-blocking resources, unminified and unused CSS. These are the likely reason the mobile home page drops to 98.
