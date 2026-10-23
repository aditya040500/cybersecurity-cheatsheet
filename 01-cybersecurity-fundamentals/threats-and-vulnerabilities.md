# Threats, Vulnerabilities, and Risk

## Key terms

| Term | Meaning | Example |
| --- | --- | --- |
| Asset | Something valuable that needs protection. | Customer data, a service, or an employee account. |
| Threat | A circumstance or actor that could cause harm. | A phishing campaign targeting staff. |
| Vulnerability | A weakness that can be exploited or otherwise cause failure. | An unpatched internet-facing application. |
| Exploit | A method or code that takes advantage of a vulnerability. | A crafted request that triggers an application flaw. |
| Risk | The potential for loss, commonly assessed through likelihood and impact. | A reachable flaw could expose sensitive records. |

## Common weakness patterns

These are useful beginner categories; their presence alone does not establish exploitability or business risk.

| Pattern | Example | Defensive response |
| --- | --- | --- |
| Missing or delayed updates | An exposed application runs a version with a known flaw. | Inventory, prioritize, test, and deploy approved updates. |
| Weak identity protection | Reused credentials allow an attacker to enter an account. | MFA, unique credentials, rate limits, and sign-in monitoring. |
| Misconfiguration | A storage location is readable by unintended users. | Secure baselines, least privilege, and configuration review. |
| Excessive privilege | A routine account can administer unrelated systems. | Role review, just-in-time elevation, and audit logs. |
| Injection or input handling flaw | Untrusted input is interpreted as a command or query. | Safe APIs, validation, encoding, and security testing. |
| Unnecessary exposure | A service listens on an interface or port without a business need. | Remove or restrict the service and verify network policy. |

Threat, vulnerability, and risk are related but not synonyms. A vulnerability may exist without a likely threat path; risk depends on context, exposure, impact, and existing safeguards.

## Assessing a scenario

Use a repeatable sequence:

1. Identify the asset and the harm that matters.
2. Identify relevant threats and weaknesses.
3. Estimate likelihood and impact using the organization's method.
4. Consider existing controls and residual risk.
5. Record an owner, decision, and review date for treatment.

### Example

An internet-facing service stores customer details. The service has a known unpatched weakness. The asset is customer information; the threat could exploit the exposed service; the weakness is the missing patch; potential impact includes unauthorized disclosure and service disruption. The team should validate exposure and business impact, apply the approved remediation, and verify the fix.

## Common misconceptions

- A threat is not the same thing as a vulnerability: one can exploit the other.
- Risk is not a fixed property of a vulnerability; exposure and business impact change it.
- A high-severity score is an input to prioritization, not a complete business risk decision.
- "No known exploitation" does not prove that a weakness is harmless.

## A short triage worksheet

| Question | Record |
| --- | --- |
| What asset and owner are involved? | Name the system, data, and accountable owner. |
| What is the weakness and evidence? | Record version/configuration, finding, or observed behavior. |
| Is there a credible path to impact? | Note reachability, required access, and dependencies. |
| What is the likely harm? | Consider disclosure, alteration, outage, safety, or compliance. |
| Which controls already reduce exposure? | Confirm they are configured and operating. |
| What decision is needed? | Treatment, owner, due date, and verification step. |

## Revision points

- Trace the relationship: asset -> threat path -> weakness -> possible impact -> risk.
- Include current safeguards when estimating remaining risk.
- Record assumptions and revisit decisions as exposure or threat conditions change.

## Revision exercises

1. For a public service with an overdue patch, name the asset, threat, vulnerability, and possible impact separately.
2. Why is a vulnerability scanner's severity score not a complete risk decision?
3. Give one preventive and one detective control that could reduce the impact of credential theft.
4. What evidence would you collect before deciding whether an exposed service is reachable?

## References

- [Google Cybersecurity Certificate playlist](https://www.youtube.com/playlist?list=PLTZYG7bZ1u6ocTMdhDwwmfjaNv134KcWn)
- [Google course curriculum](https://grow.google/intl/en_in/cybersecurity-course)
- [NIST Cybersecurity Risk glossary](https://csrc.nist.gov/glossary/term/cybersecurity_risk)
- [NIST IR 8286 Rev. 1](https://csrc.nist.gov/pubs/ir/8286/r1/final)
