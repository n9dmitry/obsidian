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
5    build: .
6    ports:
7      - "5000:5000"
8
```

[[Python]]