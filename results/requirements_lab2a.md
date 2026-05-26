Version: 1.0
Date: 2026-05-27

# Business Requirements Document — "About Me" Portfolio

Purpose: Define requirements for a recruiter-focused "About Me" personal portfolio page. This BRD follows the workspace Copilot instructions: MoSCoW prioritization, Given/When/Then acceptance criteria, and ID prefixes (BR-, NFR-, US-).

---

## Profile

BR-PRO-001
- Description: Concise hero section with candidate name, primary role/title, 1–2 sentence value proposition, and availability status (open-to-work / availability window).
- Priority: Must have
- Rationale: Recruiters need to assess fit within ~10 seconds; the hero must communicate role and intent immediately.
- Acceptance Criteria (Given/When/Then):
  - Given a visitor arrives on the page, when they look at the top of the page, then they see full name, role/title, a 20–30 word value sentence, and availability status.

BR-PRO-002
- Description: Short personal summary (2–3 sentences) describing domain expertise, impact-oriented strengths, and role preferences.
- Priority: Must have
- Rationale: Clarifies candidate focus and helps recruiters match roles quickly.
- Acceptance Criteria:
  - Given the profile section, when a recruiter reads it, then they can identify domain, seniority level, and two example impacts or focus areas.

BR-PRO-003
- Description: Optional supporting details: professional headshot, location/timezone, preferred work arrangements (remote/hybrid/relocation), visa status.
- Priority: Should have
- Rationale: Reduces uncertainty for hiring teams; improves matching for location-sensitive roles.
- Acceptance Criteria:
  - Given the profile area, when details are present, then all items are visible, unobtrusive, and accessible.

---

## Skills

BR-SKL-001
- Description: Grouped skill lists by category (Languages, Frameworks, Tools, Methodologies) with top 6–10 highlighted.
- Priority: Must have
- Rationale: Structured skills speed recruiter scanning and filtering.
- Acceptance Criteria:
  - Given the skills section, when viewed on desktop or mobile, then categories are clear, and top skills are visually emphasized.

BR-SKL-002
- Description: Visual indicators of proficiency (labels like Expert/Proficient/Familiar or neutral bars) kept simple and consistent.
- Priority: Should have
- Rationale: Gives quick context about strength without overstating capability.
- Acceptance Criteria:
  - Given the skills entries, when a skill has an indicator, then the meaning is documented in a tooltip or legend.

BR-SKL-003
- Description: Linkable badges or anchors for deeper skill evidence (e.g., projects, blog posts, GitHub search query).
- Priority: Could have
- Rationale: Enables recruiters to validate claims with one click.
- Acceptance Criteria:
  - Given a skill, when a recruiter clicks evidence link, then it opens a relevant resource in a new tab.

---

## Portfolio (Projects)

BR-PORT-001
- Description: Feature 3–5 highlighted projects with: title, one-line summary, role, tech stack, measurable outcomes, and links to demo/GitHub/case study.
- Priority: Must have
- Rationale: Demonstrates impact and provides proof-of-work to recruiters.
- Acceptance Criteria:
  - Given the featured projects section, when a recruiter scans it, then each project shows title, 1-line summary, role, stack and at least one link.

BR-PORT-002
- Description: Provide progressive disclosure for deeper case studies (expand/collapse or separate pages) including challenges, approach, and outcomes with metrics.
- Priority: Should have
- Rationale: Keeps the main page scannable while allowing depth for interested reviewers.
- Acceptance Criteria:
  - Given a project card, when the user chooses to view details, then a case study with problem, approach, role, and measurable results is displayed.

BR-PORT-003
- Description: Ensure live demos and repos are reachable and include a short README or demo screenshot on hover.
- Priority: Must have
- Rationale: Broken links reduce credibility and wasted recruiter time.
- Acceptance Criteria:
  - Given project links, when clicked, then they open to working demos or public repos; if a link is unavailable, then a clear message appears.

---

## Experience

BR-EXP-001
- Description: Concise experience highlights (3–5 most relevant roles) each with one-line outcome/impact and employer, dates optional.
- Priority: Must have
- Rationale: Provides context on career trajectory and domain experience.
- Acceptance Criteria:
  - Given the experience section, when a recruiter reads it, then they can infer seniority, role focus, and a single measurable impact per entry.

