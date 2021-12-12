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

### wget 명령어
`Web GET`의 약어로 웹 상의 파일을 다운로드할 때 사용하는 명령어
* wget 옵션 설명 : https://hippogrammer.tistory.com/158
```shell
wget [옵션] [URL]
```
<br>

### 설치된 Ubuntu 버전 확인
```shell
lsb_release -a
```
![image](https://user-images.githubusercontent.com/39071676/145700549-b9fd64c8-3cbf-490a-9df7-cde3228b5763.png)

