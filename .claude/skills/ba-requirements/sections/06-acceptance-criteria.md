# Acceptance criteria

## Purpose
Define when each user story is done, in a form testers and developers can use directly.

## Inputs
User stories above; business rules from functional requirements.

## How to write
- Gherkin style: **Given** <context>, **When** <action>, **Then** <outcome>.
- At least one happy path and one exception/edge case per Must story.
- Use concrete values (amounts, times, statuses) from context.md where possible.

## Format
#### US-01 — <short title>
- **AC1** Given …, When …, Then …
- **AC2 (exception)** Given …, When …, Then …

## Quality checks
- Each AC is independently testable with a clear pass/fail.
- Edge cases from pain points (the things that go wrong today) are covered.

## Technique note
Given/When/Then (Gherkin) comes from Behaviour-Driven Development. Writing the failure cases is where a BA adds the most value — that's where today's pain points hide.
