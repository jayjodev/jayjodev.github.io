---
title: Markdown with Mathematical Expressions  
author: Jay Jo
date: 2023-11-27 00:00:00 +09:00
categories: [tip]
tags: [tip]
image: /assets/img/posts/math-markdown.png
---

- [LaTeX 마크다운](#https://ashki23.github.io/markdown-latex.html)

## 수학 표현 (Mathematical Expressions)
Markdown과 LaTeX를 사용하여 수학적 표현을 마크다운 문서에 삽입할 수 있습니다. 인라인 LaTeX 수식은 단일 `$` 기호를 사용하고, 별도의 줄에 표시된 수식은 이중 `$`을 사용합니다.

### LaTeX 수식
#### 인라인 수식
- 인라인 수식 예: `$x + y$`는 \(x + y\)로 표시됩니다.

#### 디스플레이 수식
- 디스플레이 수식 예: 
  ```
  $$
  x + y
  $$
  ```
  이는 아래와 같이 표시됩니다:
  $$
  x + y
  $$

### 연산자 (Operators)
- 덧셈: `$x + y$`는 \(x + y\)로 표시됩니다.
- 뺄셈: `$x - y$`는 \(x - y\)로 표시됩니다.
- 곱셈: `$x 	imes y$`는 \(x 	imes y\)로 표시됩니다.
- 나눗셈: `$x \div y$`는 \(x \div y\)로 표시됩니다.
- 분수: `$\dfrac{x}{y}$`는 \(\dfrac{x}{y}\)로 표시됩니다.
- 제곱근: `$\sqrt{x}$`는 \(\sqrt{x}\)로 표시됩니다.

### 기호 (Symbols)
- 파이: `$\pi pprox 3.14159$`는 \(\pi pprox 3.14159\)로 표시됩니다.
- 플러스 마이너스: `$\pm \, 0.2$`는 \(\pm \, 0.2\)로 표시됩니다.
- 무한대: `$\dfrac{0}{1} 
eq \infty$`는 \(\dfrac{0}{1} 
eq \infty\)로 표시됩니다.

### 그리스 문자 (Greek Alphabets)
- 알파: `\alpha`는 \(lpha\)로 표시됩니다.
- 베타: `\beta`는 \(eta\)로 표시됩니다.
- 감마: `\gamma`는 \(\gamma\)로 표시됩니다.

### 방정식 (Equations)
- 자연수 집합: 
  ```
  $$
  \mathbb{N} = \{ a \in \mathbb{Z} : a > 0 \}
  $$
  ```
  이는 아래와 같이 표시됩니다:

  $$
  \mathbb{N} = \{ a \in \mathbb{Z} : a > 0 \}
  $$
