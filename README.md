# Flask_WSGI

## Update the Nginx sites-Available default file and add these lines..

```nginx
server {
    listen 80;
    server_name <server_domain>;  # Replace with your domain name or server IP

    location / {
        proxy_pass http://127.0.0.1:8000;  # Assuming Gunicorn is running on port 8000
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-for $proxy_add_x_forwarded_for;
    }
}
```
## Gunicorn wsgi server

``` 
sudo gunicorn -w 4 -b 0.0.0.0:8000 app:app
```
