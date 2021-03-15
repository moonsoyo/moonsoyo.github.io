---
title: "Django Base API view and User Create API view"
date: 2021-03-11
categories: daily post
---
Creating Base API View and User creation API View.
Used class based view (CBV).

Good things about using CBV.
1. To write code related to HTTP methods (GET, POST, etc), we will use methods instead of 
   if statements. Code will get cleaner.
2. We will use generic view and mix in, so productivity and code reusability will go up.

Example of function based view
```python
from django.http import HttpResponse

def my_view(request):
    if request.method == 'GET':
        # Write view logic here.
        return HttpResponse('result')
```
Example of class based view
```python
from django.http import HttpResponse
from django.views import View

class MyView(View):
    def get(self, request):
        # Write view logic here.
        return HttpResponse('result')
```

But before we create classes, we need to create apps.
```python
django-admin startapp apis
```
Then, go to settings.py and add the apps that we created.
```python
INSTALLED_APPS += [
    'apis,
]
```
Then, we will go to apis/views.py.

```python
from django.http import JsonResponse
from django.views import View

# BaseView class helps exchange JSON data when developing apis.
# If LogIn, LogOut, Sign up etc views inherit BaseView, JSON data can be exchanged.
class BaseView(View):
    @staticmethod
    def response(data={}, message='', status=200):
        result = {
            'data': data,
            'message': message,
        }
        return JsonResponse(result, status)


class UserCreateView(BaseView):
    @method-decorator(csrf_exempt)
    def dispatch(self, request, *args, **kwargs):
        return super(UserCreateView, self).dispatch(request, *args, **kwargs)

    def post(self, request):
        username = request.POST.get('username', '')
        password = request.POST.get('password', '')
        email = request.POST.get('email', '')

        user = User.objects.create_user(username, email, password)

        return self.response({'user.id': user.id})
```