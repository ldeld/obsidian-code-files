
In `myapp/urls.py`
```python
from django.urls import path

from . import views

urlpatterns = [
    # ex: /polls/
    path("", views.index, name="index"),
    # ex: /polls/5/
    path("<int:question_id>/", views.detail, name="detail"),
    # ex: /polls/5/results/
    path("<int:question_id>/results/", views.results, name="results"),
    # ex: /polls/5/vote/
    path("<int:question_id>/vote/", views.vote, name="vote"),
]
```

In `mainfolder/urls.py`
```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path("someurl/", include("myapp.urls")),
    path("admin/", admin.site.urls),
]
```
