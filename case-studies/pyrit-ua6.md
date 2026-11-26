# Microsoft PyRIT: type safety and YAML validation

My contribution resolved **13 `unsound-assignment` findings across nine scoped model and registry files** in Microsoft PyRIT. [PR #4523](https://github.com/microsoft/PyRIT/pull/4523) received [Roman Lutz's approval](https://github.com/microsoft/PyRIT/pull/4523#pullrequestreview-6054314426) and merged into `main` on November 25, 2026. The work combined clearer types, validation of taxonomy YAML, and regression coverage. I used AI assistance during development.

## Problem

PyRIT loads harm-category definitions (a taxonomy written in YAML) and passes metadata through its models and registry. The `ty` type checker could not establish that several values matched their declared types. Sources included YAML data, model serialization, and attributes read dynamically from component classes. The nine files were temporarily excluded from the `unsound-assignment` rule. [The patch](https://github.com/microsoft/PyRIT/pull/4523/files) shows both those exclusions and their removal.

These were static-analysis findings: the count measures typing problems, and does not establish 13 user-visible runtime failures. The practical goal was to make the types enforceable while preserving existing behavior. Taxonomy validation deliberately added earlier rejection of malformed YAML, as described in [Roman's review](https://github.com/microsoft/PyRIT/pull/4523#pullrequestreview-6010891156).

## Change

The correction used several approaches appropriate to the source of each value:

- Apply supported defaults and validate taxonomy data when loading it: require a mapping, a string version, and definitions that map strings to strings. Return explicitly typed values after those checks.
- Build typed dictionaries for response metadata and message digests. Preserve the rule that response metadata overrides request metadata, and keep inherited tool-capture coverage out of responses.
- Preserve registry metadata types through generic parameters. Use documented casts where the values already have guarantees from their construction or class declarations, and share a typed credential-fallback helper.
- Remove the nine files from the temporary override and add tests for taxonomy defaults and invalid data.

The [merged commit](https://github.com/microsoft/PyRIT/commit/bdd974aa4a5cf95cd7a5f90804547ba74373a913) contains nine production files plus the type-checker configuration and taxonomy tests: 11 changed files in total.

## Validation and review

The [PR description](https://github.com/microsoft/PyRIT/pull/4523) records the locked all-extras type check improving from 13 findings to zero. It also reports 5,346 passing tests, five skips, and two expected failures across the offline models, registry, and selected downstream suites.

Roman's [November 23 review](https://github.com/microsoft/PyRIT/pull/4523#pullrequestreview-6010891156) independently confirmed all 13 fixes and reported a clean `ty check pyrit`. He also caught an edge case: bare `version:` and `definitions:` YAML keys become `None`, whereas absent keys already received defaults. The correction treats those `None` values like absent keys and retains errors for other invalid types. He reported 69 passing harm-category tests for his combined suggestions. The [merged tests](https://github.com/microsoft/PyRIT/blob/bdd974aa4a5cf95cd7a5f90804547ba74373a913/tests/unit/models/test_harm_category.py) cover the defaulting and rejection cases.

A later [review comment](https://github.com/microsoft/PyRIT/pull/4523#issuecomment-7147600406) identified an overlap with a newer response-metadata change on `main`. The final patch preserves both behaviors. Roman subsequently approved the PR, completing the review cycle before merge.

[Back to profile](../README.md)
