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


```python

```