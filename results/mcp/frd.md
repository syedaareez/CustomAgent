# Functional Requirements Document (FRD)

- **Project:** "About me" — Personal portfolio page for recruiters
- **Version:** v1.0
- **Date:** May 28, 2026

**Top 3 Must Have**
- 1) Prominent hero summary and 3–5 core skills (immediately visible)
- 2) Resume download and clear contact CTA (email + optional form)
- 3) Featured projects gallery with direct links to code samples/demos

## Purpose
This FRD defines the functional behavior for a single-page personal portfolio targeted at recruiters and hiring managers. It enumerates user stories, acceptance criteria, UI behavior notes, example data models, and recommended implementation options.

## User Stories (Functional)
Each story ID is prefixed with `US-`.

- **US-001 — Navigation (anchor links)**
  - As a recruiter, I want quick navigation to page sections so I can jump to content of interest.
  - Acceptance (Given/When/Then):
    - Given the page is open, when I click a nav item (e.g., "Projects"), then the viewport scrolls smoothly to that section and the nav highlights the active section.
  - UI notes: Fixed top nav on desktop; collapsing hamburger menu on mobile; active section indicated by underline or color change.

- **US-002 — Hero / Professional summary**
  - As a recruiter, I want a concise headline and 3–5 key skills so I can immediately assess fit.
  - Acceptance:
    - Given the page is loaded, when I view the top fold, then I see a one-line headline and 3–5 skill badges visible without scrolling.
  - UI notes: Large type for headline; skill chips/badges with consistent color coding.

- **US-003 — Projects gallery (list/tiles)**
  - As a recruiter, I want to browse featured projects so I can evaluate hands-on work.
  - Acceptance:
    - Given the projects section, when I scan the gallery, then at least three projects are displayed with title, short summary, role, tech tags, and primary link.
  - UI notes: Responsive grid; meaningful thumbnail; hover shows brief details.

- **US-004 — Project detail modal / panel**
  - As a recruiter, I want to see more details without leaving the page to quickly evaluate a project.
  - Acceptance:
    - Given a project tile, when I click "Details", then a modal opens with extended description, responsibilities, outcomes, and links to code/demo, and can be closed with ESC or a close button.
  - UI notes: Modal supports keyboard navigation and focus trap; images/screenshots optional.

- **US-005 — Contact form and email link**
  - As a recruiter, I want an easy contact method so I can request interviews or follow-ups.
  - Acceptance:
    - Given I fill out the contact form with valid info, when I submit, then the form returns an on-screen success message and the candidate receives the message (or it posts to the configured inbox/service).
    - Given I click the email CTA, when the click occurs, then my default mail client opens with the candidate's address pre-filled.
  - UI notes: Minimal fields (name, company, role, message, optional resume attachment flag); email obfuscation optional.

- **US-006 — Resume download**
  - As a recruiter, I want to download or view the candidate's resume as a PDF.
  - Acceptance:
    - Given the resume CTA, when clicked, then the PDF opens in a new tab or downloads directly and matches the canonical resume file.
  - UI notes: Button labeled "Download Resume" with file size or last-updated tooltip.

- **US-007 — Social & code sample links**
  - As a recruiter, I want links to GitHub, LinkedIn, and other profiles to validate work.
  - Acceptance:
    - Given the social links, when I click a link, then it opens in a new tab and the link is reachable (HTTP 200 at the time of verification).
  - UI notes: Use recognizable icons; show username on hover for clarity.

- **US-008 — Skills section with proficiency indicators**
  - As a recruiter, I want to see a skills list and relative proficiency so I can gauge expertise.
  - Acceptance:
    - Given the skills section, when I view it, then skills are grouped (e.g., Languages, Frameworks, Tools) and each shows a simple proficiency indicator (e.g., Beginner/Intermediate/Advanced or 1–5 bars).
  - UI notes: Keep labels consistent; avoid ambiguous metrics.

- **US-009 — Testimonials / endorsements**
  - As a recruiter, I want to see short testimonials to understand impact and credibility.
  - Acceptance:
    - Given testimonials are present, when I open the section, then each testimonial shows a 1–2 sentence quote, author name, role, and optionally a link to the author's profile.
  - UI notes: Carousel optional; limit to 3–5 verified testimonials.

