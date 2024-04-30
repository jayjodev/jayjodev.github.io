---
title: machine learning
author: Jay Jo
date: 2024-12-11 00:00:00 +09:00
categories: [Artificial Intelligence]
tags: [AI]
image: /assets/img/posts/machine-learning.png
---

## 기계학습 이란?
기계학습이란 특정한 응용 영역에서 발생하는 데이터(경험)를 이용하여 높은 성능으로 문제를 해결하는 컴퓨터 프로그램을 만드는 작업

즉 기계학습이란 가장 정확하게 예측할 수 있는, 즉 최적의 매개변숫값을 찾는 작업. 학습과정을 마치면 그때부터 학습된 모델을 이용하여 예측할 수 있다.

훈련집합에 없는 새로운 샘플에 대한 목표값을 예측하는 과정이 테스트 이며, 기계학습의 최족 목표는 훈련집합에 없는 새로운 샘플에 대한 오류를 최소화 하는 것이다. 

## 기계학습의 차원

기계학습에서 "차원"은 일반적으로 데이터의 특성(Features) 또는 속성(Attributes)의 수를 의미합니다. 각 차원은 데이터 내의 다양한 정보를 나타내며, 이러한 정보는 기계학습 모델이 학습하는 데 사용됩니다. 차원에 대해 자세히 설명하자면:

1. 차원의 예
데이터 포인트: 데이터 포인트 내의 각 특성은 하나의 차원을 대표합니다. 예를 들어, 주택 가격을 예측하는 모델에서는 평방 미터, 방의 개수, 위치, 건축 연도 등 각각의 특성이 하나의 차원을 나타냅니다.
이미지 처리: 이미지 처리에서는 각 픽셀의 색상 값이 차원을 이룹니다. 컬러 이미지의 경우 각 픽셀은 보통 세 개의 차원(RGB)을 가집니다.
2. 차원의 중요성
특성 선택: 불필요하거나 중복되는 특성을 제거함으로써 차원을 줄이는 것은 모델의 성능을 향상시키고 계산 비용을 줄이는 데 도움이 됩니다.
모델 복잡도: 차원이 많아질수록 모델이 학습해야 할 패턴이 복잡해지고, 이는 과적합(Overfitting)으로 이어질 수 있습니다.
3. 차원의 저주(Curse of Dimensionality)
차원이 많아질수록 각 차원 내의 데이터 포인트들 사이의 거리가 급격히 증가합니다. 이는 여러 가지 문제를 일으키는데, 대표적으로:

데이터 부족: 높은 차원에서는 동일한 양의 데이터도 희박(Sparse)해 보일 수 있습니다. 즉, 모델이 학습하기에 충분한 데이터를 확보하기 어렵습니다.
계산 복잡도 증가: 차원이 많아질수록 모델을 훈련시키는 데 필요한 계산량과 시간이 증가합니다.
성능 저하: 차원이 증가하면 일반화를 위해 필요한 데이터 양도 증가합니다. 적절한 데이터가 없다면 모델의 성능이 저하될 수 있습니다.
4. 차원 축소(Dimensionality Reduction)
차원 축소는 고차원 데이터를 저차원의 데이터로 변환하는 기술입니다. 이는 데이터의 중요한 정보를 유지하면서 차원의 수를 줄이는 것을 목표로 합니다. PCA(주성분 분석), t-SNE, LDA(선형 판별 분석) 등이 대표적인 차원 축소 기법입니다.
차원은 데이터의 복잡성을 나타내는 중요한 요소로, 기계학습 모델의 성능과 직접적으로 관련이 있습니다. 따라서 효과적인 차원 관리는 기계학습에서 매우 중요합니다.

## 목적함수 란?
목적함수(Objective Function), 또는 비용함수(Cost Function) 또는 손실함수(Loss Function)는 기계학습에서 모델이 최적의 성능을 찾아가는 과정에서 핵심적인 역할을 합니다. 이 함수는 기계학습 모델이 얼마나 잘 또는 얼마나 못하고 있는지를 수치적으로 나타내며, 모델 훈련 과정에서 이 값을 최소화하거나 최대화하는 방향으로 모델을 조정합니다. 목적함수가 등대와 같은 역할을 하는 이유는 다음과 같습니다:

