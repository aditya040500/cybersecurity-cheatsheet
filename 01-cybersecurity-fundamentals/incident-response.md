# Incident Response

## Purpose

Incident response provides an organized way to handle suspected or confirmed security events. A consistent workflow helps limit harm, coordinate decisions, preserve useful evidence, restore services, and improve future readiness.

## A practical workflow

| Stage | Main activity | Example question |
| --- | --- | --- |
| Prepare | Define roles, contacts, tools, escalation, and decision authority. | Who can isolate a production endpoint? |
| Detect and analyze | Validate signals, establish scope, and assess severity. | Is this login pattern expected, and which accounts are involved? |
| Contain | Limit ongoing impact while preserving critical operations. | Can the affected host be isolated safely? |
| Eradicate | Remove the cause and unauthorized access. | Has the vulnerable service been fixed and persistence removed? |
| Recover | Restore services and monitor for recurrence. | Are systems clean, stable, and approved to return? |
| Learn | Record findings and improve controls and procedures. | Which detection or response step should change? |

Organizations may name or combine these stages differently. Follow the approved incident plan and applicable reporting requirements.

### Decision points

| Decision | Information to establish |
| --- | --- |
| Is this an incident? | Validate the signal and apply the organization's incident criteria. |
| How severe is it? | Scope affected assets, data, accounts, service impact, and safety concerns. |
| What containment is safe? | Consider ongoing harm, business continuity, dependencies, and evidence preservation. |
| Who must be engaged? | Follow escalation roles, legal/privacy requirements, and communications plans. |
| Is recovery complete? | Confirm the cause is addressed, systems are monitored, and the owner approves return to service. |

## Evidence and communication

Keep a clear timeline, record actions and decision-makers, preserve relevant logs and artifacts according to policy, and restrict access to sensitive incident material. Coordinate communications through designated roles. Avoid changing affected systems before evidence needs and containment trade-offs have been considered.

## Example

A SIEM alert shows a privileged account used from an unusual location. An analyst validates the event with identity and endpoint records, escalates under policy, and works with the system owner to contain access. The team determines scope, removes unauthorized access, restores normal operation, and documents follow-up actions.

## Common mistakes

- Confusing an alert with a confirmed incident.
- Delaying escalation while waiting for certainty.
- Making undocumented changes that complicate investigation or recovery.
- Restoring systems before confirming the cause has been addressed.
- Closing the incident without recording lessons and owners for follow-up work.

## Revision points

- Prepare before an incident: roles, authority, contacts, and evidence handling.
- Validate and scope before selecting containment actions.
- Track a timeline, communicate through assigned channels, and verify recovery.
- Use lessons learned to improve readiness and controls.

## Revision exercises

1. A suspicious sign-in generates an alert. What should happen before deciding it is a confirmed incident?
2. Give an example where immediate containment could affect evidence or service availability.
3. Name four items to record in an incident timeline.
4. What evidence supports a decision to return a host to service?

## References

- [Google Cybersecurity Certificate playlist](https://www.youtube.com/playlist?list=PLTZYG7bZ1u6ocTMdhDwwmfjaNv134KcWn)
- [Google course curriculum](https://grow.google/intl/en_in/cybersecurity-course)
- [NIST SP 800-61 Rev. 3: Incident Response Recommendations and Considerations](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
