# lab_documento

The following documentation is using default settings for Self-Hosting on Ubuntu 22.0.4. Through trial and error this should  have Documenso-1.10_rc.5 working.  The difference between that I found from version 1.9.0 and 1.10_rc.5 is the build command  on the 1.9.0. version  makes directory  /web and the 1.10 does not. The following steps will show this.

## Virtual Machine prerequisite

4 CPU, 4 GB RAM and 80 GB Drive.

Ubuntu 22.0.4
```
sudo apt update && apt upgrade
```
```
sudo timedatectl set-timezone America/Chicago
```
```
sudo apt install net-tools plocate vim git sendmail
```

## Install Node v22
```
sudo apt install -y ca-certificates curl gnupg
```
```
sudo mkdir -p /etc/apt/keyrings
```
```
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
```
```
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_22.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
```
```
sudo apt update
```
```
sudo apt install nodejs -y
```
```
node --version
```

### PostrgeSQL 14 Install
```
sudo apt install postgresql postgresql-contrib
```
```
sudo -u postgres psql
```
```
CREATE ROLE documenso LOGIN;
```
```
CREATE DATABASE documenso;
```
```
GRANT CONNECT, CREATE ON DATABASE documenso TO documenso;
```
```
ALTER USER documenso PASSWORD 'password';
```
```
\q
```

NOTE: Reminder this is in a /tmp directory and a reboot/restart may get deleted.
### Download Documenso 

```
cd /tmp/
```
```
git clone https://github.com/documenso/documenso.git
```
```
cd documenso
```
```
cp .env.example .env
```
```
vi .env
```
## Edit the file .env 

NOTE: I removed "0" from port number so default Postgress is used. The correct configurations are shown below. Adjust the IP Address.

```
NEXTAUTH_SECRET="secret"

NEXT_PUBLIC_WEBAPP_URL="http://192.168.1.112:3000"

NEXT_PRIVATE_DATABASE_URL="postgres://documenso:password@127.0.0.1:5432/documenso"

NEXT_PRIVATE_DIRECT_DATABASE_URL="postgres://documenso:password@127.0.0.1:5432/documenso"

NEXT_PRIVATE_SMTP_PORT=25
```
### OPTIONAL: Defines the password to use with the SMTP server.

Commented out the following line for testing purposes.
```
# NEXT_PRIVATE_SMTP_USERNAME="documenso"
```

```
# NEXT_PRIVATE_SMTP_PASSWORD="password"
```
## Javascript heap out of memory.

I increase the heap to 4GB so there was no more issues during the building phase. This would depend on how much memory you have on the instance. 

```
export NODE_OPTIONS=--max_old_space_size=4096
```

## Build
Navigate to directory
```
cd /tmp/documenso
```
```
npm i
```
```
npm run build
```
```
npm run prisma:migrate-deploy
```
## Signing certificate 

I used the default signing certificate for testing. 
Default signing certificate is located here

```
cd /tmp/documenso/apps/remix/example/cert.p12
```
Edit .env file
```
vi /tmp/documenso/.env
```
Add this full path to the .env file.

```
NEXT_PRIVATE_SIGNING_LOCAL_FILE_PATH=/tmp/documenso/apps/remix/example/cert.p12
```
Leave NEXT_PRIVATE_SIGNING_PASSPHRASE setting blank.

Navigate to directory
```
cd /tmp/documenso/apps/remix
```
```
npm run start
```

Testing Note:
 
* Upload PDF file.
* General Section click Continue.
* Add Signers Email and Name.
* Drop down box  next to Name select Needs  to approve.
* Add fields section , select Signature. then click Continue.
* Distribute Document section  fill out required fields and click send.
* Click the email link for approve. On the Approve Document section click the Green Approve button.
* Window pops open then click approve button.
* Stay on that page and after ten seconds it will show Everyone has signed.
