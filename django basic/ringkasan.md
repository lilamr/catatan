$ mkdir hellodjango
$ cd hellodjango
$ virtualenv .venv
$ source .venv/bin/activate
$ pip install django
$ django-admin startproject hellodjango
$ python manage.py migrate
$ python manage.py createsuperuser
$ python manage.py startapp homepage
$ mkdir templates

hellodjango/settings.py >> add
```
'DIRS': [BASE_DIR / "templates", ],
```

templates/index.html >> add
```
<h1>Greetings</h1>
<p>Hello, world!</p>
<p>{{ my_statement }}</p>
<p>{{ view.say_bye }}</p>
```

homepage/views.py >> replace
```
from django.views.generic import TemplateView

class HomepageView(TemplateView) :
    template_name = 'index.html'
    
    def get_context_data(self, **kwargs):
        context = super().get_context_data(**kwargs)
        context['my_statement'] = 'Nice to see you!'
        return context
        
    def say_bye(self):
        return 'Goodbye'
```

hellodjango/urls.py >> add
```
from homepage.views import HomepageView

path('', HomepageView.as_view(), name='home'),
```

$ python manage.py runserver