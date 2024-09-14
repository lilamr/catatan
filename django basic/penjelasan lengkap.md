//We started off with a barebones Django project that we generated with django-admin startproject. We created a database and started up Django’s development server.  
  
Then we created a Django superuser so that we could access the Django admin. We explored the admin UI.  
  
Next, we added a simple Django app to the project. We called it “homepage” and explored what files it gave us to start with.  
  
After that, we learned about views and templates in Django. We created our first view by subclassing TemplateView. We connected it to a URL pattern and a simple static HTML template.  
  
Finally, we turned the static HTML template into a dynamic one. We learned how to put variables into the template and populate them in our Python code. We also learned how to call view methods from our template.//  
  
========================================  
  
$ mkdir hellodjango  
$ cd hellodjango  
$ virtualenv .venv  
$ source .venv/bin/activate  
  
$ pip install django  
  
$ python -m django --version  
  
$ django-admin startproject hellodjango  
  
//This creates a minimal Django project called hellodjango. Type ls to check that there’s now a hellodjango directory in our current working directory.//  
  
$ code hellodjango  
  
//  
hellodjango  
├── hellodjango  
│├── [__init__.py](http://__init__.py)  
│├── [asgi.py](http://asgi.py)  
│├── [settings.py](http://settings.py)  
│├── [urls.py](http://urls.py)  
│└── [wsgi.py](http://wsgi.py)  
└── [manage.py](http://manage.py)  
//  
  
//[manage.py](http://manage.py) module is something we call to run various Django commands. For most Django projects this code is never touched.//  
  
//[settings.py](http://settings.py) module is much larger than the [manage.py](http://manage.py) module. It’s where we can globally change Django’s behavior via settings. These settings are special variables identified by their UPPERCASE nature. All formally defined settings must be UPPERCASE and are considered to be constants. In the future we’ll modify these settings to empower our projects to do great things.//  
  
$ cd hellodjango  
  
$ ls  
  
//  
hellodjango  
[manage.py](http://manage.py)  
//  
  
$ python [manage.py](http://manage.py) migrate  
  
//When we run the migrate command for the first time, a database gets created, and some starter tables in the database are set up.//  
  
$ ls  
  
//  
db.sqlite3  
hellodjango  
[manage.py](http://manage.py)  
//  
  
$ python [manage.py](http://manage.py) runserver  
  
//This means that the development server is now running on our computer.//  
  
http://127.0.0.1:8000  
  
//In order to log into the Django admin, we need to create a Django superuser. If runserver is still running, use CTRL-c to stop it.//  
  
$ python [manage.py](http://manage.py) createsuperuser  
  
//Enter a username, email, and password for our Django superuser.//  
  
//We just created a superuser for a Django project. Out of the box this superuser has access to Django’s admin tool. This allows them to make changes to database records, including the user list.//  
  
$ python [manage.py](http://manage.py) runserver  
  
http://127.0.0.1:8000/admin/  
  
//Enter the Django superuser’s username “admin” and password now. Then click “Log In”.//  
  
========================================  
  
Recreate the database:  
  
//At the command-line, type ctrl-c. This should stop the server.//  
  
//In Visual Studio Code, find and right-click on the db.sqlite3 database file. Choose the Delete option.//  
  
$ python [manage.py](http://manage.py) migrate  
  
$ python [manage.py](http://manage.py) createsuperuser  
  
========================================  
  
$ python [manage.py](http://manage.py) startapp homepage  
  
//Use the startapp management command to create a new Django app called homepage. The startapp command created a new directory in our project called homepage.//  
  
//If this doesn’t work, double-check that we’re still inside the outer hellodjango project directory, at the same level as manage.py.//  
  
$ code hellodjango  
  
//  
hellodjango  
├── db.sqlite3  
├── hellodjango  
│├── [__init__.py](http://__init__.py)  
│├── [asgi.py](http://asgi.py)  
│├── [settings.py](http://settings.py)  
│├── [urls.py](http://urls.py)  
│└── [wsgi.py](http://wsgi.py)  
├── homepage  
│├── [__init__.py](http://__init__.py)  
│├── [admin.py](http://admin.py)  
│├── [apps.py](http://apps.py)  
│├── migrations  
││└── [__init__.py](http://__init__.py)  
│├── [models.py](http://models.py)  
│├── [tests.py](http://tests.py)  
│└── [views.py](http://views.py)  
└── [manage.py](http://manage.py)  
//  
  
//• A Django project is a folder containing all the code (Python, templates, etc.) needed to run a website.  
• A Django app is a folder within a Django project.  
• Django apps are isolated components that do one specific thing in a Django project.  
• Combining Django apps is one of the primary things we do when we build a Django project.//  
  
//Before we can start writing views that use templates, we need to modify our project’s settings.//  
  
//Search the [settings.py](http://settings.py) module for the TEMPLATES setting. It’s a list of dictionaries.//  
  
//Notice how DIRS is an empty list. We can change that to specify where we want Django to look for templates. Go ahead and modify that slightly, by adding BASE_DIR / "templates", to the DIRS list.//  
  
`'DIRS': [BASE_DIR / "templates", ],  
  
//This change tells Django to look inside a templates directory within the base directory of our project, which we’ll create later.//  
  
========================================  
  
[https://docs.python.org/3/tutorial/introduction.html#lists](https://docs.python.org/3/tutorial/introduction.html#lists)  
  
//In Python, a list consists of comma-separated values wrapped in square brackets.//  
  
`['Ice cream!', 2, 'cones', 3, 4]  
  
[https://docs.python.org/3.8/tutorial/datastructures.html#dictionaries](https://docs.python.org/3.8/tutorial/datastructures.html#dictionaries)  
  
//Python Dictionary is a set of key: value pairs.//  
  
```
{  
'vanilla': 'vainilla',  
'chocolate mint': 'choco menta',  
'coffee': 'café',  
}  
```

========================================  
  
//To add a Simple Homepage View, open the [views.py](http://views.py) file of the homepage app. Remove the code that is there and replace it with the following.//  

```
from django.views.generic import TemplateView  
  
class HomepageView(TemplateView) :  
template_name = 'index.html'  
```

//• We created the Python class HomepageView  
• HomepageView subclassed TemplateView. Django comes with a number of built-in views, which we can inherit from. We use these built-in views throughout the rest of this book  
• Associated the index.html template with the class.//  
  
//In the same inner hellodjango directory containing settings.py, there’s also a file called [urls.py](http://urls.py) that associate the Django view we just wrote with a web location on our site.//  
  
//Notice that it defines a list of urlpatterns.//  
  
//Right now, there’s only one item in the urlpatterns list: a URL pattern for admin/. That corresponds to the Django admin UI, which we saw earlier. When a browser requests a page starting with admin/ (i.e. matching the regular expression 'admin/'), it gets routed by the server to admin.site.urls. In a typical Django project, this file will be full of URL routes. But it starts almost empty.//  
  
//To add a URL Pattern for the Homepage First, import HomepageView into [urls.py](http://urls.py). Right below the Django imports in urls.py, add this line.//  
  
`from homepage.views import HomepageView  
  
//Then add this URL pattern to the urlpatterns list, right after the one for the Django admin.//  
  
`path('', HomepageView.as_view(), name='home'),  
  
//• When a browser requests a page matching the blank value of '/' (that is, the root at http://127.0.0.1:8000)  
• Route it to HomepageView.as_view().  
• And name this route home.//  
  
$ python [manage.py](http://manage.py) runserver  
  
http://127.0.0.1:8000  
  
TemplateDoesNotExist at /  
  
//If we see that above error, we are doing it right! Specifically, our view is correctly wired into the [urls.py](http://urls.py) module, but its template, index.html, doesn’t exist yet.//  
  
//Templates are what Django uses to generate the HTML that is shown in browsers.//  
  
//At the same level as manage.py, create a templates directory.//  
  
$ mkdir templates  
  
//  
hellodjango/  
├── hellodjango/  
├── homepage/  
├── templates/  
└── [manage.py](http://manage.py)  
//  
  
//Inside of templates/, create a file called index.html. As of now, this is just plain HTML.//  
  
```
<h1>Greetings</h1>  
<p>Hello, world!</p>  
```

$ python [manage.py](http://manage.py) runserver  
  
//• Our browser requests http://127.0.0.1:8000  
• Django’s development server looks up where to route the request  
• Since the index was requested, it matches the path of ''  
• Therefore the matching URL pattern is:  
path('', HomepageView.as_view(), name='home'),  
• HomepageView is the view corresponding to that URL:  
class HomepageView(TemplateView):  
template_name = 'index.html'  
• It’s a TemplateView, so it renders its template and returns the result  
• We see the page in the browser!//  
  
//• Views are how a Django project communicates with the user. They send out web pages, JSON, spreadsheets, PDFs, and so much more.  
• Templates are often used by views to render HTML for web pages.  
• A TemplateView renders a Django template and sends it to a browser.//  
  
//Without variables we would not have a dynamic web application, there would be no way to interact with the data in the database, essentially we would have a standard static website.//  
  
//Right now, templates/index.html is a Django template that only contains static HTML. But it can also contain variables that get populated dynamically from Python code.//  
  
//Open up templates/index.html and add the following line at the end.//  
  
`<p>{{ my_statement }}</p>  
  
//The curly braces around my_statement mean that it won’t be displayed on the page as-is. Instead, it’ll be evaluated on the Python side and then the result will be displayed.//  
  
//At this point we haven’t defined my_statement yet in our Python code. It can be any of the following:  
• A Python expression, such as a string, number, or instantiated object  
• A function or method call.//  
  
//Open up the homepage app’s [views.py](http://views.py). define a view method called get_context_data(). This is a special method that lets you pass variables to your template. Right below template_name = 'index.html', add a blank line. Then below it, add this method to your HomepageView class.//  
  
```
def get_context_data(self, **kwargs):  
    context = super().get_context_data(**kwargs)  
    context['my_statement'] = 'Nice to see you!'  
    return context  
```

//Look carefully at the line involving my_statement. There, you defined a context variable called my_statement. You assigned it the value of Nice to see you!. Note that context is a Python dictionary. my_statement is a key, and Nice to see you! is its corresponding value.//  
  
========================================  
  
[https://stackoverflow.com/questions/3786881/what-is-a-method-in-python](https://stackoverflow.com/questions/3786881/what-is-a-method-in-python)  
  
//A method is a Python function that’s a member of a class. In our example, get_context_data() is a function that’s a member of the HomepageView class.//  
  
//With Python, indentation is of absolute importance. It is how code blocks are defined. In this case, make certain that get_context_data() is indented from the  
class. Also, the last three lines of the get_context_data() method are indented. This isn’t just a code clarity issue in Python, if it is not done then Python will throw errors.//  
  
========================================  
  
//Go back to the browser, and refresh http://127.0.0.1:8000. (If runserver isn’t still running from before, start it up again.) The value of {{ my_statement }} should now be replaced with Nice to see you!, as shown in the image below or on the next page.//  
  
//The standard Django way to add data to a template’s context is via get_context_data().//  
  
//Here’s an alternative approach. We’re going to add data by calling a method and displaying the result.//  
  
//Add the following say_bye method to the HomepageView class.//  
  
```
def say_bye(self):  
    return 'Goodbye'  
```
  
//Add this to the bottom of our index template.// 

`<p>{{ view.say_bye }}</p>

//Notice something strange: in the template, we call the say_bye() method, but there are no parentheses after it. That’s because Django templates intelligently check to see if something can be called as a method.//  
  
//Go back to the browser, and refresh http://127.0.0.1:8000. We should now see the return value of say_bye() displayed on our homepage.//  
  
//View Method Different From Context Data. It’s the difference between evaluating a variable and evaluating a function call.  
- Context data: Variables used in the template.  
- View methods: Functions that we can call from the template.  
Typically projects rely on Context Data, but there are advanced use cases for using view methods instead.//  
  
//Congratulations! By now we understand what makes up a very minimal Django project. We recommend keeping the hellodjango project we created as a reference project, so we can refer back to it when we need to revisit how Django views, templates, and URL patterns work together.//  