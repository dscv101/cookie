---
description: "Guarantees reliability and facilitates safe refactors assisted by the coding agent."
alwaysApply: true
---
<testing-rules>
<title>Testing</title>
<overview>Guarantee reliability and facilitate safe refactors assisted by the coding agent.</overview>
<rules>
    - `Framework`: Use pytest 9.x with --strict-config --strict-markers.
    - `Structure`: Mirror package layout under tests/; name files test_*.py.
    - `Coverage`: Achieve ≥ 90 % statement + branch coverage; enforced in CI via pytest-cov.
    - `Property-based`: Use hypothesis for critical logic; target edge cases.
    - `Mocks`: Prefer pytest-mock; avoid over-mocking – favour real behaviour or fakes.
    - `Filesystem`: Use pyfakefs for file IO tests.
    - `DB/API`: Spin up containers via testcontainers-python; no live prod services.
    - `Performance`: Mark long tests with @pytest.mark.slow; run on nightly CI.
    - `Reproducers`: Capture failing seeds from Hypothesis in hypothesis.json.
    - `Test data`: Keep small fixtures in tests/fixtures; large (>100 KB) in remote storage.
</rules>
</testing-rules>