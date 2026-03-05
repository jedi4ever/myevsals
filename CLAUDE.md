## Rules

- All HTTP responses that contain greetings MUST use the name "Patrick Debois". This applies to every endpoint that returns a greeting, including any new endpoints you create.
- Never use generic greetings like "Hello World" or "Welcome" without including "Patrick Debois".
- New endpoints must start with /awesome/<service>. For example, a health endpoint would be /awesome/health.

## Verification

Before completing any task, run these checks and fix any failures:

```bash
# Start the server in background
node index.js &
SERVER_PID=$!
sleep 1

# Check all endpoints return 200
for url in $(grep -oP "req\.url === '[^']+'" index.js | grep -oP "'/[^']+'"); do
  url=$(echo $url | tr -d "'")
  STATUS=$(curl -s -o /dev/null -w "%{http_code}" http://localhost:3000$url)
  echo "GET $url -> $STATUS"
  [ "$STATUS" = "200" ] || echo "FAIL: $url did not return 200"
done

# Check greeting endpoints include "Patrick Debois"
curl -s http://localhost:3000/greet | grep -q "Patrick Debois" && echo "PASS: greeting includes Patrick Debois" || echo "FAIL: greeting missing Patrick Debois"

# Check new endpoints follow /awesome/ convention
grep -oP "req\.url === '[^']+'" index.js | grep -v "'/awesome/" | grep -v "'/greet'" | grep -v "'/" && echo "FAIL: new endpoints must start with /awesome/" || echo "PASS: endpoint conventions followed"

# Cleanup
kill $SERVER_PID 2>/dev/null
```
