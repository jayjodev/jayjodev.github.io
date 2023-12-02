---
title: AI 학습을 위한 개발 환경 구축
author: Jay Jo
date: 2023-09-10 00:00:00 +09:00
categories: [dev, env]
tags: [dev, env]
image: /assets/img/posts/dev-env.png
---

# AI 학습 을 위한 개발 환경 구축

### 개발 플랫폼
1. Anaconda & Jupyter Notebook

### Library
1. numpy
2. pandas
3. keras
4. sklearn

## 1. Anaconda & Jupyter Notebook

Anaconda는 데이터 과학, 기계 학습, 과학 계산 및 기타 고급 분석 작업을 위한 오픈 소스 분산 컴퓨팅 플랫폼과 패키지 관리자입니다. 주로 Python과 R 프로그래밍 언어를 위해 설계되었으며, 다음과 같은 특징을 가지고 있습니다:

1. 패키지 관리: Anaconda는 Python 및 R 언어를 위한 패키지 관리자인 Conda를 사용합니다. Conda를 통해 사용자는 다양한 과학적 라이브러리와 도구들을 손쉽게 설치, 관리할 수 있습니다.

2. 환경 관리: 사용자는 Conda를 사용하여 다양한 프로젝트에 대해 별도의 환경을 생성하고 관리할 수 있습니다. 이를 통해 프로젝트 별로 다른 버전의 라이브러리와 도구들을 독립적으로 사용할 수 있습니다.

3. 대규모 데이터 세트 작업 용이: Anaconda는 데이터 과학과 관련된 대규모 데이터 세트를 쉽게 다룰 수 있도록 설계되었습니다.

4. 다양한 도구 및 라이브러리: Anaconda는 NumPy, Pandas, SciPy, Matplotlib 등과 같은 데이터 과학과 관련된 다양한 인기 있는 라이브러리들을 포함합니다. 또한 Jupyter Notebook과 같은 도구도 제공합니다.

5. 커뮤니티 및 상업용 버전: Anaconda는 개인 사용자나 연구자를 위한 무료 커뮤니티 버전과 기업을 위한 유료 상업용 버전을 제공합니다.

### Install Anaconda & Jupyter
* https://www.anaconda.com/download

### Change Default Python Version 

* Tensorflow 설치시 지원 버전 
python[version='3.10.*|3.9.*|3.8.*|3.7.*|3.6.*|3.5.*']
으로 파이썬 버전 변경

```
conda update conda
```
```
conda install python=3.10
```

```
conda -V
conda 23.10.0
python -V
Python 3.10.13
```

### 설치된 패키지 확인
```
conda list
```

### 패키지 설치
```
conda install 
```

### Install tensorflow and surprise
```
conda install -c conda-forge scikit-surprise
conda install tensorflow
```

### 설치된 패키지 삭제
```
conda remove {$package name}
conda remove -n {$env name} {$package name}
```

