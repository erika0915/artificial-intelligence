#  MNIST MLP 실험 정리

> 목표: 다양한 MLP 모델 구조, 활성화 함수, 옵티마이저, 학습률을 조합하여 MNIST 숫자 분류 정확도를 비교하고 학습 곡선을 시각화함.

## 📌 실험 개요
- 데이터셋: MNIST (28×28 흑백 손글씨 숫자 이미지)
- 클래스 수: 10개 (0~9)
- 모델 구조: MLP (Fully-connected 신경망)
- 목표: 이미지 → 숫자 분류

## 🧪 실험
### Experiment 1: 기본 MLP

- 구조: 2-layer MLP (784 → 32 → 10)
- Activation: Sigmoid
- Optimizer: SGD (lr=0.1)
- Test Accuracy: 95.03%
- Test Loss: 0.1444
- 학습 곡선:  
  ![image](https://github.com/user-attachments/assets/3f01fd5b-b7a5-4bc6-9295-3c40524defa9)


### Experiment 2: Deep MLP (은닉층 6개)

- 구조: 6-layer MLP (784 → 32 x 6 → 10)
- Activation: Sigmoid
- Optimizer: SGD (lr=0.1)
- Test Accuracy: 11.35%
- Test Loss: 2.3019
- Overfitting + Gradient Vanishing 현상 발생
- 학습 곡선:  
  ![image](https://github.com/user-attachments/assets/e4e69cda-492c-47ca-ac64-d2c1dbfcc9cc)



### Experiment 3: Wide MLP (512 units)

- 구조: 2-layer MLP (784 → 512 → 10)
- Activation: Sigmoid
- Optimizer: SGD (lr=0.1)
- Test Accuracy: 97.08%
- Test Loss: 0.0966
- 학습 곡선:  
  ![image](https://github.com/user-attachments/assets/ff0523c9-61ca-48d3-ad6f-ff4c4d43a54d)



### Experiment 4: Activation Function 비교

- 구조: 2-layer MLP (784 → 32 → 10)
- Optimizer: SGD (lr=0.1)
- 비교 항목:
  - Sigmoid → Accuracy: 낮음
  - Tanh → 중간
  - ReLU → 가장 우수
- Best Accuracy: 96.84% (ReLU 기준)
- Test Loss: 0.1127
- 학습 곡선:  
  ![image](https://github.com/user-attachments/assets/0593367b-6932-4ed4-a269-283de55cc539)



### Experiment 5: Optimizer 변경 (Adam)

- 구조: 2-layer MLP (784 → 512 → 10)
- Activation: Sigmoid
- Optimizer: Adam (lr=0.1)
- Test Accuracy: 83.94%
- Test Loss: 0.7173
- 학습 불안정: 과한 learning rate로 인한 진동
- 학습 곡선:  
  ![image](https://github.com/user-attachments/assets/32d597e1-c5e0-412d-ae38-ce7b5c76e423)



### Experiment 6: Learning Rate 비교 (Adam)

- 구조: 2-layer MLP (784 → 512 → 10)
- Activation: Sigmoid
- Optimizer: Adam
- 학습률 비교:
  - lr = 1.0: Accuracy 11.35%
  - lr = 0.1: Accuracy 96.99%
  - lr = 0.01: Accuracy 97.19% (최고 성능)
- 학습 곡선:  
  ![image](https://github.com/user-attachments/assets/aa6a2b28-2bc0-4a50-8d01-fa2bb2d20f29)



## 📌 결론 요약

| 실험 | 구조                  | 특이점 / 변경점              | Accuracy                          | 비고                               |
|------|-----------------------|-------------------------------|-----------------------------------|------------------------------------|
| 1    | 기본 MLP              | -                             | 95.03%                            | 안정적 기본 성능                   |
| 2    | 깊은 MLP (6층)        | 은닉층 6개                    | 11.35%                            | 학습 실패 (vanishing)              |
| 3    | 넓은 MLP (512 units)  | 은닉 유닛 512                 | 97.08%                            | 성능 향상                          |
| 4    | 다양한 Activation     | Sigmoid / Tanh / ReLU 비교   | 96.84% (ReLU 기준)                | ReLU 성능 가장 우수                |
| 5    | Optimizer 변경        | Adam, lr=0.1                  | 83.94%                            | 불안정 (lr 너무 큼)                |
| 6    | 학습률 비교 (Adam)    | lr=1.0 / 0.1 / 0.01           | 97.19% (lr=0.01 기준 최고 성능)   | lr=0.01이 가장 안정                |


