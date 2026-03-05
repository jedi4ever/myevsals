# Test Script

```bash
node index.js &
sleep 1
curl -s -I http://localhost:3000/awesome/version | grep -qi "X-Powered-By: myevsals" && echo "PASS: X-Powered-By header present" || echo "FAIL: X-Powered-By header missing"
curl -s http://localhost:3000/awesome/version | grep -q "version" && echo "PASS: version endpoint works" || echo "FAIL: version endpoint broken"
kill %1
```
