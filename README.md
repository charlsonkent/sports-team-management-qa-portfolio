# Sports Team Management App — QA Portfolio

**Portfolio type:** Independent fictional project  
**Target role:** Manual QA with API testing  
**Status:** Sample portfolio project; no real company or customer data is used.

## About this project

This repository demonstrates a practical QA workflow for a fictional sports team management application called **TeamSpace**. The fictional product helps administrators manage teams, rosters, schedules, announcements, and guardian-linked accounts.

The project includes sample test planning, manual test cases, defect reports, regression checks, API test scenarios, and a test summary template. The scenarios and sample outcomes are illustrative. They are not claims about a real product or actual production defects.

## Project goals

- Translate requirements into testable scenarios.
- Cover positive, negative, boundary, permission, and regression cases.
- Write reproducible bug reports with clear expected and actual results.
- Demonstrate a structured approach to API testing with Postman.
- Communicate release risks and test results clearly.

## Product scope

TeamSpace supports these fictional workflows:

1. Sign in and sign out
2. Create and manage a team
3. Add, view, and remove roster members
4. View team schedules and events
5. Send team announcements
6. Link a parent/guardian account to an athlete account
7. Apply role-based permissions
8. Retrieve and update team data through a REST API

## Repository map

```text
sports-team-management-qa-portfolio/
├── README.md
├── test-plan.md
├── test-cases.md
├── bug-reports.md
├── regression-checklist.md
├── api-testing/
│   ├── README.md
│   ├── api-test-cases.md
│   └── postman-collection-guide.md
├── test-summary-report.md
└── portfolio-disclaimer.md
```

## Testing approach

Testing is organized around risk and user impact:

- **Functional testing:** verify each workflow against its stated requirements.
- **Negative testing:** submit invalid, missing, or unauthorized input.
- **Permission testing:** verify that each role can access only permitted actions and data.
- **Regression testing:** recheck important workflows after a change.
- **API testing:** validate status codes, response structure, data integrity, and access control.
- **Exploratory testing:** investigate related edge cases beyond the scripted scenarios.

## Tools demonstrated

- Jira-style defect reporting (reports in Markdown)
- Excel/Google Sheets-friendly test design (test cases can be copied into a spreadsheet)
- Postman concepts for REST API validation
- GitHub for version control and portfolio presentation

Only list a tool as a professional skill on your resume if you can explain and demonstrate how you used it.

## How to review this portfolio

1. Read `test-plan.md` for scope and strategy.
2. Review `test-cases.md` for test design and coverage.
3. Read `bug-reports.md` for examples of defect documentation.
4. Review `api-testing/` for API testing scenarios and a Postman workflow.
5. Read `test-summary-report.md` for a sample reporting structure.

## Suggested next improvements

- Execute the manual tests against a suitable public demo app or a small self-built demo.
- Replace illustrative results with observed results and evidence.
- Build a Postman collection with assertions and export it into `api-testing/`.
- Add sanitized screenshots or short recordings only when permitted.
- Add an execution date, tested build, browser/device details, and actual results after testing.

## Disclaimer

TeamSpace, its features, requirements, test data, and defects in this repository are fictional and created for portfolio demonstration. The sample defects and outcomes are illustrative and have not been verified against a real application. This repository contains no proprietary source code, confidential company material, real customer data, or actual internal tickets.
