# Introduction-to-Flask-for-Python

## What is Flask?

### History

Flask was created by [Armin Ronacher](https://en.wikipedia.org/wiki/Armin_Ronacher). It is a web-framework that features a rich library to build web applications and APIs and is designed to be used with the Python programming language. it is the second most popular web-framework right behind Django and can be seen as the javascript equivalent to Express. Both Express and Flask provide tools to create C.R.U.D opperations and provide tools to create and manage server logic.

Armin developed Flask along with group that he was a part of known as Pocoo. Pocoo was also responsible for the creation of Werkzeug and Jinja which are some of the components that make up flask.

### Components

**Werkzeug** is a [WSGI](https://wsgi.readthedocs.io/en/latest/what.html) web/utility library for Python that provides a set of tools for building web applications working with HTTP request and responses and meet a set of standards for building web applications using python.

**Jinja** is known as a web template engine for Python it allows developers to create the structural layout of the page using HTML while also incorporating the application's logic that will handle the users interactions and data processing using python-themed syntax. This will make it easier to manage and maintain web application code. Jinja can be seen as the javascript equivalent of Handlebars.js.

### Installation

- First make sure you have python installed by typing python --version in the terminal. if you dont have it installed use this [link](https://www.python.org/downloads/).

- Once python is installed so will [Python Package Index (PyPI)](https://pypi.org/) which is a package manager for python just like npm is for javascript.

Before installing flask its important to understand best practices for using python packages. By default, installing a Python library installs it globally. However, Python provides a feature called a virtual environment—a self-contained directory that maintains its own version of Python and its own library dependencies. This way, multiple Python projects can reside on the same machine without interfering with each other.

To start the virtual environment run this code on the terminal python `-m venv venv` this will create a file named venv that will make the virtual environment possible. to start the virtual environment run `.\venv\Scripts\activate` if your using Windows or `. venv/bin/activate` for Mac. Once the virtual environment starts you can begin to download your dependencies. 

if you see `(venv) PS C:\Users\UserName\Desktop\projects\python-project>` the (venv) signifies that you are now working in a virtual environment. finally type `pip install flask` to install Flask. this will come with additional files like jinja2 that will allow you to start programming right away.




 

