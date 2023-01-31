Anaconda는 대규모 데이터 처리, 예측 분석 및 과학 컴퓨팅에 사용되는 가장 인기 있는 <b>파이썬 데이터 과학 및 머신러닝 플랫폼</b>입니다. <br>
아나콘다 배포에는 1,000개 이상의 데이터 패키지, 콘다 명령줄 도구 및 아나콘다 네비게이터라는 데스크톱 그래픽 사용자 인터페이스가 함께 제공됩니다.
<br>

## 기본 사용법
```python
# 버전화인 
conda --version

# 아나콘다 업데이트
conda update conda

# 가상환경 생성하기
conda create -n <환경명> python=<버전>
conda create -n jeewoo_test python=3.8

# 가상환경 활성화하기
conda activate <환경명>

# 가상환경 비활성화하기
conda deactivate <환경명>

# 가상환경 삭제
conda remove -n <환경명> -0all
```

## import gensim시에 cannot import name 'open' from 'smart_open' 이슈
gensim 이슈 버전 때문. 그래서 구체적인 버전을 정해서 다시 설치
```shell
conda uninstall gensim
conda install gensim==3.4.0
```
<br>

## 가상환경에 대한 정보 확인하기
* 설치된 가상환경에 대한 정보
```shell
conda info --envs
```

* 현재 가상환경에서 설치된 패키지들의 이름과 버전 정보
```shell
conda list
```
<br>

## 가상환경 제거하기
설치한 가상환경을 제거하고 싶다면 아래의 명령어를 입력하면 된다.
```shell
conda remove --name [가상환경 이름] --all

conda env remove --n [가상환경 이름]
```

<br>

## jupyter notebook에서 import torch 에러
가상환경에서 pytorch를 설치했음에도 불구하고 jupyter notebook에서 `import torch`가 실행되지 않을 수도 있다.

1. jupyter 모듈이 설치 안 된 경우
그러면 `conda list`를 통해 가상환경에 설치된 모듈을 확인해보자. 확인 결과 jupyter 모듈이 존재하지 않으면 실행되지 않는다.
```shell
conda install jupyter
```

2. ipython을 설치해주지 않았을 경우
아나콘다로 가상환경을 사용하고 있었는데 해당 가상환경에 ipython을 설치해주지 않았으면 문제가 발생한다
```shell
conda install ipython
```
<br>

