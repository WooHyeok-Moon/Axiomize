---
author: "Woohyeok Moon"
date: 2023-07-11
title: AI대학원 면접 준비
categories: Artificial Intelligence
tags: [Machine Learning, Deep Learning]
showtoc: false
weight: 10
---

## 1. L1, L2 Regulerization

- 과제: 과적합을 감소시켜야 한다.
- 해결 방법: 규제(Regulerization)

- 과적합을 감소시키기 위해서 규제라는 개념을 도입하게 되는데, 이렇게 규제가 적용된 regression에는 Ridge와 Lasso가 있다.

- Ridge는 L2, Lasso는 L1 norm이 규제로써 작동되는 regression으로, L1 norm은 manhattan distance이고, L2 norm은 euclidean distance의 개념이다.

- L1 norm은 특정 feature을 없앨 수 있어 feature selection에 유리하다.

- L2 norm은 제곱 연산이 들어있어 이상치에 민감하다.

- L1 norm은 절댓값이 취해져 있어 0에서 미분불가능하다

## Gradient Descent

- 손실함수의 비용이 최소가 되는 지점을 찾을 때까지 기울기가 낮은 쪽으로 계속 이동시키는 과정을 반복한다.

- 이때 x축은 weight, y축은 cost이다. cost가 최소가 되도록 weight값을 갱신하는 과정을 반복

- 초기 형태인 Batch Gradient Descent는 한 번에 모든 데이터를 업데이트하기 때문에 대용량 데이터를 처리하기에 적합하지 않다. 

## Sthochastic Gradient Descent

- 그리하여 데이터셋을 batch 단위로 쪼개 학습하는 방법을 적용하게 된다.

## Batch Normalization

- internal covariate shift를 줄이기 위한 기법

- covariate shift란 train set의 분포와 test set의 분포가 달라 제대로 예측하지 못하는 현상을 말함

- internal covariate shift는 이러한 현상이 neural network 내부에서 일어나는 것을 말하는데, hidden layer에 입력으로 들어오는 데이터의 분포가 달라지는 것을 의미하며, layer가 깊을수록 심화될 수 있다.

- 또한 이는 mini batch 기법에서는 batch마다 분포가 달라져 특히 성능에 critical한 문제가 될 수 있다.

- 이 분포를 단순히 whitening하게 되면 편향이 사라지게 되어 유의미한 정보가 유실될 수 있다.

- batch마다 평균과 분산을 계산하여 표준화하되 scale factor($\gamma$)와 shift factor($\beta$)를 적용시킨다.

- 학습 시 batch normalization은 activation function으로 들어가기 전에 수행되는데, scale factor와 shift factor가 들어옴으로써 relu를 사용할 때 음수에 해당하는 부분이 모두 0으로 사라져버리는 것을 방지할 수 있고, sigmoid activation function을 사용할 때 비선형성이 사라지는 현상 또한 방지할 수 있고, normalization하기 전인 원래 형태에 대해서도 학습을 진행할 수 있어 backpropagation 또한 적용할 수 있다.

- 추론 시 batch normalization은 테스트 데이터 하나에 대해 답을 내야 하므로 평균과 분산을 낼 수 없으므로 training 시 mini-batch들의 평균과 분산을 대신 사용한다.

## CNN(Convolution Neural Network)

- 기존의 DNN은 1차원 형태의 데이터를 사용하므로 2차원 형태의 이미지가 입력값으로 들어왔을 때에는 1차원으로 Flatten시켜줘야 한다. 이 과정에서 정보 손실이 일어난다. 또한 추상화 과정 없이 바로 연산을 진행하는데, 이로 인해 효율성이 저하된다.

- CNN은 이미지를 이미지 그대로 받아 공간적/지역적 정보를 유지할 수 있다.

- 이미지는 이미지 전체보다는 특징적인 부분과 그 주변 픽셀들의 연관성에 집중해야 한다. CNN은 이를 위해 Convolution 연산을 사용한다.

- 하나의 Convolution layer에는 Convolution과 Activation이 포함되어 있다. Activation Function으로는 RELU를 사용한다.

- 이후 생성된 여러 개의 결과값에 Max Pooling을 적용하여 크기를 줄여준다.

- 다시 Convolution, Activation, Pooling을 진행한다.

- 나온 Feature data들을 Flatten하여 1차원 형태의 데이터로 만든다.

- FC(Fully connected) layer를 통과시켜 Softmax를 적용해주면 최종 output이 나온다.

## Activation Function

- 활성화 함수는 선형 분류기를 비선형 분류기로 만들어주는 역할을 한다.

- 선형 함수를 사용하면 층을 깊게 쌓는 의미가 없다.

- 활성화 함수 없이 feedforwarding을 진행하게 된다면 아래와 같이 진행된다.
$$
\begin{align}
   f(x) &= w \times x\\\
   f(f(x)) &= w \times w \times x &= w^2x\\\
   f(f(f(x))) &= w \times w \times w \times x &= w^3x\\\
   &\dots
\end{align}
$$

- 이는 $y = ax$인 선형 함수에서 $a = w^3$인 선형 함수가 되었을 뿐이며 이는 weight가 $w^3$인 한 개 층으로도 네트워크를 구성할 수 있음을 의미한다. -> Deep Network의 의미가 없다.
