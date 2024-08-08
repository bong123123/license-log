

git init : 깃 폴더 생성 (초기화 값)

git add (file name) : staging 폴더에 file name을 추가

git status 현재 폴더의 상황 확인 (staging 여부 등)

git commit -m "massage" : 현재 staging에 저장된 파일들을 repositories에 저장

git log , git log --oneline 여태까지의 진행상황을 보여줌


git reset -soft <commit hashcode>
git reset -mixed <commit hashcode>
git reset -hard <commit hashcode>
이전 시점으로 돌아감, 단 stage파일과 commit파일 모두 리셋할지 일부만 리셋할지는 뒤의 명령어에 따라 다름
- hard : 돌아간 커밋 이후의 변경 이력을 전부 삭제
- soft : 변경 이력 삭제, 변경 내용은 남아있음, 인덱스 초기화(git add가 안되어 있는 상태)
- mixed : 변경 이력 삭제, 변경 내용은 남이있음, 인덱스도 유지(git add까지 되어 있음) 

git branch : 사용자 조회
git branch (user name) : 사용자 생성

git switch (user name) : 사용자 변경

git merge (user name) : 다른 사용자의 자료 통합

Branch는 일종의 분기점이라고 생각하면 편함
