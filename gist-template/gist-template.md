# Introduction-to-Flask-for-Python

## What is Flask?

### History

Flask was created by [Armin Ronacher](https://en.wikipedia.org/wiki/Armin_Ronacher). It is a web-framework that features a rich library to build web applications and APIs and is designed to be used with the Python programming language. It is the second most popular web-framework right behind Django and can be seen as the javascript equivalent to Express. Both Express and Flask provide tools to create C.R.U.D opperations and provide tools to create and manage server logic.

Armin developed Flask along with group that he was a part of known as Pocoo. Pocoo was also responsible for the creation of Werkzeug and Jinja which are some of the components that make up flask.

### Components

**Werkzeug** is a [WSGI](https://wsgi.readthedocs.io/en/latest/what.html) web/utility library for Python that provides a set of tools for building web applications working with HTTP request and responses and meet a set of standards for building web applications using python.

**Jinja** is known as a web template engine for Python it allows developers to create the structural layout of the page using HTML while also incorporating the application's logic that will handle the users interactions and data processing using python-themed syntax. This will make it easier to manage and maintain web application code. Jinja can be seen as the javascript equivalent of Handlebars.js in the same way that they both combine their respective coding language's syntax and logic with the structural code (i.e HTML) used to present the application.

### Installation

- First make sure you have python installed by typing `python --version` in the terminal. If you dont have it installed use this [link](https://www.python.org/downloads/).

- Once python is installed so will [Python Package Index (PyPI)](https://pypi.org/) which is a package manager for python just like npm is for javascript in the same way that that both are expansive libraries and help manage your dependancies (downloaded packages).

Before installing flask its important to understand best practices for using python libraries. By default, installing a Python library installs it globally meaning all future python projects will have the installed packages. However; Python provides a feature called a virtual environment—a self-contained directory that maintains its own version of Python and its own library dependencies. This way, multiple Python projects can reside on the same machine without interfering with each other.

To start the virtual environment run this script on the terminal python `-m venv venv` this will create a file named venv that will make the virtual environment possible. to start the virtual environment run `.\venv\Scripts\activate` if your using Windows or `. venv/bin/activate` for Mac. Once the virtual environment starts you can begin to download your dependencies. 
the folder will look something similar to this.

![](../assets/Flask.png)

If you see `(venv) PS C:\Users\UserName\Desktop\projects\python-project>` in the terminal then you have started the virtual environment successfully. The (venv) signifies that you are now working in a virtual environment so always make sure its there before you begin working. Finally type `pip install flask` to install Flask. This will come with additional files like jinja2 that will allow you to start programming right away.

The folder will look something similar to this.

![flask folder](../assets/flask-folder2.png)

## how to work with Flask

### Set up

once flask is installed you can begin coding. In the root directory (or main folder) of your project, create a new directory called app. In this directory, create a new file called `__init__.py`. That's two underscores on each side. 

**`__init__.py`** is an important file that's used in Python projects, and it is typically found in every directory, including the root directory of a Python package. It serves several key purposes. Firstly, it acts as an entry point to the directory in a similar way that one might use an index.js file in a JavaScript project to define the entry point for a module or package however when the `__init__.py` is in the root directory it can be seen as the server.js equivalent. Secondly, `__init__.py` is essential for Package Initialization. When a package is imported, the `__init__.py` file is executed. This allows you to perform any necessary package initialization tasks, such as setting up variables, importing modules, or defining package functions and classes. Anything you place in the `__init__.py` file is executed when the package is first imported. Here's a sample code example to illustrate its usage:

```
from flask import Flask
from app.routes import home, dashboard, api
from app.db import init_db
from app.utils import filters

def create_app(test_config=None):
  # set up app config
  app = Flask(__name__, static_url_path='/')
  app.url_map.strict_slashes = False
  app.config.from_mapping(
    SECRET_KEY='super_secret_key'
  )
  app.jinja_env.filters['format_url'] = filters.format_url
  app.jinja_env.filters['format_date'] = filters.format_date
  app.jinja_env.filters['format_plural'] = filters.format_plural
  
  @app.route('/hello')
  def hello():
   
   return 'hello world'
  
# register routes
  app.register_blueprint(home)
  app.register_blueprint(dashboard)
  app.register_blueprint(api)
  init_db(app)
  return app
```
#### imports

As soon as `__init__.py` runs it starts to import the necessary modules and packages. it imports flask from Flask, imports home, dashboard, api files from the routes folder which is inside the root folder called app, imports init_db module from db folder which is inside app, and imports the filter file from the utils folder which is inside of the app folder.

####  Create_app()

After its done with the imports it defines a function named create_app() which is used to create and configure the Flask application. It takes an optional test_config parameter, which can be used to configure the application differently for testing purposes. The app object is created with Flask(__name__, static_url_path='/'), which initializes the Flask application. The static_url_path parameter specifies the URL path for serving static files (e.g., CSS, JavaScript).

#### Configuration Settings

These lines configure the Flask application. app.url_map.strict_slashes = False allows routes to match with or without trailing slashes. The app.config.from_mapping() method is used to set configuration variables, such as the SECRET_KEY, which is often used for cryptographic operations in Flask.

#### Registering Jinja Filters

These lines register custom Jinja2 template filters. The app.jinja_env.filters dictionary is used to add custom filters, which can be accessed within your templates to format data.

#### Route Definitions

This defines a simple route /hello that responds with "hello world" when accessed. The @app.route() decorator associates the function hello() with the URL path /hello.

#### Registering Blueprints

These lines register Flask blueprints with the application. Blueprints are a way to organize and modularize routes and views in a Flask application.

#### Database Initialization

This line initializes the database by calling the init_db() function with the Flask app instance as an argument.

#### Returning the Flask Application

Finally, the create_app function returns the configured Flask application, making it ready for running with a web server.



 

