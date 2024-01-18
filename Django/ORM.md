Defined in the `models.py` file

Example: 
```python
from django.db import models

class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField("date published")

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```


Generate migrations
```
python manage.py makemigrations myapp
```

Run migration
```
python manage.py migrate
```


Much like Rails, you can add custom instance methods

Basic commands (see [[Advanced ORM]] for more)

```python
Question.objects.all()

Question.objects.filter(id=1) # Equivalent to .where, returns Queryset

question = Question.objects.get(pk=1) # Equivalent to .find

question.choice_set.all() # Equivalient to question.choices

question.choice_set.create(choice_text="The sky", votes=0)


# The API automatically follows relationships as far as you need.
# Use double underscores to separate relationships.
# This works as many levels deep as you want; there's no limit.
# Find all Choices for any question whose pub_date is in this year
# (reusing the 'current_year' variable we created above).
Choice.objects.filter(question__pub_date__year=2022)
```