---
title: Chirpy Theme for Blog
author: Jay Jo
date: 2023-09-01 00:00:00 +09:00
categories: [blog]
tags: [blog]
comments: true
---

# Chirpy Theme Blog 시작하기

[https://chirpy.cotes.page/posts/getting-started](https://chirpy.cotes.page/posts/getting-started/)

## 목차
1. [Jekyll과 GitHub Pages 소개](#jekyll과-github-pages-소개)
2. [Windows 10 기준 설치법](#windows-10-기준-설치법)
3. [Deploy (배포)](#deploy-배포)

## Jekyll과 GitHub Pages 소개

### Jekyll
- **정의**: Ruby로 작성된 정적 사이트 생성기.
- **기능**: 마크다운이나 유사한 마크업 언어로 작성된 텍스트 콘텐츠로 HTML 웹사이트 생성.
- **장점**: 데이터베이스나 서버 사이드 스크립팅에 의존하지 않는 빠르고 안전한 웹사이트 제공.
- **사용 사례**: 블로그, 개인 및 프로젝트 웹사이트, 문서 사이트 등.

### GitHub Pages
- **정의**: GitHub에서 제공하는 웹사이트 호스팅 서비스.
- **특징**: GitHub 저장소에서 직접 웹사이트 호스팅 가능.
- **장점**: 별도의 서버나 호스팅 비용 없이 웹사이트 무료 호스팅, 버전 관리 기능을 통한 웹사이트 변경사항 추적 및 관리.
- **Jekyll과의 통합**: Jekyll로 생성된 사이트를 쉽게 배포 및 호스팅 가능.

### Jekyll과 GitHub Pages의 조합
- **이점**: 효율적인 웹 개발, 쉬운 관리 및 배포.
- **적용 예시**: 개인 블로그, 포트폴리오, 프로젝트 문서화, 작은 기업 웹사이트 등.

## Windows 10 기준 설치법 

### 사전 준비
- Node.js
- Ruby(Gem)
- Jekyll
- bundle

### Installing Node.js
[Node.js 다운로드](https://nodejs.org/en)

### Installing Ruby
[Ruby Installer 다운로드](https://rubyinstaller.org/downloads/)

```bash
gem install jekyll bundler
```

###  버전 확인
```bash
ruby --version
gem --version
bundler --version
```
### 시작
```bash
bash tools/init
```
### Installing Dependencies
```bash
bundle
```
### Running Local Server
```bash
bundle exec jekyll s
```

#### CI/CD Location
CI/CD 
.github/workflows/
.travis.yml

## Deploy (배포)
GitHub Actions를 사용하여 배포

### GitHub Actions
GitHub 'Settings > Pages > Build and deployment' GitHub Actions.

**준비사항**
GitHub 무료 계정 사용 시, 깃허브 페이지 저장소를 공개 상태 유지 필요.

Gemfile.lock 파일 업데이트
```bash
bundle lock --add-platform x86_64-linux
```
GitHub Pages 설정 방법

#### 자동 배포
GitHub에 커밋을 푸시하여 Actions 워크플로우 트리거.
Actions 탭에서 빌드 및 배포 워크플로우 확인.

#### 수동 배포
```bash
JEKYLL_ENV=production bundle exec jekyll b
```
생성된 파일은 프로젝트 루트 디렉터리의 _site 폴더에 배치 되며 파일을 대상 서버에 업로드 필요.