## Ignoring invalid distribution -ip 에러 해결
주어진 경로로 이동한 후, '~'로 시작되는 디렉토리 삭제하기. 이유는 임시폴더를 만들어놨는데 아직 지우지 않았거나 이름이 잘못 배정되어있는 경우에 저런폴더가 나타난다.<br>
![image](https://user-images.githubusercontent.com/39071676/139386520-6939fafb-eff2-4907-9329-2dc2711eb935.png)
<br>
<br>

## Tensorflow 설치 오류
```python
ERROR:root:Internal Python error in the inspect module.
```
이러한 오류의 원인은 Tensorflow와 Keras 버전호환 문제때문이다. 현 시점에서는 `Python 3.6.4, Keras 2.3.1, Tensorflow 2.0` 3개의 조합이 Best 이다.
```shell
pip install tensorflow==2.0
pip install keras==2.3.1
```
<br>
<br>

## import konlpy 오류 해결 (tweepy) 
메시지는 AttributeError: module 'tweepy' has no attribute 'StreamListener'라는 오류 메시지가 뜨면, konlpy를 import하는 과정에서 tweepy.StreamListener 이 부분에서 tweepy가 StreamListener이라는 속성을 가지고 있지 않다는 의미이다. <br>

▶ 해결방법 <br>
tweepy의 버전이 4.0.0으로 업그레이드되어 생기는 문제로, tweepy를 3.7.0 ~ 3.10.0 사이로 설치해보라고 답변이 나와 있다. `pip list` 명령어를 실행하면 설치된 라이브러리 목록과 버전을 확인할 수 있다. `pip install tweepy==3.10.0`으로 버전을 다운그레이드 해보자!
<br>
<br>

## SystemError: java.nio.file.InvalidPathException 에러
```python
SystemError: java.nio.file.InvalidPathException: Illegal char <*> at index 52:
```
<br>

▶ 해결방법 <br>
1. JAVA_HOME 환경변수 설정 확인
2. Python 버전과 JPype1 버전이 일치하는지 확인
3. `C:\Users\suljeewoo\anaconda3\envs\zeze\Lib\site-packages\konlpy\jvm.py`에서 마지막 <b>*</b> 제거
<br>

## pororo 설치 
카카오브레인에서 제공하는 api이며 자연어처리(요약, mrc 등) 및 스피치 관련 여러 기능들을 제공함. 
```python
conda create -n pororo python=3.6
conda activate pororo
 
# cpu only로 설치 GPU 설치 등은 아래 링크 참조
# https://pytorch.org/get-started/previous-versions/#v160
conda install pytorch==1.6.0 torchvision==0.7.0 cpuonly -c pytorch
 
pip install pororo
```

![image](https://user-images.githubusercontent.com/39071676/151689996-5ee39f68-090f-46d6-b6eb-bf9396f98bb1.png)
단, 주의할점은 `torchvision==0.7.0` 버전이 필요하다. 아니면, 충돌이 일어난다.
그리고 `fairseq==0.10.2` 가장 최신 버전으로 설치해야 하는데 ~~여기서 권한 충돌이 일어난다.. 아직 해결중!~~ (해결완)
<br>

## Fairseq 권한 해결방법
pororo 설치 나왔던 권한 에러를 해결안 방안은 다음과 같다. 아무래도 Anaconda에서 fairseq를 설치할때 `pip` 명령어로 설치하면 버전 `0.10.2`에러가 난다. 그래서 fresh한 가상환경에서 아래의 명령어를 실행해보자.

### 방안1) conda 명령어
```python
# https://anaconda.org/conda-forge/fairseq
conda install -c conda-forge fairseq
```
![image](https://user-images.githubusercontent.com/39071676/152257794-06839e23-e9b3-4b19-8070-39597ed4ca0f.png)

### 방안2) git clone 후 폴더에서 실행
1) anaconda 관리자 권한으로 실행 (이 경우 conda 'base' 환경에서 설치를 진행해야 한다) <br>
2) github fairseq에서 나와있는 설치 방법대로 실행함 <br>
```python
git clone https://github.com/pytorch/fairseq
cd fairseq
pip install --editable ./
```
<br>

## Win10에 Mecab 설치방법
* https://uwgdqo.tistory.com/363
* https://cleancode-ws.tistory.com/97
위의 2개의 사이트가 제일 자세히 나와있음. 주의할점은 Mecab 디렉토리를 생성할 때 꼭 `C:\Mecab`으로 해야지 아니면 따로 경로를 설정해줘야함!
```python
from konlpy.tag import Mecab

mecab = Mecab(dicpath=r"C:/Mecab/mecab-ko-dic")
mecab.pos("아버지가 방에 들어가신다")
$ [('아버지', 'NNG'), ('가', 'JKS'), ('방', 'NNG'), ('에', 'JKB'), ('들어가', 'VV'), ('신다', 'EP+EC')]
```
<br>

## pyrouge 설치방법
summarization task에서 rouge evaluation package 설치하는 방법 <br>
이미 `pip` 명령어로 pyrouge가 설치되어있는 경우, `pip uninstall pyrouge`를 수행하길 바란다.
[stackoverflow](https://stackoverflow.com/questions/45894212/installing-pyrouge-gets-error-in-ubuntu)에서 첫번째 답안을 제일 추천한다.

* 잘못된 case
```shell
FileNotFoundError: [Errno 2] No such file or directory: '/root/.pyrouge/settings.ini'
```
pyrouge만 설치하고 환경 설정을 하지 않았다면 위와 같은 Error가 뜬다
<br>

* 올바른 case
```python
# install pyrouge from source
git clone https://github.com/bheinzerling/pyrouge
cd pyrouge
pip install -e .

# Install official ROUGE script
git clone https://github.com/andersjo/pyrouge.git rouge

# Point Pyrouge to official rouge script
# pyrouge_set_rouge_path [absolute path]
pyrouge_set_rouge_path /workspace/pyrouge/rouge/tools/ROUGE-1.5.5/

# Install libxml parser
sudo apt-get install libxml-parser-perl

# Regenerate the Exceptions DB
cd rouge/tools/ROUGE-1.5.5/data
rm WordNet-2.0.exc.db
./WordNet-2.0-Exceptions/buildExeptionDB.pl ./WordNet-2.0-Exceptions ./smart_common_words.txt ./WordNet-2.0.exc.db

# Run the tests
python -m pyrouge.test
```

* 성공 시 실행화면 <br>
![image](https://user-images.githubusercontent.com/39071676/156963768-b830b348-76f5-4303-88aa-dc657227fd59.png)
<br>

## pytorch_transformers 설치방법
NLP의 SOTA pre-trained models 라이브러리 설치 방법
```python
pip install pytorch-transformers
```
<br>

## Standford CoreNLP 설치
* link : https://stanfordnlp.github.io/CoreNLP/download.html

```python
# 1) Download the CoreNLP zip file
wget http://nlp.stanford.edu/software/stanford-corenlp-latest.zip

# 2) Unzip the release
unzip stanford-corenlp-latest.zip

# 3) Enter the newly unzipped directory
cd stanford-corenlp-4.4.0

# 4) Set up your classpath
for file in `find . -name "*.jar"`; do export
CLASSPATH="$CLASSPATH:`realpath $file`"; done

# 5) Try it out
echo "the quick brown fox jumped over the lazy dog" > input.txt
java -mx3g edu.stanford.nlp.pipeline.StanfordCoreNLP -outputFormat json -file input.txt
```

▼ 5번 실행화면
![image](https://user-images.githubusercontent.com/39071676/169191359-d12e927d-422e-4597-a19d-8bd2e601661e.png)
<br>

## Wandb 사용하기
* [참조 사이트](https://greeksharifa.github.io/references/2020/06/10/wandb-usage/)
* [wandb site](https://wandb.ai/site)
```python
# 0. wandb 설치
pip install wandb

# 1. 초기 설정
wandb login

## 프로젝트 이름 설정
wandb.init(proejct=[프로젝트 이름], reinit=True)

## 실행 이름 설정
wandb.run.name = [실행 이름]
wandb.run.save()

# 2. config 저장
wandb.config.update(args)

# 3. model 저장
wandb.watch(model)

# 4. log 저장
wandb.log({
	'accuracy': acc,
	'loss': loss
})
```

## cuDF 활용하기

1. RAPIDS 설치하기 (Docker)
link : https://rapids.ai/start.html

```python
# download and install
docker pull rapidsai/rapidsai-core:22.08-cuda11.4-base-ubuntu20.04-py3.8
docker run --runtime=nvidia -e NVIDIA_VISIBLE_DEVICES=1 --volume ~/workspace:/workspace -it --name jeewoo_test rapidsai/rapidsai-core:22.08-cuda11.4-base-ubuntu20.04-py3.8 /bin/bash
```
<br>

## pyemd 설치
moverscore를 사용하기 위해서는, pyemd가 설치되어있어야 한다. 하지만, 만약 설치 중 에러가 난다면, gcc, g++이 설치되어있는지 확인해라!
```python
# check update
apt-get update

sudo apt-get install g++
sudo apt-get install gcc

pip install pyemd
```
