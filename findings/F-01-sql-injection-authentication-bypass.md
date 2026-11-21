# Finding F-01: SQL Injection Authentication Bypass

## Status
**Confirmed in the local OWASP Juice Shop lab.**

## Summary
A SQL injection input submitted through the login email field caused the application to authenticate the tester as the administrator without valid administrator credentials.

## Scope and environment
- **Application:** OWASP Juice Shop
- **Target:** `http://localhost:3000`
- **Deployment:** Local Docker container
- **Test data:** No real user credentials were used
- **Authorization:** The group's own isolated local lab

## Reproduction record
1. Open the Juice Shop login page on the local target.
2. Submit the following controlled test input in the email field: `' OR 1=1--`
3. Use a dummy value in the password field.
4. Submit the login form.
5. Observe that the application redirects to the product dashboard.
6. Observe the success banner: **"You successfully solved a challenge: Login Admin (Log in with the administrator's user account.)"**

## Evidence
- **Evidence E-01:** Screenshot of the successful challenge banner on the local Juice Shop dashboard, captured during the test.
- **Evidence E-02:** Screenshot showing the submitted input and login form response, if retained separately.

The success banner explicitly identifies the administrator-login challenge as solved. This is stronger evidence than a dashboard redirect alone.

## Expected secure behaviour
The application should treat user-supplied email and password values as data, not as part of a database query's executable SQL. Invalid credentials should be rejected, and no unauthenticated user should gain an administrator session.

## Observed behaviour
The crafted email input resulted in administrator authentication, as confirmed by the Juice Shop challenge-success banner.

## Impact
An attacker able to exploit the same behaviour could bypass normal authentication and gain administrator-level access. Depending on the application's administrative functions, this could expose or allow modification of sensitive application data and operations.

## Severity rationale
**High (provisional).** The demonstrated outcome is authentication bypass to an administrator account. The final severity should be aligned with the course rubric and any formal scoring method required by the instructor.

## Recommended remediation
- Use parameterized queries / prepared statements for all database operations involving user input.
- Never concatenate untrusted input into SQL statements.
- Apply server-side input validation as a supplementary control; validation is not a substitute for parameterization.
- Use least-privilege database accounts and avoid exposing detailed database errors to users.
- Add regression tests confirming that malformed or SQL-like login inputs cannot authenticate a user.

## Retest
Not yet performed. A remediation must be implemented in an appropriate code example or controlled test version, then the same test should be repeated to verify that authentication is rejected.

## Limitations
This finding documents the behaviour demonstrated by the local Juice Shop challenge. It does not establish that any external website or production system is vulnerable. Testing was limited to the authorized local lab.
