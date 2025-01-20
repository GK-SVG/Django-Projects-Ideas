# Django Project Nginx Configuration
```shell
server {
        listen 80;
        server_name {server_name};
        return 301 https://$host$request_uri;
    }

    server {
        listen 443 ssl;
        server_name {server_name};

        ssl_certificate /etc/letsencrypt/live/{server_name}/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/{server_name}/privkey.pem;

        client_max_body_size 11M;

        location = /favicon.ico { access_log off; log_not_found off; }

        location /staticfiles/ {
            alias /root/productize-dashboard/;
        }

        location /media/ {
            root /root/productized-dashboard/;
        }

        location / {
            include proxy_params;
            proxy_pass http://unix:/run/gunicorn.sock;
        }

    }
```