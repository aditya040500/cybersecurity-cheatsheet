# Security Controls

## What a control does

A security control is a safeguard or process used to prevent, detect, or respond to unwanted events and reduce risk. Controls can be grouped by purpose or by how they are implemented.

| Grouping | Types | Examples |
| --- | --- | --- |
| By function | Preventive, detective, corrective | Access restrictions; monitoring alerts; restoring from a known-good backup. |
| By implementation | Technical, administrative, physical | MFA; an approved access policy; a locked server room. |

A control's presence does not prove it works. Define its intended outcome, assign ownership, and check operation and coverage.

## Layered protection

Layering controls reduces reliance on one safeguard. For example, MFA can reduce account takeover risk, least-privilege authorization can limit what a compromised account can do, and logging can help detect suspicious activity. Each control has failure modes; together they can limit the chance or impact of harm.

## Practical example

To protect an administrative account: require strong authentication, grant elevated permissions only when needed, log privileged actions, alert on unusual use, and maintain a tested recovery path. Review access when job duties change.

## Common mistakes

- Assuming a policy alone enforces a control.
- Treating a tool purchase as evidence that risk is reduced.
- Applying a control without considering usability, exceptions, and bypass paths.
- Relying on one preventive measure without detection or recovery capability.

## Revision points

- State the risk a control addresses and the result it should produce.
- Distinguish prevention, detection, and correction.
- Validate that the control is configured, operating, and reviewed.

## References

- [Google Cybersecurity Certificate playlist](https://www.youtube.com/playlist?list=PLTZYG7bZ1u6ocTMdhDwwmfjaNv134KcWn)
- [Google course curriculum](https://grow.google/intl/en_in/cybersecurity-course)
