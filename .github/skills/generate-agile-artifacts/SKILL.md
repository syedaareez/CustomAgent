---
name: generate-agile-artifacts
description: Generates agile artifacts including epics, story estimation, acceptance test cases, risk registers, sprint planning suggestions, and user journey maps from business requirements.
---

# Agile Artifacts Skill

## Epic Generation
- Group related user stories into Epics (EP-001, EP-002...)
- Each epic: ID, Title, Description, Linked Stories
- Each epic must include a Definition of Done checklist

## Story Estimation
- Add story points (Fibonacci: 1,2,3,5,8,13)
- Include "Traces to: BR-NNN" on every story
- Flag dependencies between stories (e.g., "Blocked by: US-NNN")

## Acceptance Test Cases
- Add a test case table per user story
- Columns: Test ID, Scenario, Steps, Expected Result, Pass/Fail
- Use TC-NNN format for test case IDs

## Risk Register
- Include a Risk Register section
- Columns: Risk ID (RSK-NNN), Description, Likelihood (High/Med/Low),
  Impact (High/Med/Low), Mitigation Strategy
- Cover at least: performance, accessibility, content, and security risks

## Sprint Planning Suggestion
- Recommend sprint allocation based on story points
- Assume 2-week sprints with velocity of ~20 points
- Group by dependency order, not just epic

## User Journey Maps
- Add a journey map for each major business consideration
- Include: Persona, Goal, Steps, Pain Points, Opportunities