---
title: 활성 함수 (Activation Functions)
author: Jay Jo
date: 2024-04-30 00:00:00 +09:00
categories: [ai]
tags: [ai]
---

# 활성 함수 (Activation Functions)

활성 함수는 신경망에서 중요한 역할을 합니다. 여기서는 여러 가지 활성 함수인 시그모이드(Sigmoid), 쌍곡탄젠트(tanh), ReLU, 항등 함수(Identity), 그리고 소프트맥스(Softmax)에 대해 설명하고 Python 코드 예제를 제공합니다.

## 시그모이드 함수 (Sigmoid Function)

시그모이드 함수는 입력값을 0과 1 사이의 값으로 압축합니다. 주로 이진 분류에서 사용됩니다.

### 수식
$$
S(x) = \frac{1}{1 + e^{-x}}
$$

### Python 코드
```python
import numpy as np
import matplotlib.pyplot as plt

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

x = np.linspace(-10, 10, 100)
y = sigmoid(x)

plt.plot(x, y)
plt.title("Sigmoid Function")
plt.xlabel("x")
plt.ylabel("S(x)")
plt.grid(True)
plt.show()
```

## 쌍곡탄젠트 함수 (Hyperbolic Tangent, tanh)

쌍곡탄젠트 함수는 출력 범위가 -1과 1 사이입니다. 시그모이드보다 넓은 출력 범위를 가집니다.

### 수식
$$
\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}
$$

### Python 코드
```python
import numpy as np
import matplotlib.pyplot as plt

def tanh(x):
    return np.tanh(x)

x = np.linspace(-10, 10, 100)
y = tanh(x)

plt.plot(x, y)
plt.title("Hyperbolic Tangent Function")
plt.xlabel("x")
plt.ylabel("tanh(x)")
plt.grid(True)
plt.show()
```

## ReLU 함수 (Rectified Linear Unit)

ReLU 함수는 입력이 0을 초과하면 그 값을 반환하고, 그렇지 않으면 0을 반환합니다.

### 수식
$$
R(x) = \max(0, x)
$$

### Python 코드
```python
import numpy as np
import matplotlib.pyplot as plt

def relu(x):
    return np.maximum(0, x)

x = np.linspace(-10, 10, 100)
y = relu(x)

plt.plot(x, y)
plt.title("ReLU Function")
plt.xlabel("x")
plt.ylabel("R(x)")
plt.grid(True)
plt.show()
```

## 항등 함수 (Identity Function)

항등 함수는 입력을 그대로 출력으로 반환합니다.

### 수식
$$
I(x) = x
$$

### Python 코드
```python
import numpy as np
import matplotlib.pyplot as plt

def identity(x):
    return x

x = np.linspace(-10, 10, 100)
y = identity(x)

plt.plot(x, y)
plt.title("Identity Function")
plt.xlabel("x")
plt.ylabel("I(x)")
plt.grid(True)
plt.show()
```

## 소프트맥스 함수 (Softmax Function)

소프트맥스 함수는 클래스 확률을 계산하기 위해 사용됩니다.

### 수식
$$
\text{Softmax}(z_i) = \frac{e^{z_i}}{\sum_{j} e^{z_j}} 	ext{ for } i = 1, 2, ..., K 	ext{ and } z = (z_1, ..., z_K)
$$

### Python 코드
```python
import numpy as np
import matplotlib.pyplot as plt

def softmax(z):
    exp_z = np.exp(z)
    return exp_z / np.sum(exp_z)

z = np.linspace(-10, 10, 100)
y = softmax(z)

plt.plot(z, y)
plt.title("Softmax Function")
plt.xlabel("z")
plt.ylabel("Softmax(z)")
plt.grid(True)
plt.show()
```

### Python 코드
```python
import torch
import torch.nn as nn
import matplotlib.pyplot as plt

# Softmax 모듈 초기화
m = nn.Softmax(dim=1)

# 데이터 벡터 생성 및 차원 변환
z = torch.linspace(-10, 10, 100).unsqueeze(0)  # 차원을 (1, 100)으로 변경

# Softmax 함수 적용
y = m(z)

# 결과 플롯
plt.plot(z.numpy().flatten(), y.numpy().flatten())
plt.title("Softmax Function with nn.Softmax")
plt.xlabel("z")
plt.ylabel("Softmax(z)")
plt.grid(True)
plt.show()

```
