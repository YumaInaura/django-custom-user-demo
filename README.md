# django-custom-user-demo

django で AbstractUser でカスタムユーザーを作ってマイグレーションするまでの最終手順のデモ

# Commands

```
django-admin startproject some
cd some

./manage.py startapp users

vim users/models.py
vim some/settings.py
vim users/admin.py

./manage.py makemigrations
./manage.py migrate
```
