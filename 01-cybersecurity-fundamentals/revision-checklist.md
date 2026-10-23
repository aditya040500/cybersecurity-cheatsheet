# Final Revision Checklist

Use this page to explain a security scenario out loud, then check the supporting topic notes for detail.

## Core reasoning sequence

1. Name the asset and its owner.
2. State the security property at risk: confidentiality, integrity, availability, or more than one.
3. Separate the threat, vulnerability, exposure, and possible impact.
4. Describe likelihood and impact using the organization's method and assumptions.
5. Identify preventive, detective, and recovery controls; verify that they work.
6. Record the decision, owner, escalation path, and review point.

## Identity and network checks

- Authentication verifies the identity; authorization limits permitted actions; audit records support accountability.
- MFA combines different factor classes. Least privilege limits the damage a compromised account can cause.
- A port number is a transport endpoint convention, not proof of service identity or vulnerability.
- Listening locally does not mean reachable remotely. Consider address, route, firewall, and application behavior.
- An alert is a lead for investigation, not confirmation of an incident.

## Scenario prompt

A public web service stores customer data. An account signs in from an unusual location, and the host has an unneeded service listening. Explain what evidence you would gather, how you would scope the risk, what controls you would verify, who should make containment decisions, and how you would confirm recovery. Avoid assuming compromise from one signal alone.
