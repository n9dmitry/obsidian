wraps

=================================================================

```python
from functools import wraps
2
3def my_decorator(func):
4    @wraps(func)  # Сохраняем метаданные оригинальной функции
5    def wrapper(*args, **kwargs):
6        print("Перед вызовом функции")
7        result = func(*args, **kwargs)  # Вызов оригинальной функции
8        print("После вызова функции")
9        return result
10    return wrapper
11
12@my_decorator
13def say_hello(name):
14    """Выводит приветствие."""
15    print(f"Привет, {name}!")
16
17say_hello("Мир")
18print(say_hello.__name__)  # Выведет 'say_hello'
19print(say_hello.__doc__)   # Выведет 'Выводит приветствие.'
```






[[Python]]