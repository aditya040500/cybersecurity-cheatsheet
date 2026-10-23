# Networking Commands

Use read-only network commands first. Results depend on permissions, installed tools, host configuration, DNS, and network policy.

| Command | What it inspects | Example and notes |
| --- | --- | --- |
| `ip address show` | Local interfaces and assigned addresses. | `ip address show` |
| `ip route show` | Local routing table. | `ip route show` |
| `ss -tulpen` | Listening and established sockets; options select TCP/UDP, listening sockets, numeric endpoints, processes, and extended details. | `ss -tulpen`; process details may require elevated access. |
| `ping -c 4 HOST` | Attempts four ICMP echo requests. | `ping -c 4 example.com`; filtering or policy may prevent replies. |
| `getent hosts HOST` | Queries configured name-service sources for host records. | `getent hosts example.com` |
| `curl -I URL` | Requests response headers from a URL. | `curl -I https://example.com`; contacts the remote host and may be logged. |
| `traceroute HOST` | Attempts to show network hops to a host. | `traceroute example.com`; availability and results depend on the path and installed package. |

## Troubleshooting sequence

1. Inspect interface state and address configuration with `ip address show`.
2. Inspect the route table with `ip route show`.
3. Check name resolution with `getent hosts HOST`.
4. Test reachability only when appropriate; a missing ping reply does not prove a host is offline.
5. Inspect local listening sockets with `ss` and compare them with expected services.

## Common mistakes and precautions

- Treating ICMP failure as proof that an application is unreachable.
- Running active probes against systems without authorization.
- Assuming a local listening socket is exposed externally; firewalls and routing affect reachability.
- Sharing outputs that contain internal addresses, usernames, or process details without review.
- Using `curl` or other clients to send requests to systems outside the approved scope.

## Revision points

- Establish local interface, route, and DNS state before concluding where a failure occurs.
- Distinguish local listening state from remote reachability.
- Stay within authorized systems and record the exact host and time when troubleshooting.

## References

- [NetworkChuck Linux for Hackers playlist](https://www.youtube.com/playlist?list=PLIhvC56v63IJIujb5cyE13oLuyORZpdkL)
- [ip manual](https://man7.org/linux/man-pages/man8/ip.8.html)
- [ss manual](https://man7.org/linux/man-pages/man8/ss.8.html)
- [curl manual](https://curl.se/docs/manpage.html)
