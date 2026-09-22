# Vortex Tech Cyber Security — Week 3 Intermediate

## Basic Security Audit of OWASP Juice Shop

This repository contains my Week 3 security audit of the intentionally vulnerable **OWASP Juice Shop** application running locally through Docker.

### Scope

- **Target:** OWASP Juice Shop
- **URL:** `http://localhost:3000`
- **Testing environment:** Local Docker container
- **Tool:** OWASP ZAP 2.17.0
- **Assessment type:** Beginner/intermediate web security audit
- **Authorization:** Practice target designed for security testing

## What was completed

The audit used OWASP ZAP against the local Juice Shop instance and produced four alert types:

| Finding / Alert | Risk | Category used in audit |
|---|---|---|
| Content Security Policy (CSP) Header Not Set | Medium | Security Misconfiguration |
| Cross-Domain Misconfiguration | Medium | CORS / Access-Control Misconfiguration |
| Timestamp Disclosure - Unix | Low | Information Disclosure |
| Modern Web Application | Informational | Informational — not counted as a vulnerability |

Together, the CSP, CORS, and Information Disclosure findings cover three distinct OWASP Top 10 vulnerability categories, as required by the task.

## Repository structure

```text
vortextech-cybersec-week3/
├── README.md
├── .gitignore
├── docker-compose.yml
├── report/
│   ├── security-audit.md
│   └── VortexTech_Week3_Security_Audit_Professional.pdf
├── evidence/
│   ├── zap-report.html
│   ├── zap-report.pdf
│   └── README.md
└── screenshots/
    ├── 01-juice-shop-running.png
    ├── 02-docker-container.png
    ├── 03-zap-scan.png
    └── 04-timestamp-finding.png
```

## Run OWASP Juice Shop

### Option 1 — Docker command

```bash
docker pull bkimminich/juice-shop
docker run -d --name juice-shop -p 3000:3000 bkimminich/juice-shop
```

Open:

```text
http://localhost:3000
```

### Option 2 — Docker Compose

```bash
docker compose up -d
```

To stop the container:

```bash
docker compose down
```

## Reproduce the ZAP scan

1. Start Juice Shop on `http://localhost:3000`.
2. Open OWASP ZAP.
3. Start an Automated Scan against the local target.
4. Use `http://localhost:3000` as the target.
5. Review the Alerts tab.
6. Export the report (Report → Generate Report) as HTML and/or PDF.
7. Place the exported report(s) in `evidence/`.

**Important:** Only use this workflow against the local practice target or another system for which you have explicit authorization.

## Findings documented

The detailed audit is in [`report/security-audit.md`](report/security-audit.md). Each finding includes:

- Clear title
- Discovery steps
- Vulnerability category / OWASP mapping
- Evidence from ZAP
- Real-world impact
- One practical remediation recommendation
- Risk level reported by ZAP

## Evidence

The original ZAP scan output is stored in `evidence/zap-report.html` (native export) and `evidence/zap-report.pdf`.

The ZAP report was generated on **21 September 2026 at 19:07:33** using **ZAP 2.17.0** and targeted `http://localhost:3000`.

## Disclaimer

This project is an educational security assessment of OWASP Juice Shop, a deliberately vulnerable practice application. No real production website was intentionally tested.
