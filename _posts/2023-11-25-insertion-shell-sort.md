---
title: 삽입 정렬(Insertion Sort) 및 쉘 정렬(shell Sort)
author: Jay Jo
date: 2023-11-25 00:00:00 +09:00
categories: [Algorithms]
tags: [algorithms]
image: /assets/img/posts/basic-sort1.png
---

# 기본 정렬 알고리즘 [삽입 정렬(insertion-sort) 및 쉘 정렬(shell-sort)]

## 목차
1. [삽입 정렬 (Insertion Sort)](#삽입-정렬-insertion-sort)
   - [정의](#정의)
   - [작동 원리](#작동-원리)
   - [알고리즘 복잡도](#알고리즘-복잡도)
   - [예시 코드](#예시-코드)
2. [쉘 정렬 (Shell Sort)](#쉘-정렬-shell-sort)
   - [정의](#정의-1)
   - [작동 원리](#작동-원리-1)
   - [알고리즘 복잡도](#알고리즘-복잡도-1)
   - [예시 코드](#예시-코드-1)

<a name="삽입-정렬-insertion-sort"></a>
## 삽입 정렬 (Insertion Sort)

### 정의
삽입 정렬은 각 요소를 이미 정렬된 배열 부분에 적절한 위치에 삽입하는 방식으로 작동하는 정렬 방법입니다.

### 작동 원리
1. 두 번째 요소부터 시작하여, 해당 요소를 그 이전의 요소들과 비교합니다.
2. 요소가 이전의 요소보다 작으면, 그 요소의 앞으로 이동합니다.
3. 이 과정을 모든 요소에 대해 반복합니다.
4. 배열의 모든 요소가 올바른 순서로 정렬될 때까지 이 과정을 반복합니다.

### 알고리즘 복잡도
- 최악의 경우 시간 복잡도: O(n^2)
- 최선의 경우 시간 복잡도: O(n)
- 평균 시간 복잡도: O(n^2)
- 공간 복잡도: O(1)

### 예시 코드
```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j] :
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr
```

<a name="쉘-정렬-shell-sort"></a>
## 쉘 정렬 (Shell Sort)

### 정의
쉘 정렬은 삽입 정렬을 개선한 버전으로, 배열을 간격별로 나누어 삽입 정렬을 수행합니다. 이 간격은 점차 줄어들며, 마지막에는 일반 삽입 정렬을 수행합니다.

### 작동 원리
1. 초기 간격 `gap`을 설정합니다 (예: 배열 길이의 절반).
2. `gap`만큼 떨어진 요소들에 대해 삽입 정렬을 수행합니다.
3. `gap`의 크기를 줄여가며 위의 과정을 반복합니다.
4. `gap`이 1이 되면, 일반 삽입 정렬을 수행합니다.

### 알고리즘 복잡도
- 평균 및 최악의 경우 시간 복잡도: O(n^1.5) (간격에 따라 다름)

### 예시 코드
```python
def shell_sort(arr):
    n = len(arr)
    gap = n // 2
    while gap > 0:
        for i in range(gap, n):
            temp = arr[i]
            j = i
            while j >= gap and arr[j - gap] > temp:
                arr[j] = arr[j - gap]
                j -= gap
            arr[j] = temp
        gap //= 2
    return arr
```

