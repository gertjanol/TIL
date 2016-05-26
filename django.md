# Django

## Create contenttypes and permissions for new models
### Django < 1.9
```python
from django.db.models import get_app, get_models
from django.contrib.auth.management import create_permissions
app = get_app('my_app')
update_contenttypes(app, get_models())
create_permissions(app, get_models(), 0)
```
### Django >= 1.9
```python
from django.apps import apps
from django.contrib.auth.management import create_permissions
from django.contrib.contenttypes.management import update_contenttypes

app_config = apps.get_app_config('my_app')
update_contenttypes(app_config)
create_permissions(app_config)
```
