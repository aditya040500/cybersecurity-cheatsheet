# Security Fundamentals

## Purpose of cybersecurity

Cybersecurity protects systems, networks, people, and information from unauthorized access, disruption, alteration, or destruction. A security decision should preserve business services while reducing the likelihood or impact of harm.

### Why it matters

An organization depends on trustworthy information and available services. A compromised account, altered record, or unavailable system can affect customers, operations, safety, and legal obligations.

## The CIA triad

| Property | Meaning | Example |
| --- | --- | --- |
| Confidentiality | Information is seen only by authorized parties. | Restrict payroll records to approved roles. |
| Integrity | Information remains accurate and changes are authorized. | Log and validate changes to a payment record. |
| Availability | Systems and information are usable when needed. | Maintain tested backups and redundant service capacity. |

Controls often support more than one property. Encryption can protect confidentiality, while hashes and signed records can help detect unauthorized changes. Backups support availability, but do not alone ensure a service can be restored quickly.

### Practical example

For an online appointment service, access control limits who can view patient data (confidentiality), audit trails record updates (integrity), and resilient hosting with recovery procedures helps keep booking available.

### Common mistakes

- Treating the CIA properties as interchangeable. A control can improve one property while leaving another weak.
- Assuming encryption alone makes data secure. Key handling, access, endpoints, and recovery still matter.
- Equating a successful backup job with a tested recovery capability.

## Identity and access

Authentication establishes which identity is requesting access. Authorization determines what that identity may do. Accounting or auditing records relevant actions.

| Term | Question answered | Example |
| --- | --- | --- |
| Authentication | Who are you? | Password plus a security key. |
| Authorization | What may you access or change? | A help-desk role can reset accounts but cannot export payroll. |
| Auditing | What happened, and by whom? | A record of a privileged configuration change. |

Use least privilege: grant only the access needed for a defined task and review it when roles change. Multi-factor authentication combines different factor types, such as something known and something possessed; two passwords are still one factor type.

## Security operations and monitoring

Security monitoring reviews events from endpoints, identity systems, networks, and applications to find activity that needs investigation. Logs provide records of events; a SIEM collects and correlates events to support searches, alerts, and investigations.

An alert is a signal to examine, not proof of an incident. Analysts validate context, preserve evidence, determine scope, and follow the organization's escalation process. Time synchronization, useful log fields, retention, and access controls affect whether records can support an investigation.

### Practical example

A SIEM rule may flag repeated failed logins followed by a successful login from an unusual source. The analyst checks the account history, source details, endpoint activity, and user context before deciding whether to contain or escalate.

### Common mistakes

- Treating every alert as a confirmed compromise.
- Ignoring false negatives, missing data sources, or incorrect time settings.
- Collecting logs without limiting access or retention to an approved policy.

## Revision points

- Start with confidentiality, integrity, and availability; identify which property is at risk.
- Separate identity verification from permission decisions.
- A log is evidence of an event; a SIEM helps organize and correlate it; an alert still requires investigation.
- Apply least privilege, record important activity, and test recovery arrangements.

## References

- [Google Cybersecurity Certificate playlist](https://www.youtube.com/playlist?list=PLTZYG7bZ1u6ocTMdhDwwmfjaNv134KcWn)
- [Google course curriculum](https://grow.google/intl/en_in/cybersecurity-course)
