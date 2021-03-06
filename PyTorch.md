![image](https://user-images.githubusercontent.com/39071676/143232700-9a223812-4f38-4433-a33d-ee5fac9d82e8.png)
<img width="35%" src="https://user-images.githubusercontent.com/39071676/154631900-f26b846b-ebe6-473c-95b9-c5fed8aac566.png">

### GPU에서 저장하고 GPU에서 불러오기
**GPU 모델 저장**
```shell
torch.save(model.state_dict(), PATH)
```

**저장한 모델을 GPU에서 로드**
```shell
# GPU device 저장
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

# 모델 불러오기
model = TheModelClass(*args, **kwargs)
model.load_state_dic(torch.load(PATH))
model.to(device)
```
GPU에서 학습된 모델을 GPU에서 불러올 때는 초기화된 model에 model.to(torch.device('cuda'))를 호출하여 CUDA 최적화 모델로 변환해야 함 <br>
또한 모델에 데이터를 제공하는 모든 입력에 .to(torch.device('cuda')) 함수를 호출해야한다. <br>
* 참조 : https://tutorials.pytorch.kr/beginner/saving_loading_models.html#device
<br>

### view()
원소의 수를 유지하면서 텐서의 크기(shape)를 변경한다

**view 규칙**
1) view는 기본적으로 변경 전과 변경 후의 Tensor 안의 원소의 개수가 유지되어야 한다
2) view는 사이즈가 설정되면 다른 차원으로부터 해당 값을 유추한다.
```python
ft2 = np.array([[[0, 1, 2],[3, 4, 5]],[[6, 7, 8],[9, 10, 11]]])
ft2 = torch.FloatTensor(ft2)
print('ft2:', ft2, ',  shape:', ft2.shape)

# view를 사용하여 shape을 2차원 텐서로 변경
print(ft2.view([-1, 3]))    # ft라는 텐서를 (?,3) 크기로 변경
print(ft2.view([-1, 3]).shape)  # -1 : 1번째 차원은 사용자가 잘 모르겠으니 PyTorch에 맡기겠다
```
<br>

### squeeze(), unsqueeze()
* squeeze 함수 : 차원이 1인 차원을 제거해준다. 따로 차원을 설정하지 않으면 1인 차원을 모두 제거한다. 
```python
x = torch.rand(3,1,20,128)
x = x.squeeze() # [3,1,20,128] --> [3,20,128]
```

* unsqueeze 함수 : 특정 위치에 1인 차원을 추가한다. 그래서 어느 차원에 1인 차원을 생성할지 꼭 지정해주어야 한다.
```python
x = torch.rand(3,20,128)
x = x.unsqueeze(dim=1) # [3,20,128] -> [3,1,20,128]
```
<br>

### torch.no_grad()
해당 블록을 history 트래킹 하지 않겠다는 뜻이다. 
역전파를 수행후 모델의 기울기를 이용하여 가중치와 bias를 업데이트한다. 다음 기울기 계산에 기록되지 않도록 torch.no_grad()를 실행한다.
```python
with torch.no_grad():
    pred = model(x)
    predicted, actual = classes[pred[0].argmax(0)], classes[y]
    print(f'Predicted: "{predicted}", Actual: "{actual}"')
```
<br>

