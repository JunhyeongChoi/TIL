# Django를 위한 DB

## DB
* 데이터를 저장하는 공간

## DBMS
* DataBase Management Service

* DB안에 데이터를 관리해주고 다른 소프트웨어가 이 DB에 접근할 수 있게 해주는 소프트웨어

* MySQL, ORACLE, SQLServer, SQLite (장고에서 기본적으로 제공하는 DBMS), PostgreSQL 등등..

### RDBMS
* 관계형 데이터베이스
* 표처럼 데이터를 관리하는 DB (표로써 데이터를 관리하면 굉장히 편하기 때문에 가장 대중적으로 쓰이는 방식)
##### 예를들어

|이름|ID|PW|
|------|---|---|
|김OO|kim123|********|
|최OO|choi123|******|
|박OO|park123|*******|

위와 같은 표 하나하나를 Table이라고 부름

* 앞서 말한 DBMS 종류 MySQL 등등. 모두 RDBMS

## SQL
* DBMS을 이용해서 DB에 접근하고 조작하는 언어
