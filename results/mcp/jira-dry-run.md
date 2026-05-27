# Jira Dry-Run: "About Me" Portfolio — 2026-05-28

## 1) Summary
- BRs parsed: 8 (BR-001 → BR-008)
- Functional stories (US-): 10 (US-001 → US-010)
- NFRs parsed: 9 (NFR-001 → NFR-009)

## 2) Mapping strategy
- Requirement → Jira mapping:
  - BR (business requirement) → Epic
  - US- (functional user story) → Story
  - NFR- (non-functional requirement) → Task (or sub-task under a QA/Infrastructure Epic)
- MoSCoW → Jira Priority:
  - Must Have → Highest
  - Should Have → High
  - Could Have → Medium
  - Won't Have → Lowest
- Labels/components: use `frontend`, `ux`, `backend`, `analytics`, `accessibility`, `ci/cd` as appropriate.
- Link strategy: create Epics first, then create Stories and Tasks and link Stories to Epics. NFR Tasks will be created under a dedicated Epic `NFR: Quality & Constraints` and cross-linked to impacted Epics where relevant.

## 3) Issue plan (Epics + child issues)
Notes: Acceptance criteria are copied where available (Given/When/Then). If missing, marked "needs clarification".

- Epic: BR-001 — Clear professional headline & elevator summary
  - Type: Epic
  - Linked IDs: BR-001
  - Description: Provide a concise headline (role/title) and 2–3 sentence elevator summary communicating domain, years, and one differentiator.
  - Acceptance Criteria: "Given a recruiter lands on the page, When they scan the top of the page for ≤10 seconds, Then they can read a headline and a 2–3 sentence summary that states role, years of experience, and one differentiator."
  - Priority: Highest
  - Labels: frontend, ux
  - Child Stories:
    - Story: US-002 — Hero / Professional summary
      - Linked IDs: US-002
      - Description: Implement hero headline and 3–5 skill badges visible in top fold.
      - Acceptance Criteria: from US-002 (Given/When/Then in FRD)
      - Priority: Highest; Story points: 3
      - Labels: frontend, ux
    - Story: US-001 — Navigation (anchor links)
      - Linked IDs: US-001
      - Description: Implement smooth anchor navigation and active section highlighting.
      - Acceptance Criteria: from US-001
      - Priority: High; Story points: 2
      - Labels: frontend
    - Story: US-008 — Skills section with proficiency
      - Linked IDs: US-008
      - Description: Skill groups and simple proficiency indicators visible and consistent.
      - Acceptance Criteria: from US-008
      - Priority: High; Story points: 2

- Epic: BR-002 — Resume download & primary CTA
  - Type: Epic
  - Linked IDs: BR-002
  - Description: Prominent resume download button and clear primary CTA (download/contact) near top.
  - Acceptance Criteria: BR-002 G/W/T (download and CTA behaviors)
  - Priority: Highest
  - Labels: frontend
  - Child Stories:
    - Story: US-006 — Resume download
      - Linked IDs: US-006
      - Description: Resume opens/downloads as PDF; accessible and matches canonical file.
      - Acceptance Criteria: from US-006
      - Priority: Highest; Story points: 1
      - Labels: frontend, ux

- Epic: BR-003 — Project showcase with outcomes and links
  - Type: Epic
  - Linked IDs: BR-003
  - Description: Highlight 3–5 projects with problem→contribution→outcome, role, tech, and links.
  - Acceptance Criteria: BR-003 G/W/T (project card contents)
  - Priority: Highest
  - Labels: frontend, ux
  - Child Stories:
    - Story: US-003 — Projects gallery (list/tiles)
      - Linked IDs: US-003
      - Description: Responsive gallery displaying at least three projects with summary and links.
      - Acceptance Criteria: from US-003
      - Priority: Highest; Story points: 5
      - Labels: frontend, ux
    - Story: US-004 — Project detail modal / panel
      - Linked IDs: US-004
      - Description: Modal/panel with extended project details, links, and keyboard accessibility.
      - Acceptance Criteria: from US-004
      - Priority: High; Story points: 3
      - Labels: frontend, accessibility

- Epic: BR-004 — Contact flow & follow-up options
  - Type: Epic
  - Linked IDs: BR-004
  - Description: Contact form, mailto link, social links; form forwards to configurable email with confirmation.
  - Acceptance Criteria: BR-004 G/W/T (form submission confirmation and email delivery)
  - Priority: Highest
  - Labels: frontend, backend
  - Child Stories:
    - Story: US-005 — Contact form and email link
      - Linked IDs: US-005
      - Description: Implement minimal contact form and mailto fallback; success UX and delivery to candidate inbox.
      - Acceptance Criteria: from US-005
      - Priority: Highest; Story points: 3
      - Labels: frontend, backend

- Epic: BR-005 — Basic analytics and conversion tracking
  - Type: Epic
  - Linked IDs: BR-005
  - Description: Instrument page views, resume downloads, contact submissions, and CTA clicks (privacy-compliant).
  - Acceptance Criteria: weekly counts for page views, resume downloads, contact submissions (stakeholder examples)
  - Priority: High
  - Labels: analytics
  - Child Stories:
    - Story: AN-001 — Implement analytics events & reporting
      - Linked IDs: BR-005
      - Description: Add event instrumentation (resume download, contact submit, CTA clicks) and privacy options.
      - Acceptance Criteria: verify events in staging and weekly report delivery; privacy consent gating as required.
      - Priority: High; Story points: 3
      - Labels: analytics, privacy

- Epic: BR-006 — Social & code profile links
  - Type: Epic
  - Linked IDs: BR-006
  - Description: Visible links to GitHub, LinkedIn, and other profiles; code samples section per project.
  - Priority: High
  - Child Stories:
    - Story: US-007 — Social & code sample links
      - Linked IDs: US-007
      - Description: Implement social icons and repo links that open in new tabs.
      - Acceptance Criteria: from US-007
      - Priority: High; Story points: 1
      - Labels: frontend

