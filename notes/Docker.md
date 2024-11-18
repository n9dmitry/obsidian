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



### 1. Docker Volumes

**Docker Volumes** — это способ хранения данных, который позволяет сохранять данные вне контейнеров. Это особенно полезно, когда контейнеры перезапускаются или удаляются, и вы не хотите потерять данные.

- **Создание Volume**:
    
    bash
    
    ```bash
    1docker volume create my_volume
    2
    ```
    
- **Использование Volume в контейнере**:
    
    bash
    
    ```bash
    1docker run -d -v my_volume:/path/in/container my_image
    2
    ```
    
- **Список всех Volume**:
    
    bash
    
    ```bash
    1docker volume ls
    2
    ```
    
- **Удаление Volume**:
    
    bash
    
    ```bash
    1docker volume rm my_volume
    2
    ```

### 2. Docker Networks

**Docker Networks** позволяют контейнерам общаться друг с другом. Существует несколько типов сетей, но самыми распространенными являются bridge и overlay.

- **Создание сети**:
    
    bash
    
    ```bash
    1docker network create my_network
    2
    ```
    
- **Запуск контейнера в сети**:
    
    bash
    
    ```bash
    1docker run -d --network my_network --name my_container my_image
    2
    ```
    
- **Просмотр сетей**:
    
    bash
    
    ```bash
    1docker network ls
    2
    ```
    
- **Удаление сети**:
    
    bash
    
    ```bash
    1docker network rm my_network
    ```

### 3. Dockerfile

**Dockerfile** — это текстовый файл с инструкциями, которые Docker использует для создания образа.

Пример простого Dockerfile:

Dockerfile

```dockerfile
1# Используем базовый образ
2FROM ubuntu:latest
3
4# Установка приложения
5RUN apt-get update && apt-get install -y nginx
6
7# Копируем файлы в образ
8COPY . /usr/share/nginx/html
9
10# Открываем порт
11EXPOSE 80
12
13# Запуск службы
14CMD ["nginx", "-g", "daemon off;"]
15
```

Чтобы создать образ из Dockerfile, используйте:

bash

```bash
1docker build -t my_image .
```

### 4. Docker Compose

**Docker Compose** — это инструмент для работы с многоконтейнерными приложениями. Вы определяете конфигурацию в файле `docker-compose.yml`.

Пример `docker-compose.yml`:

yaml

```yaml
1version: '3'
2services:
3  web:
4    image: nginx
5    ports:
6      - "80:80"
7  
8  db:
9    image: postgres
10    environment:
11      POSTGRES_DB: mydatabase
12      POSTGRES_USER: user
13      POSTGRES_PASSWORD: password
14
```

Для запуска контейнеров по этому файлу, используйте команду:

bash

```bash
1docker-compose up
2
```


[[Python]]