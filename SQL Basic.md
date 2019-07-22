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
            
      SELECT empno, ename, job, sal, deptno
      FROM EMP
      WHERE sal>=2800 and job in ('manager', 'MANAGER'); // job='manager' or job='MANAGER'
      // = or 형태는 무조건 조건의 뒤부터 순차적으로 결과를 판단한다. (F6 활용)
      
      SELECT *
      FROM emp
      WHERE sal not between 1250 and 2500; // 1250 미만, 2500 초과            

  
------
  
# 2. '19.07.23


------

# 3. '19.07.24


