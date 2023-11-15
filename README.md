Subindo as paradas:

```
docker-compose build
docker-compose up -d
```
```

No vscode, com extensão docker, clicar em attach shell, depois subir o Ambiente virtual:

```
cd django
python -m venv ./venv
source venv/bin/activate
pip install django
```

### O que foi feito neste projeto

Criado o projeto e um app chamadp person:

```
django-admin startproject setup .
python manage.py startapp person
```

Em setup/settings.py:

```
ALLOWED_HOSTS = ['0.0.0.0']
LANGUAGE_CODE = 'pt-br'
TIME_ZONE = 'America/Sao_Paulo'
```

Model criado em person/models.py:

```
from django.db import models

class Person(models.Model):
    name = models.CharField(max_length=100)
    description = models.TextField()
    age = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return self.name
```

Incluir app *person* no setup/settings.py:

```
INSTALLED_APPS = [
    ...,
    'person',
]
```

Criando tabela Person:

```
python manage.py makemigrations
python manage.py migrate
```

Em person/admin.py

```
from django.contrib import admin
from person.models import Person

admin.site.register(Person)
```

Criado um usuário super admin:

```
python manage.py createsuperuser
```

Cadastrar pessoas usando http://0.0.0.0:7000/admin depois de subir o server:


```
python manage.py runserver 0.0.0.0:7000
```


