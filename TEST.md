# Test Script

```bash
which curl && echo "PASS: curl available" || echo "FAIL: curl not found"
node index.js &
sleep 1
curl -s http://localhost:3000 | grep -q "myevsals v2" && echo "PASS: welcome message correct" || echo "FAIL: welcome message wrong"
curl -s -o /dev/null -w "%{http_code}" http://localhost:3000 | grep -q "200" && echo "PASS: returns 200" || echo "FAIL: bad status code"
kill %1
```
