# Building a Postman Collection

This guide outlines how to turn the API test cases into a reusable Postman collection.

## 1. Create a collection

Suggested name: `TeamSpace API QA — Portfolio Demo`

Add a description stating that the collection is a portfolio exercise and that its requests must be configured for a real, documented, authorized test API before execution.

## 2. Create an environment

Use variables such as:

| Variable | Example value | Notes |
|---|---|---|
| `baseUrl` | Set to your permitted test API URL | Do not use a fictional URL as a live target |
| `accessToken` | Set locally when needed | Keep secret; do not commit real tokens |
| `teamId` | A synthetic test ID from the test environment | Replace with a real test ID returned by the API |

Do not commit secrets in exported environments. If a variable contains credentials, use a local/private environment or a safe secret-management method.

## 3. Organize requests

Suggested folders:

- Authentication
- Teams
- Roster
- Schedule
- Permissions / Negative tests

Use only endpoints documented by the API you are authorized to test.

## 4. Add assertions

For each request, assert only documented behavior. Common checks include:

- Expected status code
- Expected content type
- Required response fields
- Field data types
- Business rules
- Authorization behavior
- Data persistence after create/update/delete operations

## 5. Execute and document

1. Confirm the base URL and environment.
2. Confirm the target is a test service you are allowed to use.
3. Run one request at a time while developing assertions.
4. Run the full collection.
5. Review failures and investigate them rather than changing assertions just to make the run pass.
6. Save sanitized evidence and actual execution results.

## 6. Publish safely

Before committing the collection:

- Remove real access tokens, cookies, passwords, and API keys.
- Remove private customer information.
- Avoid publishing private URLs or internal hostnames.
- Check saved example responses for sensitive data.
- State which public/demo API was tested and when.
- Do not include test results that you did not actually observe.
