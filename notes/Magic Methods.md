
```
### В Python

1. **Общие магические методы**:
    
    - `__init__(self, ...)`: конструктор класса.
    - `__str__(self)`: строковое представление объекта, используется в функции `print`.
    - `__repr__(self)`: формальное представление объекта, используется для отладки.
    - `__len__(self)`: возвращает длину объекта (например, для списков).
    - `__getitem__(self, key)`: позволяет использовать индексацию (например, `obj[key]`).
    - `__setitem__(self, key, value)`: позволяет задавать значения по индексу.
2. **Сравнение и арифметика**:
    
    - `__eq__(self, other)`: определяет оператор `==`.
    - `__ne__(self, other)`: определяет оператор `!=`.
    - `__lt__(self, other)`: определяет оператор `<`.
    - `__gt__(self, other)`: определяет оператор `>`.
    - `__add__(self, other)`: определяет оператор `+`.
    - `__sub__(self, other)`: определяет оператор `-`.
3. **Итерация**:
    
    - `__iter__(self)`: делает объект итерируемым.
    - `__next__(self)`: возвращает следующий элемент итератора.

### В Django

Дjango также использует множество магических методов, особенно в моделях и представлениях:

1. **Модели**:
    
    - `__str__(self)`: строковое представление экземпляра модели.
    - `save(self, *args, **kwargs)`: метод, вызываемый при сохранении объекта.
    - `delete(self, using=None)`: метод для удаления объекта.
    - `get_absolute_url(self)`: возвращает URL для доступа к конкретному объекту.
2. **Формы**:
    
    - `clean(self)`: метод для валидации данных формы.
    - `save(self, commit=True)`: сохраняет данные формы в базу данных.
3. **Представления**:
    
    - `dispatch(self, request, *args, **kwargs)`: метод, служащий точкой входа для обработки запросов.
```

[[Python]]