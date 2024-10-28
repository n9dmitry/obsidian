
### Определение модели
```python
from django.db import models
2
3class Book(models.Model):
4    title = models.CharField(max_length=100)
5    author = models.CharField(max_length=100)
6    published_date = models.DateField()
7    isbn = models.CharField(max_length=13)
8
9    def __str__(self):
10        return self.title
```

```bash
python manage.py makemigrations
2python manage.py migrate
```

Использование orm
создание
```python
book = Book(title="Война и мир", author="Лев Толстой", published_date="1869-01-01", isbn="1234567890123")
2book.save()
```
получение всех
```python
books = Book.objects.all()
2for book in books:
3    print(book)
```
получение конкретной
```python
tolstoy_books = Book.objects.filter(author="Лев Толстой")
2
```
получение по id
```python
book = Book.objects.get(id=1)
2print(book)
```
обновление
```python
book = Book.objects.get(id=1)
2book.title = "Новая версия Войны и мира"
3book.save()
```
удаление книги
```python
book = Book.objects.get(id=1)
2book.delete()
```



[[Django]]