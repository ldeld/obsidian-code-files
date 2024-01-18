Defined in `myapp.py`, correspond to Rails controllers

A set of methods that take a request object as argument, optional url params like id, and must return an HttpResponse object

We use a shortcut method `render` to load and render templates:

```python
from django.shortcuts import render

from .models import Question

def index(request):
    latest_question_list = Question.objects.order_by("-pub_date")[:5]
    context = {"latest_question_list": latest_question_list}
    return render(request, "polls/index.html", context)
```

You can manually raise HttpErrors:
```python
from django.http import Http404
from django.shortcuts import render

from .models import Question

# ...
def show(request, question_id):
    try:
        question = Question.objects.get(pk=question_id)
    except Question.DoesNotExist:
        raise Http404("Question does not exist")
    return render(request, "polls/show.html", {"question": question})
```

There is a shortcut for this pattern (get element or raise 404)

```python
from django.shortcuts import get_object_or_404, render

from .models import Question

# ...
def show(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    return render(request, "polls/show.html", {"question": question})
```