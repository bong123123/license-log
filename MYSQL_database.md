create databases db_name ;  // database 생성
drop db_name     //database 삭제

use db_name;          //database 사용 명시
create table tbl_name(
컬럼명 자료형 제약조건
컬럼명 자료형 제약조건      //table및 column생성
        .
        .
        .
컬럼명 자료형 제약조건);

제약조건 종류 : NOT NULL
               UNIQUE
               PRIMARY KEY
               FOREIGN KEY
               DEFAULT


show databases;       //database 확인
desc tbl_name;           //table구조확인

ALTER TABLE `db_name`.`tbl_name` //db_name은 현재 사용중인 db에 추가하는 경우 생략가능함. 
ADD COLUMN `column2` VARCHAR(1024) NULL AFTER//생략가능 `column1`; //columnname1 뒤에 columnname2를 문자 자료형(1024), null제약조건으로 작성

ALTER TABLE `db_name`.`tbl_name` 
DROP COLUMN `column1`;    // column2 삭제

ALTER TABLE `db_name`.`tbl_name` 
CHANGE COLUMN `column2` `change_column` VARCHAR(512) NOT NULL ; //column2의 이름을 change_column으로, 자료형을 varchar(512)로 제약조건을 not null로 변경

select *from tb1_name : *은 모두를 의미 즉, tb1_name의 요소를 확인 할 수 있다.
select column1 from tb1_name : tb1_name의 column1의 값을 확인 할 수 있다.

INSERT INTO `db_name`.`tbl_name` (`column1`, `column2`, `column3`) VALUES ('값1', '값1', '값3');
INSERT INTO `db_name`.`tbl_name` VALUES ('값1', '값1', '값3'); : 모든 열에 값을 할당한다면 열이름을 생략 할 수 있다.
INSERT INTO `db_name`.`tbl_name` (`column1`, `column3`) VALUES ('값1', '값3'); : 일부 열에만 값을 할당할땐, 제약조건을 확인해야한다 (제약조건이 non-null 일경우 반드시 값을 넣어야함)

UPDATE `db_name`.`tbl_name` SET `column1` = 'user1', `column2` = '김범수', `column3` = '대전' WHERE (`column1` = 'user1');
                                                                                             WHERE(열이름,'값') : primary key를 주로 사용한다
UPDATE 'db_name'.'tb1_name' SET 'column2' = '홍길동' 'column3' = '창원' WHERE ('column1' = 'user1');

DELETE FROM `test1db`.`tbl_user` WHERE (`user_Id` = 'user3'); : 값 삭제


root 계정(admin 관리자)으로 사용자를 만들고, 권한을 부여할 수 있다.
select *from user; : user데이터베이스의 테이블 목록을 확인 할 수 있다.
select host,user from user; : user데이터베이스의 host,user테이블만 확인해보자

create user user1@localhost identified by '1234'; : user테이블에 localhost로 user1라는 이름의 계정 생성, 비밀번호로 '1234'부여
select host,user from user;로 다시 한번 확인해보면 user1이라는 새로운 행이 생성되었음을 확인 가능
mysql -u user1 -p;
password : 1234로 user1으로 다시 접속후 show databases;를 입력하면 제대로 된 데이터베이스를 확인 할 수 없다.
root 계정으로 user1에게 권한을 부여해야한다.
grant select on test1db.* to user1@localhost;로 test1db의 모든것(*)을 select할 수 있는 권한을 주었다.
user1계정으로 접속한 cmd에서 select *from test1db.tbl_user;로 test1db의 tbl_user테이블을 확인할 수 있게 되었다.

그러나 insert into test1db.tbl_user values('user1234','홍길동','대전');를 입력해보면, 아직 insert권한을 부여 받지 못했기때문에 오류를 확인 할 수 있다.
grant select,insert on test1db.* to user1@localhost; : user1에게 select와 insert 권한을 부여함
insert into test1db.tbl_user values('user1234','홍길동','서울');을 입력해보면 insert의 동작을 확인가능

grand all privileges on test1db.* to user1@localhost로 모든 권한을 부여할수도 있다.
localhost는 하나의 컴퓨터에서 접근 할 수 있는 계정이란 뜻임. 즉 다른 컴퓨터로는 접속 할 수 없음

create user user2@'%' identified by '1234'; 
%는 와일드카드 문자로 0개 이상의 임의의 문자를 나타내며, 이를 통해 호스트 이름이나 IP 주소의 일부만 일치시키는 패턴을 지정할 수 있음.
ex) '192.168.1.%'로 설정하면 192.168.1로 시작하는 모든 ip주소를 나타냄.
즉 위에서 user2@'%'는 모든 ip주소나 호스트에 대한 접근을 허용하는것
이제 user2는 모든 ip에서 접속할 수 있음.

mysql -u user2 -p -h 192.168.5.50 : user2는 원격접속이 가능함 192.168.5.50에게 접속한다는 뜻
