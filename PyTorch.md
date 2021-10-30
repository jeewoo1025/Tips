### GPU에서 저장하고 GPU에서 불러오기
**GPU 모델 저장**
```shell
torch.save(model.state_dict(), PATH)
```

**저장한 모델을 GPU에서 로드**
```shell
# GPU device 저장
device = torch.device("cuda")

# 모델 불러오기
model = TheModelClass(*args, **kwargs)
model.load_state_dic(torch.load(PATH))
model.to(device)
```
GPU에서 학습된 모델을 GPU에서 불러올 때는 초기화된 model에 model.to(torch.device('cuda'))를 호출하여 CUDA 최적화 모델로 변환해야 함 <br>
또한 모델에 데이터를 제공하는 모든 입력에 .to(torch.device('cuda')) 함수를 호출해야한다. <br>
* 참조 : https://tutorials.pytorch.kr/beginner/saving_loading_models.html#device
<br>

### squeeze, unsqueeze 함수
* squeeze 함수 : 차원이 1인 차원을 제거해준다. 따로 차원을 설정하지 않으면 1인 차원을 모두 제거한다. 
```python
x = torch.rand(3,1,20,128)
x = x.squeeze() # [3,1,20,128] --> [3,20,128]
```

* unsqueeze 함수 : 1인 차원을 생성하는 함수이다. 그래서 어느 차원에 1인 차원을 생성할지 꼭 지정해주어야 한다.
```python
x = torch.rand(3,20,128)
x = x.unsqueeze(dim=1) # [3,20,128] -> [3,1,20,128]
```
