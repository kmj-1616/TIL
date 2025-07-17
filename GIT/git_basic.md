# GIT 명령어
## 프로젝트 시작할 때 한 번만
```
git init
```
(master) -> git 저장소로 초기화

## 프로젝트 진행 중 계속 할 것
```
git add <파일명>
```
git에 추가할 준비 (staging area로 이동)
```
git commit -m <메시지>
```
staging에 있는 파일들을 저장소에 기록
### <메시지> 예시
- "first commit"
- "add commands" : 변경사항 추가

## 확인
```
git status
```
현재 변경 사항 내역 + staging area 표시
```
git log (--oneline)
```
여태까지 변경 내역을 (한 줄로) 확인
```
git config --global -l 
```
git global 설정 정보 보기

## 직전 커밋 메시지 수정
```
git commit --amend
```
i (입력) -> esc (탈출) -> :wq (종료)

## 깃헙 원격 저장소
```
git remote add origin
git remote -v
```
깃헙 원격 저장소 등록 및 확인
```
git push origin master
```
깃헙 push
```
git add <파일명>
git commit -m "커밋명"
git push origin master
```
추가적인 변경 사항 푸시 **add->commit->push**

## pull&clone
```
git pull <name> <branch>
git pull origin master
```
원격 저장소에 있는 내용을 가져온다.
```
git clone remote_repo_url
```
원격 저장소 전체를 복제 