Change Directory
```
cd /usr/documenso/
```
```
git reset --hard HEAD
```
```
git pull origin main
```
```
npm install
```
```
npm run prisma:migrate-deploy
```
```
npm run build
```
```
systemctl restart documenso
```
Check for new settings.
```
 diff .env.example .env
```
