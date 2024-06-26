---
title: 기계학습 기초 (클러스터링)
author: Jay Jo
date: 2023-11-11 00:00:00 +09:00
categories: [Artificial Intelligence]
tags: [AI]
---

# 클러스터링(Clustering)

[scikit-learn 클러스터링](https://scikit-learn.org/stable/modules/clustering.html)

클러스터링은 데이터의 내재된 구조를 파악하는 데 중요한 역할을 하는 비지도 학습 기법입니다. 이 문서는 클러스터링의 다양한 방법들과 그 특징들을 탐색합니다.

## 목차
1. [클러스터링 개요](#1-클러스터링-개요)
2. [K-평균 클러스터링(K-Means Clustering)](#2-K-평균-클러스터링K-Means-Clustering)
3. [DBSCAN 클러스터링](#3-DBSCAN-클러스터링)
4. [계층적 클러스터링(Hierarchical Clustering)](#4-계층적-클러스터링Hierarchical-Clustering)
5. [클러스터링 알고리즘 비교](#5-클러스터링-알고리즘-비교)
6. [결론](#6-결론)

---

## 1. 클러스터링 개요

### 비지도 학습과 클러스터링
- **비지도 학습(Unsupervised Learning)**: 레이블 없이 입력 데이터만을 사용하여 학습을 진행하는 방식. 데이터의 패턴이나 구조를 탐색하는 데 주로 사용됩니다.
- **클러스터링**: 데이터를 유사성 기준에 따라 그룹화하는 과정. 여러 종류의 알고리즘이 있으며, 각각 다른 특성과 사용 사례를 가집니다.

### 지도 학습 vs 비지도 학습

| 구분 | 지도 학습 (Supervised Learning) | 비지도 학습 (Unsupervised Learning) |
|------|---------------------------------|--------------------------------------|
| 학습 데이터 | 입력(input)과 정답(label) | 입력만 사용 |
| 정답의 유무 | 정답은 사람이 만든 정보 | 정답 없음 |
| 학습 목적 | 입력과 정답에 대한 관계 학습 | 입력의 패턴 및 상관관계 학습 |
| 예시 | 기존 정보(데이터셋)를 토대로 새로운 입력에 대한 정답 추측 | 클러스터링, 차원 축소 등 |

## 2. K-평균 클러스터링(K-Means Clustering)

K-평균 클러스터링은 가장 널리 사용되는 클러스터링 알고리즘 중 하나입니다. 이 방법은 데이터 포인트들을 K개의 클러스터로 그룹화합니다. 이 과정은 다음과 같은 단계로 이루어집니다.

K-평균 클러스터링(K-Means Clustering) 알고리즘에서 클러스터의 중심(centroid)은 초기에 무작위로 선택되고, 이후 반복적인 과정을 통해 점진적으로 조정됩니다. 이 과정은 다음과 같이 진행됩니다:

초기 센터 선택: 알고리즘 시작 시, K개의 클러스터 중심은 일반적으로 데이터 포인트들 중에서 무작위로 선택되거나, 데이터 공간에서 무작위 위치에 배치됩니다. 이 초기 선택 방법은 클러스터링의 결과에 영향을 미칠 수 있습니다.

반복적인 할당과 업데이트:

할당 단계: 각 데이터 포인트는 현재 클러스터 중심 중 가장 가까운 중심에 할당됩니다. 이때 일반적으로 유클리드 거리가 사용됩니다.
업데이트 단계: 할당된 데이터 포인트들을 기반으로 각 클러스터의 중심이 다시 계산됩니다. 새로운 중심은 해당 클러스터에 속한 데이터 포인트들의 평균 위치로 설정됩니다.
수렴 조건: 클러스터의 할당이 더 이상 변하지 않거나, 중심이 일정 기준 이하로만 변경되거나, 특정한 반복 횟수에 도달할 때까지 위의 할당과 업데이트 과정을 반복합니다.

이 과정에서 클러스터 중심은 초기 무작위 선택에서 시작하여 각 반복마다 데이터의 구조에 맞춰 조정됩니다. 이는 클러스터링이 더 이상 개선되지 않거나, 다른 지정된 중단 기준이 충족될 때까지 계속됩니다.

K-평균 클러스터링의 결과는 초기 중심의 선택에 따라 달라질 수 있으므로, 일반적으로 여러 번의 실행과 중심의 다른 초기 선택을 통해 가장 안정적인 클러스터링 결과를 얻기 위한 노력이 필요합니다.

### 주요 단계
1. **초기화**: 클러스터의 개수 K를 결정하고, 데이터셋에서 무작위로 K개의 포인트를 선택하여 각 클러스터의 초기 중심으로 설정합니다.
2. **할당 단계**: 데이터셋의 각 포인트에 대해, 모든 중심점에 대한 거리를 계산하고, 각 데이터 포인트를 가장 가까운 중심점을 갖는 클러스터에 할당합니다.
3. **업데이트 단계**: 할당된 데이터 포인트들을 기반으로 각 클러스터의 새로운 중심을 계산합니다. 새로운 중심은 클러스터 내 포인트들의 평균 위치로 설정됩니다.
4. **수렴 확인**: 중심점이 더 이상 변하지 않거나, 정해진 반복 횟수에 도달하거나, 클러스터 할당이 더 이상 변하지 않을 때까지 할당과 업데이트 단계를 반복합니다.
5. **결과 출력**: 최종 클러스터 할당과 중심점을 출력합니다.

### 클러스터링 평가 방법
- **엘보우 방법 (Elbow Method)**: 클러스터 수(K) 결정에 사용됩니다. WCSS(Within-Cluster Sum of Squares)를 계산하여 최적의 K값을 찾습니다. WCSS는 클러스터 내 각 포인트와 해당 클러스터 중심점과의 거리의 제곱 합으로 정의됩니다.
  ```
  WCSS = ∑(i=1 to k) ∑(x ∈ Ci) ||x - μi||²
  ```
  여기서 `k`는 클러스터의 수, `Ci`는 i번째 클러스터, `x`는 클러스터 내의 데이터 포인트, `μi`는 i번째 클러스터의 중심점입니다.
  
- **실루엣 점수 (Silhouette Score)**: 클러스터 내 코히전과 클러스터 간 분리를 측정합니다. 각 데이터 포인트에 대한 실루엣 점수는 다음과 같이 계산됩니다.
  ```
  s(i) = (b(i) - a(i)) / max{a(i), b(i)}
  ```
  여기서 `a(i)`는 동일한 클러스터 내의 다른 데이터 포인트들과의 평균 거리, `b(i)`는 가장 가까운 다른 클러스터의 데이터 포인트들과의 평균 거리입니다.

## 3. DBSCAN 클러스터링

DBSCAN (Density-Based Spatial Clustering of Applications with Noise)은 밀도 기반의 클러스터링 알고리즘입니다.

### 주요 특징
- 이상치에 강하고 임의의 형태의 클러스터 탐지가 가능합니다.
- 클러스터의 수를 미리 결정할 필요가 없습니다.

### 주요 파라미터
- `ε (epsilon)`: 이웃을 찾을 때 사용되는 반경.
- `MinPts`: 클러스터를 형성하기 위한 최소 포인트 수.

### 작동 원리
- 밀도가 높은 지점에서 클러스터를 시작하여 이웃하는 포인트들을 연결합니다.
- 밀도가 낮은 포인트들은 이상치로 분류됩니다.

### 클러스터링 평가 방법
- **실루엣 점수 (Silhouette Score)**: 클러스터 내 코히전과 클러스터 간 분리를 측정합니다. 실루엣 점수는 -1(잘못된 클러스터링)에서 1(아주 밀집된 클러스터링) 사이의 값을 가집니다.
  ```
  s(i) = (b(i) - a(i)) / max{a(i), b(i)}
  ```
  여기서 `a(i)`는 동일한 클러스터 내의 다른 데이터 포인트들과의 평균 거리, `b(i)`는 가장 가까운 다른 클러스터의 데이터 포인트들과의 평균 거리입니다.
- **덴드로그램(Dendrogram)**: DBSCAN 클러스터링의 결과를 시각적으로 평가하기 위해 사용됩니다. 덴드로그램은 클러스터 간의 거리나 유사도를 나타내는 트리 형태의 그래프입니다.

DBSCAN은 밀도 기반 클러스터링을 통해 다양한 형태의 클러스터를 탐지하고, 이상치를 효과적으로 식별할 수 있습니다. 이러한 특성으로 인해 복잡한 데이터 구조에 적합한 클러스터링 방법입니다.

## 4. 계층적 클러스터링(Hierarchical Clustering)

계층적 클러스터링은 데이터를 계층 구조로 분류하는 클러스터링 방법입니다.

### 주요 특징
- 클러스터를 점진적으로 병합하거나 분할하는 방식으로 작동합니다.
- 덴드로그램을 사용하여 클러스터 간의 관계를 시각적으로 표현할 수 있습니다.

### 학습 과정
1. **초기화**: 각 데이터 포인트를 하나의 클러스터로 간주합니다.
2. **클러스터 간 거리 계산**: 선택된 거리 측정 방법(예: 단일 연결, 완전 연결 등)을 사용하여 모든 클러스터 쌍 간의 거리를 계산합니다.
3. **클러스터 병합**: 가장 가까운 클러스터 쌍을 병합하여 새로운 클러스터를 형성합니다.
4. **거리 행렬 업데이트**: 병합 후 거리 행렬을 업데이트하고, 남은 클러스터 간의 거리를 다시 계산합니다.
5. **종료 조건**: 모든 데이터가 하나의 클러스터에 속하거나 지정된 클러스터 수에 도달할 때까지 병합 과정을 반복합니다.
6. **결과 시각화**: 덴드로그램을 사용하여 클러스터링 결과를 시각화합니다.

### 클러스터 간 거리 측정 방법
- **단일 연결(Single Linkage)**: 클러스터 간의 최소 거리를 사용합니다.
- **완전 연결(Complete Linkage)**: 클러스터 간의 최대 거리를 사용합니다.
- **평균 연결(Average Linkage)**: 클러스터 간의 평균 거리를 사용합니다.
- **Ward 방법**: 클러스터 내의 분산을 최소화하는 방식으로 병합합니다.

### 클러스터링 평가 방법
- **덴드로그램**: 클러스터의 계층적 구조와 클러스터 간의 거리를 시각적으로 표현합니다.
- **실루엣 점수 (Silhouette Score)**: 클러스터 내 코히전과 클러스터 간 분리를 측정합니다.
- **자카드 지수 (Jaccard Index)**: 클러스터 간의 유사성과 다양성을 측정하는 데 사용됩니다. 이 지수는 교집합과 합집합의 비율로 계산됩니다.
  ```
  Jaccard Index = (Intersection of Clusters) / (Union of Clusters)
  ```
## 5. 클러스터링 알고리즘 비교

| 알고리즘 | 장점 | 단점 |
|----------|------|------|
| K-평균 클러스터링 | 간단하고 이해하기 쉬움 | 클러스터의 수를 미리 결정해야 함 |
| 계층적 클러스터링 | 클러스터 수를 미리 결정할 필요 없음 | 대규모 데이터셋에 비효율적 |
| DBSCAN | 이상치에 강함 | 밀도 차이가 큰 데이터셋에서 성능 저하 |
| 스펙트럴 클러스터링 | 비구형 클러스터에 효과적 | 파라미터 선택이 중요 |

## 6. 결론

클러스터링은 다양한 방법으로 구현될 수 있으며, 각 방법은 고유의 장단점을 가집니다. 데이터의 특성과 요구 사항에 맞는 적절한 클러스터링 방법을 선택하는 것이 중요합니다.
