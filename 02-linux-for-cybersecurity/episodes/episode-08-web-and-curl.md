# Episode 8: A Local Web Server and `curl`

**Video:** [2 cool (web) things to do in Linux // EP 8](https://www.youtube.com/watch?v=HSRghjwTTOQ)
**Source evidence:** The public description says the episode demonstrates managing web services with `curl`. Chapter markers cover starting a one-command website, changing directories and ports, making requests from the command line, and inspecting request headers.
**Practice level:** Bind the test server to loopback and keep requests local.

## Learning objectives

- Start a temporary HTTP server for local learning.
- Understand that a server listens on an address and port.
- Use `curl` to make an HTTP request and inspect response or request metadata.

## Commands

| Syntax | Purpose and arguments | Impact |
| --- | --- | --- |
| `python3 -m http.server PORT --bind 127.0.0.1 --directory DIR` | Serve files from `DIR` on a local test port. | Starts a network listener, restricted here to loopback |
| `curl URL` | Send an HTTP request and print the response body. | Contacts the target; responses may be logged |
| `curl -I URL` | Request headers only where supported by the server. | Network request |
| `curl -v URL` | Show connection and protocol details, including request/response headers. | May expose sensitive headers; use only on lab traffic |

## Safe practice in a Kali VM

Terminal 1:

```bash
mkdir -p "$HOME/web-lab"
printf '%s\n' 'Local practice page' > "$HOME/web-lab/index.html"
python3 -m http.server 8000 --bind 127.0.0.1 --directory "$HOME/web-lab"
```

Terminal 2:

```bash
curl -i http://127.0.0.1:8000/
```

Expected behavior: the second terminal displays an HTTP status line, response headers, and the page body; the server logs a request in the first terminal. This is a documented expected behavior of the commands, not a captured test result. Stop the server with Ctrl+C when finished.

## Common mistakes

- Binding to all interfaces when only local testing is needed.
- Treating a port number as proof of which application is listening.
- Confusing request headers sent by a client with response headers returned by a server.
- Following redirects, submitting data, or using verbose output without considering sensitive content.

## Security application

Use `curl` to inspect HTTP behavior in an authorized local lab, verify expected headers, and troubleshoot a service. Keep test services bound to loopback unless an isolated network lab explicitly requires other hosts to connect.

## Revision questions

1. What is the difference between `127.0.0.1` and a wildcard bind address?
2. Which option asks for response headers only? Which provides verbose protocol details?
3. What does a listening port tell you, and what does it not tell you?
4. How do you stop the temporary Python server?

## References

- [Episode 8 video and chapters](https://www.youtube.com/watch?v=HSRghjwTTOQ)
- [Python `http.server` documentation](https://docs.python.org/3/library/http.server.html)
- [curl manual](https://curl.se/docs/manpage.html)
