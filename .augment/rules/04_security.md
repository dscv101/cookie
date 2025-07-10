---
description: "Minimises vulnerabilities and ensures compliance with OWASP Top 10 for Python."
alwaysApply: true
---
<security-rules>
<title>Security</title>
<overview>Minimise vulnerabilities and ensure compliance with OWASP Top 10 for Python.</overview>
<rules>
  - `Dependency scanning`: Run Safety and pip-audit weekly in CI; fail on high severity CVEs.
  - `Static analysis`: Enable Ruff-bandit and bandit rules; zero high/medium findings.
  - `Secrets`: Enforce GitGuardian scan on every push; block committed secrets.
  - `Least privilege`: Store credentials in env vars or HashiCorp Vault; never in code.
  - `Sandboxing`: For dynamic eval/exec, use ast.literal_eval or a restricted execution environment.
  - `HTTPS everywhere`: Use requests with verify=True; pin certs where possible.
  - `Deserialization safety`: Disallow pickle for untrusted input; prefer json or orjson.
  - `Runtime hardening`: Use python -X frozen_modules=on -X warn_default_encoding in production.
</rules>
</security-rules>