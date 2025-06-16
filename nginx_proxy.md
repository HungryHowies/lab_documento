### Nginx configuration
* Ningix is on 192.168.1.100
* Documenso is on 192.168.1.200
* Latest version of Documenso 1.11.0
Create self-signed certificates for Nginx.
```
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/netbox.key -out /etc/ssl/certs/netbox.crt
```

```
server {
        if ($host = 192.168.1.100) {
        return 301 https://$host$request_uri;
}
        listen 80;
        server_name 192.168.1.100;
        return 404;
}
server {
    listen 443 ssl;
    server_name 192.168.1.100;
    ssl_certificate /etc/ssl/certs/netbox.crt;
    ssl_certificate_key /etc/ssl/private/netbox.key;
    #add_header 'Content-Security-Policy' 'upgrade-insecure-requests';
    location / {
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_pass http://192.168.1.200:3000;

    }

}
```
### Documenso  Configurations

```
# [[URLS]]
## The Public address should be the IP address or FQDN of the Proxy server.
NEXT_PUBLIC_WEBAPP_URL="https://192.168.1.100"
## URL used by the web app to request itself (e.g. local background jobs)
