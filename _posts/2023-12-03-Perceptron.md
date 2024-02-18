---
title: Perceptron Model
author: Jay Jo
date: 2023-12-03 00:00:00 +09:00
categories: [Artificial Intelligence]
tags: [AI]
---

# 퍼셉트론 모델

퍼셉트론 모델은 인공 신경망의 가장 기본적인 형태 중 하나로, 프랑크 로젠블라트가 1957년에 개발한 알고리즘입니다. 이는 입력과 출력으로 구성된 단순한 선형 분류기입니다.

## 퍼셉트론 작동 원리:

1. **입력값과 가중치**: 각 입력값은 해당 입력의 중요도를 나타내는 가중치와 결합됩니다. 입력값은 해당 가중치와 곱해집니다.

2. **합산 및 활성화 함수**: 입력값과 가중치의 곱셈 결과를 모두 더한 후, 활성화 함수를 통과시켜 출력을 생성합니다. 대표적인 활성화 함수로는 단계 함수가 있습니다.

3. **출력**: 활성화 함수의 결과에 따라, 퍼셉트론은 두 가지 클래스 중 하나로 입력 데이터를 분류합니다.

퍼셉트론은 간단한 선형 문제에는 효과적이지만, XOR 문제와 같은 비선형 문제를 해결하는 데는 한계가 있습니다.

## Python 코드 예시:

```python
import numpy as np

class Perceptron:
    def __init__(self, learning_rate=0.01, n_iters=1000):
        self.lr = learning_rate
        self.n_iters = n_iters
        self.activation_func = self._unit_step_func
        self.weights = None
        self.bias = None

    def fit(self, X, y):
        n_samples, n_features = X.shape
        self.weights = np.zeros(n_features)
        self.bias = 0

        y_ = np.array([1 if i > 0 else 0 for i in y])

        for _ in range(self.n_iters):
            for idx, x_i in enumerate(X):
                linear_output = np.dot(x_i, self.weights) + self.bias
                y_predicted = self.activation_func(linear_output)
                update = self.lr * (y_[idx] - y_predicted)
                self.weights += update * x_i
                self.bias += update

    def predict(self, X):
        linear_output = np.dot(X, self.weights) + self.bias
        return self.activation_func(linear_output)

    def _unit_step_func(self, x):
        return np.where(x >= 0, 1, 0)
```
