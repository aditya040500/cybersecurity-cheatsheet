# Security Fundamentals

## Purpose of cybersecurity

Cybersecurity protects systems, networks, people, and information from unauthorized access, disruption, alteration, or destruction. A security decision should preserve business services while reducing the likelihood or impact of harm.

### Why it matters

An organization depends on trustworthy information and available services. A compromised account, altered record, or unavailable system can affect customers, operations, safety, and legal obligations. Security decisions should connect a technical weakness to the information or service at stake, likely harm, and safeguards that reduce it.

## The CIA triad

| Property | Meaning | Example |
| --- | --- | --- |
| Confidentiality | Information is seen only by authorized parties. | Restrict payroll records to approved roles. |
| Integrity | Information remains accurate and changes are authorized. | Log and validate changes to a payment record. |
| Availability | Systems and information are usable when needed. | Maintain tested backups and redundant service capacity. |

Controls often support more than one property. Encryption can protect confidentiality, while hashes and signed records can help detect unauthorized changes. Backups support availability, but do not alone ensure a service can be restored quickly.

```text
Asset -> threat event -> vulnerability or exposure -> impact
                         ^                         |
                         |--- controls reduce -----|
Risk is assessed from likelihood and impact in context.
```

This is a simplified reasoning aid: controls can affect likelihood and impact, and real assessments consider dependencies and uncertainty.

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

Use least privilege: grant only the access needed for a defined task and review it when roles change. Common authentication factor classes are something known (such as a password), something possessed (such as a security key), and something inherent (such as a biometric). MFA combines different factor classes; two passwords are still one factor type. Authentication does not automatically grant permission to every resource.

### Access control in practice

Access control decisions use an identity, a resource, and a policy. Role-based access control assigns permissions through job or service roles; attribute-based approaches can consider properties such as department, device state, or location. A file ACL, application role, or cloud policy can implement authorization. Review both direct grants and inherited group access.

| Check | Example |
| --- | --- |
| Identity | Is this the employee's individual account, not a shared account? |
| Authentication | Was the sign-in verified with appropriate factors? |
| Authorization | Does the role allow viewing this record, or only updating it? |
| Accountability | Can the action be associated with a user and time in an audit record? |

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

## Revision exercises

1. A ransomware event encrypts shared files and delays a service. Identify the CIA properties affected and name one control relevant to each.
2. Explain why MFA and authorization solve different problems.
3. A SIEM reports failed logins followed by a success. List three sources of context to review before declaring an incident.
4. Draw the path from an asset through a threat and weakness to business impact. Show where controls can reduce likelihood or impact.

## References

- [Google Cybersecurity Certificate playlist](https://www.youtube.com/playlist?list=PLTZYG7bZ1u6ocTMdhDwwmfjaNv134KcWn)
- [Google course curriculum](https://grow.google/intl/en_in/cybersecurity-course)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
