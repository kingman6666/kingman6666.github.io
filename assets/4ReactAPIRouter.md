# API Router (React Router) in nextjs

### file system:
```
app
 |---api/xxx/route.js
 |---xxx/page.js
```

### code demo:
```
// xxx/page.js

  let res = await fetch('/api/xxx', { method: 'GET/POST/...' })
  res = await res.json()
```

```
// api/xxx/route.js

  export async function GET/POST/...(request, response) {
    // GET
    return new Response(JSON.stringify({xxx}),{ //data
      headers: { 'Content-Type': 'application/json' },
      status: 200
    })

    // POST
    let body = await request.json()
    return new NextResponse.json({
      message: 'success',
      data: {xxx} // data
    }, {
      headers: { 'Content-Type': 'application/json' },
      status: 200
    })
  }
```