1. 성능 평가
목적함수는 모델의 현재 성능을 정량적으로 평가합니다. 이 수치는 모델이 학습 데이터에 얼마나 잘 맞는지, 즉 예측 오차가 얼마나 되는지를 나타냅니다. 예를 들어, 회귀 문제에서는 평균 제곱 오차(Mean Squared Error, MSE)가 자주 사용되며, 분류 문제에서는 교차 엔트로피(Cross-Entropy)가 사용됩니다.

2. 학습 방향 지시
목적함수는 모델이 학습 과정에서 따라야 할 방향을 제시합니다. 즉, 이 함수의 값을 최소화하거나 최대화함으로써 모델의 매개변수를 조정합니다. 경사하강법(Gradient Descent)과 같은 최적화 알고리즘이 이 목적함수의 기울기(Gradient)를 계산하여 모델의 매개변수를 업데이트합니다.

3. 모델의 일반화
적절한 목적함수를 선택하면 모델의 일반화 능력을 향상시킬 수 있습니다. 즉, 훈련 데이터 뿐만 아니라 새로운, 보지 못한 데이터에 대해서도 잘 작동하는 모델을 만들 수 있습니다. 예를 들어, 과적합을 방지하기 위해 정규화 항(Regularization term)을 목적함수에 추가할 수 있습니다.

4. 최적화 프로세스의 안내
목적함수는 모델의 최적화 과정에서 '등대'와 같은 역할을 합니다. 이 함수의 값을 최소화하거나 최대화하는 방향으로 매개변수를 조정함으로써, 모델이 점진적으로 개선됩니다. 이 과정은 마치 등대가 배에게 방향을 제시하는 것과 유사합니다.

결론:
기계학습에서 목적함수는 모델의 성능을 평가하고, 최적화 과정에서 방향을 제시하는 중요한 역할을 합니다. 이를 통해 모델은 점차 최적의 매개변수를 찾아가며, 이는 곧 최적의 성능을 달성하는 것을 의미합니다.

### 목적 함수 (손실 함수)의 예시 
### 1. 회귀 문제

**상황**: 연속적인 값을 예측하고 싶은 경우 (예: 주택 가격, 온도 등)

**목적함수**: 평균 제곱 오차(Mean Squared Error, MSE)
- **식**: $$( MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 )$$
- **설명**: $$( y_i )$$는 실제 값, $$( \hat{y}_i )$$는 모델이 예측한 값, $$( n )$$은 데이터 포인트의 개수입니다. MSE는 실제 값과 예측 값 사이의 차이의 제곱의 평균을 측정합니다.

### 2. 분류 문제

**상황**: 레이블(카테고리)을 예측하고 싶은 경우 (예: 이메일 스팸 분류, 이미지 분류 등)

**목적함수**: 교차 엔트로피(Cross-Entropy)
- **식**: $$( CE = -\sum_{i=1}^{n} y_i \log(\hat{y}_i) )$$
- **설명**: $$( y_i )$$는 실제 레이블(0 또는 1), $$( \hat{y}_i )$$는 모델이 예측한 확률입니다. 교차 엔트로피는 모델이 실제 레이블을 얼마나 잘 예측하는지를 측정합니다.

### 3. 클러스터링 문제

**상황**: 데이터를 유사한 그룹으로 나누고 싶은 경우 (예: 고객 세분화)

**목적함수**: 클러스터 내 분산 최소화
- **식**: 일반적으로 유클리드 거리의 합을 최소화하는 형태입니다.
- **설명**: 클러스터링에서는 클러스터 내부의 데이터 포인트 간 거리를 최소화하여, 유사한 데이터 포인트들이 같은 클러스터에 속하도록 합니다.

각 문제 유형에 따라 적절한 목적함수를 선택하고, 이를 최적화하는 것이 기계학습에서 중요합니다. 데이터의 특성과 문제의 목적에 맞는 목적함수를 정의하는 것이 핵심입니다.


1번 상황인 회귀 문제에 대해 목적함수를 예를 들어 만들어 보겠습니다. 가정해볼 수 있는 상황은 주택 가격 예측입니다.

죄송합니다, 내용을 다시 확인하고 필요한 수정을 해서 다시 제공하겠습니다. 경사 하강법을 사용한 가중치 찾기 과정을 명확하게 표현하겠습니다. 

### 경사 하강법을 이용한 가중치 찾기

#### 초기화
- 가중치 \( w \)를 임의의 값으로 초기화합니다.

#### 그래디언트 계산
- MSE에 대한 \( w \)의 그래디언트를 계산합니다.
  $$ \frac{\partial MSE}{\partial w} = \frac{-2}{N} \sum_{i=1}^{N} x_i (y_i - \hat{y}_i) $$

