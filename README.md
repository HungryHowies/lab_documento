# lab_documento

VM prerequisite

Ubuntu 22.0.4

sudo apt update && apt upgrade

sudo timedatectl set-timezone America/Chicago

sudo apt install net-tools plocate vim git sendmail


## Install Node v22

sudo apt install -y ca-certificates curl gnupg

sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg

echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_22.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list

sudo apt update

sudo apt install nodejs -y

node --version


### PostrgeSQL 14 Install

sudo apt install postgresql postgresql-contrib

sudo -u postgres psql

CREATE ROLE documenso LOGIN;

CREATE DATABASE documenso;

GRANT CONNECT, CREATE ON DATABASE documenso TO documenso;

ALTER USER documenso PASSWORD 'password';

\q

mkdir /tmp/documenso

cd /tmp/documenso 

git clone https://github.com/documenso/documenso.git

cd documenso

cp .env.example .env

vi .env

## Edit the file .env 

NOTE: I removed "0" from port number so defualt Postgress is used.

NEXTAUTH_SECRET="secret"

NEXT_PUBLIC_WEBAPP_URL="http://192.168.1.112:3000"

NEXT_PRIVATE_DATABASE_URL="postgres://documenso:password@127.0.0.1:5432/documenso"

NEXT_PRIVATE_DIRECT_DATABASE_URL="postgres://documenso:password@127.0.0.1:5432/documenso"

NEXT_PRIVATE_SMTP_FROM_NAME="Documenso"

NEXT_PRIVATE_SMTP_FROM_ADDRESS="noreply@documenso.com"

## Build
```
npm i
```
### This doesn work, error's out.
```
npm run build:web
```
### Option
```
npm run build
```
```
npm run prisma:migrate-deploy
```
### Command with error's 
```
npm i && npm run prisma:generate -w @documenso/prisma && npm run build -w @documenso/web
```

### Notes 

Clean NodeJS cache.

```
npm cache clean --force
```
javascript heap out of memory
```
export NODE_OPTIONS=--max_old_space_size=4096
```
Update trubo
```
npx @turbo/codemod update
```
