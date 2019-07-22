# 1. '19.07.22

* DB 및 DBMS 기본내용

* 자주 쓰는 기본쿼리

      SELECT *
      FROM tab; // 접속가능한 모든 테이블 목록조회

      DESC dept; // 해당 테이블 구조조회
      
* SQL 기초(SELECT, WHERE절)

      @C:\create1.sql
      
      SELECT 1 AS "1"
      FROM dual;
      
      SELECT '직업 : ' ||emp.job  || ' / 이름 : ' || emp.ename || ' / 연봉 : ' || emp.sal as "내가 새로 만든거라구~"
      FROM emp;
      
      SELECT distinct count(*)
      FROM emp;
      
      SELECT *
      FROM EMP;
      where ROWNUM = 2; // 에러
      
      SELECT *
      FROM emp A
      WHERE A.sal>=
            (
              SELECT AVG(B.SAL)
              FROM emp B
            );
            

  
------
  
# 2. '19.07.23


------

# 3. '19.07.24


