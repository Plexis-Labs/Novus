# Novus

> A browser platform that turns a user’s natural-language request into a safe, persistent micro-app that works alongside the website they are already using.

## The Idea

Websites are built for average workflows. But every person needs something slightly different.

A user may be looking at:

* an employee dashboard and need department analytics
* GitHub and need a PR review workspace
* LeetCode and need a revision queue
* YouTube and need a learning tracker

Novus adds a personal workspace layer on top of the website already open in the browser.
The user describes what they need. Novus creates a persistent micro-app beside the website.

## Example

On a paginated employee dashboard, a user asks:

> Collect all employee pages, group active employees by department, save a monthly snapshot, and draft a report.

Novus:

1. detects the available employee table and pagination
2. asks before collecting additional pages
3. collects rows through the visible UI
4. deduplicates records and shows data coverage
5. creates a persistent analytics workspace
6. restores the workspace when the user returns

## Architecture

```text
Host Website
    ↓
Site Adapter
    ↓
Trusted Novus Runtime
    ↓
Sandboxed Generated Micro-App
```

### Site Adapter
The adapter translates messy website HTML into clean typed entities.

type Employee = {
  id: string;
  name: string;
  department: string;
  status: "ACTIVE" | "INACTIVE";
};

### Trusted Runtime
The runtime controls:

* permissions
* data collection approval
* local storage
* feature lifecycle
* route changes
* manifest validation
* typed communication with generated apps

### Generated Micro-App
AI creates the product layer:

* dashboards
* charts
* filters
* calculations
* notes
* report drafts
* local workflow state

The generated app does not get unrestricted access to the website DOM, cookies, tokens, or extension APIs.

## MVP
The first demo is a controlled Acme HR dashboard.

* Open Acme HR dashboard
* → ask for workforce analytics
* → approve collection across paginated pages
* → see progress and coverage
* → receive a native-looking right-side workspace
* → reload the page
* → workspace and saved state return

## What Novus Is Not

* not a promise to work on every website
* not an unrestricted AI userscript generator
* not a tool for reading private databases or tokens
* not a replacement for official APIs
* not an automatic email sender in v1

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

## Contributing
Read [CONTRIBUTING.md](./CONTRIBUTING.md) before opening a pull request.

## Governance
Read [GOVERNANCE.md](./GOVERNANCE.md)

## License
License decision pending founding-team agreement.
