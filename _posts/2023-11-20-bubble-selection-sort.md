---
title: 버블 정렬 (Bubble Sort) 선택 정렬 (Selection Sort)
author: Jay Jo
date: 2023-11-20 00:00:00 +09:00
categories: [Algorithms]
tags: [algorithms]
image: /assets/img/posts/basic-sort.png
---

# 기본 정렬 알고리즘 [버블 정렬(Bubble Sort), 선택 정렬(Selection Sort)]

1. [버블 정렬 (Bubble Sort)](#버블-정렬-bubble-sort)
   - [정의](#정의)
   - [작동 원리](#작동-원리)
   - [알고리즘 복잡도](#알고리즘-복잡도)
   - [예시 코드](#예시-코드)
2. [선택 정렬 (Selection Sort)](#선택-정렬-selection-sort)
   - [정의](#정의-1)
   - [작동 원리](#작동-원리-1)
   - [알고리즘 복잡도](#알고리즘-복잡도-1)
   - [예시 코드](#예시-코드-1)

<a name="버블-정렬-bubble-sort"></a>
## 버블 정렬 (Bubble Sort)

### 정의
버블 정렬은 가장 간단한 정렬 알고리즘 중 하나입니다. 이 알고리즘은 반복적으로 리스트를 순회하며 인접한 요소를 비교하고, 필요한 경우 위치를 교환합니다.

### 작동 원리
1. 리스트의 첫 번째 요소부터 시작하여 인접한 요소끼리 비교합니다.
2. 만약 앞의 요소가 뒤의 요소보다 크면, 두 요소의 위치를 교환합니다.
3. 이 과정을 리스트의 모든 요소에 대해 반복합니다.
4. 한 번의 순회가 끝날 때마다, 가장 큰 요소가 리스트의 마지막으로 이동하게 됩니다.
5. 리스트의 모든 요소가 정렬될 때까지 이 과정을 반복합니다.

### 알고리즘 복잡도
- 최악의 경우 시간 복잡도: O(n^2)
- 최선의 경우 시간 복잡도: O(n)
- 평균 시간 복잡도: O(n^2)
- 공간 복잡도: O(1)

### 예시 코드
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr
```
<a name="선택-정렬-selection-sort"></a>

## 선택 정렬 (Selection Sort)
### 정의
선택 정렬은 다른 정렬 알고리즘과 비교하여 상대적으로 단순한 알고리즘입니다. 이 알고리즘은 주어진 배열에서 최소값을 찾아 앞으로 이동시키는 방식으로 작동합니다.

### 작동 원리
1. 배열의 전체 요소를 순회하며, 현재 위치에서 가장 작은 요소를 찾습니다.
2. 가장 작은 요소를 현재 위치의 요소와 교환합니다.
3. 다음 위치로 이동하여 이 과정을 반복합니다.
4. 배열의 모든 요소가 정렬될 때까지 이 과정을 반복합니다.
### 알고리즘 복잡도
- 최악의 경우 시간 복잡도: O(n^2)
- 최선의 경우 시간 복잡도: O(n^2)
- 평균 시간 복잡도: O(n^2)
- 공간 복잡도: O(1)
### 예시 코드
```python
def selection_sort(arr):
    for i in range(len(arr)):
        min_idx = i
        for j in range(i+1, len(arr)):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr
```