#### 가중치 업데이트
- 그래디언트를 사용하여 가중치를 업데이트합니다.
  $$ w = w - \alpha \cdot \frac{\partial MSE}{\partial w} $$

#### 반복
- 위의 과정을 목적함수가 수렴할 때까지 반복합니다.

#### 목적함수 (MSE) 
- 평균 제곱 오차(Mean Squared Error)
  $$ MSE = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2 $$

이 과정을 통해, 모델은 주어진 데이터에 대해 최적의 가중치 $$( w )$$ 를 찾아가며, 이는 주택 가격을 예측하는 데 사용됩니다. 경사 하강법은 반복적인 최적화 방법으로, 각 단계에서 모델의 성능을 조금씩 개선합니다.

기계학습에서 목적함수를 사용하는 주된 목적은 모델의 파라미터(예: 가중치 $$( w )$$ )를 최적화하는 것입니다. 목적함수 자체는 모델의 성능을 측정하는 기준을 제공합니다. 결국, 이 목적함수를 최소화(또는 최대화)하는 과정에서 최적의 파라미터 값을 찾는 것이 핵심입니다.

### 목적함수와 파라미터 최적화

1. **목적함수의 역할**: 목적함수는 모델이 학습 데이터에 얼마나 잘 적합하는지를 수치적으로 나타냅니다. 예를 들어, 회귀 문제에서 평균 제곱 오차(MSE)나 분류 문제에서의 교차 엔트로피(Cross-Entropy) 등이 이에 해당합니다.

2. **파라미터 최적화**: 목적함수의 값을 최소화하는 모델 파라미터(가중치 $$( w )$$ 와 편향 $$( b )$$ 등)를 찾는 과정입니다. 이 과정은 보통 경사 하강법과 같은 최적화 알고리즘을 통해 이루어집니다.

### 최종 목표

- **모델 성능 향상**: 최적의 파라미터를 찾음으로써, 모델의 성능을 개선합니다. 즉, 새로운 데이터에 대한 모델의 예측 정확도를 높이는 것이 최종 목표입니다.

- **일반화 능력 강화**: 또한, 좋은 목적함수와 적절한 최적화 과정은 모델이 학습 데이터에만 과적합(overfitting)하지 않고, 일반적인 데이터에 대해서도 잘 작동하도록 만듭니다.

요약하자면, 기계학습에서 목적함수를 사용하는 궁극적인 목적은 가장 효과적인 파라미터(가중치 $$( w )$$)를 찾아 모델의 성능을 최적화하는 것입니다.

다만, 기계학습의 최종 목표는 훈련 집합에 없는 새로운 샘플을 정확하게 예측하는 것이므로 과소적합이나 과잉적합 모두 바람직하지 않다.

---


비지도 학습에서는 목적함수가 있긴 하지만, 지도 학습과는 다르게 작동합니다. 비지도 학습의 경우, 학습 데이터에 레이블이나 명확한 '정답'이 주어지지 않습니다. 대신, 데이터의 구조, 패턴, 분포를 학습하여 유의미한 정보를 추출하는 데 초점을 맞춥니다. 

비지도 학습에서 사용되는 목적함수의 예시는 다음과 같습니다:

1. **클러스터링(Clustering)**: 클러스터링 알고리즘(예: K-평균)은 데이터 포인트를 유사한 그룹으로 나눕니다. 이때의 목적함수는 클러스터 내 분산을 최소화하고 클러스터 간 분산을 최대화하는 것입니다. 예를 들어, K-평균에서는 클러스터 내 제곱 오차의 합을 최소화합니다.

2. **차원 축소(Dimensionality Reduction)**: 예를 들어, 주성분 분석(PCA)는 데이터의 분산을 최대한 보존하면서 차원을 축소하는 것을 목적으로 합니다.

3. **자기 인코딩(Autoencoding)**: 자기 인코더는 입력을 저차원 공간으로 압축한 후 다시 복원하는 방식으로 작동합니다. 목적함수는 복원된 데이터가 원본 데이터와 얼마나 유사한지를 측정합니다.

비지도 학습에서 목적함수는 데이터의 숨겨진 구조나 패턴을 발견하는 데 도움을 주며, 이를 통해 데이터의 특성을 더 잘 이해하거나, 데이터를 효율적으로 표현하거나, 유용한 정보를 추출하는 데 사용됩니다.