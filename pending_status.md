## Set the signing certificate in .env file

```
# [[SIGNING]]
# The transport to use for document signing. Available options: local (default) | gcloud-hsm
NEXT_PRIVATE_SIGNING_TRANSPORT="local"
# OPTIONAL: The passphrase to use for the local file-based signing transport.
NEXT_PRIVATE_SIGNING_PASSPHRASE="password"
# OPTIONAL: The local file path to the .p12 file to use for the local signing transport.
NEXT_PRIVATE_SIGNING_LOCAL_FILE_PATH="/tmp/documenso/apps/web/resources/certificate.p12"
# OPTIONAL: The base64-encoded contents of the .p12 file to use for the local signing transport.
NEXT_PRIVATE_SIGNING_LOCAL_FILE_CONTENTS=
# OPTIONAL: The path to the Google Cloud HSM key to use for the gcloud-hsm signing transport.
NEXT_PRIVATE_SIGNING_GCLOUD_HSM_KEY_PATH=
# OPTIONAL: The path to the Google Cloud HSM public certificate file to use for the gcloud-hsm signing transport.
NEXT_PRIVATE_SIGNING_GCLOUD_HSM_PUBLIC_CRT_FILE_PATH=
# OPTIONAL: The base64-encoded contents of the Google Cloud HSM public certificate file to use for the gcloud-hsm signing transport.
NEXT_PRIVATE_SIGNING_GCLOUD_HSM_PUBLIC_CRT_FILE_CONTENTS=
# OPTIONAL: The path to the Google Cloud Credentials file to use for the gcloud-hsm signing transport.
NEXT_PRIVATE_SIGNING_GCLOUD_APPLICATION_CREDENTIALS_CONTENTS=
```
Execute run command
```
npm run start
```
Error
```
[JOBS]: Job internal.seal-document failed p [BackgroundTaskExceededRetriesError]: Task exceeded retries
    at Object.runTask (/tmp/documenso/apps/web/.next/server/chunks/9125.js:1:31898)
    at async Module.b (/tmp/documenso/apps/web/.next/server/chunks/6822.js:1:2710)
    at async Object.handler (/tmp/documenso/apps/web/.next/server/chunks/9125.js:1:39860)
    at async /tmp/documenso/apps/web/.next/server/chunks/9125.js:1:30329
    at async K (/tmp/documenso/node_modules/next/dist/compiled/next-server/pages-api.runtime.prod.js:20:16853)
    at async U.render (/tmp/documenso/node_modules/next/dist/compiled/next-server/pages-api.runtime.prod.js:20:17492)
    at async NextNodeServer.runApi (/tmp/documenso/node_modules/next/dist/server/next-server.js:600:9)
    at async NextNodeServer.handleCatchallRenderRequest (/tmp/documenso/node_modules/next/dist/server/next-server.js:269:37)
    at async NextNodeServer.handleRequestImpl (/tmp/documenso/node_modules/next/dist/server/base-server.js:816:17)
    at async invokeRender (/tmp/documenso/node_modules/next/dist/server/lib/router-server.js:174:21)
API response for /api/trpc/team.getTeams,document.getDocumentById?batch=1&input=%7B%220%22%3A%7B%22json%22%3Anull%2C%22meta%22%3A%7B%22values%22%3A%5B%22undefined%22%5D%7D%7D%2C%221%22%3A%7B%22json%22%3A%7B%22documentId%22%3A3%7D%7D%7D exceeds 4MB. API Routes are meant to respond quickly. https://nextjs.org/docs/messages/api-routes-response-size-limit
API response for /api/trpc/team.getTeams,document.getDocumentById?batch=1&input=%7B%220%22%3A%7B%22json%22%3Anull%2C%22meta%22%3A%7B%22values%22%3A%5B%22undefined%22%5D%7D%7D%2C%221%22%3A%7B%22json%22%3A%7B%22documentId%22%3A3%7D%7D%7D exceeds 4MB. API Routes are meant to respond quickly. https://nextjs.org/docs/messages/api-routes-response-size-limit
API response for /api/trpc/team.getTeams,document.getDocumentById?batch=1&input=%7B%220%22%3A%7B%22json%22%3Anull%2C%22meta%22%3A%7B%22values%22%3A%5B%22undefined%22%5D%7D%7D%2C%221%22%3A%7B%22json%22%3A%7B%22documentId%22%3A3%7D%7D%7D exceeds 4MB. API Routes are meant to respond quickly. https://nextjs.org/docs/messages/api-routes-response-size-limit
```
