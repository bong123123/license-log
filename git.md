
# Git 기본 명령어

git init : .git 폴더 생성 (초기화 값)
git add (file name) : staging 폴더에 file name을 추가
git status 현재 폴더의 상황 확인 (staging 여부 등)
git commit -m "massage" : 현재 staging에 저장된 파일들을 repositories에 저장
git log , git log --oneline 여태까지의 진행상황을 보여줌

git reset -soft <commit hashcode>
git reset -mixed <commit hashcode>
git reset -hard <commit hashcode>
이전 시점으로 돌아감, 단 stage파일과 commit파일 모두 리셋할지 일부만 리셋할지는 뒤의 명령어에 따라 다름
- hard : 돌아간 커밋 이후의 변경 이력을 전부 삭제 (working directory : 삭제 / stage area : 삭제)
- soft : 변경 이력 삭제, 변경 내용은 남아있음, 인덱스 초기화(working directory : 유지 / stage area : 유지)
- mixed : 변경 이력 삭제, 변경 내용은 남이있음, 인덱스도 유지(working directory : 유지 / stage area : 삭제)



git branch : 사용자 조회
git branch (branch name) : 사용자 생성

git switch (branch name) : 사용자 변경

git merge (branch name) : 다른 사용자의 자료 통합
git merge --continue (충돌해결 후 fast-foward merge)
git merge --abort (충돌무시 merge)

Branch는 일종의 분기점이라고 생각하면 편함

git과 github연동 과정
git init
git add fileName
git branch -M main    ** 커밋전 브랜치 main으로 설정
git commit -m "massage"
git remote -v
git remote add origin githubRepositoryURL

github
new Repository 생성 (README 생성 X)

github에서 git으로 연동
github
new Repository 생성 (README 생성 O)

git
git clone URL
작업
git push origin
git pull origin
git fetch origin
