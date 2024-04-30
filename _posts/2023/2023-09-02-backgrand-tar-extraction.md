---
title: 백그라운드에서 여러 TAR 파일 자동 압축 해제하기
author: Jay Jo
date: 2023-09-02 00:00:00 +09:00
categories: [Linux]
tags: [linux]
---

## 개요
서버에서 여러 TAR 파일을 다루는 작업은 수동으로 각각 압축 해제해야 할 경우 시간이 많이 소요됩니다. 다행히 간단하지만 강력한 한 줄짜리 Bash 스크립트를 사용하면 이 과정을 백그라운드에서 자동화할 수 있습니다. 이는 많은 수의 파일을 다루거나, 연결이 지속적으로 유지되지 않는 원격 서버에서 작업을 수행할 때 특히 유용합니다.

## 명령어
이 스크립트는 `for` 루프, `nohup`, 그리고 `tar` 명령어의 조합을 사용합니다. 스크립트는 다음과 같습니다:

```bash
for file in ./*.tar; do nohup tar -xf "$file" & done
```

### 스크립트 분석
1. **`for file in ./*.tar; do`**: 스크립트의 이 부분은 현재 디렉토리의 `.tar` 확장자를 가진 모든 파일을 반복 처리합니다.
2. **`nohup`**: `nohup` 명령어(‘hang up하지 않음’의 줄임말)는 로그아웃하거나 터미널을 닫아도 스크립트가 백그라운드에서 계속 실행되도록 합니다.
3. **`tar -xf "$file"`**: 이 명령어는 `$file`로 지정된 TAR 파일을 압축 해제(`-x`)합니다. `-f` 플래그는 파일명을 지정하는 데 사용됩니다.
4. **`&`**: 이 기호는 `tar` 명령어를 백그라운드에서 실행하게 하여, 현재 실행 중인 작업이 완료될 때까지 기다리지 않고 즉시 다음 반복 작업을 시작할 수 있게 합니다.
5. **`done`**: 루프의 끝을 표시합니다.

이 명령어를 사용하면 현재 디렉토리에 있는 모든 `.tar` 파일들이 각각의 폴더로 추출됩니다. 이 과정은 백그라운드에서 실행되며, 출력이나 오류 메시지는 `nohup.out` 파일에서 확인할 수 있습니다. 특히 서버 환경에서 여러 TAR 파일을 다루는 과정을 크게 간소화할 수 있습니다. 압축 해제 프로세스를 백그라운드에서 실행함으로써 작업 흐름이 중단되지 않도록 합니다.

---
