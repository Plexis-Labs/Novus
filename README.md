# Novus

> A browser platform that turns a user’s natural-language request into a safe, persistent micro-app that works alongside the website they are already using.[cite: 1, 9]

## The Idea

Websites are built for average workflows. But every person needs something slightly different.[cite: 1]

A user may be looking at:

* an employee dashboard and need department analytics[cite: 1]
* GitHub and need a PR review workspace[cite: 1, 9]
* LeetCode and need a revision queue[cite: 1, 9]
* YouTube and need a learning tracker[cite: 9]

Novus adds a personal workspace layer on top of the website already open in the browser.[cite: 1, 9]
The user describes what they need.[cite: 1] Novus creates a persistent micro-app beside the website.[cite: 1]

## Example

On a paginated employee dashboard, a user asks:[cite: 1]

> Collect all employee pages, group active employees by department, save a monthly snapshot, and draft a report.[cite: 1, 5]

Novus:

1. detects the available employee table and pagination[cite: 5]
2. asks before collecting additional pages[cite: 1, 5]
3. collects rows through the visible UI[cite: 5]
4. deduplicates records and shows data coverage[cite: 1, 5]
5. creates a persistent analytics workspace[cite: 1, 5]
6. restores the workspace when the user returns[cite: 1, 9]

## Architecture

Host Website
    ↓
Site Adapter
    ↓
Trusted Novus Runtime
    ↓
Sandboxed Generated Micro-App
[cite: 9]

### Site Adapter
The adapter translates messy website HTML into clean typed entities.[cite: 1]

type Employee = {
  id: string;
  name: string;
  department: string;
  status: "ACTIVE" | "INACTIVE";
};[cite: 1]

### Trusted Runtime
The runtime controls:

* permissions[cite: 1, 9]
* data collection approval[cite: 1, 9]
* local storage[cite: 1, 9]
* feature lifecycle[cite: 1, 9]
* route changes[cite: 9]
* manifest validation[cite: 9]
* typed communication with generated apps[cite: 9]

### Generated Micro-App
AI creates the product layer:[cite: 1]

* dashboards[cite: 1]
* charts[cite: 1, 5]
* filters[cite: 1, 5]
* calculations[cite: 1, 5]
* notes[cite: 1, 5]
* report drafts[cite: 1, 5]
* local workflow state[cite: 5]

The generated app does not get unrestricted access to the website DOM, cookies, tokens, or extension APIs.[cite: 9]

## MVP
The first demo is a controlled Acme HR dashboard.[cite: 1]

* Open Acme HR dashboard[cite: 1]
* → ask for workforce analytics[cite: 1]
* → approve collection across paginated pages[cite: 1]
* → see progress and coverage[cite: 1]
* → receive a native-looking right-side workspace[cite: 1]
* → reload the page[cite: 1]
* → workspace and saved state return[cite: 1]

## What Novus Is Not

* not a promise to work on every website[cite: 1, 9]
* not an unrestricted AI userscript generator[cite: 1, 9]
* not a tool for reading private databases or tokens[cite: 1, 9]
* not a replacement for official APIs[cite: 9]
* not an automatic email sender in v1[cite: 1]

## Repository Structure

apps/
  extension/
  acme-hr-demo/

packages/
  contracts/
  runtime/
  bridge/
  adapters/
  collector/
  microapp-sdk/
  ui-kit/

tests/
  e2e/
  adapter-fixtures/
[cite: 10]

## Contributing
Read CONTRIBUTING.md before opening a pull request.[cite: 10]

## Governance
Read GOVERNANCE.md.

## License
License decision pending founding-team agreement.
