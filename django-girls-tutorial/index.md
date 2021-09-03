# 장고걸스 튜토리얼

> _[장고걸스 튜토리얼](https://tutorial.djangogirls.org/ko/)을 직접 수행하며 웹의 작동 원리를 이해했고, 웹을 개발/수정/관리하는 법을 배웠다. 객체지향 프로그래밍을 통해 웹사이트를 구성하고, 각각의 요소들이 상호작용할 수 있도록 하는 방식을 알 수 있었다. git, command line, python, django 등 많은 개발 툴들도 여러 예제와 친절한 설명으로 쉽게 사용방법을 익힐 수 있었다. 위 링크를 들어가서 직접 튜토리얼을 직접 수행해보는 것을 추천한다._

## Index

- [들어가며](#0-들어가며)
- [Python 시작하기](#1-python-시작하기)
- [나의 첫 번째 Django 프로젝트](#2-나의-첫-번째-django-프로젝트)
- [Django 모델](#3-django-모델)
- [Django 관리자](#4-django-관리자)
- [배포하기](#5-배포하기)
- [Django urls](#6-django-urls)
- [Django 뷰 만들기](#7-django-뷰-만들기)
- [Django ORM](#8-django-orm)
- [템플릿 동적 데이터](#9-템플릿-동적-데이터)
- [Django 템플릿](#10-django-템플릿)
- [템플릿 확장하기](#11-템플릿-확장하기)
- [Django 폼](#12-django-폼)
- [마치며](#13-마치며)

## 0. 들어가며

#### &emsp; 이 페이지는 장고걸스 튜토리얼의 내용을 그대로 복사한 것은 아니다. 튜토리얼을 총 2회 수행하는 동안 (개인적으로) 튜토리얼 내의 설명만으로는 진행이 어려웠던 부분을 나름대로 쉽게 정리해보려고 위 페이지를 작성했다. 튜토리얼 자체가 친절하고 자세하게 설명이 적혀있지만, 오탈자 등의 실수나 잘못된 이해로 인해서 나는 한 문제에 하루를 꼬박 고민한 시간도 있었다. 튜토리얼을 진행하다가 발생하는 오류들은 대부분 <u>구글에 오류 내용을 그대로 검색</u> 하면 도움을 받을 수 있다. 또, 오탈자나 잘못된 이해로 인한 문제일 수도 있으니 막힌 부분에서 뒤로 돌아가서 다시 천천히 수행하다보면 틀린 곳을 찾을 수도 있다.<br>천천히 포기하지 않고 끝까지 완주할 수 있길 응원한다.

> 튜토리얼의 모든 페이지를 정리하지는 않았다. 프로그램을 설치하는 페이지, 충분히 이해가 가능한 간단한 내용들은 제외하고 정리했다. 긴 코드가 나온 것들은 따로 한줄씩 내용을 정리해서 쉽게 이해할 수 있게 설명을 썼다.

## 1. Python 시작하기
 
- 메소드(method) : "(Ola)".upper()에서 메소드는 .upper() 부분에 해당한다. 메소드는 파이썬이 객체 (ex)Ola) 를 대상으로 행동을 수행하는 일련의 명령이다.

- 변수 : 매번 작성한 코드를 기억해서 다시 쓸 필요없이, 변수를 지정해서 계속 사용될 내용을 저장해놓는 것이라고 이해하면 쉽다. 예를 들어, (>>> name = "Ola") 라고 name 이라는 변수를 만들면 다음에는 name 이라고 쓰면 name 변수 안의 내용이 입력되는 것과 같은 효과를 낸다.

> 이번 장에는 python의 기본 문법들을 직접 사용해보고 기능을 이해하는 예제가 많았다. 눈으로만 보고 이해하지말고, 직접 코드를 입력해보면서 이해하는 것이 훨씬 좋은 방법이다. 이번 장에 배운 문법들을 지금 모두 외울 필요는 없다. 지금은 이해하면서 넘어가고 나중에 헷갈리면 다시 돌아와서 익혀도 좋다.

## 2. 나의 첫 번째 Django 프로젝트

- manage.py : 다른 설치없이 우리가 지금 사용중인 컴퓨터에서 웹서버를 시작할 수 있게 도와주는 스크립트다. 이후 가상환경(virtualenv)에서 'python manange.py runserver' 를 입력해서 로컬 서버를 열때 자주 보게 될 파일이다.
- settings.py : 웹사이트의 설정이 정리된 파일이다. 웹사이트에 적용되는 시간, 언어 등을 정의하는 내용이 들어있다. 
 
> 코드를 수정하는 작업들은 가상환경에서 진행되어야한다. Command Line 를 사용해 djangogirls 폴더에서 가상환경을 활성화 할 일이 매우 많을 것이다. 한번 외워두면 앞으로 작업할때 편하다. 

> (windows) myvenv\Scripts\activate (mac/linux) source myvenv/bin/activate * 윈도우 키보드에 '\' 키가 없어도 당황하지말고, 'Enter' 키 위에 있는 '￦' 키를 누르면 된다. 나는 처음에 '\' 키가 없어서 당황했다.

## 3. Django 모델

- 객체(object) : 속성(propoties) + 행동(methods) (= model)

```python
#### blog/models.py ####

from django.conf import settings
from django.db import models
from django.utils import timezone

class Post(models.Model):
    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(
            default=timezone.now)
    published_date = models.DateTimeField(
            blank=True, null=True)

    def publish(self):
        self.published_date = timezone.now()
        self.save()

    def __str__(self):
        return self.title
```
- from / import : from에 해당되는 파일에서 import에 해당되는 내용을 위 파일에 불러온다. 반복되는 내용을 여러 파일에 쓰지 않고, 이렇게 불러올 수 있다.
- class : 객체를 정의한다. 
- class Post : 객체에 이름을 Post로 정의한다. (객채 이름의 첫 글자는 항상 대문자)
- models. : Post가 장고 모델임을 의미한다. 이 코드를 통해서 장고는 Post가 데이터베이스에 저정되어야 하는 것을 알게 된다.
- Post의 속성 : auther/title/text/created_date/published_date/
- Post의 행동 : publish
- def publish(self) : publish라는 행동을 정의함. (소문자로 써야하고 공백대신 언더바)

> 갑자기 긴 코드문이 나와서 처음에는 조금 어려웠다. 그래서 이해할 수 있는 부분까지만 이해하고, 그 챕터를 마무리하기 위해 코드를 일단 모두 입력했다. 그리고 천천히 코드를 보면서 이해하기 위한 시간을 가졌다. 이해가 안되는 내용은 구글에 검색해보기도 하고, 그래도 잘 모르겠으면 넘어갔다. 이후에 나중에 나오는 챕터를 수행하면서 저절로 이해가 되는 부분도 있었다.

## 4. Django 관리자

``` python
#### blog.admin.py ####

from django.contrib import admin
from .models import Post

admin.site.register(Post)

```

- from .models import Post : models.py 파일 안에 정의된 Post 모델의 내용을 위 파일로 가져온다.
- admin.site.register(Post) : 관리자페이지에서 Post 모델을 등록한다.

> .models 에서 '.' 부분은 같은 폴더에 있는 파일을 선택하는 것이고, models.py 라고 쓰지 않아도, 그 폴더에 models 이름을 쓰는 파일이 하나밖에 없어서 .models 라고 써도 된다.

## 5. 배포하기

#### &emsp; 가장 많은 시간이 들었고 이해하기 어려운 부분이었다. 중간에 발생하는 오류도 많았고, git, github, pythonanywhere 를 한번에 배워서 하다보니까 다른 챕터보다 양도 많았다. 내가 겪었던 시행착오가 도움이 되었으면 한다. 앞서 이야기한 내용이지만 문제가 발생하면 구글에 해당 문제를 직접 검색해보는 것이 가장 빠르고 효과적인 문제해결 방법임을 잊지말자.

- git : git 프로그램은 버전 관리 시스템이며, 우리가 지정한 코드 저장소(repository, 줄여서 repo라고도 함)에 있는 파일들의 변화를 추적하고 관리해준다.
- github : 내 컴퓨터에서 로컬(Local)로 작업한 코드들을 온라인에 저장해주는 사이트이다. git 프로그램을 통해 추적하고 관리되고 있는 내 컴퓨터의 코드들을 배포(push)해서 github 사이트 내에 있는 저장소에 저장한다.
- pythonanywhere : 무료로 서버를 제공해주는 사이트다. 내 컴퓨터에서 작업한 내용을 git에 배포했는데, 그 배포된 내용을 가져와서(pull) 온라인에 있는 웹사이트에 노출시켜준다.

> 내가 이해한 웹 개발의 과정 = 로컬에서 코드를 변경/관리 -> 변경된 사항은 git을 통해 배포(push)된다. 배포된 코드들은 github에 버전별로 저장한다. 웹사이트는 서버가 지속적으로 방문객들을 응대하고 있다가, 로컬에서 변경된 코드가 있을때, git으로 배포된 내용을 가져와서(push) 온라인에 있는 웹사이트에 변경된 내용을 보여준다. 이렇게 해서 코드를 변경/관리하는 동안 웹사이트는 정상적으로 운영할 수 있다.

```
** git 작업 중 발생한 두 가지 오류 **

1. 'git pull origin master' 문구 진행중 'couldn't find remote ref master' 오류 발생

-> 2020년 10월부터 github의 기본 branch 이름이 'master'에서 'main'으로 변경되어서 발생하는 오류라고 한다. 'master'를 'main'으로 바꾸고 하면 정상 진행된다. 저렇게 바뀐 이유는 'master' 단어가 가지고 있는 주종관계의 의미와 인종차별적 요소에 대한 부분을 고려해서 변경하기로 결정했다고 한다.

2. 'git push - u origin master' 문구 진행 중 'support for password authentication was removed' 오류 발생

-> 2021년 8월부터 git에서 암호를 저장해서 로그인 해주는 기능이 없어졌다고 한다. 따라서, github에서 제공하는 personal access tokens 를 발급 받아서 암호 입력란에 넣어야한다. 
-> https://github.com/settings/profile 링크로 들어가서 developers settings 탭에서 토큰을 발급받을 수 있다. 발급 받을때 note에는 간단한 설명을 쓰고, 체크박스는 repo에 해당되는 것만 해주고 'update token'을 누르면 발급된다. 발급된 암호를 복사하고 다시 push를 진행할 때 비밀번호 란에 해당 암호를 붙여넣기 하면 해결된다.

```

## 6. Django urls

```python
#### mysite/urls.py ####

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('blog.urls')),
]
```
- path(‘admin/‘, admin.site.urls), : 장고가 admin/ 으로 시작하는 모든 URL을 view와 대조해서 찾아낸다.
- path(‘’, include(‘blog.urls’)) : 홈페이지로 들어오는 모든 접속 요청을 blog.urls 로 보내서 추가적인 명령을 찾아내겠다.

```python
#### blog/urls.py ####

from django.urls import path
from . import views

urlpatterns = [
    path('', views.post_list, name='post_list'),
]
```
- from django.urls import path / from . import views : 장고 함수인 path와 (blog 에서 사용할) views를 위 파일로 가져온다.
- urlpatterns = [path('', views.post_list, ] : 홈페이지로 처음 들어왔을때 모든 경우에 대해서 ('') views.post_list를 보여줘라.
- name='post_list'), : 앞에 정의한 경로로 들어오는(여기서는 ''이므로 첫 방문 모든 경로) URL에 post_list 라는 이름을 붙여서 view를 구분하겠다.

> 여기도 코드들을 이해하는 것이 조금 어려웠다. 머리속에 홈페이지가 작동하는 구조가 잘 그려지지 않아서 그런것 같았다. 이후에 나오는 views.py 와 urls.py, models.py 세 파일이 연결되면서 유기적으로 홈페이지가 작동하는 것을 이해하면 조금 더 쉽게 이해할 수 있다. 지금은 조금 이해가 안되더라도 나중에 다시 와서 보도록 하자.

## 7. Django 뷰 만들기

#### views.py : 홈페이지에서 진행되는 로직을 넣는 곳. 방문자들에게 홈페이지가 수행하는 행동을 정의해놓는 곳이라고 이해하면 쉽다. 이전 장에서 만들었던 models.py에서 정의된 '모델' 들을 ‘템플릿’에 전달하는 역할을 한다. 템플릿은 다음장에 만들 예정이다.

```python
#### blog/views.py ####

from django.shortcuts import render

def post_list(request):
    return render(request, 'blog/post_list.html', {}) 
```
- def post_list(request): : 이 파일에서 post_list 라는 함수를 정의하겠다고 선언하는 문장이다.  
- return render(request, 'blog/post_list.html', {}) : 이 함수는 요청(request) 이 들어오면, Render 행동(method)을 하는데, blog/post_list.html 템플릿을 보여주라는 뜻이다.

> 템플릿은 바로 다음 챕터인 'HTML 시작하기'에서 배우지만, 여기서 간단히 편지와 편지지의 예를들어 설명하겠다. 편지를 여러 통을 쓰게되면 내용이나 수신인 주소는 매번 달라진다. 그때, 편지지의 디자인과 레이아웃 등의 편지지 양식을 고정해놓고 여러 장의 편지지를 만들어놓으면, 내용과 주소만 수정해서 여러통의 편지를 쉽게 작성할 수 있을 것이다. 웹사이트도 매번 방문자들에게 다른 페이지를 제공할때마다 다른 페이지를 만드는 것이 아니라, '템플릿'을 통해서 기본 양식을 만들어 놓고 변경해야할 내용만 수정해서 보여주면 훨씬 쉽고 빠를 것이다. 그래서 '템플릿'을 사용하는 것이다.

## 8. Django ORM

- QuerySet : 데이터베이스로부터 데이터를 읽고, 필터를 걸고, 정렬하는것을 도와주는 역할을 한다.
- 장고 쉘 : 장고에서 제공하는 파이선 입력기라고 이해하면 쉽다. 장고에서 제공하는 웹사이트 제작에 매우 유용한 기능들을 사용할 수 있게 도와준다.

> 인스턴스? 챕터를 진행하던 중에 '인스턴스' 라는 단어가 나와서 이해를 위해 구글에 검색을 했다. 클래스와 인스턴스의 개념을 같이 설명하면서 붕어빵틀과 붕어빵의 예를 든 이야기가 가장 이해하기 쉬웠다. 챕터 3. django 모델에서 나온 클래스(class) 내용을 보고 오면 더 좋겠다. 붕어빵틀은 클래스이고, 붕어빵은 인스턴스라고 이해하면 쉽다. 붕어빵틀은 하나로 고정되어있고, 붕어빵의 모양을 정의할 수 있다. 붕어빵틀에서 나오는 붕어빵은 틀 안에 재료를 넣으면 같은 붕어빵이 계속해서 나올수 있다. 그렇게 나온 붕어빵이 인스턴스다.

> 그래서 뭐? 라고 생각할 수 있지만, 일단 지금은 이해만 하고 넘어가자. 뒤에서 또 인스턴스를 다룰 일이 있게 된다. 

## 9. 템플릿 동적 데이터

#### &emsp;
 

>

## 10. Django 템플릿

#### &emsp;
 

>

## 11. 템플릿 확장하기

#### &emsp;
 

>

## 12. Django 폼

#### &emsp;
 

>

## 13. 마치며

#### &emsp;
 

>

