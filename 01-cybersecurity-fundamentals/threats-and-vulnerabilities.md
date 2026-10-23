# Threats, Vulnerabilities, and Risk

## Key terms

| Term | Meaning | Example |
| --- | --- | --- |
| Asset | Something valuable that needs protection. | Customer data, a service, or an employee account. |
| Threat | A circumstance or actor that could cause harm. | A phishing campaign targeting staff. |
| Vulnerability | A weakness that can be exploited or otherwise cause failure. | An unpatched internet-facing application. |
| Exploit | A method or code that takes advantage of a vulnerability. | A crafted request that triggers an application flaw. |
| Risk | The potential for loss, commonly assessed through likelihood and impact. | A reachable flaw could expose sensitive records. |

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

## Revision points

- Trace the relationship: asset -> threat path -> weakness -> possible impact -> risk.
- Include current safeguards when estimating remaining risk.
- Record assumptions and revisit decisions as exposure or threat conditions change.

## References

- [Google Cybersecurity Certificate playlist](https://www.youtube.com/playlist?list=PLTZYG7bZ1u6ocTMdhDwwmfjaNv134KcWn)
- [Google course curriculum](https://grow.google/intl/en_in/cybersecurity-course)
