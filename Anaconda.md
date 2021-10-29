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
<br>

## Ignoring invalid distribution -ip 에러 해결
주어진 경로로 이동한 후, '~'로 시작되는 디렉토리 삭제하기. 이유는 임시폴더를 만들어놨는데 아직 지우지 않았거나 이름이 잘못 배정되어있는 경우에 저런폴더가 나타난다.<br>
![image](https://user-images.githubusercontent.com/39071676/139386520-6939fafb-eff2-4907-9329-2dc2711eb935.png)
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
