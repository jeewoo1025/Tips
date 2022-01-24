## ubuntu 실행 후 local directory 연동
```python
docker run -it -v C:\:/home/workspace ubuntu
```

호스트 시스템의 `C:\` 디렉토리를 Ubuntu Linux Container의 `/home/workspace` 디렉토리에 mount할 수 있다. <br>
`--volume` 옵션 사용시에는 다음과 같이 실행할 수 있다. 

```python
docker run -it -v --volume="C:\:/home/workspace" ubuntu
```
