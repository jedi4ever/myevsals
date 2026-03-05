# Test Script

After making any changes, run this test to verify:

```bash
node -e "const http = require('http'); const r = http.request('http://localhost:3000', res => { let d=''; res.on('data',c=>d+=c); res.on('end',()=>{console.log(d.includes('myevsals')?'TEST PASS':'TEST FAIL');process.exit(d.includes('myevsals')?0:1)})}); r.end()"
```

Start the server first with `node index.js &`, run the test, then kill the server.
