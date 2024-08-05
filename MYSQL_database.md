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

INSERT INTO `db_name`.`tbl_name` (`column1`, `column2`, `column3`) VALUES ('값1', '값1', '값3');
INSERT INTO `db_name`.`tbl_name` VALUES ('값1', '값1', '값3'); : 모든 열에 값을 할당한다면 열이름을 생략 할 수 있다.
INSERT INTO `db_name`.`tbl_name` (`column1`, `column3`) VALUES ('값1', '값3'); : 일부 열에만 값을 할당할땐, 제약조건을 확인해야한다 (제약조건이 non-null 일경우 반드시 값을 넣어야함)

UPDATE `db_name`.`tbl_name` SET `column1` = 'user1', `column2` = '김범수', `column3` = '대전' WHERE (`column1` = 'user1');
                                                                                             WHERE(열이름,'값') : primary key를 주로 사용한다
UPDATE 'db_name'.'tb1_name' SET 'column2' = '홍길동' 'column3' = '창원' WHERE ('column1' = 'user1');

DELETE FROM `test1db`.`tbl_user` WHERE (`user_Id` = 'user3'); : 값 삭제
