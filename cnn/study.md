# 💡CNN (Convolutional Neural Network) 
> 이미지나 영상을 다루는 컴퓨터 비전에서 가장 대표적으로 사용되는 인공신경망
> - Convolutional Layer : 이미지의 공간적 정보를 학습
> - Pooling Layer : Convolutional Layer의 차원 형태의 크기를 줄임으로써 학습 Parameter 개수를 감소
> - Fully Connected Layer : 최종 출력을 위한 다층 퍼셉트론 구조
>   
> <img src="https://github.com/user-attachments/assets/2ab33966-9714-463b-8dd6-2b7b88083df0" width="300"/>

## 📌 Convolutional Layer
- CNN에서 가장 핵심이 되는 부분으로 이미지의 중요한 정보를 뽑는 역할을 한다. 
- 이미지에 Filter를 적용하여 Convolution(합성곱 연산)을 수행한다. 
 
<img src = "https://github.com/user-attachments/assets/69efaff8-5250-4034-a58b-4c0f55102857" width="300"/>

### Filter (또는 Kernel) 
Filter는 CNN에서 학습할 가중치로써 다층 퍼셉트론과 마찬가지로 초기에는 랜덤으로 주어지며 손실함수가 줄어드는 방향으로 학습된다.
다양한 특징을 뽑기 위해 여러 개의 Filter를 사용하며 CNN 내부에서 다양한 Filter를 적용한 feature map으로 이미지의 여러 정보를 결합하여 분류를 잘하도록 학습이 진행된다. 


### Hyperparameters (초매개변수) 
Convolutional Layer에서 정해야 할 **Hyperparameter** 로는 Filter 크기, Stride와 Padding 사용 여부가 있다. 
- Stride : Filter 를 움직이는 간격
- Padding : Convolution을 수행하면 크기가 줄어드는 것을 방지하고자 입력 이미지 외각에 임의의 값(0또는 이미지의 최외곽과 동일한 값)을 부여하는 기술

<img src = "https://github.com/user-attachments/assets/8d6bf2ba-75b0-4707-8592-1d4ee4eabbde" width = "300"/>

## 📌 Pooling Layer (폴링 계층) 
Convolutional Layer로 계산된 feature map 의 크기를 줄여 연산량을 줄이는 역할을 한다. 
Convolutional Layer와 달리 단순 계산만 진행하기 때문에 학습한 가중치는 따로 없다. 
또한 Pooling Layer는 모든 Convolution Layer에 적용할 필요는 없으며 선택사항이다. 

<img src = "https://github.com/user-attachments/assets/c7f5b1f1-7a28-4fc8-93c4-aaf496228347" width = "300"/>

### 종류 
- Max Pooling : 영역 내에서 최대값만 추출
- Average Pooling : 평균값을 계산


## 📌 Fully-Connected Layer (완전연결층) 
이미지의 입력 데이터는 Convolutional Layer와 Pooling Layer를 통과하면서 주요 특징만 추출된 여러 개의 feature map의 형태이다.  고차원의 feature map이 출력값의 형태인 1차원 벡터로 변환되기 위해 Flatten Layer를 거치게 된다.  Fully-Connected Layer는 Flatten Layer를 통과한 벡터를 출력값의 길이로 변환시키는 역할을 한다.  MLP 구조와 같기 때문에, 여러 Layer를 쌓아 원하는 구조로 구성하면서 마지막 출력층의 노드 개수만 목적에 맞게 설계하면 된다.  일반적으로 Fully-Connected Layer는 Convolutional Layer보다 가중치가 많이 필요하므로 Layer를 많이 쌓는 것은 과적합 및 학습 속도를 늦추는 원인이 된다.  

