---
title: 동적 계획법 (Dynamic Programming)
author: Jay Jo
date: 2023-12-04 00:00:00 +09:00
categories: [Algorithms]
tags: [algorithms]
image: /assets/img/posts/Dynamic-Programming.png
---

# 동적 계획법 (Dynamic Programming)

동적 계획법은 복잡한 문제를 효율적으로 해결하기 위한 알고리즘 설계 기법입니다. 이 기법은 큰 문제를 작은 하위 문제로 나누고, 이러한 하위 문제들의 해결책을 저장하여 재사용합니다. 이 방식은 중복되는 계산을 줄여 알고리즘의 효율성을 향상시킵니다.

## 핵심 개념
1. **최적 부분 구조 (Optimal Substructure)**: 큰 문제의 최적 해결책이 하위 문제들의 최적 해결책으로부터 구성될 수 있음을 의미합니다.
2. **중복되는 하위 문제 (Overlapping Subproblems)**: 같은 하위 문제가 여러 번 발생할 경우, 한 번 계산한 결과를 저장하고 재사용합니다.

## 특징:

1. 목적: 중복 계산을 줄이고 효율성을 향상시키기 위해, 큰 문제를 작은 문제로 나누어 해결합니다.
2. 알고리즘 예시: 피보나치 수열, 최단 경로 문제(다익스트라, 벨만-포드), 배낭 문제 등이 있습니다.
3. 응용: 최적화 문제 해결, 복잡한 계산 문제 해결, 다양한 프로그래밍 문제 등에 사용됩니다.

## 피보나치 수열 예시

피보나치 수열은 동적 계획법을 설명하는데 자주 사용되는 간단한 예시입니다. 피보나치 수열의 각 숫자는 앞의 두 숫자의 합으로 구성됩니다.

### Python 코드

```python
def fibonacci(n):
    # n이 0 또는 1인 경우, 바로 값을 반환
    if n <= 1:
        return n

    # dp 테이블 초기화
    dp = [0] * (n + 1)
    dp[1] = 1

    # 피보나치 수열 계산
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]

    return dp[n]

# 예시 사용
print(fibonacci(10)) # 10번째 피보나치 수 출력
```

## 편집 거리 문제 (Edit Distance Problem)

편집 거리 문제는 두 문자열을 주어진 편집 연산을 사용해 서로 변환하는 데 필요한 최소 편집 연산의 수를 찾는 문제입니다.

### 문제 설명

- 두 문자열 `str1`과 `str2`가 주어집니다.
- 목표는 `str1`을 `str2`로 변환하는 데 필요한 최소 편집 연산의 수를 찾는 것입니다.
- 가능한 연산: 삽입, 삭제, 교체.

### 동적 계획법 적용

1. **테이블 생성**: `str1`의 길이를 `m`, `str2`의 길이를 `n`이라 하고, `(m+1) x (n+1)` 크기의 테이블을 생성합니다.
2. **기저 사례 초기화**: 테이블의 첫 번째 행과 열을 초기화합니다.
3. **하위 문제 해결**: 테이블을 채우면서 각 하위 문제를 해결합니다.
4. **최종 해답**: 테이블의 마지막 셀에 최종 해답이 저장됩니다.

### 예시 코드: 편집 거리 계산 (Python)
```python
def edit_distance(str1, str2):
    m, n = len(str1), len(str2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]

    for i in range(m + 1):
        for j in range(n + 1):
            if i == 0:
                dp[i][j] = j
            elif j == 0:
                dp[i][j] = i
            elif str1[i-1] == str2[j-1]:
                dp[i][j] = dp[i-1][j-1]
            else:
                dp[i][j] = 1 + min(dp[i-1][j],    # Delete
                                   dp[i][j-1],    # Insert
                                   dp[i-1][j-1])  # Replace

    return dp[m][n]
```