- **US-010 — Blog / publications link**
  - As a recruiter, I want to access blog posts or publications to assess thought leadership.
  - Acceptance:
    - Given blog links are provided, when I click a link, then the article opens in a new tab or in an integrated reading panel.
  - UI notes: Show most recent 2–3 posts with title and short excerpt; link to full blog.

## UI Behavior Notes (cross-story)
- Responsive: Layout adapts across mobile/desktop; hamburger nav under 768px.
- Accessibility: All interactive elements keyboard accessible and use proper ARIA roles.
- Performance: Above-the-fold content prioritizes hero and skills; lazy-load project images.

## Data model / JSON examples
Sample JSON structures for projects and testimonials to be used by the frontend or CMS.

Projects example:

```json
{
  "projects": [
    {
      "id": "proj-001",
      "title": "Performance Analytics Dashboard",
      "summary": "Built a real-time dashboard to monitor user metrics, reducing incident response time by 40%.",
      "role": "Full-stack Engineer",
      "tech": ["React", "Node.js", "Postgres"],
      "thumbnail": "/images/proj-001.png",
      "links": {
        "repo": "https://github.com/username/perf-dashboard",
        "live": "https://demo.example.com"
      },
      "date_range": "2024-06 to 2025-01",
      "metrics": {"impact": "40% faster incident response"}
    }
  ]
}
```

Testimonials example:

```json
{
  "testimonials": [
    {
      "id": "t-001",
      "quote": "Consistently delivered high-quality features on time.",
      "author": "Alex Johnson",
      "role": "Engineering Manager, Acme Corp",
      "link": "https://www.linkedin.com/in/alex-johnson"
    }
  ]
}
```

## Recommended tech options (concise pros/cons)

- Static HTML/CSS/JS (hand-coded)
  - Pros: Fast, minimal hosting cost, maximum control, simplest for a single-page site.
  - Cons: Manual updates; not ideal if non-technical candidate wants frequent edits.

- React Single Page App (CRA or Vite)
  - Pros: Rich interactivity (modals, client routing), component reuse, wide ecosystem.
  - Cons: Heavier initial load unless optimized; requires build step and hosting.

- Static Site Generator (SSG) — Next.js (static export), Gatsby, Astro
  - Pros: Best balance of performance and developer ergonomics; supports Markdown/MDX, easy deployment to Netlify/Vercel; good SEO.
  - Cons: Slightly more setup; build step required.

- Headless CMS / Git-backed CMS (Netlify CMS, Contentful, Sanity, GitHub + Actions)
  - Pros: Non-technical content updates, versioned content, structured data for projects/testimonials.
  - Cons: Added integration complexity and potential costs (hosted CMS tiers).

- Hosting and extras
  - Lightweight hosting: GitHub Pages or Netlify for static sites (cheap/free).
  - Analytics: Google Analytics / GA4 for event tracking, or Plausible for privacy-focused metrics.
  - Contact form backend: Formspree, Netlify Forms, or simple serverless function to forward messages.

## Implementation recommendations (short)
- For ease of updates and polished UX: use an SSG (Next.js or Astro) + Git-backed CMS (if candidate wants to edit content without developer involvement).
- For minimal effort: static site with resume PDF and `mailto:` + GitHub Pages deployment.
- Always enable link health checks (automated test) and basic analytics for resume/download tracking.

## Test cases / Acceptance checklist (high level)
- Hero and skills visible on initial load (manual check)
- Resume downloads and opens (manual + automated link check)
- Project links open in new tab and are reachable (automated link test)
- Contact form sends and candidate receives submission (end-to-end test)
- Analytics events recorded for key interactions (verification in analytics)

## Delivery notes
- Minimum viable release: Must cover US-001 → US-007 with analytics and resume download.
- Optional enhancements: US-008 → US-010 for differentiation in later iteration.

## Clarifying questions for the Business Analyst
1. Should the contact method prioritize `mailto:` (direct email) or a hosted form (collect and forward messages)?
2. Is there an existing canonical resume PDF and image assets (project thumbnails) available to include at launch?
3. Which analytics events are highest priority to track for recruiting (page visit, resume download, project click, contact submission)?

---
*Document version v1.0 — May 28, 2026*