- Epic: BR-007 — Maintenance, versioning, and edit process (Could Have)
  - Type: Epic
  - Linked IDs: BR-007
  - Description: Simple update workflow (markdown/CMS) and visible "Last updated" date.
  - Priority: Medium
  - Child Tasks:
    - Task: Content-edit workflow
      - Linked IDs: BR-007
      - Description: Decide and implement content editing approach (Markdown + CI or light CMS).
      - Acceptance Criteria: owner can update content with defined process; "Last updated" displayed.
      - Priority: Medium; Story points: 2
      - Labels: ci/cd

- Epic: BR-008 — Accessibility & mobile-first presentation (Could Have)
  - Type: Epic
  - Linked IDs: BR-008
  - Description: Mobile-first design and accessibility; note: NFRs include Must-level accessibility enforcement.
  - Priority: Medium
  - Child Stories/Tasks:
    - Task: Accessibility checks and remediation
      - Linked IDs: BR-008, NFR-002
      - Description: Run axe-core and manual checks; fix critical issues.
      - Acceptance Criteria: No critical axe-core violations; keyboard navigation verified.
      - Priority: Highest (per NFR); Story points: 5
      - Labels: accessibility, frontend

- Epic: NFR: Quality & Constraints
  - Type: Epic
  - Linked IDs: (NFR-001 → NFR-009)
  - Description: Non-functional targets (performance, accessibility, security, SEO, CI/CD, hosting).
  - Priority: Highest for Must NFRs; labels: ci/cd, accessibility, performance, security
  - Child Tasks (one per NFR):
    - Task: NFR-001 — Performance targets (Lighthouse budgets)
      - Acceptance Criteria: Lighthouse scores and budgets (see NFR doc)
      - Priority: Highest; Story points: 5
    - Task: NFR-002 — Accessibility (WCAG 2.1 AA)
      - Acceptance Criteria: axe-core & manual testing passes
      - Priority: Highest; Story points: 5
    - Task: NFR-003 — Security & privacy for contact form
      - Acceptance Criteria: anti-spam + HTTPS + privacy checklist
      - Priority: Highest; Story points: 3
    - Task: NFR-004 — SEO basics
      - Priority: High; Story points: 2
    - Task: NFR-005 — Cross-device/browser compatibility
      - Priority: Highest (core); Story points: 3
    - Task: NFR-006 — Maintainability (lint, tests)
      - Priority: High; Story points: 3
    - Task: NFR-007 — Hosting & CI/CD
      - Priority: Highest; Story points: 3
    - Task: NFR-008 — Analytics & Tracking
      - Priority: High; Story points: 3
    - Task: NFR-009 — Observability & error handling
      - Priority: Medium; Story points: 2

> Notes: Where a requirement lacked explicit Given/When/Then, the item is marked "needs clarification" in the description.

## 4) Sample Jira REST API payloads (replace placeholders)
- Epic (Jira Cloud):

```json
{
  "fields": {
    "project": {"key": "PROJECT_KEY"},
    "summary": "BR-001: Clear professional headline & elevator summary",
    "issuetype": {"name": "Epic"},
    "description": "Provide a concise headline and 2–3 sentence elevator summary (BR-001).",
    "labels": ["portfolio","epic"],
    "customfield_10011": "BR-001 Headline" // Replace with your instance's Epic Name custom field ID/name
  }
}
```

- Story (Jira Cloud):

```json
{
  "fields": {
    "project": {"key": "PROJECT_KEY"},
    "summary": "US-002: Hero / Professional summary",
    "issuetype": {"name": "Story"},
    "description": "Implement hero headline and skill badges. Acceptance: [Given/When/Then]...",
    "labels": ["frontend","ux"],
    "priority": {"name": "Highest"}
  }
}
```

- Task (Jira Cloud):

```json
{
  "fields": {
    "project": {"key": "PROJECT_KEY"},
    "summary": "NFR-001: Performance targets (Lighthouse budgets)",
    "issuetype": {"name": "Task"},
    "description": "Targets: FCP<=1.5s (desktop), Lighthouse >=90; see NFR doc.",
    "labels": ["performance","nfr"],
    "priority": {"name": "Highest"}
  }
}
```

> Linkage: After creating Epics, link Stories to Epics using your instance's Epic Link field or the Jira API endpoint for linking issues to an Epic.

## 5) Creation checklist
- Preconditions:
  - Confirm Jira `PROJECT_KEY` and user credentials with API token.
  - Identify Epic Name custom field id (commonly `customfield_10011`) in your Jira instance.
  - BA/Stakeholder approval to create issues.
- Approvals required: Business Analyst and Project Owner sign-off on MoSCoW mapping and priorities.
- Required fields to supply in API: `project.key`, `issuetype.name`, `summary`, `description`, `priority` (optional but recommended), and Epic Name custom field for Epics.
- Roll-back / cleanup:
  - All created issues can be deleted via DELETE `/rest/api/3/issue/{issueIdOrKey}`.
  - Save created issue keys in a transaction log to support clean-up if needed.

## 6) Next step / Approval
Proceed with Jira creation? (yes/no)

---

If you need clarification, please answer up to 3 quick questions:
1. Jira `PROJECT_KEY` to use for issue creation?
2. Do you prefer a single dedicated Epic for all NFRs (`NFR: Quality & Constraints`) or NFR Tasks attached directly to each related Epic?
3. Confirm default assignee (unassigned / pipeline user / specific username)?


*Prepared by Jira Sync — dry-run plan saved to `outputs/jira-dry-run.md`.*
