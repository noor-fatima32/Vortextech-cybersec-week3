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

The audit used OWASP ZAP against the local Juice Shop instance and produced five alert types:

| Finding / Alert | Risk | Category used in audit |
|---|---|---|
| CSP: Failure to Define Directive with No Fallback | Medium | Security Misconfiguration |
| Content Security Policy (CSP) Header Not Set | Medium | Security Misconfiguration |
| Cross-Domain Misconfiguration | Medium | CORS / Access-Control Misconfiguration |
| Timestamp Disclosure - Unix | Low | Information Disclosure |
| Modern Web Application | Informational | Informational — not counted as a vulnerability |

The two CSP alerts are related to the same security-control area and are documented as separate findings under **Security Misconfiguration**. Together with the **CORS / Access-Control Misconfiguration** and **Information Disclosure** findings, the audit covers three different vulnerability categories as required.

## Repository structure

```text
vortextech-cybersec-week3/
├── README.md
├── .gitignore
├── docker-compose.yml
├── report/
│   └── security-audit.md
├── evidence/
│   ├── zap-report.html
│   └── README.md
└── screenshots/
    └── README.md
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
3. Start a scan against the local target.
4. Use `http://localhost:3000` as the target.
5. Review the Alerts tab.
6. Export the HTML report.
7. Place the exported report in `evidence/zap-report.html`.

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

The original ZAP HTML output is stored in `evidence/zap-report.html`.

The uploaded ZAP report was generated on **14 September 2026 at 08:23:51** using **ZAP 2.17.0** and targeted `http://localhost:3000`.

## Disclaimer

This project is an educational security assessment of OWASP Juice Shop, a deliberately vulnerable practice application. No real production website was intentionally tested.
