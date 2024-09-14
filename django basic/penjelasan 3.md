# Django for Beginners: A Simple Tutorial

Welcome to the world of Django! Django is a popular web framework that makes it easy to build web applications with Python. In this tutorial, we'll guide you through the basic steps of setting up a Django project and creating a simple web page. Don’t worry if you’re not familiar with programming—this tutorial is designed for beginners and will walk you through each step.

## Step 1: Setting Up Your Environment

Before we start, you’ll need to prepare your computer for Django. This involves creating a special space where we can keep all the tools we need for our project. 

1. **Create a New Directory for Your Project:**
   ```bash
   mkdir hellodjango
   cd hellodjango
   ```
   This command creates a folder called `hellodjango` and then moves into it. This folder will hold all the files for your project.

2. **Set Up a Virtual Environment:**
   ```bash
   virtualenv .venv
   source .venv/bin/activate
   ```
   A virtual environment is like a separate workspace where we can install Python packages without affecting other projects. The first command creates this workspace, and the second command activates it.

3. **Install Django:**
   ```bash
   pip install django
   ```
   This command installs Django, the tool we’ll use to build our web application.

## Step 2: Creating Your Django Project

Now that we have Django installed, we can create a new project.

1. **Start a New Django Project:**
   ```bash
   django-admin startproject hellodjango
   ```
   This command sets up a basic Django project structure in a folder named `hellodjango`.

2. **Apply Initial Database Migrations:**
   ```bash
   python manage.py migrate
   ```
   This command sets up the database that Django will use to store data. Think of it as setting up the initial structure for storing your web app’s information.

3. **Create a Superuser:**
   ```bash
   python manage.py createsuperuser
   ```
   This command creates an admin account that lets you manage your website through a special admin interface.

4. **Start a New App:**
   ```bash
   python manage.py startapp homepage
   ```
   In Django, an app is a component of your project that handles a specific piece of functionality. We’re creating an app called `homepage` for this tutorial.

## Step 3: Building Your Web Page

1. **Create a Directory for Templates:**
   ```bash
   mkdir templates
   ```
   This folder will hold the HTML files for your website’s design.

2. **Add HTML Content:**
   Create a file called `index.html` inside the `templates` folder with the following content:
   ```html
   <h1>Greetings</h1>
   <p>Hello, world!</p>
   <p>{{ my_statement }}</p>
   <p>{{ view.say_bye }}</p>
   ```
   This HTML file is the template for your web page. It contains placeholders (like `{{ my_statement }}`) where dynamic content will be inserted later.

3. **Update the Settings File:**
   Open `hellodjango/settings.py` and find the `TEMPLATES` setting. Modify it to include the `templates` directory:
   ```python
   'DIRS': [BASE_DIR / "templates", ],
   ```
   This tells Django where to find your HTML files.

4. **Set Up Views:**
   Open `homepage/views.py` and replace its content with:
   ```python
   from django.views.generic import TemplateView

   class HomepageView(TemplateView):
       template_name = 'index.html'
       
       def get_context_data(self, **kwargs):
           context = super().get_context_data(**kwargs)
           context['my_statement'] = 'Nice to see you!'
           return context
       
       def say_bye(self):
           return 'Goodbye'
   ```
   This code defines a view that will handle requests to your website’s homepage. It tells Django to use `index.html` as the template and provides dynamic content like `my_statement` and `say_bye`.

5. **Update URLs:**
   Open `hellodjango/urls.py` and add the following code:
   ```python
   from homepage.views import HomepageView

   urlpatterns = [
       path('', HomepageView.as_view(), name='home'),
   ]
   ```
   This sets up a route so that when someone visits your site’s homepage, Django will use the `HomepageView` to generate the page.

## Step 4: Running Your Website

1. **Start the Development Server:**
   ```bash
   python manage.py runserver
   ```
   This command starts a local server on your computer. You can view your website by opening a web browser and going to `http://127.0.0.1:8000/`.

Congratulations! You’ve just built a basic Django website. If you visit the URL provided, you should see a page with the message "Hello, world!" and the dynamic content we set up.

Feel free to explore Django further and build more features. Happy coding!