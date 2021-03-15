---
title: "Creating Log In logic in Django"
date: 2021-03-11
categories: daily post
---
After views, create urls.py inside apis folder and make local path.
```python
from django.urls import pathlib

from apis.views import UserCreateView

urlpatterns = [
    path('v1/users/create/', UserCreateView.as_view(), name='apis_v1_user'),
]
```
Then, go to the main urls.py and use include() to finish creating the path.
```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('admin/', admin.site.urls),
    path('apis/', include('apis.urls')),
]
```
To add an integrity check for user IDs, do the following on views.py
```python
try:
            user = User.objects.create_user(username, email, password)
        except IntegrityError:
            return self.response(message='This ID already exists.', status=400)

        return self.response({'user.id': user.id})
```
To create the actual log in page, first add UserLoginView in urls.py in apis.
```python
from django.urls import pathlib

from apis.views import UserCreateView, UserLoginView

urlpatterns = [
    path('v1/users/create/', UserCreateView.as_view(), name='apis_v1_user_create'),
    path('v1/users/login/', UserLoginView.as_view(), name='apis_v1_user_login'),
]
```
Then, go to views.py and create UserLoginView.
```python
class UserLoginView(BaseView):
            def post(self, request):
                username = request.POST.get('username', '')
                if not username:
                    return self.response(message='Please put in the username', status=400)
                password = request.POST.get('password', '')
                if not password:
                    return self.response(message='Please put in the password', status=400)
                
                user = authenticate(request, username=username, password=password)
                if user is None:
                    return self.response(message='This user does not exist', status=400)
                login(request, user)

                return self.response()
```
Now, let's create a page that we can use to test the log in API.
We will create another app to make the testing view.
After creating another app, we need to add that in settings.py file.
And testing view will be in html so we will create a 'templates' folder and add that path in settings.py as well. 

Then, create a template view in contents's view.py.
And add the path to the main urls.py.

Then, make _base.html and home.html under templates folder.


