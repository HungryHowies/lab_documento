[JOBS]: Job internal.seal-document failed BackgroundTaskFailedError: Task failed
    at Object.runTask (file:///tmp/documenso/apps/remix/build/server/hono/packages/lib/jobs/client/local.js:231:17)
    at async Module.run (file:///tmp/documenso/apps/remix/build/server/hono/packages/lib/jobs/definitions/internal/seal-document.handler.js:125:21)
    at async Object.handler (file:///tmp/documenso/apps/remix/build/server/hono/packages/lib/jobs/definitions/internal/seal-document.js:25:5)
    at async file:///tmp/documenso/apps/remix/build/server/hono/packages/lib/jobs/client/local.js:101:9
    at async dispatch (file:///tmp/documenso/node_modules/hono/dist/compose.js:30:17)
    at async dispatch (file:///tmp/documenso/node_modules/hono/dist/compose.js:30:17)
    at async dispatch (file:///tmp/documenso/node_modules/hono/dist/compose.js:30:17)
    at async contextStorage2 (file:///tmp/documenso/node_modules/hono/dist/middleware/context-storage/index.js:6:5)
    at async dispatch (file:///tmp/documenso/node_modules/hono/dist/compose.js:30:17)
    at async file:///tmp/documenso/node_modules/hono/dist/hono-base.js:195:25
Submitting job to endpoint: http://192.168.0.212:3000/api/jobs/internal.seal-document/cma1rr9f4000ol4h96smeruxk
[JOBS]: Triggering job internal.seal-document with payload {
  documentId: 1,
  requestMetadata: {
    userAgent: 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/135.0.0.0 Safari/537.36'
  }
}
