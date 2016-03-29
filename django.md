# Django

## Create contenttypes and permissions for new models
```python
from django.db.models import get_app, get_models
from django.contrib.auth.management import create_permissions
app = get_app('my_app')
update_contenttypes(app, get_models())
create_permissions(app, get_models(), 0)
```
