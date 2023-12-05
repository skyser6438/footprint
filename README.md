# footprint
통관보조로봇
정해진 좌표로 가서 상자촬영을 한 후 이미지 저장 상자에 누수가 있으면 검출 이후 검수버튼을 누르면 db에 있는 데이터를 출력
조회도 가능하고 전송을 누르면 지정된 서버로 사진 전송 

데이터베이스 서버구축(Mariadb)

sudo mysql -u root -p   //접속
show databases;      //DB의 기본 목록
select version();        //DB의 버전확인

create database --- ;  //데이터베이스 만들기
//character set utf8 collate utf8_general_ci;  //유니코드 사용 (한글사용을 위한)캐릭터셋을 utf8로 지정. 
//문자 비교시에도 utf8을 이용하여 비교할수 있도록 collate를 지정
create table type (ID int, NAME varchar(30), BARCODE int) default charset=utf8;//utf8로 설정해야 한글이 안깨짐
create table IMG (ID int, IMG mediumblob) default charset=utf8;

explain type;     //type의 테이블 구조 확인

drop database 데이터명  //데이터베이스 제거

alter table 테이블명 modify ----id int Not Null;    //테이블명쓰고 ----에 테이블 안에있는 id를 Not Null 로 적용
alter table 테이블명 add constraint pk_stinfo primary key(----id); //필드에 기본값 설정

ALTER TABLE type CHANGE BARCODE NUM int;    //컬럼명 변경
ALTER TABLE type MODIFY ID INT(20);         //칼럼 타입 변경   (11 -> 20)

ALTER TABLE type MODIFY ID varchar(30);   //int 변경

UPDATE type SET ID='8809733715007' WHERE ID='101';      //  set은 바꿀 값 where은 기존 값
insert into IMG (ID) values(880973351376);     //하나의 컬럼에 값 추가

//데이터베이스 등록
select * from type;     //조회
insert into type values (18801046367831, '애경' , 7831);    //상품 등록
update type set ID = 8809733517005 where ID = 8809733717005;   //쿼리 수정 앞에 set이 바꿀꺼 where 이 원본
