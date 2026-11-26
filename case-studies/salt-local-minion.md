# Salt: restoring local minion connections

**Outcome:** Added a missing asynchronous cleanup method and regression coverage for Salt minions configured with `file_client: local`. Maintainers accepted [PR #70653](https://github.com/saltstack/salt/pull/70653) into the `3008.x` branch on November 23, 2026.

This was an AI-assisted contribution. I directed, reviewed, and tested the change, as disclosed in the PR.

## Problem

A reported failure prevented a Salt minion—the agent on a managed machine—from completing its connection to the master when it used local files. The connection raised `AttributeError: 'AsyncPillar' object has no attribute 'aclose'`. The affected minion remained unavailable to commands from the master, although local `salt-call` commands still worked. [Original report](https://github.com/saltstack/salt/issues/70637)

The cause was an interface mismatch during cleanup of pillar configuration data. The minion awaited `aclose()` after compiling that data. With the affected local configuration, the factory returned `AsyncPillar`, which lacked that method; the remote implementation already provided it. The same cleanup interface was used during initialization and pillar refresh. [Diagnosis and scope](https://github.com/saltstack/salt/pull/70653)

## Change

The production correction added `AsyncPillar.aclose()` and delegated to the existing `destroy()` method. Reusing that method preserved the established cleanup of its two client objects and the guard that prevents repeated destruction. Both asynchronous call sites could use the expected interface without duplicating the teardown logic. [Merged implementation](https://github.com/saltstack/salt/blob/1351f22a1294f50e44359516c803a8559b7675e1/salt/pillar/__init__.py)

The contribution also added a focused unit test and a changelog entry. The complete patch changed three files: the pillar implementation, its regression test, and the changelog. [Accepted changes](https://github.com/saltstack/salt/pull/70653/files)

## Validation and review

The [PR's recorded validation](https://github.com/saltstack/salt/pull/70653) reports the regression test failing without the correction and passing with it: one failure before, one pass after.

The test obtains the local pillar through `get_async_pillar()` with mocked dependencies, checks the returned class, and awaits `aclose()` twice. After both calls, it verifies that each client was destroyed exactly once. This covers the missing asynchronous method and safe repeated cleanup in the affected configuration. [Regression test](https://github.com/saltstack/salt/blob/1351f22a1294f50e44359516c803a8559b7675e1/tests/pytests/unit/pillar/test_async_pillar.py)

Repository checks also exposed a Python 3.8 syntax compatibility issue in the test. A follow-up commit replaced parenthesized context-manager syntax with `contextlib.ExitStack`, preserving the patches and their order while meeting Salt's configured syntax baseline. This feedback came from Ruff, as documented in the [compatibility commit](https://github.com/saltstack/salt/commit/1d364160439629610fd7964975971f44e674862c).

Maintainer `dwoz` [approved the final contribution](https://github.com/saltstack/salt/pull/70653#pullrequestreview-6018126974) before it merged into `3008.x`.

[Back to profile](../README.md)
