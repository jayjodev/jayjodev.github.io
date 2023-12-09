---
title: 분할 정복 (Divide and Conquer)
author: Jay Jo
date: 2023-12-07 00:00:00 +09:00
categories: [Algorithms]
tags: [algorithms]
image: /assets/img/posts/divide-and-conquer.png
---

# 분할 정복 (Divide and Conquer)

## 개요
분할 정복(Divide and Conquer)은 복잡한 문제를 더 작고 관리하기 쉬운 하위 문제로 분할하여 해결하는 알고리즘 설계 패러다임입니다. 이 방법은 문제를 분할하고, 각 부분을 개별적으로 해결한 다음, 그 결과를 합쳐 전체 문제의 해결책을 얻습니다.

## 특징
- **문제 분할:** 큰 문제를 여러 하위 문제로 나눕니다.
- **정복:** 각 하위 문제를 독립적으로 해결합니다.
- **결합:** 하위 문제의 해결책을 결합하여 전체 문제의 해결책을 도출합니다.

- 방법: 문제를 더 작고 관리하기 쉬운 하위 문제로 나누고, 이를 독립적으로 해결한 다음, 그 결과를 결합하여 전체 문제의 해를 도출합니다.
- 하위 문제: 각 하위 문제는 독립적이며, 서로 겹치지 않습니다.
- 적용 예: 병합 정렬(Merge Sort), 퀵 정렬(Quick Sort), 이진 탐색(Binary Search) 등.
- 효율성: 중복된 하위 문제가 없기 때문에, 한 번 계산된 하위 문제를 다시 계산할 필요가 없습니다.

## 예시: 병합 정렬 (Merge Sort)

병합 정렬은 분할 정복 알고리즘의 전형적인 예입니다. 이 알고리즘은 배열을 반으로 나누고, 각 부분을 재귀적으로 정렬한 다음, 정렬된 부분 배열들을 병합하여 전체 배열을 정렬합니다.

### 코드 예시 (Python)

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        L = arr[:mid]
        R = arr[mid:]

        merge_sort(L)
        merge_sort(R)

        i = j = k = 0

        # Merge the two halves
        while i < len(L) and j < len(R):
            if L[i] < R[j]:
                arr[k] = L[i]
                i += 1
            else:
                arr[k] = R[j]
                j += 1
            k += 1

        # Checking if any element was left
        while i < len(L):
            arr[k] = L[i]
            i += 1
            k += 1

        while j < len(R):
            arr[k] = R[j]
            j += 1
            k += 1

    return arr

# 예시: 배열 정렬
example_array = [12, 11, 13, 5, 6, 7]
sorted_array = merge_sort(example_array)
print("Sorted array:", sorted_array)
```

이 코드는 주어진 배열을 반으로 나누고, 각 부분을 재귀적으로 정렬한 후, 정렬된 부분 배열들을 병합하여 전체 배열을 정렬합니다.
