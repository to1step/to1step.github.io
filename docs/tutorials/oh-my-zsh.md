---
layout: default
title: oh-my-zsh
parent: 튜토리얼
nav_order: 5
---

개발을 진행하다 보면 터미널을 자주 사용하게 된다.

더 이쁜 터미널과 터미널을 더 편하게 사용할 수 있도록 도와주는 플러그인이 있다.

예를 들어 `git puhs --force` 를 `gpf` 로 사용할 수 있다.

# Mac 설치하기

과거 `인텔 맥`을 사용했을 때는 문제가 없었지만, `Mac M1`에는 `oh-my-zsh` 에 이슈가 있었다.

하지만 `iTerm2` 을 설치하면 `Mac M1` 에서 발생하던 `oh-my-zsh` 이슈는 없다고 한다.

`Mac M1 ohmyzsh 설치하기` 키워드로 잘된 예시를 따라하는게 좋을 수 있다.

테마, 폰트 등등.. 하다보면 1-2시간은 걸릴 수 있다.

## iTerm2 설치

- https://iterm2.com

## ohmyzsh 설치

- https://ohmyz.sh/#install

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 테마 적용

```bash
# 열기
vi ~/.zshrc

# ZSH_THEME 에 있는 값을 바꿔준다.
```

## 폰트가 깨지니까 D2Cofing 추가

https://github.com/naver/d2codingfont

---

# 플러그인 추천

Oh My Zsh 에서 플러그인을 제공하는데, 개인적으로 추천하는건 이렇다.

- Auto Suggestions: 과거에 사용했던 터미널 명령어를 자동왼성 해준다.

- Syntax Highlighting: 커멘터가 틀렸으면 빨간색, 맞으면 초록색으로 표시해준다.
