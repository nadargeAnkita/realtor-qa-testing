# Realtor.com — Manual QA Testing Project

**Type:** Independent Manual QA Portfolio Project
**Application Under Test:** [realtor.com](https://www.realtor.com) (public production site)
**Role:** Manual QA Tester / Test Case Design / Defect Reporting

## Overview

This project demonstrates end-to-end manual black-box QA testing performed against realtor.com's public-facing website. It covers **50 manual test cases across 11 modules**, applying formal black-box testing techniques to uncover functional, UI, negative, boundary, and security defects — with a particular focus on input validation gaps in the **mortgage calculator**.

This is an independent QA practice project built to demonstrate manual testing skills for a QA Engineer / SDET role. It is not affiliated with, endorsed by, or performed on behalf of Realtor.com / Move, Inc. All testing was exploratory/educational, read-only, and limited to publicly available pages (no automated scraping, load testing, or account abuse).

## What's in this repo

```
realtor-qa-project/
├── README.md                              ← you are here
├── test-plan/
│   └── Test_Plan.md                       ← scope, approach, techniques, environment
├── test-cases/
│   └── Realtor_Test_Cases.xlsx            ← 50 test cases + summary dashboard
├── defect-reports/
│   └── Realtor_Defect_Log.xlsx            ← 9 logged defects, mapped to test cases
└── screenshots/                            ← (optional) evidence captures
```

## Modules Covered (11)

| # | Module | Test Cases |
|---|--------|------------|
| 1 | Search Filters (price, beds/baths, home type) | 6 |
| 2 | Property Details Page | 5 |
| 3 | Mortgage Calculator | 6 |
| 4 | Sign-in / Registration | 6 |
| 5 | Map View | 5 |
| 6 | Agent Finder | 5 |
| 7 | Saved Homes / Favorites | 4 |
| 8 | Photo Gallery / Media | 4 |
| 9 | Contact Agent Form | 4 |
| 10 | Site Navigation (header/footer) | 3 |
| 11 | Notifications / Email Alerts | 2 |

**Total: 50 test cases**

## Testing Techniques Applied

- **Equivalence Partitioning** — grouping valid/invalid input classes (e.g., price ranges, ZIP codes, password lengths)
- **Boundary Value Analysis** — testing edges such as $0 price, 0% interest rate, min/max password length, 50+ saved listings
- **Error Guessing** — probing likely failure points based on tester experience (e.g., down payment exceeding home price)
- **Negative Testing** — invalid inputs, malformed data, non-existent IDs, empty required fields
- **Security (Black-Box) Checks** — XSS payloads in search/message fields, SQL-injection-style login attempts, brute-force login handling

## Key Results

- **50** test cases executed → **39 Passed / 11 Failed**
- **9** defects logged and tracked to closure status
- **Highest-impact finding:** the mortgage calculator does not validate numeric input — it accepts negative home prices, non-numeric text, and a down payment greater than the home price, silently producing incorrect or negative monthly payment figures (see `DEF-001` in the defect log)
- Additional defects found in filter validation, password policy enforcement, login brute-force protection, and empty-state handling on Map View / Agent Finder

## Test Case & Defect Tracking Structure

**Test Cases** (`Realtor_Test_Cases.xlsx`) — one row per case with:
`Test Case ID | Module | Test Scenario | Test Type | Preconditions | Test Steps | Test Data | Expected Result | Actual Result | Status | Priority | Related Defect ID`

Includes a **Summary Dashboard** tab with live formulas (pass rate, per-module breakdown, priority distribution).

**Defect Log** (`Realtor_Defect_Log.xlsx`) — one row per defect with:
`Defect ID | Related Test Case(s) | Module | Summary | Severity | Priority | Steps to Reproduce | Expected Result | Actual Result | Status | Environment | Reported By | Date Reported | Resolution Notes`

## Tools Used

- **Manual black-box testing** (no automation framework — deliberately scoped as a manual QA exercise)
- **Microsoft Excel** for test case design and defect tracking
- Browser DevTools for boundary/security input experiments (network throttling, viewport resizing)

## How to Use This Repo

1. Open `test-plan/Test_Plan.md` for scope, approach, and entry/exit criteria.
2. Open `test-cases/Realtor_Test_Cases.xlsx` to review the full test suite and dashboard.
3. Open `defect-reports/Realtor_Defect_Log.xlsx` to see defects, severity/priority, and repro steps.

## Resume Summary

> **Manual QA Testing – Realtor.com** | Black-Box Testing, Test Case Design, Defect Reporting
> Designed and executed 50 manual black-box test cases for realtor.com across 11 modules (search filters, property details, mortgage calculator, sign-in/registration, map view, agent finder), covering functional, UI, negative, boundary, and security scenarios. Applied equivalence partitioning, boundary value analysis, and error guessing to identify edge-case gaps in filter validation and form handling. Identified and logged 9 defects, including critical input-validation issues on the mortgage calculator. Maintained structured test case and defect tracking artifacts (Excel) with test case ID, steps, expected/actual results, status, and defect severity/priority.

---
*This is a self-directed learning/portfolio project intended to showcase manual QA methodology.*
