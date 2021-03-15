장고 프로젝트에서 앱 개발.

장고 프로젝트는 1개 이상의 앱을 가진다. 앱은 블로깅 기능, 단일 페이지 보여주기 기능 과 같이
특정 기능을 수행하는 단위 모듈을 말한다. 

python manage.py startapp blog

장고의 장점 중 하나는 모델을 이용해 장고 웹 프레임워크 안에서 데이터베이스를 관리할 수 있다는 것이다.

모델은 데이터를 저장하기 위한 하나의 단위라고 보면 된다. 장고의 모델을 이용하면 파이썬만으로
CRUD 기능을 쉽게 구현할 수 있고 관리자 페이지, 입력 폼 등도 쉽게 만들 수 있다. 

모델의 예시
```python
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=30)
    content = models.TextField()

    created_at = models.DataTimeField()
```

모델을 만든 뒤에는 python.manage.py makemigrations를 해서 데이터베이스에 반영해야
실제 테이블이 생성된다. 

그런데 그 전에 settings.py에 앱 이름을 등록해 주어야 한다.

하지만 아직 모델이 적용되지 않은 상태이다. 
모델을 적용하려면 python manage.py migrate를 해줘야 한다.

```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```
어드민에 블로그 섹션을 만들어 줄 수 있다. 

파이썬은 스크립트 기반의 언어여서 컴파일 과정 없이 한 줄씩 그때그떄 실행시킬 수 있다.
장고 shell을 사용하면 이런 장점을 활용할 수 있다.

python manage.py shell