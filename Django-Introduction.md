# How to start Django Project from scratch - minimum required
## TO INSTALL PYTHON:
###### Check if it's already installed:
>`python --version`

If not installed or you want to update, go to **[python.org](https://www.python.org/downloads/)**. (2.7.something should be automatically installed on Mac.)

#### NOTE:
You need to decide which version of Python you want to use. [Helpful Resource](https://wiki.python.org/moin/Python2orPython3).

***

#### Next:
###### Install pip *[(Python Package Installer)](https://pip.pypa.io/en/stable/)* :
Check if you already have it:
>`pip --version`

If not installed, download **[here](https://pip.pypa.io/en/stable/installing/#installing-with-get-pip-py/)**.

Then go to containing folder in terminal, and type:
>`sudo python get-pip.py`

*OR update using:*
>`pip install -U pip`

***
### TO INSTALL DJANGO:
>`sudo pip install Django`  or `sudo pip install django==version_number` (e.g. `1.9`, most recent)

Check installation with:
>`django-admin --version`

***
## TO START DJANGO PROJECT:
Go to folder where you want project to go, type:

>`django-admin startproject projectname`

Now go into project folder, should see a file with the name **projectname** and a **manage.py** file.

You can type `python manage.py` to see available subcommands.

Now to run server type:
>`python manage.py runserver` (this provides web server for development of Django project)

To check that it worked, visit: http://127.0.0.1:8000/ (**for local**)

___
#### Hopefully now you will say....
## It's aliiiive!!
___

### STARTING AN APP:
Go to your Django project directory (e.g. user/workspace/projectname), i.e. folder where manage.py is located.

Type:
>`python manage.py startapp appname`

Check that it's in folder, alongside (for example) the **manage.py**, the **projectname** file, and a database file (such as **db.sqlite3**).

###### \* Note: you will now have to go into **projectname/settings.py** (NOT in the app folder) to add your app(s) to the INSTALLED_APPS list.

Look for the declaration `INSTALLED_APPS`. It should now look something like:

```
INSTALLED_APPS = (
  'django.contrib.admin',
  '...',
  'django.contrib.staticfiles',
  'appname', <-- this is where you're adding your app
                        (don't forget trailing comma)
)
```

Save.

---

#### Some definitions:
- **Django *APP*** = folder with Python files
  - More like a component than entire application
  - has specific role/purpose
- **Django project** = overall program
  - Can contain one or more apps

#### All in all, your directory structure will look something like this:
(Within say your `Practicing Django` folder)
```
├── projectname             <-- project root (what you check into Git)
│   ├── projectname           <-- Django project root
│   │   ├── \__init__\.py
│   │   ├── settings.py
│   │   ├── urls.py
│   │   └── wsgi.py
│   ├── manage.py
│   └── appname
│   │   ├── \__init__\.py
│   │   ├── admin.py
│   │   ├── migrations
│   │   ├── models.py
│   │   ├── tests.py
│   │   ├── views.py
│   │   ├── forms      <-- you would add later
│   │   ├── templates    <-- you would add later
│   │   └── ...
│   ├── db.sqlite3  <-- or some other DB
│   ├── ...

... = add more later if necessary
```


#### Now, what do those files in your Django project (within *top* folder called projectname) mean?
1. **projectname/\__init__\.py** -- *DO NOT EDIT*
  - tells Django where project folder is
2. **manage.py** -- *DO NOT EDIT*
  - runs Commands
3. **projectname/wsgi.py** -- *DO NOT EDIT*
  - provides hook for web servers
4. **projectname/settings.py**
  - configures Django
5. **projectname/urls.py**
  - routes request based on URL

#### Within the Django app, you should have the following files:
1. **\__init__\.py**
2. **admin.py**
  - administrative interface
4. **migrations** *folder*
  - holds migration files
5. **models.py**
  - data layter
6. **tests.py**
   - tests the app
8. **views.py**
  - control layer

#### Useful Commands:
> `python manage.py runserver`
>
 `python manage.py createsuperuser`
  - will have to enter username, email address, and password
  - run the server again (see command above) and visit http://127.0.0.1:8000/admin/ (**for local**). Try it out with your admin information.

>`python manage.py makemigrations`
  - tells Django that you’ve made some changes to your models (or you’ve made new ones) and that you’d like to store them as a migration
*Note*: Migrations are how Django stores changes to your models

>`python manage.py migrate`
  - run this after `makemigrations`
  - creates model tables in your database, synchronizes changes you've made with the existing schema in the database.

#### Settings you will probably change throughout a project:
  - `INSTALLED_APPS`
    - When adding/removing/renaming (new) Django apps
  -  `TEMPLATES`
    - When adding templates for the first time
  -  `STATIC_DIRS`
    - When adding static assets (e.g. CSS/JavaScript) for the first time
  - `DEBUG`
    - Set to false when deploying to production
  - `DATABASES`
    - When changing engines and name entries
    - Need to set user/password entries for authentication

##### Other Stuff:
+ [python packages](https://docs.python.org/3/installing/)
+ views.py --> program logic. Takes http web request, turns it into http response
+ [Django documentation](https://docs.djangoproject.com/en/1.9/)
+ [Another Django tutorial](http://www.tangowithdjango.com/) -- only for Django 1.7/Python 2.7
