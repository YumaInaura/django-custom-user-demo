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


 # 参考
 

>プロジェクトの開始時にカスタムのユーザーモデルを使用する¶
新しくプロジェクトを始める場合は、デフォルトの User で十分である場合でも、カスタムユーザーモデルを作成>することを強く推奨します。このモデルはデフォルトのユーザーモデルと同様に動作しますが、必要に応じて将来的にカスタマイズすることができます:


[Django の認証方法のカスタマイズ | Django ドキュメント | Django](https://docs.djangoproject.com/ja/2.2/topics/auth/customizing/#using-a-custom-user-model-when-starting-a-project)

---


>カスタムUserを使う場合の注意点
>カスタムUserを使うには、migrationsのinit(0001)時点でカスタムUserを使うことを含めなければならない。

[Djangoでは常にカスタムUserを使用すべき - Qiita](https://qiita.com/NAKKA-K/items/7627b6a22f364941b989)


>すでにmigrateしている場合は、DBを初期化してmakemigrationsし直すのが楽。

---

>アプリケーションを独立させると、他プロジェクトでの再利用性と、アプリケーション単位でダンプファイル操作が可能になるメリットがあります。

>「users」はcookiecutter-djangoでも使われている名前です。こちらで統一するのがよいと思います。
参考：cookiecutter-djangoを使ってみた

[Django ユーザー カスタマイズ方法 - Qiita](https://qiita.com/okoppe8/items/10ae61808dc3056f9c8e)


# その他の参考記事


[DjangoのUserモデルを継承してカスタマイズ | Hornet|静岡拠点のWeb、ホームページ制作](https://hombre-nuevo.com/python/python0048/#h2_1)

[Userモデルのカスタマイズ | Narito Blog](https://narito.ninja/blog/detail/39/)

[Django Best Practices - William Vincent](https://wsvincent.com/django-best-practices/)

[Django マイグレーション まとめ - Qiita](https://qiita.com/okoppe8/items/c9f8372d5ac9a9679396)
 
