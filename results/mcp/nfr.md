# Non-Functional Requirements (NFR)

**Project:** About Me — Personal Portfolio (recruiter-facing)

**Version:** 1.0.0

**Date:** 2026-05-28

---

## Top 3 Must Have
- **Fast enough to retain recruiters:** Page interactive within 2s on modern desktop (NFR-001, Must)
- **Accessible:** WCAG 2.1 AA compliance for key flows (NFR-002, Must)
- **Secure & privacy-friendly contact:** Spam-protected contact form, no sensitive storage (NFR-003, Must)

---

## Summary
This document defines measurable non-functional requirements for a single-page "About me" portfolio targeted at recruiters and hiring managers. Each requirement has an ID prefixed with `NFR-` and a MoSCoW priority.

## Requirements

- **NFR-001 — Performance (Must)**
  - Target: Lighthouse Performance score >= 90 on desktop and >= 80 on mobile.
  - Load targets: First Contentful Paint (FCP) <= 1.5s (desktop), <= 2.5s (mobile); Time to Interactive (TTI) <= 2.0s (desktop), <= 3.5s (mobile).
  - Budgets: total network payload (critical path) <= 250 KB; JS bundle <= 120 KB compressed; images delivered <= 200 KB combined (use responsive images / modern formats).
  - Server targets: TTFB <= 500 ms for CDN-backed static hosting.
  - Testing/validation: Lighthouse CI in CI pipeline, performance budgets enforced, synthetic checks (WebPageTest median on mobile 4G), Lighthouse programmatic audits.

- **NFR-002 — Accessibility (Must)**
  - Target: Conform to WCAG 2.1 AA for primary recruiter flows (view profile, read projects, open contact modal, download resume).
  - Measurables: No critical violations from axe-core; contrast ratio >= 4.5:1 for body text; keyboard navigable and focus visible for all interactive controls.
  - Testing/validation: Automated axe-core checks in unit/E2E tests, CI gating, manual audit checklist (keyboard-only, screen reader - VoiceOver and NVDA), pa11y and Lighthouse accessibility audits.

- **NFR-003 — Security & Privacy (Must)**
  - Contact form: Anti-spam measures required (honeypot + rate limiting or reCAPTCHA/turnstile). Do not collect or store sensitive PII beyond name/email/message unless explicitly consented.
  - Transport: HTTPS/TLS with HSTS; all external analytics loaded via secure endpoints.
  - Data: No server-side resume parsing or persistent personal data storage unless approved; if any data is stored, follow GDPR/CCPA considerations and provide a privacy policy link.
  - Testing/validation: Static analysis of dependencies, Snyk/Dependabot alerts, basic security headers checked in CI, manual privacy checklist.

- **NFR-004 — SEO Basics (Should)**n+  - Target: Lighthouse SEO score >= 80.
  - Requirements: meaningful title and meta description, semantic HTML (structured content sections), Open Graph and Twitter Card metadata, resume downloadable as PDF with crawlable link, schema.org Person markup where appropriate.
  - Testing/validation: Lighthouse CI SEO audits, periodic SERP checks for name+role, validate structured data with Google's Rich Results test.

- **NFR-005 — Cross-Device & Browser Compatibility (Must for core, Could for legacy)**
  - Target platforms: latest two major versions of Chrome, Edge, Firefox, Safari (desktop and iOS); Android WebView modern versions.
  - Responsive: Layout tested at common breakpoints (320px, 375px, 428px, 768px, 1024px, 1440px).
  - Testing/validation: Matrix of automated visual snapshots (Playwright or Percy) for representative pages and breakpoints; smoke tests on real devices or BrowserStack for critical flows.

- **NFR-006 — Maintainability (Should)**
  - Code quality: Linting (ESLint / stylelint), consistent formatting (Prettier), component-driven structure (reusable UI components), clear README and contribution notes.
  - Tests: Unit tests for UI components and critical logic; minimal E2E tests for contact flow and resume download.
  - Dependency management: Dependabot or equivalent for dependency updates; monthly dependency review.
  - Testing/validation: CI lint/test gates, codeowners for PR review, maintainability score via static analysis.

