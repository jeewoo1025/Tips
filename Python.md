### requirements.txt로 패키지 한번에 관리하기
requirements.txt는 다수의 패키지 목록이 나열되어 있는 텍스트 파일이다. (대부분 프로젝트에서 이 이름으로 관리함) <br>
```shell
pip3 install -r requirements.txt
```
<br>

### 라이브러리
#### `numpy` 
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

