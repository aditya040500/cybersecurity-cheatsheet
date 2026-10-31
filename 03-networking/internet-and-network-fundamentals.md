# Internet and Network Fundamentals

These notes combine the NetworkChuck video titled “What is a Network? - Day 0” with Lecture 01 of CS-340 Intro to Computer Networking, taught by Steve Tarzia. CS-340 is the learner's primary networking source. Explanations here are original summaries, not transcripts.

## Source coverage

- NetworkChuck: [FREE CCNA - What is a Network? - Day 0](https://www.youtube.com/watch?v=S7MNX_UD7vY&list=PLIhvC56v63IJVXv0GJcl9vO5Z6znCVb1P&index=1)
- Primary course: [CS-340 Intro to Computer Networking - Lecture 01: Introduction (Steve Tarzia)](https://www.youtube.com/watch?v=EN0efud3M5U&list=PLWl7jvxH18r3nnotitKkyAjq268PQGc0-&index=1)
- The lecture description's outline includes Internet overview, network control and organization, Internet versus Web, distributed design, protocols, access networks, local-area networks, PSTN, DSL and cable access, wired and wireless media, circuit and packet switching, and performance measures. Its transcript was not available in the inspected page, so notes stay within those published chapter topics and standard technical definitions.

Useful lecture timestamps from the published outline: [Internet overview, 4:45](https://www.youtube.com/watch?v=EN0efud3M5U&t=285s), [Internet vs. Web, 21:48](https://www.youtube.com/watch?v=EN0efud3M5U&t=1308s), [access networks and LANs, 33:01](https://www.youtube.com/watch?v=EN0efud3M5U&t=1981s), [DSL and cable, 44:41](https://www.youtube.com/watch?v=EN0efud3M5U&t=2681s), [network core, 56:24](https://www.youtube.com/watch?v=EN0efud3M5U&t=3384s), [packet switching, 1:02:05](https://www.youtube.com/watch?v=EN0efud3M5U&t=3725s), and [performance measures, 1:06:24](https://www.youtube.com/watch?v=EN0efud3M5U&t=3984s).

## What is a network?

A **computer network** is a set of connected devices and links that exchange information according to shared rules called **protocols**. A network can be small, such as devices connected to one home router, or large and interconnected, like the global Internet.

The **Internet** is a global system of interconnected networks. It is not one computer, one cable, or one company. Different networks connect and exchange traffic using common protocols. The **World Wide Web** is one service that runs over the Internet; email and voice services are other examples.

### A simplified path

    Laptop or phone
         |
    Local network / Wi-Fi
         |
    Home or campus access router
         |
    Internet provider and other networks
         |
    Destination service

This is a conceptual path. Real traffic may cross many networks, and the route may change over time.

## Network edge, access, and core

- **Network edge:** end devices and services that create or receive traffic.
- **Access network:** the part that connects a user or organization to a provider network.
- **Local-area network (LAN):** a network serving a limited local area, such as a home, office, or campus building.
- **Network core:** interconnected provider and backbone networks that carry traffic between edge networks.
- **Internet service provider (ISP):** an organization that provides network connectivity and may connect its customers to other networks.

No single organization controls the entire Internet. Operators, standards bodies, network providers, and service owners each manage parts of it. The network is distributed, so communication can continue across alternate paths when some links fail, although availability depends on the actual topology and failures.

## Protocols

A **protocol** is an agreed set of rules for communication. Protocols define how participants format messages, what messages mean, and what actions happen next. The lecture uses human conversation as an analogy: people need shared expectations for taking turns and interpreting a message. Computer protocols provide precise rules that machines can follow.

The analogy helps explain why shared rules matter, but human conversation is not a technical network protocol. Real protocols are defined by specifications and implementations.

## Access networks and transmission media

Networks use **guided media**, where signals travel through a physical medium such as copper or fiber, and **unguided media**, where signals travel over radio. Wi-Fi is a common wireless access technology; Ethernet and fiber are common wired technologies.

The lecture reviews earlier telephone and cable infrastructure as examples of how Internet access has evolved:

- **PSTN:** the public switched telephone network, built primarily for voice calls.
- **DSL:** broadband access that carries digital data over telephone-line infrastructure.
- **Cable access:** broadband that uses cable television infrastructure, commonly including coaxial cable.
- **Frequency-division multiplexing (FDM):** dividing available spectrum into frequency bands so multiple signals can share a medium.

These are introductory examples from the lecture outline. Provider designs vary, and they do not describe every modern access network.

## Circuit switching and packet switching

| Idea | Circuit switching | Packet switching |
| --- | --- | --- |
| Basic approach | Establishes a path with reserved resources for a communication session | Breaks data into packets that share network links with other traffic |
| Resource use | Capacity can remain reserved for the session | Links are shared as packets are forwarded |
| Example context | Traditional telephone-network design | The Internet's general data transport model |

In **packet switching**, packets may encounter different delay or take different paths. A receiving protocol or application may need to handle missing, delayed, or reordered data. Packet switching uses shared links efficiently, but experienced performance can vary with congestion and the route.

The table is a high-level comparison. Real networks use additional mechanisms for service quality, reliability, and traffic engineering.

## Introductory network performance

- **Bandwidth / link capacity:** the maximum data rate a link can carry under a stated unit and context.
- **Throughput:** the data rate actually achieved by an application or flow.
- **Latency / delay:** the time required for data to travel between points; round-trip time includes the return path.
- **Jitter:** variation in packet delay over time.
- **Packet loss:** packets that do not reach the intended receiver.
- **Cumulative distribution function (CDF):** a way to summarize measurements by showing the fraction of observations at or below different values.

**Example:** A video call may have enough average throughput but still feel poor when delay varies sharply or packets are lost. One measurement does not fully describe performance; collect repeated observations and note where and when they were taken.

The lecture includes a network-performance experiment. These notes do not claim that the learner ran that experiment.

## Safe local observation

Use a host you own or are authorized to inspect. These commands only request diagnostic information; actual output depends on the operating system and network.

On Windows:

    ipconfig
    ping -n 4 <your-default-gateway>
    tracert <a-host-you-are-authorized-to-test>

On Linux:

    ip address
    ip route
    ping -c 4 <your-default-gateway>
    traceroute <a-host-you-are-authorized-to-test>

The angle-bracket values are placeholders; replace them with a local gateway or authorized destination. A failed ping does not prove that a host is offline because firewalls may block ICMP. A traceroute can also be incomplete when intermediate devices do not reply.

## Common misunderstandings

- The Internet and the Web are not synonyms.
- A network is not just a switch, router, or wireless signal; it includes connected devices, links, and protocols.
- “Distributed” does not mean every network path is always available.
- Link capacity and observed application throughput are different measures.
- A single latency measurement cannot describe changing network performance.

## Revision questions

1. How is the Internet different from the Web?
2. What is the role of an access network?
3. Why do networked devices need protocols?
4. Compare circuit switching with packet switching.
5. Distinguish bandwidth, throughput, latency, jitter, and packet loss.
6. What does a performance CDF help summarize?
7. Why can a failed ping be inconclusive?

## Key takeaways

- The Internet interconnects independently operated networks using shared protocols.
- A user's traffic travels from an edge device over an access network and through multiple networks to a destination.
- Packet switching shares links and can produce variable performance.
- Diagnose performance with repeated, contextual measurements rather than a single result.

## References

- [NetworkChuck - What is a Network? - Day 0](https://www.youtube.com/watch?v=S7MNX_UD7vY&list=PLIhvC56v63IJVXv0GJcl9vO5Z6znCVb1P&index=1)
- [CS-340 Intro to Computer Networking - Lecture 01: Introduction (Steve Tarzia)](https://www.youtube.com/watch?v=EN0efud3M5U&list=PLWl7jvxH18r3nnotitKkyAjq268PQGc0-&index=1)
- [Steve Tarzia - CS-340 course materials](https://stevetarzia.com/teaching/)
- [RFC 1122 - Requirements for Internet Hosts](https://www.rfc-editor.org/rfc/rfc1122.html)
