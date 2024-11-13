
Правка миграции
```
```python
from django.db import migrations, models
2
3
4class Migration(migrations.Migration):
5
6    initial = True
7
8    dependencies = [
9        # Указываем зависимости от других миграций, если есть
10        # ('app_name', 'previous_migration_name'),
11    ]
12
13    operations = [
14        # Создание новой модели Author
15        migrations.CreateModel(
16            name='Author',
17            fields=[
18                ('id', models.AutoField(auto_created=True, primary_key=True, serialize=False, verbose_name='ID')),
19                ('name', models.CharField(max_length=100)),
20                ('birthdate', models.DateField(null=True, blank=True)),
21            ],
22        ),
23        
24        # Изменение модели Book
25        migrations.AddField(
26            model_name='book',
27            name='author',
28            field=models.ForeignKey(
29                to='app_name.Author',  # Замените 'app_name' на имя вашего приложения
30                on_delete=models.CASCADE,
31                null=True,
32                blank=True,
33            ),
34        ),
35
36        # Добавление индекса на поле name в Author
37        migrations.AddIndex(
38            model_name='author',
39            index=models.Index(fields=['name'], name='author_name_idx'),
40        ),
41
42        # Пример для изменения существующего поля в модели Book
43        migrations.AlterField(
44            model_name='book',
45            name='title',
46            field=models.CharField(max_length=200),
47        ),
48    ]
```
```








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