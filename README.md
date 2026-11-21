# CS 353 Information Security — Group 14

## Web Application Security Assessment using OWASP Juice Shop

This repository contains the coursework for **CS 353 – Information Security (Fall 2026)**. The group assesses selected security weaknesses in its own locally deployed OWASP Juice Shop instance, records reproducible evidence, explains security impact, and documents appropriate remediation.

> **Authorization boundary:** Testing is limited to the group's local Juice Shop instance at `http://localhost:3000`, using synthetic test data. Do not test public websites, university production systems, third-party services, or unrelated containers.

## Team

| Member | Responsibility |
|---|---|
| Hammal Baloch | Local setup, project scope and assessment plan, injection/SQL injection investigation, repository integration |
| Seema | Basic access-control check using two test accounts |
| Ayesha Ahmer | XSS investigation, remediation guidance and retest |

These are investigation assignments. A vulnerability is reported as confirmed only when the observed behaviour is reproducible and supported by evidence.

## Objectives

- Deploy and assess OWASP Juice Shop in an authorized local lab.
- Investigate selected injection, access-control and XSS behaviours.
- Record test steps, observed results, evidence, impact and severity rationale.
- Explain suitable remediation and retest where feasible.
- Produce the technical report, presentation and demonstration video required by the course.

## Tools

- OWASP Juice Shop
- Docker / Docker Desktop
- Web browser and developer tools
- OWASP ZAP (manual proxy/request inspection; automated scanning only when deliberately scoped to localhost)
- Git and GitHub

## Local setup

### Prerequisites

- Docker Desktop installed and running.
- A web browser.
- OWASP ZAP, if using the proxy-based assessment workflow.

### Run Juice Shop

Open PowerShell or a terminal and run:

```bash
docker run --rm -d --name juice-shop -p 3000:3000 bkimminich/juice-shop
```

Open:

```text
http://localhost:3000
```

To check the container:

```bash
docker ps
```

To stop the lab when finished:

```bash
docker stop juice-shop
```

If port 3000 is already in use, stop and identify the conflicting local service before choosing another port. Keep all assessment traffic directed only to the local Juice Shop instance.

## Repository structure

```text
.
├── README.md
├── LICENSE
├── .gitignore
├── docs/
│   ├── project-scope.md
│   ├── assessment-plan.md
│   └── architecture.md
├── findings/
│   └── F-01-sql-injection-authentication-bypass.md
├── remediation/
│   └── sql-injection-remediation.md
└── evidence/
    └── README.md
```

## Current assessment record

- **F-01 — SQL Injection Authentication Bypass:** documented as demonstrated in the local Juice Shop lab. The finding record describes the test input, observed administrator authentication, impact, provisional severity and remediation guidance.
- The remediation document is an educational secure-query example; it is **not** a claim that the Juice Shop source code has been patched.
- Access-control and XSS investigations must be recorded separately by the assigned members. Do not describe them as confirmed until their tests support that conclusion.

See:
- [Project scope](docs/project-scope.md)
- [Assessment plan](docs/assessment-plan.md)
- [Architecture and threat model](docs/architecture.md)
- [F-01 finding](findings/F-01-sql-injection-authentication-bypass.md)
- [SQL injection remediation example](remediation/sql-injection-remediation.md)
- [Evidence instructions](evidence/README.md)

## Evidence and reporting

For each test, record the date, local target, feature tested, test account/data (without passwords or tokens), steps, expected behaviour, actual observation, result, impact, severity rationale and remediation. Store screenshots in the relevant evidence folder. **Redact passwords, session tokens, cookies, personal data and other secrets before committing evidence.**

The final course submission should include the required technical report (PDF, maximum 12 pages), presentation (at least 15 slides and 20 minutes), and 5–8 minute demonstration video. The group should also tag the final repository submission as `v1.0` after the required content has been completed and reviewed.

## Safe testing rules

- Use only the group's own local Juice Shop instance and synthetic data.
- Do not target public websites, public IPs, campus production systems, third-party services or unrelated containers.
- Do not perform denial-of-service, destructive testing, persistence or actions outside the approved scope.
- Do not commit credentials, authentication tokens, API keys, private keys or personal information.
- Report inconclusive or unsuccessful tests honestly; an unusual response alone does not prove a vulnerability.

## License

This project is provided under the MIT License. See [LICENSE](LICENSE).
