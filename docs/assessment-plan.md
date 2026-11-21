# Security Assessment Plan

## 1. Objective
Assess selected security behaviour in the Group 14 local OWASP Juice Shop laboratory. The assessment will use controlled test data, reproducible steps, and safe evidence. The team will explain the impact of verified weaknesses and document remediation or secure-coding guidance.

## 2. Target and authorization
- **Target:** The group's own OWASP Juice Shop instance.
- **Base URL:** http://localhost:3000
- **Deployment:** Docker on the project computer.
- **Authorization boundary:** Only this local Juice Shop instance is in scope.
- **Data:** Synthetic test accounts and non-personal test data.

Do not direct tools or tests at public websites, campus systems, other Docker containers, or any third-party target.

## 3. Team assessment areas
| Member | Assigned investigation | Expected contribution |
|---|---|---|
| Hammal | Local setup, scope and plan, injection/SQL injection investigation, repository integration | Deployment details, reproducible test notes, evidence, impact and remediation research |
| Seema | Basic access-control check using two test accounts | Test-account setup, permitted/denied access observations, evidence and conclusion |
| Ayesha Ahmer | XSS investigation and remediation | Reproducible XSS checks, evidence, impact, secure-coding example and retest |

These are investigation assignments, not assumptions that a vulnerability exists. Report only behaviour that is actually verified.

## 4. Tools
- OWASP Juice Shop running locally in Docker.
- Web browser and browser developer tools.
- OWASP ZAP or Burp Suite Community, if needed and configured to target only localhost.
- Git and GitHub for version control and evidence documentation.

## 5. Assessment workflow
1. **Confirm environment:** Check that the Juice Shop page loads at the local URL and that its Docker container is running.
2. **Record baseline:** Note the test date, application URL, deployment method, browser/tool versions where relevant, and any test-account details that are safe to share.
3. **Map the relevant feature:** Identify the Juice Shop page or function related to the assigned test area. Do not assume a vulnerability from the feature's presence.
4. **Plan a controlled test:** State the security question, test account/data, expected secure behaviour, and the exact local feature being checked.
5. **Perform the test:** Interact only with the local application. Avoid destructive actions and real personal data.
6. **Capture evidence:** Save screenshots and concise notes showing the steps and observed result. Remove or mask any credentials, tokens, or personal information.
7. **Evaluate:** Explain whether the result demonstrates a weakness, what an attacker could achieve in this lab scenario, and the likely security impact. Give a severity rationale based on demonstrated impact and prerequisites.
8. **Recommend remediation:** Describe a suitable defensive control or secure-code change. Do not claim a fix has been implemented unless it has been.
9. **Retest:** Repeat the relevant test after a remediation example or configuration change, where feasible, and record whether the behaviour changed.
10. **Document honestly:** Mark each test as confirmed, not reproduced, inconclusive, or not assessed. Do not report an unverified issue as a finding.

## 6. Hammal's injection / SQL injection investigation
For the injection investigation, use this sequence:

1. Identify a relevant Juice Shop feature that accepts user input and determine what the feature is expected to do.
2. Write down the input, expected normal behaviour, and the security property being checked.
3. Use only the local Juice Shop interface and controlled test inputs. Do not use the same test against any other site or service.
4. Observe the application's response and, where useful, review browser developer tools or the local application's visible behaviour.
5. Determine whether the observation actually demonstrates injection or another issue. An unusual error or unexpected response alone is not sufficient proof of SQL injection.
6. Capture the minimum evidence needed to reproduce the result safely.
7. Explain possible impact only to the extent supported by the evidence.
8. Research and document appropriate defensive practices, such as parameterized database queries and server-side input validation, as applicable to the verified issue.
9. If a remediation example is available, explain it and retest the same behaviour.

Record the exact feature and test steps in the finding notes. Do not invent a vulnerable endpoint, database error, or successful exploit.

## 7. Evidence record template
For every test, record:

- **Finding/test ID:**
- **Assigned member:**
- **Date and environment:**
- **Feature/page tested:**
- **Security question:**
- **Preconditions and test data:**
- **Steps performed:**
- **Expected secure behaviour:**
- **Actual observed behaviour:**
- **Evidence file(s):**
- **Result:** Confirmed / Not reproduced / Inconclusive / Not assessed
- **Impact and severity rationale:**
- **Recommended remediation:**
- **Retest result:**

## 8. Safety and data handling
- Keep the assessment within the local Docker-hosted Juice Shop instance.
- Use synthetic accounts and test data only.
- Do not commit passwords, session tokens, API keys, private keys, or personal information.
- Do not test public IP addresses, third-party services, campus production systems, or unrelated containers.
- Stop if an action appears likely to affect anything outside the authorized target.

## 9. Planned outputs
The team will aim to document at least three vulnerability demonstrations where supported by the lab, together with evidence, impact explanations, severity rationale, and remediation or secure-code examples for selected findings. The results will support the technical report, presentation, and 5–8 minute demonstration video.
