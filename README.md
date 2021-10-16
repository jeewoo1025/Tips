소소한 팁들

목차 <br>
[1. Linux](#Linux) <br>
[2. Python](#Python) <br>
[3. Pycharm](#Pycharm) <br>
[4. Django](#Django) <br>
<br>

# Linux
### Ubuntu 16.04에 Anaconda 설치
[Anaconda 홈페이지]()에 가서 설치 스크립트 파일 다운로드 한다. 그리고 터미널로 가서 다음 명령어를 입력한다
```shell
bash <anaconda .sh 파일명>
```
`.bashrc`에 PATH 등록을 한다. 
```shell
vim ~/.bashrc
export PATH="anaconda 경로/bin:$PATH" 추가
source ~/.bashrc
```
그 이후 `conda list` 등의 명령어가 정상적으로 동작하는지 확인한다.
<br><br>

# Python 
### requirements.txt로 패키지 한번에 관리하기
requirements.txt는 다수의 패키지 목록이 나열되어 있는 텍스트 파일이다. (대부분 프로젝트에서 이 이름으로 관리함) <br>
```shell
pip3 install -r requirements.txt
```

# Pycharm 
### Pycharm 터미널 설정 
프로젝트 진행시, 터미널을 통해 작업이 이루어지는 경우가 빈번하다. 그래서 터미널을 `Git Bash` 쉘로 설정해주고 시작해야 한다.
* link : https://opentutorials.org/course/3718/24657
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
