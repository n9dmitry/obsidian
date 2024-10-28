Сериализаторы
```python
from rest_framework import serializers
2from .models import Book
3
4class BookSerializer(serializers.ModelSerializer):
5    class Meta:
6        model = Book
7        fields = ['id', 'title', 'author', 'published_date']
```
Вьюха
```python
from rest_framework import viewsets
2from .models import Book
3from .serializers import BookSerializer
4
5class BookViewSet(viewsets.ModelViewSet):
6    queryset = Book.objects.all()
7    serializer_class = BookSerializer
```

Миксины
Круд

```python
from rest_framework import mixins, viewsets
2
3class CRUDMixin(mixins.CreateModelMixin,
4                 mixins.ListModelMixin,
5                 mixins.RetrieveModelMixin,
6                 mixins.UpdateModelMixin,
7                 mixins.DestroyModelMixin,
8                 viewsets.GenericViewSet):
9    pass
```

```python
class BookViewSet(CRUDMixin):
10    queryset = Book.objects.all()
11    serializer_class = BookSerializer
```




[[Django]]