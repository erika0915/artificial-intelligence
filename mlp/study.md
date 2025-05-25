# 💡MLP (Multi-Layer Perceptron)
> MLP는 입력층(input layer)와 출력층(output layer) 사이에 한 개 이상의 은닉층(hidden layer)이 쌓인 구조
> - 입력층(input layer) : 입력 데이터를 받는 layer
> - 은닉층(hidden layer) : 이전 레이어의 출력과 가중치 곱의 합을 입력받음으로써 활성 함수가 적용된 layer
> - 출력층(output layer) : 다층 퍼셉트론에서 최종 결과를 얻는 layer
> <img src="https://github.com/user-attachments/assets/97ea8427-d308-44c1-9983-3fe24b2eacd6" width="300"/>

## MLP에서 사용되는 주요 구성 요소 및 학습 기법 
MLP는 완전연결 신경망 구조로, 다양한 학습 보조 기법을 통해 성능을 높이고 과적합을 방지할 수 있다. 아래는 MLP에서 자주 활용하는 대표적인 구성 요소와 학습 기법들을 분류해서 정리해놓았다. 

### 1. 모델 구성 요소 (구조적 요소) 
- `활성화 함수 (Activation Function)` : 선형 계층만 반복하면 비선형 패턴 학습이 불가능하므로 비선형 함수가 반드시 필요하다.

  | 함수 | 특징 |
  |------|------|
  | Sigmoid | 0~1 출력, gradient 소실 문제가 있음 |
  | Tanh  | -1~1 출력, Sigmoid보다 출력 범위 넓고 대칭적 |
  | ReLU    | 0 이상만 출력, 학습 빠르고 효과 좋음 (기본값처럼 사용됨) |


- `출력 함수 (Output Layer)` : 문제의 유형에 따라 다른 손실 함수 및 출력 방식이 사용된다.
  
  | 문제 유형 | 출력 함수 / 손실 함수 |
  |-----------|------------------------|
  | 다중 클래스 분류| `CrossEntropyLoss` (Softmax 내장) |
  | 이진 분류        | `Sigmoid` + `BCEWithLogitsLoss` |
  | 회귀             | `Linear` 출력 + `MSELoss` 등 사용 |

### 2. 학습 방법 (Training Methods) 
- `미니 배치 (Mini-batch)` : 전체 데이터를 작은 묶음(batch)으로 나누어 학습. 이렇게 되면 학습이 더 안정적이고 메모리 효율적이게 된다.
- `경사하강법 (Gradient Descent)` : 손실함수를 줄이기 위한 최적화 기법으로, 신경망 학습의 기본 원리
> Optimizer : 딥러닝 모델이 경사하강법을 어떻게 적용할지를 결정하는 구체적인 알고리즘 
>  
  | Optimizer | 특징 |
  |-----------|------|
  | SGD   | 단순하고 널리 사용됨 |
  | Adam  | 적응형 학습률 사용, 빠르게 수렴 |
  | RMSprop | 시간에 따른 변화 반영, 시계열에 강함 |

### 3. 정규화 기법 (Regularization Techniques) 
- `드롭아웃 (Dropout)` : 학습 시 일부 뉴런을 무작위로 비활성화(drop)하여 과적합을 방지. 일반화 성능 향상에 효과적이다.
- `배치 정규화 (Batch Normalization)` : 각 미니배치마다 입력의 분포를 정규화하여 학습 안정화와 수렴 속도 향상을 도모

