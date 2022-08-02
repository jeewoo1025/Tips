## ubuntu 실행 후 local directory 연동
```python
docker run -it -v C:\:/home/workspace ubuntu
```

호스트 시스템의 `C:\` 디렉토리를 Ubuntu Linux Container의 `/home/workspace` 디렉토리에 mount할 수 있다. <br>
<br>

## docker 이미지 커밋
1. 실행 중인 도커 컨테이너 종료하기
2. 종료된 도커 컨테이너 ID 확인하기
```python
docker ps -a
```
3. commit 명령을 입력하여 종료된 도커 컨테이너 상태 그대로의 이미지를 생성하기
```python
docker commit [CONTAINER ID] [IMAGE NAME]
```
4. `docker images` 명령어로 새로운 이미지가 생성된 것을 확인하기
5. 새로 생성된 이미지로부터 도커 컨테이너 실행할 수 있다. 실행 시 이전까지 진행했던 작업 상태가 보존된 것을 확인할 수 있다
```python
docker run -it [REPOSITORY]:[TAG]
```
<br>

## docker 컨테이너 삭제
```python
# id 값으로 삭제
docker rm [컨테이너 id]

# 이름으로 삭제
docker rm [컨테이너 이름]
```
<br>

## docker inspect
컨테이너와 이미지의 세부 정보를 JSON 형태로 출력하는 명령어이다. 
```python
docker inspect [컨테이너 또는 이미지 이름]
```
<br>

## docker images 삭제
```python
docker rmi [이미지 id]

docker images
```
<br>

## docker 메모리 사용량 확인하기
docker contiainer CPU/메모리 사용량 확인
```python
# 전체 컨테이너 확인
docker stats 

# 특정 컨테이너 확인
docker stats [컨테이너 id or 이름]
```
<br>

## VS code에서 원격 서버의 docker contanier로 바로 접속해서 실행하기
▶ 개발환경 <br>
로컬 : Window 10 <br>
서버 : Ubuntu 20.04 LTS <br>
<br>

▶ 실행방법 <br>
1. 서버 1 ~ 서버 4 중 원하는 서버에서 docker container 실행 (기존과 동일) <br>
2. 로컬 VS code에서 `Ctrl + Shift + P` 키 누름 <br>
3. Remote Containers: Attach to Running Container 클릭 -> 원하는 container 선택 <br>
4. Python 파일을 실행하려면 python interpreter 선택 (conda 'base')
이때 서버에서 debuging 자유롭게 할려면 서버에 python extension pack 설치하기
5. [디버깅없이 실행] Ctrl + F5 누르거나 왼쪽 상단에 ▶ 버튼 누르면 python 파일 실행됨!
[디버깅모드]는 밑의 영상 링크 참고 <br>
개인적으로 https://www.youtube.com/watch?v=w77D5KuJ7eE 이 동영상이 제일 설명 잘 되있음 <br>
해당 동영상에서 디버깅 방법도 자세히 설명되있음. <br>

## docker save & load
commit한 docker image를 backup하고 load하는 방법 <br>

### docker save
commit한 상태 백업하기
```python
docker save -o [저장할 이름].tar [이미지 이름]
docker save -o jeewoo_brio.tar jeewoo_brio/pytorch:latest
```

### docker load
tar 파일을 복원하기
```python
docker load < [백업한 파일이름].tar
docker load < jeewoo_brio.tar
```
