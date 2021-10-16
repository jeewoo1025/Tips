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
<br>
