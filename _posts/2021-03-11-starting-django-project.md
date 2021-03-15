---
title: "How to start a Django Project"
date: 2021-03-11
categories: daily post
---
This is a general guide on starting a new Django project. 

1. Check if you have a 'venvs' folder.
2. Create a new venv folder.
```python
python -m venv mysite
```
3. cd into mysite\Scripts and do 'activate'.
4. Install Django and upgrade pip.
```python
pip install django==3.1.3
python -m pip install --upgrade pip
```
5. Check if you have a 'projects' folder.
6. Move to 'projects' folder which is the project root directory.
7. Activate venv in 'projects'.
```python
C:\venvs\mysite\Scripts\activate
```
8. Create mysite directory inside virtual environment.
9. cd mysite
10. Create Django project by making the current directory as project directory.
```python
django-admin startproject config .
```
Now, start the server by executing python manage.py runserver.

To create the database for the project do the following.
```python
python manage.py migrate
```

Then, to do the first commit,
```python
git init
git status
git add
git commit -m "First commit"
git remote add origin https://github.com/moonsoyo/mysite.git
git push -u origin master
```
