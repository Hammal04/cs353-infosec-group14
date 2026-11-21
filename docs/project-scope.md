# Project Scope Statement

## Project
**Course:** CS 353 – Information Security (Fall 2026)  
**Group:** 14  
**Project title:** Web Application Security Assessment using OWASP Juice Shop  
**Team members:** Hammal, Seema, Ayesha Ahmer

## Purpose
The project assesses selected web application security weaknesses in an intentionally vulnerable OWASP Juice Shop instance running in an authorized local laboratory. The team will explain the security impact of any weakness that is actually verified, preserve safe evidence, and document suitable remediation or secure-coding guidance.

The aim is to understand vulnerabilities and defensive practices, not merely to collect challenge flags.

## Authorized target and environment
- **Application:** OWASP Juice Shop
- **Access URL:** http://localhost:3000
- **Deployment:** Docker container running on the team's local computer
- **Test data:** Synthetic accounts and other non-real test data only
- **Assessment access:** Local instance controlled by the project team

## In-scope activities
1. Confirm the local application is available and document the deployment.
2. Review the application's relevant attack surface.
3. Investigate selected input-handling/injection behaviour, including SQL injection where supported by the application.
4. Assess selected cross-site scripting (XSS) behaviour.
5. Perform a limited access-control check using test accounts.
6. Record reproducible steps, screenshots or other safe evidence, observed impact, and a reasoned severity assessment.
7. Recommend or demonstrate appropriate remediation for selected, verified findings, and retest where feasible.

A test area is not automatically a finding. The report will distinguish confirmed vulnerabilities, unsuccessful tests, and areas that could not be assessed.

## Out of scope and safety boundaries
- Public websites, public IP addresses, and systems belonging to other people or organizations.
- University/campus production systems and networks.
- Real user accounts, real credentials, personal information, or non-synthetic data.
- Other Docker containers and projects running on the computer, including unrelated Hyperledger Fabric services.
- Denial-of-service, destructive testing, persistence, malware, or actions that could affect systems outside the local Juice Shop instance.

All security testing must remain within the authorized local lab and use test data only.

## Assumptions and limitations
- The assessment is limited to the locally deployed Juice Shop instance and the tests selected by the group.
- Results may depend on the application version and local configuration; record these details during testing.
- A vulnerability will be reported only when the team can reproduce and explain the behaviour.
- Findings that cannot be safely or reliably validated will be documented as unverified or not assessed, rather than presented as confirmed.

## Expected outputs
- Local deployment and this scope statement.
- Assessment plan and selected vulnerability findings.
- At least three vulnerability demonstrations where supported by the lab.
- Evidence, impact explanation, and severity rationale.
- Remediation demonstration or secure-code example for selected findings.
- Technical report, presentation, and a 5–8 minute demonstration video.

## Approval and change control
Any change to the target, environment, test data, or testing activities must be reviewed by the group and confirmed as authorized before testing begins.
