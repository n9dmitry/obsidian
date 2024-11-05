wraps
``````python
import time
2from functools import wraps
3
4def timer_decorator(func):
5    @wraps(func)  # Сохраняем метаданные оригинальной функции
6    def wrapper(*args, **kwargs):
7        start_time = time.time()  # Запоминаем время начала
8        result = func(*args, **kwargs)  # Вызов оригинальной функции
9        end_time = time.time()  # Запоминаем время окончания
10        execution_time = end_time - start_time  # Вычисляем время выполнения
11        print(f"Функция '{func.__name__}' выполнялась {execution_time:.4f} секунд.")
12        return result  # Возвращаем результат
13    return wrapper
14
15@timer_decorator
16def sample_function():
17    """Пример функции, выполняющей длительную операцию."""
18    time.sleep(1)  # Имитация длительной операции
19
20# Вызов декорированной функции
21sample_function()
22
23# Проверка метаданных
24print(sample_function.__name__)  # Вывод: 'sample_function'
25print(sample_function.__doc__)   # Вывод: 'Пример функции, выполняющей длительную операцию.'
```

[[Python]]