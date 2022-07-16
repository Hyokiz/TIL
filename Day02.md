# Day 02 
## Git 복습
1. git init을 두번 하지 않기
2. typora 업데이트 하지 않기 (현재 베타 버전 서비스 종료)
3. git 에 직접 파일 저장 하지 않기.

## README
- 반드시 대문자로 README.md 작성 << Github의 대문
- README 또한 git add, commit, push로 커밋


## .gitignore
- 앞에 .이 붙으면 숨김파일, 숨김폴더
- .gitignore에 ignore.txt를 작성 후 저장하면 git status에 뜨지 않는다.

### .gitignore를 사용하는 이유
1. 남에게 보여주면 안되는 보안 파일 작성
2. 굳이 올리지 않아도 되는 파일 작성

**폴더 생성 시 필수로 .gitignore, README.md를 작성**
> .gitignore 보다 먼저 생성된 파일의 경우 ignore 되지 않는다.

[gitignore.io](http://gitignore.io) ex)python, windows, visualstuidocode, django

## Clone
git clone : 다운로드 (remote 서버의 파일을 local로 다운로드 받는다.)
git clone 시
1. 폴더 생성
2. git init
3. git remote add
4. 버전, 파일 생성
이 동시에 된다. 즉, 처음 아무것도 없는 상태일 때 git clone을 한다.

### git clone 사용법
폴더를 만들고 싶은 곳에서 git clone (클론할 폴더 주소)

## Pull
git pull : 업데이트
업데이트 후 git push > git pull

### remote와 local 에서 pull 하지 않고 push만 해서 버전이 충돌할 경우
pull 해서 선택하기 후 git status > git add, commit, push

## Merge
합친다는 개념.

## Commit message convention
커밋 할 때의 규칙이다. 통일해야한다.
ex) add sth, update sth, remove sth ...

---
> 모르는 것은 알게 될 때 까지 노력하는 것이 중요하다.
> > 정확한 정보를 알고 남에게 전파할 수 있을 정도로 공부하자.