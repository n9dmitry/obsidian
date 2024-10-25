
```nginx
server {
2    listen 80;
3    server_name example.com;  # Укажите ваше доменное имя или IP адрес
4
5    location / {
6        root /var/www/html;  # Укажите путь к директории с файлами
7        index index.html index.htm;
8    }
9
10    location /api {
11        proxy_pass http://backend_server:5000;  # Проксирование на сервер приложений
12        proxy_set_header Host $host;  # Установить заголовок Host
13        proxy_set_header X-Real-IP $remote_addr;  # Передать IP клиента
14        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
15    }
16
17    error_page 404 /404.html;  # Обработка ошибок
18    location = /404.html {
19        internal;
20    }
21}
```

[[Python]]