# Manual Test Cases — TeamSpace

**Note:** These are designed test cases, not proof that tests have been executed. Record observed results and evidence when running them against an available test application.

## Test data and conventions

- Product: TeamSpace (fictional)
- Example team: Falcons U14
- Use synthetic accounts and data only.
- Priority: P1 = highest, P2 = normal, P3 = lower.
- Actual result and status should remain `Not Run` until execution.

| ID | Feature | Scenario | Preconditions | Steps | Expected result | Priority | Status |
|---|---|---|---|---|---|---|---|
| TC-001 | Sign in | Sign in with valid credentials | Active test account exists | 1. Open sign-in page. 2. Enter valid credentials. 3. Submit. | User is authenticated and lands on the permitted home page. | P1 | Not Run |
| TC-002 | Sign in | Reject incorrect password | Active test account exists | 1. Enter valid email. 2. Enter incorrect password. 3. Submit. | Sign-in is rejected; a safe, understandable error is displayed. | P1 | Not Run |
| TC-003 | Sign in | Required fields are validated | Sign-in page is available | 1. Leave both fields blank. 2. Submit. | Required-field validation appears; no session is created. | P2 | Not Run |
| TC-004 | Sign out | Signed-out user cannot reopen protected page | User is signed in | 1. Open a protected page. 2. Sign out. 3. Use browser back. | Protected content is not accessible after sign-out; user is redirected or asked to sign in. | P1 | Not Run |
| TC-005 | Team | Admin creates a team with valid data | Admin is signed in | 1. Open team management. 2. Select create team. 3. Enter valid name and season. 4. Save. | Team is created once and appears in the team list. | P1 | Not Run |
| TC-006 | Team | Team name is required | Admin is signed in | 1. Open create team. 2. Leave team name blank. 3. Save. | Team is not created; required-field validation appears. | P2 | Not Run |
| TC-007 | Team | Prevent accidental duplicate submission | Admin is signed in | 1. Fill valid team details. 2. Click Save repeatedly or quickly. | Only one team is created, or duplicate handling is clearly defined. | P2 | Not Run |
| TC-008 | Team | Staff cannot access an unassigned team | Staff account is assigned to Team A only | 1. Sign in as staff. 2. Attempt to open Team B via navigation or direct URL. | Team B data is denied or omitted according to the permission model. | P1 | Not Run |
| TC-009 | Roster | Admin adds a valid athlete | Admin can manage roster | 1. Open roster. 2. Add athlete with valid synthetic details. 3. Save. | Athlete appears once with the correct details. | P1 | Not Run |
| TC-010 | Roster | Reject malformed email address | Add-athlete form is available | 1. Enter an invalid email format. 2. Save. | Input is rejected with clear validation; invalid record is not saved. | P2 | Not Run |
| TC-011 | Roster | Search finds matching member | Roster contains Alex Sample | 1. Open roster. 2. Search for `Alex Sample`. | Matching member appears; unrelated records are not incorrectly presented as matches. | P2 | Not Run |
| TC-012 | Roster | Empty search result is handled | Roster is available | 1. Search for a unique nonexistent name. | Empty state is clear; page remains usable. | P3 | Not Run |
| TC-013 | Roster | Removed athlete loses team access | Athlete is currently on a team | 1. Admin removes athlete. 2. Sign in as athlete. 3. Open team page. | Removed athlete no longer has access to restricted team content. | P1 | Not Run |
| TC-014 | Schedule | Upcoming event is visible to permitted member | Event exists for the team | 1. Sign in as an authorized member. 2. Open schedule. | Event appears with correct date, time, title, and location. | P1 | Not Run |
| TC-015 | Schedule | Event time is displayed consistently | Event has a defined time zone | 1. Open event details. 2. Compare event card and details. | Time is consistent and displayed according to documented time-zone behavior. | P1 | Not Run |
| TC-016 | Schedule | User cannot view a restricted team's event | User has no access to Team B | 1. Sign in as user. 2. Attempt to access Team B event directly. | Restricted event details are not disclosed. | P1 | Not Run |
| TC-017 | Announcements | Authorized staff publishes announcement | Staff has announcement permission | 1. Open announcements. 2. Create announcement. 3. Publish. | Announcement is saved and visible to its intended audience. | P1 | Not Run |
| TC-018 | Announcements | Staff without permission cannot publish | Staff lacks announcement permission | 1. Sign in as staff. 2. Attempt to publish through UI. 3. If applicable, attempt the protected API action. | Publish action is unavailable or rejected; no announcement is created. | P1 | Not Run |
| TC-019 | Announcements | Empty announcement is rejected | Authorized staff is signed in | 1. Open create announcement. 2. Leave required content blank. 3. Publish. | Validation appears and no empty announcement is created. | P2 | Not Run |
| TC-020 | Linked accounts | Guardian links to an athlete with valid invitation | Guardian and athlete test accounts exist | 1. Start the linking flow. 2. Use a valid invitation. 3. Complete confirmation. | The correct accounts become linked and the relationship is shown accurately. | P1 | Not Run |
| TC-021 | Linked accounts | Invalid or expired invitation is rejected | Invalid/expired invitation is available | 1. Open linking flow. 2. Submit the invalid invitation. | Link is not created; a safe error explains that the invitation is invalid or expired. | P1 | Not Run |
| TC-022 | Linked accounts | Guardian cannot access an unlinked athlete | Guardian is linked to Athlete A only | 1. Sign in as guardian. 2. Attempt to open Athlete B's restricted information. | Access to Athlete B's restricted information is denied. | P1 | Not Run |
| TC-023 | Permissions | Enabling communication does not grant manager privileges | Staff can be configured with separate permissions | 1. Enable communication only. 2. Sign in as staff. 3. Check chat and management actions. | Communication access follows the requirement; unrelated manager actions remain unavailable. | P1 | Not Run |
| TC-024 | Permissions | Disabling a permission removes access | Staff currently has a permission | 1. Disable the permission as admin. 2. Refresh or sign in again as staff. 3. Attempt the restricted action. | The disabled action is no longer permitted, including via direct route/API where applicable. | P1 | Not Run |
| TC-025 | API | Get teams returns valid response | API base URL and test access are configured | 1. Send documented GET teams request. 2. Inspect status and body. | Response matches the API contract and contains only data the caller may access. | P1 | Not Run |
| TC-026 | API | Invalid team identifier is handled | API endpoint supports team lookup | 1. Request a syntactically valid but nonexistent team ID. | API returns the documented not-found response without leaking unrelated data. | P2 | Not Run |
| TC-027 | API | Missing required field is rejected | API endpoint creates a team | 1. Submit create-team request without required name. | API returns documented validation response; no invalid team is created. | P1 | Not Run |
| TC-028 | API | Unauthenticated request is rejected | Protected endpoint is available | 1. Remove authorization. 2. Request protected resource. | Request is rejected with documented authentication status; protected data is not returned. | P1 | Not Run |
| TC-029 | API | Read-only user cannot modify team | Read-only user token is available | 1. Send update request using read-only token. | API rejects the unauthorized update; data remains unchanged. | P1 | Not Run |
| TC-030 | Regression | Roster and schedule remain available after a change | A change affecting team membership has been deployed | 1. Add/remove a test member. 2. Reopen roster. 3. Open schedule. 4. Check permitted accounts. | Roster and schedule load correctly and permission behavior remains correct. | P1 | Not Run |

## Execution log template

Copy this table for each execution cycle.

| Test Case ID | Build | Tester | Date | Actual Result | Status | Defect ID | Evidence |
|---|---|---|---|---|---|---|---|
| TC-001 | TBD | TBD | TBD | Not executed | Not Run | — | — |

## Test design notes

- Do not assume a particular result where the requirement is unclear. Confirm expected behavior first.
- For date/time testing, establish the product's documented time-zone rules.
- For access control, test both the UI and server-side enforcement when API access is available.
- Use synthetic accounts and data only.
