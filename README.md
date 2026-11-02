# Shawn Russ

**Software development · Python automation · Web interfaces**

I build focused software tools with AI-assisted development, automated tests, and clear documentation. My public work includes interactive dashboards, public-data exports, repeatable reports, simulations, and video templates.

**Available for small freelance projects and focused bug fixes.**  
US Eastern · Calls by appointment · [Discuss a project on Upwork](https://www.upwork.com/freelancers/~01159cc098d8e7ab67)

## What I can help with

- **Web interfaces:** small dashboards, interactive components, filters, and data displays.
- **Python automation:** CSV processing, public-data API integrations, saved-page extraction, and command-line tools.
- **Testing and fixes:** reproduce a bug, implement a scoped change, and add regression checks.
- **Video templates:** turn structured content into reusable Remotion title cards.

## Selected work

These are original portfolio demonstrations using fictional, simulated, or public data. They are AI-assisted projects, not client engagements.

### [Fern & Field — member dashboard](https://github.com/shawnrruss/demo-dashboard)

Member profiles, booking filters, date sorting, and volunteer totals in an Astro + React interface. Tests cover data isolation, date boundaries, and component interactions; CI also checks types, lint, and the production build.

**Astro · React · TypeScript · Tailwind CSS · Vitest**  
[Code and setup](https://github.com/shawnrruss/demo-dashboard#quick-start) · [Tests](https://github.com/shawnrruss/demo-dashboard/tree/main/tests) · [CI](https://github.com/shawnrruss/demo-dashboard/actions/workflows/ci.yml)

[![Fern & Field member dashboard with booking filters and volunteer totals; fictional demo data](https://raw.githubusercontent.com/shawnrruss/demo-dashboard/main/docs/preview.png)](https://github.com/shawnrruss/demo-dashboard)

*Static demo with local fixture data; no authentication or backend.*

### [Price Watch — catalogue changes to reports](https://github.com/shawnrruss/demo-price-watch)

Extracts product records from saved HTML, stores dated SQLite snapshots, and reports price, stock, addition, and removal changes. Includes fixture-based tests, CSV/JSON exports, and an HTML report. CI runs the example workflow as well as tests and lint.

**Python · CSS selectors · SQLite · HTML/SVG · unittest**  
[Example output and setup](https://github.com/shawnrruss/demo-price-watch#quick-start) · [Tests](https://github.com/shawnrruss/demo-price-watch/tree/main/tests) · [CI](https://github.com/shawnrruss/demo-price-watch/actions/workflows/ci.yml)

*Offline demonstration using fictional catalogues; no live crawling or scheduled monitoring.*

### [Business List — public data to CSV](https://github.com/shawnrruss/demo-lead-skill)

A Python CLI and Claude Agent Skill that turn OpenStreetMap business records into sorted, deduplicated CSV files. Includes an offline example and tests for input validation, query escaping, export behavior, and service failures.

**Python · Overpass API · CSV · unittest**  
[Offline example](https://github.com/shawnrruss/demo-lead-skill#offline-demonstration) · [Tests](https://github.com/shawnrruss/demo-lead-skill/blob/main/tests/test_offline.py) · [CI](https://github.com/shawnrruss/demo-lead-skill/actions/workflows/ci.yml)

### [Simlab — staffing and project-risk simulations](https://github.com/shawnrruss/demo-sim-lab)

Seeded queue and Monte Carlo models produce CSV results and self-contained HTML reports. Tests check reproducibility, invalid inputs, report output, and analytical reference cases. CI checks Python 3.12 and 3.14 on Windows and Ubuntu.

**Python · Discrete-event simulation · Monte Carlo · HTML/SVG · unittest**  
[Examples and assumptions](https://github.com/shawnrruss/demo-sim-lab) · [Tests](https://github.com/shawnrruss/demo-sim-lab/tree/main/tests) · [CI](https://github.com/shawnrruss/demo-sim-lab/actions/workflows/ci.yml)

*Simulated examples with explicit modeling assumptions; not validated forecasts for a real business.*

### [JSON-driven video cards](https://github.com/shawnrruss/demo-remotion-card)

Disclosure, recap, and closing cards generated from one JSON file. Tests cover frame calculations, optional sequences, and text validation. The repository includes rendered stills and local video-render commands.

**Remotion · React · TypeScript · Vitest**  
[Rendered examples and setup](https://github.com/shawnrruss/demo-remotion-card) · [Tests](https://github.com/shawnrruss/demo-remotion-card/tree/main/tests)

### [Reproducible CSV reporting — CLV demo](https://github.com/shawnrruss/demo-clv-report)

A Python reporting example using simulated sports-betting records. Demonstrates CSV validation, seeded bootstrap intervals, structured exports, and explicit small-sample limitations.

**Python · CSV/JSON · Statistical reporting · unittest**  
[Example output and method notes](https://github.com/shawnrruss/demo-clv-report#example-report) · [Tests](https://github.com/shawnrruss/demo-clv-report/tree/main/tests)

## Open-source work

- **[Microsoft PyRIT #3815](https://github.com/microsoft/PyRIT/pull/3815):** submitted a fix preserving the `QUEUED` state in scenario-history filters, URLs, and API requests, with regression tests and a TypeScript completeness check.
- **[OpenCTI #19488](https://github.com/OpenCTI-Platform/opencti/pull/19488):** submitted a Python client fix for file IDs containing reserved URL characters, with regression tests.
- **[elmo #1089](https://github.com/elmohq/elmo/pull/1089):** submitted unit tests for API-key scope conversion, ordering, deduplication, invalid inputs, and round trips.

*All three pull requests are open as of November 2, 2026; none is merged.*

## How I work

I use AI coding tools for implementation, investigation, and test development. I direct the work, review the results, and remain responsible for the deliverable.

My approach is to agree on a small scope and acceptance criteria, make reviewable changes, verify the relevant behavior, and provide setup instructions and a plain-language handover.

## Let's work together

**[Discuss your project with me on Upwork](https://www.upwork.com/freelancers/~01159cc098d8e7ab67)**

Start with the problem you want to solve, your existing stack or files, and the result you need.
