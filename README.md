# nginx-sheet
To not do the same thing again twice

## Proxy reverse (localhost)
### If using Centos after installing nginx you need to create these files:
#### 1. /etc/nginx/sites-available/default
### Content:
```
server {
    listen       80;
    listen      [::]:80;
    server_name  localhost;
    client_max_body_size 10M;

    #charset koi8-r;

    #access_log  logs/host.access.log  main;

    location / {
        proxy_pass http://localhost:1338;
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection 'upgrade';
proxy_set_header Host $host;
proxy_cache_bypass $http_upgrade;
    }
}
```

#### 2. /etc/nginx/sites-enabled/default

```include sites-available/default;```

### After that just restart it:
```sudo systemctl restart nginx```
