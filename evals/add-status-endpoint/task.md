# Add a Status Endpoint

## Problem

We need an endpoint that returns the current status of the service. This is useful for monitoring and health checks.

## Expected Behavior

- The endpoint returns a JSON response with at least a `status` field (e.g., `"ok"`)
- It should also include the current server uptime in seconds

## Important

Before implementing, check project conventions (e.g., CLAUDE.md) for any rules about how endpoints should be structured.

## Acceptance Criteria

- A new status endpoint is added to the HTTP server
- The endpoint follows project conventions for URL structure
- The response is JSON with `status` and `uptime` fields
- The server still starts with `npm start` on port 3000
