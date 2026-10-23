# Risk Management

## Managing security risk

Risk management is the continuing process of identifying, assessing, treating, and reviewing risks in the context of organizational priorities. It helps teams decide where to spend limited time and resources and who is accountable for a decision.

### Common treatment choices

| Choice | Meaning | Example |
| --- | --- | --- |
| Mitigate | Reduce likelihood or impact with safeguards. | Patch a service and restrict its network exposure. |
| Avoid | Stop the activity that creates the risk. | Retire an unsupported service. |
| Transfer/share | Allocate some financial or operational impact to another party. | Use an insurance policy while retaining security responsibilities. |
| Accept | Formally retain the risk within an approved tolerance. | Document a low-impact exception with an owner and expiry. |

Risk transfer does not remove accountability or prevent harm. Acceptance should be an informed, authorized decision, not the result of an untracked omission.

## Qualitative and quantitative assessment

Qualitative approaches use categories such as low, medium, and high. Quantitative approaches use numerical estimates. Either can be useful if the method, assumptions, and decision thresholds are understood. A precise-looking number is not automatically a precise estimate.

One simple teaching model is `risk = likelihood x impact`. It is not a universal calculation: organizations define their own scales, evidence requirements, risk appetite, and thresholds. A high-impact scenario can warrant attention even when likelihood is uncertain.

### Example workflow

For a vulnerable server, establish which data and services it supports, whether it is exposed, the plausible threat path, business impact, and current safeguards. Prioritize remediation according to impact, exploitability, exposure, and service dependencies. Record the decision and validate the change after remediation.

## Common mistakes

- Treating a risk register as a one-time inventory rather than a living record.
- Ranking solely by technical severity while ignoring reachability and business context.
- Recording a treatment without an owner, due date, or verification step.
- Assuming a vendor or insurer takes over all responsibility.

## Revision points

- Assess risk in context and state assumptions.
- Choose and document a treatment, owner, and review point.
- Reassess after material changes to assets, exposure, controls, or threats.

## Revision exercise

An internet-facing application stores customer data and has a known flaw. List the additional facts needed to estimate risk (for example, exploitability, authentication requirements, data sensitivity, compensating controls, and service dependencies). Recommend a treatment, owner, due date, and verification step. Do not assign a numerical score without a defined scale.

## References

- [Google Cybersecurity Certificate playlist](https://www.youtube.com/playlist?list=PLTZYG7bZ1u6ocTMdhDwwmfjaNv134KcWn)
- [Google course curriculum](https://grow.google/intl/en_in/cybersecurity-course)
- [NIST Cybersecurity Risk glossary](https://csrc.nist.gov/glossary/term/cybersecurity_risk)
- [NIST IR 8286 Rev. 1](https://csrc.nist.gov/pubs/ir/8286/r1/final)
