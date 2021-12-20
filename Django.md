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
<br>

### 실행 runserver
* runserver 명령어를 실행하면 기본적으로 내부 IP의 8000번 포트로 개발 서버를 띄움
```python
python manage.py runserver
```
<br>

* 포트 바꾸기
```python
python manage.py runserver 8080
```
<br>

### Django 서버 시작할 때 실행할 코드 설정하기
서버를 실행함과 동시에 특정 코드를 실행할 일이 생긴다. (모델 로드하기, 파일 읽기 등) 이때, AppConfig를 사용한다.

* Appconfig를 상속하는 클래스 생성하기
```python
### myapp/apps.py
from django.apps import AppConfig

class MyAppConfig(AppConfig):
    name = 'my_app'
    
    def ready(self):
        # TODO : Write your codes to run on startup
        pass
```

<b>※ 주의할점</b><br>
Django가 기본적으로 코드 검증 과정에서 한번, 코드 실행 과정에서 한번, 총 2번 `MyAppConfig`를 실행한다.
두번 실행되는 일을 피하기 위해서 Django 서버를 실행할 때 다음과 같이 `--noreload` 옵션을 넣어준다.
```python
python manage.py runserver --noreload
```
<br>
