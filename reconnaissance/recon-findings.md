# Reconnaissance Findings  
### Web Application Security Audit – DEFENSIFY

---

## 1. Overview

The reconnaissance phase focused on identifying the exposed attack surface of the target web application without performing intrusive or destructive actions.  
This phase aimed to understand how the application is structured, what technologies are in use, and where potential input vectors exist.

Reconnaissance was conducted using a combination of passive observation, light active probing, and manual analysis.

---

## 2. Target Information

- **Target URL:** http://testphp.vulnweb.com
- **Application Type:** PHP-based web application
- **Exposure:** Publicly accessible
- **Authentication Required:** Partial (some functionality accessible without login)

---

## 3. Technology Stack Identification

Based on initial reconnaissance, the following technologies were identified:

|      Component      |      Observation      |
|---------------------|-----------------------|
| Web Server          | Apache                |
| Backend Language    | PHP                   |
| Database (inferred) | MySQL                 |
| Operating System    | Linux (inferred)      |
| Frontend            | HTML, CSS, JavaScript |

> Technology identification was performed using passive tools and response analysis.  
> Exact versions were not aggressively fingerprinted to avoid unnecessary exposure.

---

## 4. Application Mapping

Manual browsing of the application revealed the following functional areas:

- Home and landing pages
- User authentication (login / registration)
- Product listings and categories
- Product detail pages
- Search functionality
- Shopping cart workflow

Several application components were accessible without authentication, increasing the potential attack surface.

---

## 5. Identified Entry Points

The following user-controlled input vectors were identified during reconnaissance:

### 5.1 URL Parameters (GET)

Examples observed:
/listproducts.php?cat=1
/artists.php?artist=1
/product.php?pid=1


These parameters were noted as potential candidates for injection-based testing.

---

### 5.2 Form Inputs (POST)

- Login form
- Search input
- Registration form

Input validation behavior was inconsistent and warranted further manual testing.

---

### 5.3 Cookies & Session Handling

- Session cookies were observed during authentication workflows
- No secure or HTTPOnly flags were consistently enforced during initial observation
- Session identifiers appeared to be reused across requests

These behaviors were flagged for deeper analysis during the manual testing phase.

---

## 6. Error Handling & Application Responses

During normal interaction with the application:
- Verbose error messages were observed under certain conditions
- Input reflection was identified in some responses
- Application behavior suggested limited server-side input sanitization

These indicators suggested a higher likelihood of injection and scripting vulnerabilities.

---

## 7. Reconnaissance Observations & Initial Risk Indicators

Based on reconnaissance alone, the following risk indicators were identified:

- Multiple user-controlled input points
- Dynamic parameters tied to backend queries
- Partial authentication coverage
- Inconsistent session handling indicators
- Verbose application responses

These observations guided prioritization for automated scanning and manual exploitation attempts.

---

## 8. Reconnaissance Summary

The reconnaissance phase revealed a **broad and exposed attack surface** with multiple high-risk input vectors.  
Findings from this phase informed subsequent testing activities, allowing for targeted vulnerability assessment rather than blind scanning.

No exploitation was performed during reconnaissance.
