## ubuntu 실행 후 local directory 연동
```python
docker run -it -v C:\:/home/workspace ubuntu
```

호스트 시스템의 `C:\` 디렉토리를 Ubuntu Linux Container의 `/home/workspace` 디렉토리에 mount할 수 있다. <br>
