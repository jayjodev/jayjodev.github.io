---
title: Homebrew On Mac 설치 및 설정 가이드
author: Jay Jo
date: 2024-02-17 00:00:00 +09:00
categories: [tip]
tags: [tip]
image: /assets/img/posts/homebrew.jpg
---

# Homebrew On M3 설치 및 설정 가이드

만약 `zsh: command not found: brew` 오류가 발생한다면, Homebrew가 설치되지 않았거나 제대로 설정되지 않은 것일 수 있습니다. 다음 단계를 따라 Homebrew를 설치하고 설정해보세요.

## Homebrew 설치하기

1. 터미널을 열고 아래 명령어를 복사하여 붙여넣기 합니다. 설치가 완료될 때까지 기다리세요.

    ```sh
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

2. 설치가 완료되면, 터미널에 나타나는 '다음 단계'를 따르세요.

## 환경 변수 설정

설치 후 나타나는 안내에 따라 Homebrew를 PATH에 추가합니다. 아래 단계를 따라 실행하세요.

1. 다음 명령어를 터미널에 복사하여 붙여넣고, 엔터를 눌러 실행합니다.

    ```sh
    echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> /Users/$USER/.zprofile
    ```

2. PATH 설정을 적용하기 위해 다음 명령어를 실행합니다.

    ```sh
    eval $(/opt/homebrew/bin/brew shellenv)
    ```

이제 Homebrew가 제대로 설치되었는지 확인하기 위해 터미널에서 `brew help` 명령어를 실행해보세요. 도움말이 표시되면 Homebrew가 정상적으로 설치되어 실행되는 것입니다.

## 문제 해결

설치 후에도 `brew` 명령어가 동작하지 않는다면, 터미널을 재시작하거나 컴퓨터를 재부팅해보세요. 그래도 문제가 해결되지 않는다면 Homebrew 문서를 참조하거나 관련 커뮤니티에 도움을 요청하세요.