# Tips
소소한 팁들

# Linux


<br>

# Django
## 기본구조
```shell
tutorial/
    manage.py
    mysite/
        __init__.py
        settings.py
        urls.py
        wsgi.py
```
* manage.py : dajngo-admin과 비슷한데, manage.py에는 DJANGO_SETTINGS_MODULE 이라는 게 있어서 해당 장고 프로젝트의 setting.py 값을 알려주는 역할을 함!
* mysite/ : 프로젝트를 위한 python 패키지들이 저장되는 폴더
* mysite/settings.py : 현재 장고 프로젝트의 환경 및 구성을 저장

### 실행 runserver
* runserver 명령어를 실행하면 기본적으로 내부 IP의 8000번 포트로 개발 서버를 띄움
```python
python manage.py runserver
```
<br>

* 포트 바꾸기
```python
python manage.py runserver 8080
``
