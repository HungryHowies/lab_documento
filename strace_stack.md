### Execute
```
npm i
```
```
npm run build
```
```
0 verbose cli /usr/bin/node /usr/bin/npm
1 info using npm@11.3.0
2 info using node@v22.15.0
3 silly config load:file:/usr/lib/node_modules/npm/npmrc
4 warn Unknown env config "auto-install-peers". This will stop working in the next major version of npm.
5 info config found workspace root at /var/www/documenso
6 silly config load:file:/var/www/documenso/.npmrc
7 warn Unknown project config "auto-install-peers". This will stop working in the next major version of npm.
8 silly config load:file:/root/.npmrc
9 silly config load:file:/usr/etc/npmrc
10 verbose title npm run with:env cross-env NODE_ENV=production node build/server/main.js
11 verbose argv "run" "with:env" "--" "cross-env" "NODE_ENV=production" "node" "build/server/main.js"
12 verbose logfile logs-max:10 dir:/root/.npm/_logs/2025-04-25T22_06_59_548Z-
13 verbose logfile /root/.npm/_logs/2025-04-25T22_06_59_548Z-debug-0.log
14 silly logfile start cleaning logs, removing 1 files
15 silly logfile done cleaning log files
16 verbose stack Error: command failed
16 verbose stack     at promiseSpawn (/usr/lib/node_modules/npm/node_modules/@npmcli/promise-spawn/lib/index.js:22:22)
16 verbose stack     at spawnWithShell (/usr/lib/node_modules/npm/node_modules/@npmcli/promise-spawn/lib/index.js:124:10)
16 verbose stack     at promiseSpawn (/usr/lib/node_modules/npm/node_modules/@npmcli/promise-spawn/lib/index.js:12:12)
16 verbose stack     at runScriptPkg (/usr/lib/node_modules/npm/node_modules/@npmcli/run-script/lib/run-script-pkg.js:79:13)
16 verbose stack     at runScript (/usr/lib/node_modules/npm/node_modules/@npmcli/run-script/lib/run-script.js:9:12)
16 verbose stack     at #run (/usr/lib/node_modules/npm/lib/commands/run-script.js:135:13)
16 verbose stack     at RunScript.execWorkspaces (/usr/lib/node_modules/npm/lib/commands/run-script.js:67:24)
16 verbose stack     at async Npm.exec (/usr/lib/node_modules/npm/lib/npm.js:208:9)
16 verbose stack     at async module.exports (/usr/lib/node_modules/npm/lib/cli/entry.js:67:5)
17 verbose pkgid @documenso/remix@1.10.0-rc.5
18 error Lifecycle script `with:env` failed with error:
19 error code 1
20 error path /var/www/documenso/apps/remix
21 error workspace @documenso/remix@1.10.0-rc.5
22 error location /var/www/documenso/apps/remix
23 error command failed
24 error command sh -c dotenv -e ../../.env -e ../../.env.local -- cross-env NODE_ENV=production node build/server/main.js
25 verbose cwd /var/www/documenso/apps/remix
26 verbose os Linux 5.15.0-138-generic
27 verbose node v22.15.0
28 verbose npm  v11.3.0
29 verbose exit 1
30 verbose code 1
```
### Execute

```
npm run prisma:migrate-deploy
```
```
npm warn Unknown env config "auto-install-peers". This will stop working in the next major version of npm.
@documenso/remix:start: npm warn Unknown project config "auto-install-peers". This will stop working in the next major version of npm.
@documenso/remix:start:
@documenso/remix:start: > @documenso/remix@1.10.0-rc.5 with:env
@documenso/remix:start: > dotenv -e ../../.env -e ../../.env.local -- cross-env NODE_ENV=production node build/server/main.js
@documenso/remix:start:
node:internal/modules/cjs/loader:1404
@documenso/remix:start:   throw err;
@documenso/remix:start:   ^
@documenso/remix:start:
@documenso/remix:start: Error: Cannot find module '/var/www/documenso/apps/remix/build/server/main.js'
@documenso/remix:start:     at Function._resolveFilename (node:internal/modules/cjs/loader:1401:15)
@documenso/remix:start:     at defaultResolveImpl (node:internal/modules/cjs/loader:1057:19)
@documenso/remix:start:     at resolveForCJSWithHooks (node:internal/modules/cjs/loader:1062:22)
@documenso/remix:start:     at Function._load (node:internal/modules/cjs/loader:1211:37)
@documenso/remix:start:     at TracingChannel.traceSync (node:diagnostics_channel:322:14)
@documenso/remix:start:     at wrapModuleLoad (node:internal/modules/cjs/loader:235:24)
@documenso/remix:start:     at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:170:5)
@documenso/remix:start:     at node:internal/main/run_main_module:36:49 {
@documenso/remix:start:   code: 'MODULE_NOT_FOUND',
@documenso/remix:start:   requireStack: []
@documenso/remix:start: }
@documenso/remix:start:
@documenso/remix:start: Node.js v22.15.0
npm error Lifecycle script `with:env` failed with error:
npm error code 1
npm error path /var/www/documenso/apps/remix
npm error workspace @documenso/remix@1.10.0-rc.5
npm error location /var/www/documenso/apps/remix
npm error command failed
npm error command sh -c dotenv -e ../../.env -e ../../.env.local -- cross-env NODE_ENV=production node build/server/main.js
npm error Lifecycle script `start` failed with error:
npm error code 1
npm error path /var/www/documenso/apps/remix
npm error workspace @documenso/remix@1.10.0-rc.5
npm error location /var/www/documenso/apps/remix
npm error command failed
npm error command sh -c npm run with:env -- cross-env NODE_ENV=production node build/server/main.js

@documenso/remix:start: ERROR: command finished with error: command (/var/www/documenso/apps/remix) /usr/bin/npm run start exited (1)


@documenso/remix#start: command (/var/www/documenso/apps/remix) /usr/bin/npm run start exited (1)

 Tasks:    2 successful, 5 total
Cached:    1 cached, 5 total
  Time:    47.727s
Failed:    @documenso/remix#start

 ERROR  run failed: command  exited (1)
```
