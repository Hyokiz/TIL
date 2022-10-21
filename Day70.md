# 20221021 TIL

# Git

1. 백업
2. 복구
3. 협업

- working directory에서 삭제
- staging area에서 working directory로 복구
- commit 후 되돌리기

## Working Directory

- git restore 파일명

  - working directory에서 작업 되돌리기
  - 직전 버전을 기준으로 복구해주는 것
  - commit 하지 않고는 restore 불가능

## Stating Area

- rm --cashed 파일명

  - 전에 git push 하지 않은, root-commit이 없을 경우 사용

- git restore --staged 파일명

  - root commit이 있을 경우

## Commit

- git commit --amend

  - i 누르면 insert mode (처음엔 명령모드)
  - i 누르고 delete로 삭제, 추가하고
  - esc 누르면 다시 명령모드
  - :wq (w : 저장, q : 나가기)
