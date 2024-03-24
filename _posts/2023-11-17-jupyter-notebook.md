---
title: Jupyter Notebook 설치 가이드 on Mac
author: Jay Jo
date: 2023-11-17 00:00:00 +09:00
categories: [dev, env]
tags: [dev, env]
---

AI 학습을 위한 개발 환경으로 널리 사용되는 Jupyter Notebook의 설치 방법을 단계별로 안내합니다. Jupyter Notebook은 코드를 작성하고 실행 결과를 바로 볼 수 있어 데이터 과학, 기계 학습, 통계 분석 등 여러 분야에서 유용하게 사용됩니다.

## 1. Python 설치 확인

Jupyter Notebook을 설치하기 전에, 시스템에 Python이 이미 설치되어 있는지 확인해야 합니다. 터미널 또는 명령 프롬프트에서 다음 명령어로 Python 버전을 확인할 수 있습니다.

```bash
python --version
```
또는
```bash
python3 --version
```

이 명령어를 실행했을 때 Python 버전 번호가 표시되면, Python이 설치되어 있는 것입니다. Python이 설치되어 있지 않다면, Python [공식 웹사이트](https://www.python.org/downloads/)에서 Python을 설치하세요.

## 2. Jupyter Notebook 설치

Python이 설치되어 있다면, 다음으로 Jupyter Notebook을 설치할 수 있습니다. 터미널 또는 명령 프롬프트에서 다음 명령어를 입력하여 설치합니다.

```bash
pip install notebook
```
Python 3 사용자는 다음과 같이 입력할 수 있습니다.

```bash
pip3 install notebook
```

## 3. Jupyter Notebook 실행

Jupyter Notebook 설치가 완료되면, 다음 명령어로 Jupyter Notebook을 실행할 수 있습니다.

```bash
jupyter notebook
```
또는 Jupyter Lab을 사용하려면:

```bash
jupyter lab
```

이 명령어는 Jupyter Notebook 또는 Jupyter Lab을 시작하며, 기본 웹 브라우저에서 새 탭을 열어 Notebook의 대시보드를 표시합니다.

## 4. Jupyter Notebook 사용하기

웹 브라우저에서 Jupyter Notebook 대시보드가 열리면, 'New' 버튼을 클릭해 새로운 노트북을 만들 수 있습니다. 이곳에서 Python 버전을 선택하여 새 노트북을 시작할 수 있습니다.

노트북에서는 코드 셀에 Python 코드를 입력하고 실행하여 결과를 바로 볼 수 있습니다. 마크다운 셀을 사용하여 노트에 설명을 추가하는 것도 가능합니다.

이제 Jupyter Notebook을 사용하여 AI 학습과 관련된 다양한 프로젝트를 시작할 수 있습니다!
