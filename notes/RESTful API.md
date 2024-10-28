`http://127.0.0.1:8000/api/items/`

Создание RESTful API с использованием Django Rest Framework (DRF) включает несколько шагов. Вот основные из них:

1. **Установка Django и DRF**: Сначала установите Django и Django Rest Framework, если они ещё не установлены:
    
    bash
    
    ```bash
    1pip install django djangorestframework
    2
    ```
    
2. **Создание нового проекта и приложения**: Создайте новый проект Django и приложение для вашего API:
    
    bash
    
    ```bash
    1django-admin startproject myproject
    2cd myproject
    3django-admin startapp myapp
    4
    ```
    
3. **Настройка приложения**: В файле `settings.py` добавьте `rest_framework` и ваше приложение в список `INSTALLED_APPS`:
    
    python
    
    ```python
    1INSTALLED_APPS = [
    2    ...
    3    'rest_framework',
    4    'myapp',
    5]
    6
    ```
    
4. **Создание моделей**: Определите модели в файле `models.py` вашего приложения:
    
    python
    
    ```python
    1from django.db import models
    2
    3class Item(models.Model):
    4    name = models.CharField(max_length=100)
    5    description = models.TextField()
    6
    7    def __str__(self):
    8        return self.name
    9
    ```
    
5. **Создание сериализаторов**: Создайте файл `serializers.py` и напишите сериализатор для вашей модели:
    
    python
    
    ```python
    1from rest_framework import serializers
    2from .models import Item
    3
    4class ItemSerializer(serializers.ModelSerializer):
    5    class Meta:
    6        model = Item
    7        fields = '__all__'
    8
    ```
    
6. **Создание представлений**: В файле `views.py` создайте представления для вашего API:
    
    python
    
    ```python
    1from rest_framework import generics
    2from .models import Item
    3from .serializers import ItemSerializer
    4
    5class ItemList(generics.ListCreateAPIView):
    6    queryset = Item.objects.all()
    7    serializer_class = ItemSerializer
    8
    9class ItemDetail(generics.RetrieveUpdateDestroyAPIView):
    10    queryset = Item.objects.all()
    11    serializer_class = ItemSerializer
    12
    ```
    
7. **Настройка маршрутов**: В файле `urls.py` вашего приложения настройте маршруты для API:
    
    python
    
    ```python
    1from django.urls import path
    2from .views import ItemList, ItemDetail
    3
    4urlpatterns = [
    5    path('items/', ItemList.as_view(), name='item-list'),
    6    path('items/<int:pk>/', ItemDetail.as_view(), name='item-detail'),
    7]
    8
    ```
    
    Затем добавьте маршруты вашего приложения в `urls.py` проекта:
    
    python
    
    ```python
    1from django.contrib import admin
    2from django.urls import path, include
    3
    4urlpatterns = [
    5    path('admin/', admin.site.urls),
    6    path('api/', include('myapp.urls')),
    7]
    8
    ```
    
8. **Миграция и запуск сервера**: Создайте миграции и примените их:
    
    bash
    
    ```bash
    1python manage.py makemigrations
    2python manage.py migrate
    3
    ```
    
    Запустите сервер:
    
    bash
    
    ```bash
    1python manage.py runserver
    2
    ```
    

Теперь ваше RESTful API готово к использованию! 🎉 Вы можете отправлять запросы к вашим эндпоинтам (например, `http://127.0.0.1:8000/api/items/` для получения списка предметов). Если у вас есть вопросы или вы хотите узнать больше, дайте знать! 😊


[[Django Rest Framework DRF]]