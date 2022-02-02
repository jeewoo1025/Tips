### 모듈 vs 패키지
Python에서는 print와 같은 기본 내장함수를 제공한다. 하지만 더 많은 기능을 이용하기 위해서 다른 사람들이 미리 만들어 놓은 모듈과 패키지를 이용할 수 있다. 
* 모듈 (module) : 특정 기능을 .py 파일 단위로 작성한 것
* 패키지 (package) : 특정 기능과 관련된 여러 모듈을 묶은 것

#### import 모듈 가져오기
모듈은 import를 통해 가져올 수 있으며, 해당 모듈의 변수,함수,클래스를 이용할 수 있다. 

#### import 모듈 as 이름
모듈을 편리하게 사용하기 위해 as를 통해 모듈 이름 지정함

#### from 모듈 import로 일부만 가져오기
from import로 변수,함수,클래스만을 바로 사용할 수 있다.
```python
from math import pi, sqrt

print(pi)
print(sqrt(3.0)
```
<br>

### requirements.txt로 패키지 한번에 관리하기
requirements.txt는 다수의 패키지 목록이 나열되어 있는 텍스트 파일이다. (대부분 프로젝트에서 이 이름으로 관리함) <br>
```shell
pip3 install -r requirements.txt
```
<br>

### `numpy` 
파이썬으로 수치 계산을 하기 위한 라이브러리. 다차원 배열을 효율적으로 구현한 넘파이 배열과 배열 간 빠른 연산을 할 수 있는 루틴을 제공한다. 단, 넘파이 배열의 원소는 모두 같은 데이터 타입이여야 한다.

* 넘파이 배열 : N차원 배열 객체로 모든 원소는 같은 타입, 같은 크기를 가지며 차원 개수만큼의 정수로 인덱싱된다. 차원(dimension)을 축(axis)라고 한다. 넘파이 배열의 타입은 `numpy.ndarray 클래스`이다.
* `ndarray.ndim` : 배열을 구성하는 차원의 개수
* `ndarray.shape` : (첫번째 차원의 크기, 두번째 차원의 크기, ..., ) - 튜플의 원소갯수 = N차원
* axis=0 : 열 방향(↓), axis=1 : 행 방향(→)

```python
import numpy as np

A = np.array([[1,2,3], [4,5,6]])  # 넘파이 배열
B = np.array([1,2,3], dtype=np.float64) # dtype를 실수 타입으로 지정

# 데이터 타입을 정수로 변경
B = B.astype(np.int32)

print(type(B)) # class 'numpy.asdarray'
print(A.ndim) # 2
print(A.shape)  # (2,3) - 2: 차원(열 방향)의 크기, 3: 차원(행 방향)의 크기

C = np.array([[1,2],[3,4]])
print(C.sum(axis=0)) # 열 방향으로 계산
print(C.sum(axis=1)) # 행 방향을 계산
```
<br>

### 상속
자식클래스를 선언할 때 소괄호로 부모클래스를 포함시킨다. 부모 메소드를 호출할 때는 `super()`키워드를 사용한다. 
Python은 C# 또는 Java와는 다르게 다중상속이 가능하다. 
```python
class 부모클래스:
    ... 내용 ...

class 자식클래스(부모클래스):
    ... 내용 ...

class 자식클래스(부모클래스1, 부모클래스2):
    ... 내용 ...

# 클래스를 작성하면 상속관계를 확인하는 메소드
자식클래스.mro()
```
<br>

### glob
glob는 파일들의 리스트를 뽑을 때 사용하는데, 파일의 경로명을 이용해서 사용할 수 있다
```python
>>> from glob import glob
>>> glob('*.exe')               # 현재 디렉터리의 .exe 파일
['python.exe', 'pythonw.exe']
>>> glob('*.txt')               # 현재 디렉터리의 .txt 파일
['LICENSE.txt', 'NEWS.txt']
```
<br>

### unicodedata
이 모듈은 모든 유니코드 문자에 대한 문자 속성을 정의하는 유니코드 문자 데이터베이스에 대한 액세스를 제공한다.
* unicodedata.normalize(form, unistr) : 유니코드 문자열에 대한 정규확 형식 form을 반환함. form : <NFC>, <NFKC>, <NFD> 
* unicodedata.category(chr) : chr 문자에 할당된 일반 범주를 문자열로 반환함 
    * LU : Letter Upper case
    * Ll : Letter Lower case
    * Mn : Mark, no spacing
    
```python
import unicodedata

all_letters = string.ascii_letters + " .,;'"  # "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ .,:''"
n_letters = len(all_letters)    # 58

# 유니코드 문자열 --> ASCII로 변환
def unicodeToAscii(s):
    return ''.join(
        c for c in unicodedata.normalize('NFD', s)
        if unicodedata.category(c) != 'Mn' and c in all_letters
    )
```
<br>

### os.path
경로명에 유용한 함수를 구현한 라이브러리이다. 
* os.path.basename(path) : 경로명 path의 기본 이름을 반환. 
* os.path.splitext(path) : 경로명 path의 root+ext에서 root, ext를 분리함
```python
import os
    
str = './data/names\\Arabic.txt'
print(os.path.basename(str)) # Arabic.txt
print(os.path.splitext(os.path.basename(str)) # ('Arabic', '.txt')
```
<br>
    
### 인코딩 확인 방법 - chardet
chardet는 미리 문자열셋을 판단해주는 패키지이다. 

![image](https://user-images.githubusercontent.com/39071676/146897594-a4eec407-7844-4431-95d1-ca4f1630c6d0.png)

<br>

### autoreload 
외부에서 import한 모듈을 수정사항 발생 시 매번 Reload하기 번거롭기 때문에 자동 reload하는 방법이다.
`%autoreload 2` 의미는 Python code를 항상 실행하기 전에 항상 모든 모듈을 Reload하라는 의미이다. 
```python
%load_ext autoreload
%autoreload 2
```
<br>
