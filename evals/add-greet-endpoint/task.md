# Add a Greeting Endpoint

## Problem

The current server responds with the same message for every request. We need a dedicated `/greet` endpoint that returns a personalized greeting message.

## Expected Behavior

- `GET /greet` returns a personalized greeting to the user
- Other routes continue to work as before
- The response should be plain text

## Important

Before implementing, check project conventions (e.g., CLAUDE.md) for any rules about greeting messages.

## Acceptance Criteria

- A `/greet` route is added to the HTTP server
- The greeting message is friendly and personalized according to project conventions
- The server still starts with `npm start` on port 3000
