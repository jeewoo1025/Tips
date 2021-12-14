장치 : NVIDIA Jetson TX2

### 초기 설정 참고 사이트
[Jetpack 설치](https://blog.naver.com/PostView.naver?blogId=msjh0329&logNo=221835887143&from=search&redirect=Log&widgetTypeCall=true&directAccess=false)

<br>

### 에러 출력시 해결방안
1. qemu-user-static package 확인 <br>
위의 패키지가 설치 안되어있으면 dependency error 출력됨
```shell
sudo apt-get install qemu-user-static
```

2. apt update / upgrade 수행 <br>
최신 버전을 못 받아와 생기는 오류일 수 있으니 아래 명령어 수행
```shell
sudo apt update
sudo apt upgrade
```
<br>

### Jetson TX2에서의 nvidia-smi 부재 문제
이 장치에서 nvidia-smi가 없어 tegra GPU 모듈을 사용함. 덕분에 GPU 현황을 파악하기 위해서는 다음을 사용
```shell
sudo tegrastats
```
<br>
<br>
