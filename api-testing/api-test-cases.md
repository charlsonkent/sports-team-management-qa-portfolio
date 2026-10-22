# API Test Cases — TeamSpace (Illustrative Contract)

**These cases describe intended checks for a fictional API. Paths and example responses are not live endpoints. Adapt them to the actual documentation of a permitted test API before execution.**

| ID | Endpoint concept | Scenario | Request variation | Expected behavior | Priority | Status |
|---|---|---|---|---|---|---|
| API-001 | `GET /teams` | Authorized user lists permitted teams | Valid access token | Documented success status; response contains only teams accessible to the caller | P1 | Not Run |
| API-002 | `GET /teams/{teamId}` | Request existing permitted team | Valid ID and authorized token | Documented success status; body matches team schema | P1 | Not Run |
| API-003 | `GET /teams/{teamId}` | Request nonexistent team | Well-formed but nonexistent ID | Documented not-found response; no unrelated data disclosed | P2 | Not Run |
| API-004 | `POST /teams` | Create team with valid fields | Required fields supplied | Documented creation status and valid response; record is persisted once | P1 | Not Run |
| API-005 | `POST /teams` | Omit required team name | Name missing | Validation response; no record created | P1 | Not Run |
| API-006 | `POST /teams` | Submit invalid field type | Team name has unsupported type | Validation response; no malformed record created | P2 | Not Run |
| API-007 | Protected endpoint | Request without authentication | No token/cookie | Documented authentication failure; protected data not returned | P1 | Not Run |
| API-008 | Protected endpoint | Request with invalid/expired token | Invalid token | Documented authentication failure | P1 | Not Run |
| API-009 | `PATCH /teams/{teamId}` | Read-only user attempts update | Valid token without edit permission | Documented authorization failure; record remains unchanged | P1 | Not Run |
| API-010 | `DELETE /teams/{teamId}` | Staff attempts admin-only deletion | Staff token | Documented authorization failure; team remains present | P1 | Not Run |
| API-011 | Roster endpoint | Add member with malformed email | Invalid email format | Validation response; invalid member not created | P2 | Not Run |
| API-012 | Roster endpoint | Submit same operation twice | Repeat request | Behavior matches documented idempotency/duplicate policy; no unintended duplicates | P2 | Not Run |
| API-013 | Schedule endpoint | Request events for accessible team | Authorized token | Documented response structure and correct team association | P1 | Not Run |
| API-014 | Schedule endpoint | Request another team's events without access | Unauthorized team ID | Access denied or safe not-found response per policy; no protected data exposed | P1 | Not Run |
| API-015 | Any error response | Check error payload | Invalid request | Error format is consistent and contains no secrets, stack traces, or unrelated personal data | P2 | Not Run |

## General validation checklist

For each request, record:

- HTTP method and sanitized path
- Authentication role (never the token itself)
- Request headers and body with secrets removed
- Status code
- Response content type
- Required response fields and data types
- Business-rule assertions
- Response time if relevant to the test objective
- Whether persistent data changed as expected
- Actual result, status, and linked defect

## Example Postman assertion patterns

Use these only after adapting them to the real API contract. Do not assume a status code or field name without checking documentation.

```javascript
// Example: assert the response status expected by your documented API.
pm.test("Response uses the documented status", function () {
  pm.expect(pm.response.code).to.eql(200);
});

// Example: verify a JSON response has an expected field.
// Replace "data" with a field defined in the actual API contract.
pm.test("Response contains expected data field", function () {
  const body = pm.response.json();
  pm.expect(body).to.have.property("data");
});
```

The first example is appropriate only for an endpoint expected to return `200`. A create operation may instead use `201`, and invalid requests should use the documented error status.
