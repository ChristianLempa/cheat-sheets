# nginx cheatsheet

Nginx is a web server that can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache. The software was created by Igor Sysoev and publicly released in 2004. Nginx is free and open-source software, released under the terms of the 2-clause BSD license. A large fraction of web servers use Nginx, often as a load balancer.

## External

- https://rtfm.co.ua/en/http-redirects-post-and-get-requests-and-lost-data/
- [Nginx Location Priority](https://stackoverflow.com/questions/5238377/nginx-location-priority)

## Configs

Bare bones website:

```
server {
    listen       80;
    server_name  localhost;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

}
```

Redirect non existing webpage to home:

```
    # define the error page
    error_page 404 = @notfound;

    # 301 redirect to / for defined error page
    location @notfound {
        return 301 /;
    }
```

Redirect a old request url to a new path on disk:

```
    # redirect old urls
    location /content/images/2019/10/logo.png {
        rewrite ^/content/images/2019/10/logo.png /assets/img/logo.png ;
    }
```
