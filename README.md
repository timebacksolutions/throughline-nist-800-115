# throughline-nist-800-115 — NIST SP 800-115 as a throughline source

A **throughline source**: a standalone, composable requirements graph that expresses **NIST
SP 800-115, "Technical Guide to Information Security Testing and Assessment"**. A consuming
project imports it under a namespace and references a technique or activity by UID:

```toml
# throughline.toml in a consuming project
[[sources]]
namespace = "nist800115"
url = "https://github.com/timebacksolutions/throughline-nist-800-115"
ref = "v1"
```

```yaml
links:
  - target: "nist800115:SR-0012"   # Penetration testing
    type: satisfies
```

It lets a team ground its security testing in the NIST methodology: "our assessment
*satisfies* `nist800115:SR-0009` (vulnerability scanning)", "we follow
`nist800115:SR-0017` (rules of engagement)" — checked structurally by
`tl-compose check --strict`. It pairs naturally with the GOV.UK "Vulnerability and
penetration testing" guidance in `throughline-govuk-testing`.

## Shape

One root intent → 6 category/phase `user_requirement`s → 25 technique/activity
`system_requirement`s.

| § | Category / phase (`user_requirement`) | Techniques / activities |
|---|---|---|
| 3 | Review techniques | documentation, log, ruleset, configuration review; network sniffing; file integrity checking |
| 4 | Target identification and analysis | network discovery; port/service identification; vulnerability scanning; wireless scanning |
| 5 | Target vulnerability validation | password cracking; penetration testing; social engineering |
| 6 | Security assessment planning | assessment policy; risk-based prioritisation; approach & objectives; rules of engagement; legal & authorization |
| 7 | Security assessment execution | coordination; execution; results analysis; secure data handling |
| 8 | Post-testing activities | root-cause analysis; reporting; remediation & tracking |

The full generated spec is [`docs/spec.md`](docs/spec.md).

## Licence

Apache-2.0 for this repository's structure and tooling — see [`LICENSE`](LICENSE). NIST SP
800-115 is a U.S. government work in the public domain; the content restated here is derived
from it, with each item's `attrs.source_ref` citing the section. The authoritative document
is at [csrc.nist.gov](https://csrc.nist.gov/pubs/sp/800/115/final). See [`NOTICE`](NOTICE).

## Editions

Modelled from the published guide (2008) on `main`, tagged `v1`. A future NIST revision would
go on its own branch/tag selected by git `ref`.
