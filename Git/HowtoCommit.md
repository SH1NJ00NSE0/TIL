# How to Commit?


### 커밋 순서
1. init
2. remote
3. add
4. commit
5. push


### 1. init

```bash
git init
```
프로젝트 생성 후 최초 1번만 실행해주면 된다.

### 2. remote

```bash
git remote add "원격 저장소 이름" "원격저장소 https"
```
프로젝트 생성 후 최초 1번만 실행해주면 된다.<br>
`"원격 저장소 이름"`은 일종의 원격저장소 별명이라고 할 수 있다. 딱히 상관 없다.<br>
`"원격저장소 https"`에서는 레포지토리의 주소를 복붙해주면 된다.

### 3. add

```bash
git add "파일명 or 폴더명"
```
특정상황에서는 파일명, 폴더명을 적어주면 되지만,<br>
보통 `git add .` 으로 한번에 모든 파일, 폴더를 다 올리는 편이다.

### 4. commit

```bash
git commit -m "커밋메세지"
```
커밋 메세지 룰에 맞춰 유연하게 커밋메세지를 작성하면 된다.

### 5. push

```bash
git push "원격 저장소 이름" "branch 이름"
```
push할 원격 저장소 이름과 branch이름을 넣는다.<br>
ex) `git push origin master`