### Tensor
* 2D Tensor : (Batch size, dim) 행의 크기가 batch_size, 열의 크기가 dim이라는 뜻이다. <br>
![image](https://user-images.githubusercontent.com/39071676/141058380-ced90306-39f1-4e4c-9d33-86267a23fefe.png)
* 3D Tensor : (Batch size, length, dim) (batch_size, 문장 길이, 단어 벡터의 차원) <br>
![image](https://user-images.githubusercontent.com/39071676/141058364-9c155e33-33db-4f91-a5fe-abf545fbb2d0.png)
<br>

#### Tensor 생성
* 랜덤한 값을 가지는 Tensor 생성
1. torch.rand() : 0과 1 사이의 숫자를 균등하게 생성
2. torch.rand_like() : 사이즈를 튜플로 입력하지 않고 기존의 텐서로 정의
3. torch.randn() : 평균이 0이고 표준편차가 1인 가우시안 정규분포를 이용해 생성
4. torch.randn_like() :  사이즈를 튜플로 입력하지 않고 기존의 텐서로 정의
5. torch.randint() : 주어진 범위 내의 정수를 균등하게 생성, 자료형은 torch.float32
6. torch.randint_like() : 사이즈를 튜플로 입력하지 않고 기존의 텐서로 정의
7. torch.randperm() : 주어진 범위 내의 정수를 랜덤하게 생성
<br>

* 특정한 값을 가지는 Tensor 생성
1. torch.arange() : 주어진 범위 내의 정수를 순서대로 생성
2. torch.ones() : "주어진 모양의 텐서를 만들어주는데, 1로 채워줘."
3. torch.zeros() : "주어진 모양의 텐서를 만들어주는데, 0으로 채워줘."
4. torch.ones_like() :  "입력 텐서와 동일한 모양의 텐서를 만들어주는데, 1로 채워줘."
5. torch.zeros_like() : "입력 텐서와 동일한 모양의 텐서를 만들어주는데, 0으로 채워줘."
6. torch.linspace() : 시작점과 끝점을 주어진 갯수만큼 균등하게 나눈 간격점을 행벡터로 출력
7. torch.logspace() : 시작점과 끝점을 주어진 갯수만큼 로그간격으로 나눈 간격점을 행벡터로 출력
<br>

### optim 패키지
PyTorch의 optim 패키지는 최적화 알고리즘에 대한 아이디어를 추상화하고 일반적으로 사용하는 최적화 알고리즘 구현체를 제공한다
* SGD, AdaGrad, RMSProp, Adam 
```python
optimizer = torch.optim.RMSprop(model.parameters(), lr=learning_rate)

# optimizer의 step 함수를 호출하면 매개변수가 갱신된다
optimizer.step()
```
<br>

### Tensor 합치기: cat(), stack()
**cat 함수** : concatenate를 해주는 함수이고 차원의 수는 유지된다.  <br>
**stack 함수** : 지정하는 차원으로 확장하여 tensor를 쌓아주는 함수이다. (차원의 수가 증가한다) <br>
```python
import torch

batch_size, N, K = 3, 10, 256

x = torch.rand(batch_size, N, K) # [2, 10, 256]
y = torch.rand(batch_size, N, K) # [2, 10, 256]

output1 = torch.cat([x,y]) # [4, 10, 256]
output2 = torch.stack([x,y]) # [M,2,N,K]
```
<br>

### torch.topk()
```python
torch.topk(input, k, dim=None, largest=True, sorted=True, *, out=None) -> (Tensor, LongTensor)
```
주어진 차원을 따라 주어진 input 텐서의 k개의 가장 큰 요소를 반환한다. 
* input : 입력 텐서
* k : top-k의 k
* dim : 정렬할 차원
<br>

### torch.cumsum()
```python
torch.cumsum(input, dim, *, dtype=None, out=None) → Tensor
```
dim=N의 방향으로 누적합을 구하는 함수이다. 만약 input이 N size의 벡터라면, 결과는 N size의 같은 크기의 벡터를 뱉는다.
![image](https://user-images.githubusercontent.com/39071676/143230205-59b15f28-60b4-46f7-90bf-d7107bf04966.png)
<br>

### torch.scatter_()
target Tensor에 원하는 index에 맞게 src Tensor의 값을 할당해주는 함수

![image](https://user-images.githubusercontent.com/39071676/154638045-606b1545-094d-4700-ae8d-0bdac6613955.png)

torch.scatter_(dim, index, source, reduce=None) → Tensor
* dim (int) : indexing의 기준이 되는 축
* index (LongTensor) : src 구성요소들이 흩어질 기준이 되는 index Tensor로 정수형 텐서로 구성되어야 한다
* src (Tensor or float) : target Tensor를 구성할 값들이 담겨있는 Tensor. 하나의 실수로 선언되면 그 값만으로 채워진다
* reduce (str, optional) : 기존의 값을 어떻게 update할 것인지 정의한다. 'multiply', 'add' 2가지 방법이 존재하며, 정의되지 않을 경우 기존의 값을 없애고 새로운 값으로 치환한다

참고 : [blog](https://hongl.tistory.com/201)
<br>

### register_buffer를 하는 이유
PyTorch로 구현한 Transformer를 공부하다가 Positional encoding code 중 `self.register_buffer('pe', pe)`의 의미를 모르겠어서 찾게 되었다.
```python
class PositionalEncoding(nn.Module):
    "Implement the PE function."
    def __init__(self, d_model, dropout, max_len=5000):
        super(PositionalEncoding, self).__init__()
        self.dropout = nn.Dropout(p=dropout)
        
        # Compute the positional encodings once in log space.
        pe = torch.zeros(max_len, d_model)
        position = torch.arange(0, max_len).unsqueeze(1)
        div_term = torch.exp(torch.arange(0, d_model, 2) *
                             -(math.log(10000.0) / d_model))
        pe[:, 0::2] = torch.sin(position * div_term)
        pe[:, 1::2] = torch.cos(position * div_term)
        pe = pe.unsqueeze(0)
        self.register_buffer('pe', pe)
        
    def forward(self, x):
        x = x + Variable(self.pe[:, :x.size(1)], 
                         requires_grad=False)
        return self.dropout(x)
```

<b>왜 register_buffer로 layer를 등록하는가?</b><br>
* optimizer를 update하지 않는다. 그러나 값은 존재한다.


즉, network를 구성함에 있어서 중간에 update를 하지 않는 layer를 넣고 싶을 때 사용할 수 있다. <br> 이 말은 model parameter로 고려하지 않는 layer를 등록하기 위해서 이를 사용한다는 의미랑 같다. <br>
그러므로 Positional Encoding에서 `self.register_buffer('pe', pe)`란 PE layer(=Positional Encoding)는 학습 시 가중치가 학습되지 않는다를 뜻한다.
<br> 

### Tensorboard 사용법
```python
# tensorboard log 출력
tensorboard --logdir=./log

# 브라우저에 접속
http://localhost:6006/
```
