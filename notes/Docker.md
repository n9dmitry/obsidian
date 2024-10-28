```dockerfile
# Используем официальный образ Python
2 FROM python:3.10-slim
3
4# Устанавливаем рабочую директорию
5 WORKDIR /app
6
7# Копируем файл зависимостей в контейнер
8 COPY requirements.txt .
9
10# Устанавливаем зависимости
11 RUN pip install --no-cache-dir -r requirements.txt
12
13# Копируем остальные файлы приложения
14 COPY . .
15
16# Указываем команду по умолчанию
17 CMD ["python", "app.py"]
```

docker-compose.yml
```yaml
version: '3.8'
2
3services:
4  web:
5    image: python:3.9
6    volumes:
7      - .:/app
8    working_dir: /app
9    command: python app.py
10    ports:
11      - "5000:5000"
12    depends_on:
13      - db
14
15  db:
16    image: postgres:13
17    environment:
18      POSTGRES_DB: mydatabase
19      POSTGRES_USER: user
20      POSTGRES_PASSWORD: password
21    volumes:
22      - pg_data:/var/lib/postgresql/data
23
24volumes:
25  pg_data:
``````

[[Python]]