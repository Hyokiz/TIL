# 20221021 TIL

# Git

1. 백업
2. 복구
3. 협업

- working directory에서 삭제
- staging area에서 working directory로 복구
- commit 후 되돌리기

# Undoing

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

# Reset

- 시계를 과거로 되돌리는 것(복구)

- git reset

  1. soft

     - git reset --soft 파일고유번호
     - Staging Area까지 돌려줌
     - back-up 가능

  2. mixed

     - git reset --mixed(없어도 됨) 파일고유번호
     - Working Directory까지 돌려줌

  3. hard

     - git reset --hard 파일고유번호
     - 다 지워버림.
     - 원래대로 돌아가는 방법
       - git reflog : 커밋에 대한 내용이 다 나옴
       - 돌아가고 싶은 파일의 번호를 복사
       - git reset --hard 번호 하면 다시 돌아온다.

- Head

  - head : 현재 브랜치를 가리킨다.
  - 브랜치 : 최신 커밋을 가리킨다.
  - 따라서 head는 최신 커밋을 가리킨다.

# Git branch

1. git graph설치
2. 커밋 세개 함
3. 브랜치 조회

   - git branch

4. 브랜치 생성

   - git branch hotfix

5. 브랜치 변경

   - git switch hotfix

- 커밋을 하고 switch 할 것이 없을때 switch를 하자

# Git merge

- 브랜치에서 작업 후 master 브랜치에 반영하는 방법

- git merge

  - 분기된 브랜치들을 하나로 합치는 명령어
  - git merge <합칠 브랜치 이름>
  - merge 하기 전에 일단 다른 브랜치를 합치려고 하는 메인 브랜치로 switch