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
