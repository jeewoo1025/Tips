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
<br>

### Ubuntu 18.04에서 Python 3.7 설치하기
* [참고 사이트](https://somjang.tistory.com/entry/PythonUbuntu%EC%97%90-Python-37-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0?category=345065)
```shell
# 1. 파이썬 홈페이지 소스 다운로드
wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tgz

# 2. tgz 파일 압축 풀기
tar xvfz Python-3.7.4.tgz 
cd Python-3.7.4

# 3. 설치하기
./configure
make
sudo make install
python3 -V

# 4. 환경변수 설정하기 (~/.bashrc)
# 파이썬 실행 위치 확인
which python3
ls -al /usr/bin/ | grep python

# update-alternatives로 파이썬 버전 등록 및 변경
# 버전 등록
sudo update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.6 2
sudo update-alternatives --install /usr/bin/python python /usr/bin/python3.7 3

# 버전 변경
sudo update-alternatives --config python
```
