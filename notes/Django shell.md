python manage.py shell
from myapp.models import Book



new_book = Book(title="My New Book", author="Author Name")
new_book.save()  # Сохраняем новый объект в базе данных



# Получить все книги
books = Book.objects.all()

# Получить одну книгу по ID
book = Book.objects.get(id=1)

# Получить книги по автору
books_by_author = Book.objects.filter(author="Author Name")

# Получить книги с определенным заголовком
specific_book = Book.objects.filter(title__icontains="New").first()


book = Book.objects.get(id=1)
book.title = "Updated Title"
book.save()  # Сохраняем изменения

book_to_delete = Book.objects.get(id=1)
book_to_delete.delete()  # Удаляем объект из базы

exit()


from pprint import pprint
pprint(books)





[[Django]]