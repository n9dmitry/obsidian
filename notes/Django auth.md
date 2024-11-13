
```python
from django.contrib.auth import authenticate, login
2
3# В представлении
4def login_view(request):
5    if request.method == 'POST':
6        username = request.POST['username']
7        password = request.POST['password']
8        user = authenticate(request, username=username, password=password)
9        if user is not None:
10            login(request, user)
11            # Перенаправление после успешного входа
12        else:
13            # Обработка неверных учетных данных
14
```