---

## Contact & Resume

BR-CON-001
- Description: Clear contact CTA: email (mailto), LinkedIn, GitHub, and downloadable ATS-friendly resume PDF.
- Priority: Must have
- Rationale: Converts interest to contact and is expected by recruiters.
- Acceptance Criteria:
  - Given the contact area, when a recruiter clicks resume, then a text-based PDF downloads; when they click email, their mail client opens with a prefilled subject.

BR-CON-002
- Description: Optional minimal contact form or calendar scheduling link with spam protection and confirmation message.
- Priority: Could have
- Rationale: Lowers friction for scheduling without exposing email directly.
- Acceptance Criteria:
  - Given contact form, when submitted, then the user receives an on-screen confirmation and the submission is stored/sent per privacy notice.

---

## Design & UX

NFR-UX-001
- Description: Visual hierarchy, typographic scale, and spacing to maximize scanability; H1 used once.
- Priority: Must have
- Rationale: Improves recruiter scanning efficiency and readability.
- Acceptance Criteria:
  - Given the page, when run through Lighthouse and manual checks, then headings and CTAs are visually distinct and readable.

NFR-UX-002
- Description: Responsive design (mobile-first) with CTA visibility on small screens and accessible navigation.
- Priority: Must have
- Rationale: Recruiters commonly browse on mobile devices.
- Acceptance Criteria:
  - Given mobile viewport, when opening the page, then navigation works and CTAs are tappable without horizontal scrolling.

NFR-UX-003
- Description: Motion limited to subtle micro-interactions and honors `prefers-reduced-motion`.
- Priority: Should have
- Rationale: Respects accessibility and user comfort.
- Acceptance Criteria:
  - Given user agent preference for reduced motion, when the page loads, then animations are disabled.

---

## Technical & Security

NFR-TECH-001
- Description: Serve as a fast static site with optimized assets (images, SVGs), lazy-loading where appropriate, and minimal third-party scripts.
- Priority: Must have
- Rationale: Performance increases engagement and SEO.
- Acceptance Criteria:
  - Given a Lighthouse audit, when tested on throttled network, then performance scores meet defined targets (TTI < 4s for MVP).

NFR-TECH-002
- Description: Add SEO and social metadata (title, description, Open Graph, Twitter Card) and JSON-LD for Person/resume where applicable.
- Priority: Should have
- Rationale: Improves discoverability and link previews.
- Acceptance Criteria:
  - Given the page HTML, when crawled, then meta tags and JSON-LD are present and valid.

NFR-TECH-003
- Description: HTTPS hosting, CSP, and privacy-first analytics option (Plausible or Fathom) with clear privacy notice if collecting data.
- Priority: Must have
- Rationale: Security and privacy compliance builds trust and avoids warnings.
- Acceptance Criteria:
  - Given deployed site, when visited, then connections are HTTPS and analytics respect privacy settings.

BR-TECH-004
- Description: Provide downloadable resume as ATS-friendly text-based PDF; ensure resume content matches site summary.
- Priority: Must have
- Rationale: Recruiters rely on downloadable resumes for ATS ingestion.
- Acceptance Criteria:
  - Given resume download, when inspected by an ATS or opened in a text editor, then text is selectable and structured.

---

## User Stories

US-001: As a recruiter, I want to understand the candidate's core strengths in under 5 seconds so I can quickly assess fit.

US-002: As a recruiter, I want to view evidence of the candidate's past work and impact so I can evaluate technical credibility.

US-003: As a recruiter, I want a clear way to contact or download the resume so I can proceed without searching.

US-004: As a candidate, I want the page to surface my top projects and skills so hiring teams see my value immediately.

US-005: As a mobile visitor, I want the page to display cleanly on my phone so I can review the candidate anywhere.

---

## Deliverables

- Hero copy (20–30 words)
- 3–5 featured project entries with links
- ATS-friendly resume PDF
- Responsive static site (HTML/CSS or static framework)

---

## Notes
- This document follows the requested Copilot workspace rules: MoSCoW priorities, Given/When/Then acceptance criteria, version/date, and prefixed IDs.
