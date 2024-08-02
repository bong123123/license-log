create databases dbname ;  // database 생성
drop dbname     //database 삭제

use dbname;          //database 사용 명시
create table tblname(
컬럼명 자료형 제약조건
컬럼명 자료형 제약조건      //table및 column생성
        .
        .
        .
컬럼명 자료형 제약조건);

show databases;       //database 확인
desc tblname;           //table구조확인

ALTER TABLE `dbname`.`tblname` //dbname은 현재 사용중인 db에 추가하는 경우 생략가능함. 
ADD COLUMN `column2` VARCHAR(1024) NULL AFTER//생략가능 `column1`; //columnname1 뒤에 columnname2를 문자 자료형(1024), null제약조건으로 작성

ALTER TABLE `dbname`.`tblname` 
DROP COLUMN `column1`;    // column2 삭제

ALTER TABLE `dbname`.`tblname` 
CHANGE COLUMN `column2` `change_column` VARCHAR(512) NOT NULL ; //column2의 이름을 change_column으로, 자료형을 varchar(512)로 제약조건을 not null로 변경
