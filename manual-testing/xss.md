# Cross-Site Scripting (XSS)  
### Web Application Security Audit – DEFENSIFY

---

## 1. Vulnerability Overview

Cross-Site Scripting (XSS) occurs when an application reflects or stores user-supplied input without proper sanitization or encoding, allowing execution of malicious scripts in a victim’s browser.

XSS can be leveraged to hijack user sessions, perform unauthorized actions, or deliver malicious payloads to end users.

---

## 2. Affected Functionality

The following functionality was observed to reflect user-controlled input:

- Search functionality
- URL parameters within dynamically generated pages

These inputs were identified during reconnaissance and later validated through manual testing.

---

## 3. Testing Methodology

Manual testing was performed using safe, non-destructive payloads to confirm whether user input was reflected and executed within the browser context.

The following techniques were used:
- Reflected input testing
- Context analysis (HTML / response body)
- Client-side execution confirmation

---

## 4. Proof of Concept (PoC)

### 4.1 Reflected XSS

A basic script payload was injected into a user-controlled input field:

--- html
<script>alert(1)</script>


Observed Behavior:

The injected script was reflected in the HTTP response

The browser executed the script successfully

No input sanitization or output encoding was applied

This confirms the presence of a reflected XSS vulnerability.


5. Impact Analysis
Technical Impact

Execution of arbitrary JavaScript in the user’s browser

Potential session hijacking

Ability to manipulate client-side application behavior

Business Impact

Risk of account compromise

Exposure to phishing or malware delivery

Loss of user trust

Brand and reputational damage

6. Severity Rating

Severity: Medium

Rationale:

Exploitable via crafted input

Requires user interaction

Does not directly compromise server-side systems

Impact primarily affects end users

7. Remediation Recommendations

To mitigate XSS vulnerabilities, the following measures are recommended:

Implement proper output encoding based on context (HTML, JavaScript, attributes)

Apply strict server-side input validation

Use modern security headers such as Content Security Policy (CSP)

Avoid reflecting raw user input in responses

Perform regular security testing during development

8. Validation Notes

Only benign test payloads were used

No user data was accessed or modified

Screenshots and evidence were sanitized prior to documentation

9. Conclusion

The identified XSS vulnerability demonstrates insufficient handling of user input and output encoding.
While not as severe as server-side injection flaws, XSS poses a meaningful risk to users and should be addressed to maintain application trust and integrity.
