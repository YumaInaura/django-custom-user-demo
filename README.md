# django-custom-user-demo

django で AbstractUser でカスタムユーザーを作ってマイグレーションするまでの最終手順のデモ

# Comands


```
django-admin startproject some
cd some

./manage.py startapp users
```

# users/models.py


```py
from django.db import models

from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
```

# some/settings.py

```diff
+ AUTH_USER_MODEL = 'user.User'
```

```diff
INSTALLED_APPS = [
+    'users.apps.UsersConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]

```


# users/admin.py

```py
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .models import User

admin.site.register(User, UserAdmin)
```

# Comands

```
./manage.py makemigrations
./manage.py migrate
```

# コード差分はPRに保存

[Custom user by YumaInaura · Pull Request #1 · YumaInaura/django-custom-user-demo](https://github.com/YumaInaura/django-custom-user-demo/pull/1)
