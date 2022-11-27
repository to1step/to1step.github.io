---
layout: default
title: 리베이스
parent: 튜토리얼
nav_order: 1
---

# Git 리베이스

서로 다른 Branch 를 합치는 방법은 3가지가 있습니다.
Pull Request(Merge), Rebase, Cherry-Pick 이 3가지를 간단히 설명해드리자면,

- Pull Request(Merge)
  A 브런치위에 B 브런치를 올려 놓는다. (Pull Request에 대한 커밋 하나가 추가됨)

- Rebase
  A 브런치와 B 브런치를 섞는다. (A 브런치와 B 브런치의 커밋 하나하나가 섞임)

- Cherry-Pick
  A 브런치와 B 브런치의 커밋 하나를 가져온다.

이정도가 있습니다.

---

## 브런치를 합치는 방법

새로 작업한 브런치 A 를 `main` 브런치에 Pull Request(Merge) 를 하기 전에, `main` 브런치를 `rebase` 합니다.

그 이유는 2가지가 있습니다.

1. 새로 작업한 브런치 A에 없는 `main` 브런치의 커밋 메세지를 가져오기 합치기 위해서 입니다.

2. A 브런치와 `main` 브런치가 충돌이 발생하면 Merge 를 할 수 없습니다. 충돌을 해결하기 위해 `rebase` 를 사용합니다.

2번의 사례는 아래 Google Drive 영상을 참고해주세요.

https://drive.google.com/file/d/1MQ1_nJjYSwKWUzZJhq5JMI6yVpVKdfJ5/view?usp=share_link
