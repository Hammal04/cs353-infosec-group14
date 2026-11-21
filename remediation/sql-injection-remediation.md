# SQL Injection Remediation: Secure Query Example

## Purpose
This document explains how parameterized database queries help prevent SQL injection. The example is educational and is not a patch to the OWASP Juice Shop source code.

## Why string concatenation is unsafe
A vulnerable application may build a database query by joining user input directly into an SQL string:

```javascript
// Illustrative insecure example — do not use
const sql =
  "SELECT * FROM Users WHERE email = '" +
  email +
  "' AND password = '" +
  password +
  "'";
```

When untrusted input is inserted into the SQL statement itself, that input may change the query's intended structure.

## Use parameterized queries
A safer pattern separates the SQL statement from the values supplied by the user:

```javascript
// Illustrative parameterized-query example
const sql = "SELECT id, email, password_hash FROM Users WHERE email = ?";
db.query(sql, [email], (error, rows) => {
  if (error) {
    // Handle the error safely; do not expose database details to the user.
    return;
  }

  // Verify the submitted password against the stored password hash
  // using an appropriate password-hashing library.
});
```

The placeholder is part of the SQL statement, while the email is supplied separately as a value. The database driver handles it as data rather than executable SQL.

## Additional authentication safeguards
- Store passwords using a dedicated password-hashing algorithm such as Argon2id or bcrypt; never store plaintext passwords.
- Verify the submitted password against the stored hash in application code.
- Use generic login error messages so the application does not reveal whether an email account exists.
- Give the application's database account only the permissions it needs.
- Keep database libraries and application dependencies updated.
- Add automated tests for invalid credentials and SQL-like input.

## Retest plan
After applying a fix in an application that the team owns or is authorized to modify:

1. Submit an ordinary incorrect email/password pair and confirm authentication is rejected.
2. Submit the same SQL-like test input used in the authorized local assessment.
3. Confirm that the input is handled as data and does not authenticate a user.
4. Confirm that valid test credentials still work.
5. Record screenshots or test output and document the result.

## Project limitation
The Group 14 test demonstrated an administrator authentication bypass in the local OWASP Juice Shop challenge. This example explains a remediation pattern; it does not claim that the Juice Shop source code has been modified or that the vulnerability has been fixed. A remediation should only be marked implemented after a real code change and successful retest.
