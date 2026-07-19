# FUTURE_CS_03 — API Security Risk Analysis

**Future Interns — Cyber Security Internship (Task 3)**
Candidate: Yousef Ahmed Fawzy
CIN ID: FIT/JUN26/CS9482
Internship Period: 29 June 2026 – 29 July 2026

---

## 📌 Overview

This project performs a read-only API Security Risk Analysis on a public test API, simulating the work of
an AppSec consultant conducting a SaaS API security audit. The goal is to identify common API vulnerabilities,
assess business impact, and provide remediation guidance — without exploitation or system abuse.

This is a **security analysis and documentation task** — no exploitation, bypass attempts, or DoS testing were performed.

---

## 🎯 Objective

- Analyze a public/test API's endpoints, authentication, and data handling
- Identify common API security risks (per OWASP API Security Top 10 categories)
- Assess authentication and access control implementation
- Explain risks in simple, business-friendly language
- Suggest clear, actionable remediation steps

---

## ⚖️ Scope & Ethics

**Allowed and performed:**
- Testing a public, no-signup demo API
- Read-only requests (GET) and safe authenticated POST requests (login)
- Header, token, and response inspection

**Not performed:**
- Exploitation or bypass attempts
- Flooding / DoS testing
- Attacks against private or production systems

---

## 🛠️ Tools & API Used

- **API tested:** [DummyJSON](https://dummyjson.com) — a free, public, no-signup REST API for testing
- **Testing tool:** Postman (request building, header inspection, response analysis)
- **Reference material (study only):** OWASP API Security Top 10, API Security Checklist (shieldfy)

**Note on API substitution:** The task originally suggested ReqRes as a second test target. At the time of
testing, ReqRes had transitioned to a paid platform requiring account signup and an API key for all
endpoints, which no longer matched the "public demo API" requirement. DummyJSON was used instead — a
free, public API covering the same authentication-testing use case, plus additional resources that allowed
full coverage of all 6 required risk categories within a single, consistent API.

---

## 🔍 Methodology

1. **Select API** — chose a public, no-signup test API suitable for security education
2. **Review Documentation** — studied available endpoints, authentication model, and resources
3. **Test Endpoints** — sent real GET/POST requests using Postman
4. **Inspect** — examined authentication requirements, response headers, and returned data
5. **Identify Risks** — evaluated results against 6 standard API risk categories
6. **Classify Severity** — rated each finding Low / Medium / High based on impact and exploitability
7. **Document & Remediate** — compiled findings into a structured PDF report with fix recommendations

---

## 📁 Repository Structure

```
FUTURE_CS_03/
├── README.md
├── Evidence/
│   └── Screenshots/
│       ├── 01_posts_no_auth.png
│       ├── 02_users_data_exposure.png
│       ├── 03_login_success.png
│       ├── 04_auth_me_success.png
│       ├── 05_no_token_rejected.png
│       ├── 06_fake_token_rejected.png
│       ├── 07_idor_user2.png
│       └── 09_input_validation_ok.png
└── Report/
    └── FUTURE_CS_03_API_Security_Risk_Analysis_Report.pdf
```

---

## 📊 Summary of Findings

| # | Finding | Category | Risk Level |
|---|---|---|---|
| 1 | Open/unauthenticated endpoints | No authentication required | 🟡 Low-Medium |
| 2 | Excessive data exposure | Passwords, SSNs, bank cards leaked via `/users` | 🔴 Critical |
| 3 | Broken authorization (IDOR) | Any user's data accessible via `/users/{id}` | 🔴 High |
| 4 | Missing rate limiting | No throttling on rapid repeated requests | 🟠 Medium |
| 5 | Token validation | Auth enforcement works correctly | 🟢 Secure |
| 6 | Input validation | Injection-style input safely rejected | 🟢 Secure |

**Key takeaway:** This API's authentication layer is properly implemented — but that protection is bypassed
entirely by endpoints (`/users`, `/users/{id}`) that expose the exact sensitive data the auth system is meant
to protect, without requiring any authentication at all.

---

## 📄 Full Report

See [`Report/FUTURE_CS_03_API_Security_Risk_Analysis_Report.pdf`](./Report/FUTURE_CS_03_API_Security_Risk_Analysis_Report.pdf)
for the complete analysis, screenshots, severity classifications, business impact, and remediation plan.

---

## ⚖️ Ethics Note

All testing in this report was performed against a public API explicitly designated for learning and testing
purposes. All requests were read-only or used safe test credentials; no exploitation, flooding, or attacks
against private/production systems were performed at any point.
