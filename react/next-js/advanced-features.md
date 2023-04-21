# Advanced Features

Tài liệu chi tiết [tại đây](https://www.sitelypro.com/pages/shopify-theme-detector)

Có rất nhiều tính năng nâng cao của NextJS, tuy nhiên có 2 tính năng được sử dụng nhiều trong các app của BSS.

- [Dynamic Import](https://nextjs.org/docs/advanced-features/dynamic-import)

Kỹ thuật này sẽ defer việc loading 1 component, giúp cải thiện performance. Có thể sử dụng cho những trường hợp
mà dev dùng 1 thư viện bên ngoài, chỉ tương thích với client site (sài các biến dạng windows...).

```
import dynamic from 'next/dynamic'

const DynamicHeader = dynamic(() => import('../components/header'), {
  loading: () => <p>Loading...</p>,
})

export default function Home() {
  return <DynamicHeader />
}
```

- [Custom Server](https://nextjs.org/docs/advanced-features/custom-server)

Kỹ thuật này cho phép Dev custom NextJS server, như chèn Middleware, thêm tính năng, can thiệp file hay CSDL lúc người dùng truy cập...

Tuy nhiên việc đánh đổi chính là performance của ứng dụng, các hỗ trợ sau của NextJS sẽ không hoạt động: serverless functions & Automatic Static Optimization.

```
// server.js
const { createServer } = require('http')
const { parse } = require('url')
const next = require('next')

const dev = process.env.NODE_ENV !== 'production'
const hostname = 'localhost'
const port = 3000
// when using middleware `hostname` and `port` must be provided below
const app = next({ dev, hostname, port })
const handle = app.getRequestHandler()

app.prepare().then(() => {
  createServer(async (req, res) => {
    try {
      // Be sure to pass `true` as the second argument to `url.parse`.
      // This tells it to parse the query portion of the URL.
      const parsedUrl = parse(req.url, true)
      const { pathname, query } = parsedUrl

      if (pathname === '/a') {
        await app.render(req, res, '/a', query)
      } else if (pathname === '/b') {
        await app.render(req, res, '/b', query)
      } else {
        await handle(req, res, parsedUrl)
      }
    } catch (err) {
      console.error('Error occurred handling', req.url, err)
      res.statusCode = 500
      res.end('internal server error')
    }
  })
    .once('error', (err) => {
      console.error(err)
      process.exit(1)
    })
    .listen(port, () => {
      console.log(`> Ready on http://${hostname}:${port}`)
    })
})
```
- [Debugging](https://nextjs.org/docs/advanced-features/debugging)

Rất tiện lợi nếu dùng với Visual Code hoặc Webstorm.