- **NFR-007 — Hosting & CI/CD (Must)**
  - Recommended hosting: static-first hosting (Netlify, Vercel, GitHub Pages) with CDN and HTTPS.
  - CI: GitHub Actions (or equivalent) to run lint, unit tests, accessibility checks (axe), Lighthouse CI, and deploy preview builds for PRs.
  - Rollback: Keep atomic deploys and quick rollback on failure; require passing checks for protected branches.

- **NFR-008 — Analytics & Tracking (Should)**
  - Minimal tracking: use privacy-friendly analytics (e.g., Google Analytics 4 with IP anonymization and consent, or Plausible/Umami for simpler footprint).
  - Consent: If using identifiable analytics, present opt-in consent banner; provide an easy opt-out mechanism.
  - Event tracking: track resume download, contact submissions, and primary link clicks. Keep event payloads minimal and non-identifying.
  - Testing/validation: verify events in staging (dev console), periodic audits of third-party scripts, check consent gating in CI or staging.

- **NFR-009 — Observability & Error Handling (Could)**
  - Error reporting: client-side error capture (Sentry or similar) with PII scrubbing.
  - Monitoring: uptime monitoring for the site (Pingdom / StatusCake) and alerts for deploy failures.
  - Testing/validation: smoke test after deploy, simulate failures in staging.

## Acceptance Criteria / Validation Matrix
- Performance: Lighthouse CI run on each PR; fail pipeline if Performance < 80 or budgets exceeded (NFR-001).
- Accessibility: CI fails on critical axe-core violations; manual sign-off for keyboard and screen-reader flows (NFR-002).
- Security: No high/severe vulnerabilities in dependency scan; contact form must implement anti-spam before enabling (NFR-003).
- SEO: Required meta tags and structured data present; SEO score >= 80 (NFR-004).
- Cross-browser: Visual regression snapshots pass for defined breakpoints (NFR-005).

## Testing & Validation Tools (recommended)
- Lighthouse / Lighthouse CI — performance, accessibility, best-practices, SEO.
- axe-core (jest-axe or axe-playwright) — automated accessibility tests.
- Playwright / Puppeteer + Jest — E2E tests and visual snapshots.
- pa11y — accessibility smoke checks.
- WebPageTest (scripted) — real-device or median mobile network checks.
- Snyk / Dependabot — dependency vulnerability scanning.

## Implementation Notes / Best Practices
- Use server-side or build-time rendering of critical content where applicable to improve SEO and FCP (static export recommended).
- Defer non-critical JS; prefer small vanilla JS or framework with good tree-shaking.
- Use responsive images: modern formats (AVIF/WebP), srcset, and lazy-loading for below-the-fold images.
- Inline critical CSS for the above-the-fold portion; defer the rest.
- Keep analytics and third-party scripts loaded async and gated behind consent when they process personal data.

## CI/CD Example Checklist (for GitHub Actions)
- On PR: run `npm ci && npm run lint && npm test && npm run axe && npm run lighthouse-ci`.
- On merge to main: run full suite and publish to hosting provider with preview and production deploys.

## Privacy & Legal
- Provide a short Privacy Notice linked from the footer describing what is collected (email for contact), retention policy, and contact for deletion requests.
- Do not store messages from contact form longer than necessary; if storing, encrypt and provide deletion workflow.

## Questions for the Business Analyst
1. Should the contact form persist messages to a backend/email only, or is a direct email link (mailto) acceptable to avoid storage? (clarifies storage/PII) 
2. Do we need analytics that identify return visits or user-level tracking, or is aggregate, anonymized analytics sufficient? (clarifies privacy/consent scope)
3. Are there brand accessibility/color constraints or design requirements that may affect contrast and WCAG targets? (clarifies accessibility scope)

---

Document owner: NFR Writer
