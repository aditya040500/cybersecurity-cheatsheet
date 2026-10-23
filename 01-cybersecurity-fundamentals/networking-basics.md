# Networking Basics for Security

This is an introductory security reference, not CCNA course notes. It covers only the network concepts needed to reason about basic service exposure and communication.

## How a connection is described

```text
Application (for example, HTTP)
        | data
Transport (TCP or UDP; ports identify application endpoints)
        | segment/datagram
Internet (IP address and routing)
        | packet
Link (local Ethernet/Wi-Fi delivery; MAC address)
```

The layers are a useful model; real protocol stacks do not map perfectly to every simplified diagram. An IP address identifies a network-layer endpoint, while a MAC address is used for delivery on a local link. A router forwards IP packets between networks. DNS resolves names to records such as IP addresses; DNS itself does not prove that a destination is trustworthy.

## Ports and protocols

A transport port helps distinguish services at an endpoint. TCP provides an ordered byte stream with connection setup and retransmission behavior. UDP sends independent datagrams without TCP's connection and delivery guarantees. Application protocols define the meaning of data carried over a transport.

| Example service | Common registered port | Typical transport | Security use |
| --- | ---: | --- | --- |
| DNS | 53 | UDP and TCP, depending on use | Name resolution; restrict and monitor resolvers appropriately. |
| SSH | 22 | TCP | Remote administration; restrict access and use strong authentication. |
| HTTP | 80 | TCP | Web traffic; plaintext HTTP is not confidential by itself. |
| HTTPS | 443 | TCP | HTTP protected with TLS in common deployments. |

Port numbers are conventions and registrations, not proof of the application actually running. Services can use non-standard ports, and a registered port does not imply safe traffic. Check observed service behavior and policy, not only the number. See the [IANA registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).

## Practical example

A web server can be running locally and listening on TCP port 443, yet still be unreachable from a particular client because of routing or firewall policy. Conversely, an open port does not prove that the service is vulnerable. For an authorized local check, `ss -lnt` inspects listening TCP sockets; `ip address show` and `ip route show` inspect local interface and route state.

## Common mistakes

- Treating a port number as a vulnerability or proof of a service identity.
- Equating "listening locally" with "reachable from the internet."
- Treating a failed ping as proof that a host or application is down; ICMP may be filtered.
- Assuming DNS resolution authenticates a site or validates the returned address.
- Confusing MAC addresses, IP addresses, hostnames, and ports.

## Defensive applications

- Inventory expected listeners and compare them with approved service requirements.
- Restrict inbound traffic to necessary sources and ports.
- Use encrypted application protocols for sensitive data in transit and validate certificates.
- Correlate DNS, network, endpoint, and identity logs with synchronized timestamps.
- Test connectivity only within an authorized scope.

## Revision exercises

1. Trace a browser request from hostname resolution through IP routing to a TCP service port.
2. Explain why a listener on port 443 may still be unreachable from another subnet.
3. Give two reasons an open port is not enough to conclude that a host is vulnerable.
4. Compare TCP and UDP at a high level and name one reason DNS may use either.

## References

- [Google Cybersecurity Certificate curriculum: Networks and Network Security](https://grow.google/intl/en_in/cybersecurity-course)
- [IANA Service Name and Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
- [RFC 9293: Transmission Control Protocol](https://www.rfc-editor.org/rfc/rfc9293)
- [RFC 768: User Datagram Protocol](https://www.rfc-editor.org/rfc/rfc768)
