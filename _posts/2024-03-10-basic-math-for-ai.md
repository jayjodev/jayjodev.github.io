---
title: Python을 이용한 기본 통계 계산
author: Jay Jo
date: 2024-03-10 00:00:00 +09:00
categories: [Mathematics]
tags: [Mathematics]
---

## 데이터

```python
original_a = [79, 54, 74, 62, 85, 55, 88, 85, 51, 85, 54, 84, 78, 47]
```

## 평균 (Mean)

평균은 모든 데이터 값을 합한 후 데이터의 개수로 나눈 값입니다.

$$\mu = \frac{1}{N} \sum_{i=1}^{N} x_i$$

```python
a = original_a + [x * 2 for x in original_a]
print(a)

import statistics
mean_a = statistics.mean(a)
print(mean_a)
```

## 중앙값 (Median)

데이터 집합의 중앙에 위치하는 값입니다.

```python
print(statistics.median(a))
```

## 범위 (Range)

최대값과 최소값의 차이입니다.

$${Range} = \max(x_i) - \min(x_i)$$

```python
print(max(a) - min(a))
```

## 사분위수 (Quartiles)

데이터 집합을 사등분한 값입니다.

```python
import numpy as np
q1 = np.percentile(a, 25)
q2 = np.percentile(a, 50)
q3 = np.percentile(a, 75)
print("Q1:", q1, "Q2:", q2, "Q3:", q3)
```

## 표본분산 (Sample Variance)

데이터가 평균으로부터 얼마나 떨어져 있는지의 평균적인 제곱 거리입니다.

$$s^2 = \frac{1}{N-1} \sum_{i=1}^{N} (x_i - \mu)^2$$

```python
variance_a = statistics.variance(a)
print(variance_a)
```

## 표본 표준 편차 (Sample Standard Deviation)

데이터의 흩어진 정도를 나타내는 값입니다.

$$s = \sqrt{\frac{1}{N-1} \sum_{i=1}^{N} (x_i - \mu)^2}$$

```python
stdev_a = statistics.stdev(a)
print(stdev_a)
```

## 모분산 (Population Variance)

모든 데이터의 분산을 나타냅니다.

$$\sigma^2 = \frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^2$$

```python
print(np.var(a))
```

## 모 표준 편차 (Population Standard Deviation)

데이터 전체의 표준 편차입니다.

$$\sigma = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (x_i - \mu)^2}$$

```python
print(np.std(a))
```

## Z-Score (표준 점수)

데이터 포인트가 평균으로부터 표준 편차의 몇 배만큼 떨어져 있는지를 나타냅니다.

$$ z = \frac{x - \mu}{\sigma} $$

```python
z_scores = [(x - mean_a) / stdev_a for x in a]
print(z_scores)
```
