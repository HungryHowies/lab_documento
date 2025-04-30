## Cretae certificates

Created my own certificate using the file SIGNING.md
```
# Creating your own signing certificate

For the digital signature of your documents you need a signing certificate in .p12 format (public and private key). You can buy one (not recommended for dev) or use the steps to create a self-signed one:

1. Generate a private key using the OpenSSL command. You can run the following command to generate a 2048-bit RSA key:

   `openssl genrsa -out private.key 2048`

2. Generate a self-signed certificate using the private key. You can run the following command to generate a self-signed certificate:

   `openssl req -new -x509 -key private.key -out certificate.crt -days 365`

   This will prompt you to enter some information, such as the Common Name (CN) for the certificate. Make sure you enter the correct information. The -days parameter sets the number of days for which the certificate is valid.

3. Combine the private key and the self-signed certificate to create the p12 certificate. You can run the following command to do this:

   `openssl pkcs12 -export -out certificate.p12 -inkey private.key -in certificate.crt`

4. You will be prompted to enter a password for the p12 file. Choose a strong password and remember it, as you will need it to use the certificate (**can be empty for dev certificates**)

5. Place the certificate `/apps/web/resources/certificate.p12` (If the path does not exist, it needs to be created)
```
Create the directory called "resources".

```
mkdir resources
```
Copied  the certs made into the directory resources.

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
