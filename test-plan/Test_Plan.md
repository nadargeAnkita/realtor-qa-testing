# Test Plan — Realtor.com Manual QA Project

## 1. Objective
Validate core functional, UI, negative, boundary, and security behavior of realtor.com's public-facing web application through structured manual black-box testing, and produce professional QA artifacts (test cases, defect log) suitable for a QA portfolio.

## 2. Scope

### In Scope
- Search & Filters (price, beds/baths, home type, keyword search)
- Property Details page
- Mortgage Calculator widget
- Sign-in / Registration / Forgot Password
- Map View
- Agent Finder
- Saved Homes / Favorites
- Photo Gallery / Media
- Contact Agent form
- Site Navigation (header/footer)
- Notifications / Email Alerts

### Out of Scope
- Native mobile apps (iOS/Android)
- Backend/API automation testing
- Load, stress, and performance benchmarking
- Any action requiring real financial transactions or contacting live agents with fabricated inquiries
- Automated scripts/bots against production (all testing performed manually, at normal human pace)

## 3. Test Approach

**Technique:** Manual black-box testing — no knowledge of internal code assumed; test design based solely on requirements, observed UI behavior, and domain expectations of a real estate search platform.

**Techniques applied:**
| Technique | Purpose | Example |
|---|---|---|
| Equivalence Partitioning | Reduce input space to representative valid/invalid classes | Valid vs. invalid ZIP codes in Agent Finder |
| Boundary Value Analysis | Test values at/just beyond limits | $0 and max price filter, 0% and 20% interest rate, 8/64-char password |
| Error Guessing | Use tester intuition for likely defect areas | Down payment greater than home price |
| Negative Testing | Confirm graceful handling of invalid/unexpected input | Non-numeric mortgage inputs, empty required form fields |
| Security (exploratory) | Basic black-box security sanity checks | XSS payload in search/message fields, SQLi-style login string, brute-force login attempts |

## 4. Test Environment

| Item | Detail |
|---|---|
| Application | realtor.com (public production) |
| Browser(s) | Chrome 128 (primary), viewport emulation for mobile (375px) |
| OS | Windows 11 |
| Network | Standard broadband + throttled "Slow 3G" profile for select UI tests |
| Test Data | Publicly available listings; no real personal or payment data used |

## 5. Entry Criteria
- Test cases drafted and reviewed against the 11 in-scope modules
- Realtor.com publicly accessible and stable (no maintenance banners)

## 6. Exit Criteria
- All 50 planned test cases executed
- All failures logged as defects with severity/priority and repro steps
- Summary dashboard reflects final pass/fail counts

## 7. Defect Severity & Priority Definitions

**Severity** (impact on the system):
- **High** — Core functionality broken, incorrect calculation, or security exposure
- **Medium** — Feature works but with incorrect/missing validation or degraded UX
- **Low** — Cosmetic, minor content, or edge-case display issue

**Priority** (urgency to fix):
- **P1** — Fix immediately (security, incorrect financial calculation)
- **P2** — Fix in next release cycle
- **P3** — Fix when convenient, moderate user impact
- **P4** — Backlog / cosmetic

## 8. Deliverables
- `Realtor_Test_Cases.xlsx` — 50 test cases with a Summary Dashboard tab
- `Realtor_Defect_Log.xlsx` — 9 tracked defects
- This Test Plan

## 9. Risks & Assumptions
- Application is a live production site, so listing data, prices, and available agents change over time; test cases reference behavior patterns rather than specific listing IDs where possible.
- No test/staging environment was available; all testing was performed against production using safe, non-destructive, read-only actions.
- Some UI text/labels may have changed since these test cases were authored, as this is an independent, unaffiliated project rather than one commissioned by Realtor.com / Move, Inc.
