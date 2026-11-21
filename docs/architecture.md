# Architecture and Threat Model

## 1. Lab architecture

The assessment uses a deliberately vulnerable OWASP Juice Shop instance running in a Docker container on the project team's computer.

```text
[Tester / Web Browser]
          |
          | HTTP to localhost:3000
          v
[OWASP Juice Shop]
[Local Docker Container]
          ^
          |
[OWASP ZAP Proxy - optional]
(inspects only authorized localhost traffic)
```

The browser is used to interact with the application. When ZAP is used, the browser's traffic is routed through the local ZAP proxy so the team can inspect requests and responses. ZAP must be configured and used only for the local Juice Shop target.

## 2. Main components

- **Tester:** A group member conducting an assigned assessment.
- **Browser:** Sends requests to and displays responses from Juice Shop.
- **OWASP Juice Shop:** The intentionally vulnerable training application under assessment.
- **Docker:** Runs the application locally and isolates it as a containerized lab service.
- **OWASP ZAP:** Optional intercepting proxy for reviewing in-scope HTTP requests and responses.
- **GitHub repository:** Stores project documentation, findings, remediation examples and sanitized evidence.

## 3. Assets to protect

- Test-account credentials and account sessions.
- Application data created during the assessment.
- The host computer and other services running on it.
- Project evidence and repository contents.
- The boundary between the local lab and external systems.

## 4. Threat assumptions

The assessment considers an attacker who may submit crafted input to application features, attempt to access another test account's data, or submit script-like content to fields that display user input. These are test scenarios, not claims that each weakness has been confirmed.

## 5. Assessment focus

| Area | Security question |
|---|---|
| Injection / SQL injection | Is user input treated as data, or can it alter an application's database operation? |
| Access control | Can one test account access information or actions that should belong only to another account or role? |
| Cross-site scripting (XSS) | Can submitted content execute as script when the application displays it? |

## 6. Trust boundaries and safety controls

- Only `http://localhost:3000` is in scope.
- Use synthetic test accounts and non-personal data.
- Do not test external websites, university production systems, public IP addresses or unrelated local services.
- Do not commit passwords, cookies, authorization headers, session tokens or personal information.
- Stop testing if traffic is directed to an unexpected host.

## 7. Limitations

This diagram describes the group's local assessment setup, not the full internal production architecture of Juice Shop. The group should update it if the actual deployment or tooling changes.
