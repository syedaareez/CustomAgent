# Business Requirements Document (BRD)

**Project:** "About me" personal portfolio page — candidate-facing single page

**Version:** 1.0

**Date:** 2026-05-28

**Top 3 Must Have**
- BR-001: Clear professional headline and 2–3 sentence elevator summary.
- BR-002: Prominent resume download and clear call-to-action for recruiters.
- BR-003: Showcase of 3–5 key projects with roles, technologies, and links to code or demos.

## Project Summary
A concise single-page portfolio to present the candidate to technical and non-technical recruiters and hiring managers. The page must enable quick assessment (skills, fit, outcomes), provide evidence (projects, code, resume), and make contacting or requesting next steps trivial.

## Primary Stakeholders
- Hiring managers
- Technical recruiters
- Non-technical recruiters
- Candidate (owner/maintainer)

## Requirements (MoSCoW)

BR-001 — Must Have
- Title: Clear professional headline & elevator summary
- Description: A concise headline (role/title) and a 2–3 sentence elevator summary that communicates the candidate's primary domain, years of experience, and top differentiators.
- Acceptance Criteria (Given/When/Then):
  - Given a recruiter lands on the page, When they scan the top of the page for ≤10 seconds, Then they can read a headline and a 2–3 sentence summary that states role, years of experience, and one differentiator.
- Rationale: Recruiters need to evaluate fit within seconds; a clear elevator pitch reduces time-to-screen and improves contact rates.

BR-002 — Must Have
- Title: Resume download & primary CTA
- Description: A prominent resume download link/button and a clear primary CTA (e.g., "Download Resume", "Contact for Interview") visible near the top of the page.
- Acceptance Criteria (Given/When/Then):
  - Given a recruiter wants the candidate's resume, When they click the resume button, Then a PDF download begins immediately and a visible confirmation (download count or toast) appears.
  - Given a recruiter wants to contact the candidate, When they click the primary CTA, Then they are presented with either a contact modal/form or a mailto link prefilled with subject line "Interview inquiry: [Candidate Name]".
- Rationale: Recruiters often want a portable resume; making it frictionless increases conversion and shortens hiring cycles.

BR-003 — Must Have
- Title: Project showcase with outcomes and links
- Description: Highlight 3–5 representative projects with a short problem→contribution→outcome summary, role, tech stack, and direct links to code, live demos, or case notes.
- Acceptance Criteria (Given/When/Then):
  - Given a recruiter evaluates technical accomplishment, When they open a project card, Then they see role, key technologies, a 1–2 sentence outcome (metric if available), and at least one link to a code sample or demo.
- Rationale: Project evidence demonstrates applied skills and impact — stronger predictor of job performance than skills lists alone.

BR-004 — Must Have
- Title: Contact flow & follow-up options
- Description: Multiple easy contact options: a short contact form (name, email, message, optional company), a mailto link, and links to LinkedIn and primary social/code profiles. The contact form must forward to a configurable candidate email.
- Acceptance Criteria (Given/When/Then):
  - Given a recruiter submits the contact form, When they press submit, Then they receive an on-screen confirmation and the candidate receives the message by email within 5 minutes.
  - Given a recruiter prefers external profiles, When they click a LinkedIn or GitHub link, Then the link opens in a new tab.
- Rationale: Multiple contact paths respect recruiter preferences and reduce missed opportunities; confirmation reduces duplicate outreach.

BR-005 — Should Have
- Title: Basic analytics and conversion tracking
- Description: Instrumentation for page views, resume download events, contact form submissions, and top CTA clicks (privacy-compliant).
- Acceptance Criteria: (stakeholder-visible KPI examples): weekly counts for page views, resume downloads, and contact submissions reported to the candidate or hiring manager.
- Rationale: Recruiters and the candidate benefit from understanding which assets drive engagement; data guides iteration and prioritization.

BR-006 — Should Have
- Title: Social & code profile links
- Description: Visible links to primary public profiles (GitHub, LinkedIn, Twitter/Dev.to), and a labeled section for “Code samples” or repos referenced for each project.
- Rationale: Provides additional context for technical reviewers and enables deeper assessment when needed.

BR-007 — Could Have
- Title: Maintenance, versioning, and edit process
- Description: A simple process for the candidate to update content (e.g., maintain a small markdown source or CMS-backed form) and a visible "Last updated" date on the page.
- Rationale: Keeps information current with minimal effort and builds trust with hiring teams about the currency of the resume and projects.

BR-008 — Could Have
- Title: Accessibility & mobile-first presentation
- Description: Page designed for mobile recruiters and keyboard/screen-reader accessibility; clear typography and contrast.
- Rationale: Many recruiters review on mobile; accessibility widens audience and reduces barriers for all stakeholders.

## Metrics of Success
- Increase recruiter contacts initiated from the site by X% (baseline to be defined).
- Resume downloads and contact submissions are logged; target: measurable conversion rate improvement within first 3 months.

## Assumptions
- Candidate will provide resume, 3–5 projects, links to public code samples, and a primary contact email.
- Hosting and domain provisioning will be handled separately (not part of this BRD).

## Risks
- Missing or incomplete project artifacts may reduce the effectiveness of the portfolio.
- Privacy/compliance concerns if analytics or contact data are handled without consent or secure delivery.

## Clarifying Questions for the Business Analyst
1. Should the resume download require capturing the downloader's contact info (lead capture), or be an immediate download with optional follow-up? Please state preference.
2. Does the candidate require analytics to be anonymized and stored only locally, or may third‑party tracking (e.g., Google Analytics) be used? Any privacy constraints?
3. Will the candidate maintain content via a simple CMS, Git-based workflow, or expect the site to be edited manually? Which update cadence is expected?

---
Version history
- 1.0 — 2026-05-28 — Initial BRD created.
