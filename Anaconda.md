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
