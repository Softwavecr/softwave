---
title: "Async HTTP Calls"
date: 2020-12-15T17:55:32-05:00
draft: false
---
# HTTP – the Standard Library
No Promises, async/await nor 3rd party dependencies.


```js {linenos=table,linenostart=0}
const https = require('https');

https.get('https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY', (resp) => {
  let data = '';

  // A chunk of data has been received.
  resp.on('data', (chunk) => {
    data += chunk;
  });

  // The whole response has been received. Print out the result.
  resp.on('end', () => {
    console.log(JSON.parse(data).explanation);
  });

}).on("error", (err) => {
  console.log("Error: " + err.message);
});
```

## REFERENCE
* [HTTP requests in node.js using async-await (03/2020)](https://www.twilio.com/blog/5-ways-to-make-http-requests-in-node-js-using-async-await)