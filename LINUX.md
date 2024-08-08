ls /etc/
ls -l /etc/		법칙 1 [명령어][옵션][타겟]
ls -al /etc/		법칙 2	명령어의 옵션은 조합이 가능하다
ls -dl /etc/    -l : 자세히보기 ( 현재 폴더내 파일에 대한 자세한 정보를 확인)
                 a : 숨김파일까지의 모든 파일에 대한 정보
                 d : 현재 폴더 자체에 대한 정보 ls -Ral /etc/
cat /retest/{a,b,c} > /retest/d (a,b,c)를 묶어서 d에 저장하고 출력

                 
1. /etc/login.defs /etc/passwd /boot/grub/grub.cfg 파일을 확인하고
   3개의 파일 /backup 디렉토리 생성한 뒤 복사

2. /backup에 있는 3개의 파일
   /backup/test 디렉토리에 각각 login pass grub 란 이름으로 이름변경 복사

3. /backup에 test1 이라는 파일 ,
	/backup/test 에 test2 라는 파일을 한줄명령어로 생성

 touch /backup/test1 /backup/test/test2

4. /backup/test 디렉토리를
	 /home/test/c/d/linux란 이름이 되도록  이름변경 보존 복사

  mkdir -p /home/test/c/d
  cp -p /backup/test /home/test/c/d/linux

5. /home으로 이동(cd /home) 한뒤
	경로를 변경하지 않고 /backup안에 있는 파일들 4개를 /home/test/c/d/linux
	 디렉토리에 한줄명령으로 보존복사 (이름변경및 디렉토리 복사 금지)

  cp -p /backup/grub.cfg /backup/login.defs /backup/passwd /backup/test1 /home/test/c/d/linux


![12](https://github.com/user-attachments/assets/ca543aef-f051-4723-98b1-b9ae87028cd7)
drwxr-xr-x  12 root root       4096 Apr 24 19:51 snap
   허가권         소유권
rwxr-xr-x : 허가권
root root : 소유권

r = Read : 읽기
w = Write : 쓰기
x = eXecute : 실행
r = 4, w = 2, x = 1 로 숫자로도 표현가능

rwxrwxr_x : r+w+x(=4+2+1=7) r+w+x(=4+2+1=7) r_x(=4+0+1=5) 
따라서 rwxrwxr_x = 775
rw_r_x__x : rwx,rw_,r_x,_wx,__x이므로 651로 표현가능
반대로 375 : _wxrwxr_x로 표현 할 수 있다.

|문서파일|디렉토리|
|-|-|
|r : cat, head, tail, more<br>(내용 보기)|r : ls (목록 보기)|
|w : vi (내용 수정)|w : cp, touch, mv, rm ... <br>(생성, 수정, 삭제)|
|x : ./파일명|x : cd (진입) |

drwxr-xr-x  12 root root       4096 Apr 24 19:51 snap
rwx : 소유자의 권한 r,w,x 모두가능 (읽기, 쓰기, 실행)
r-x : 사용자의 권한 r,x만 사용가능 (읽기, 실행)
r-x : 그외 권한 r,x만 사용가능 (읽기, 실행)

