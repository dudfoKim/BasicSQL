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
      
      // 에러 발생
      SELECT *
      FROM EMP;
      where ROWNUM = 2;
      
      SELECT *
      FROM emp A
      WHERE A.sal>=
            (
              SELECT AVG(B.SAL)
              FROM emp B
            );
            
      /*   
      1. 기본 연산자 우선순위 : 괄호 > and > or
      2. or 연산자는 조건의 뒤부터 순차적으로 결과를 판단한다. (F6 활용)
      3. 밑의 쿼리는 결과가 다르다. 한 번 생각해보기 
      */
      SELECT empno, ename, job, sal
      FROM emp
      WHERE sal>1500 and job='PRESIDENT' or job='SALESMAN';
      
      SELECT empno, ename, job, sal
      FROM emp
      WHERE sal>1500 and (job='PRESIDENT' or job='SALESMAN');
      
      // Condition : 1250 미만, 2500 초과
      SELECT *
      FROM emp
      WHERE sal not between 1250 and 2500;         

      // 정상적으로 실행되는 쿼리는 무엇이고, 에러가 발생하는 쿼리일 경우 그 이유는?
      SELECT DISTINCT job, sal+comm
      FROM emp
      ORDER BY 2;

      SELECT DISTINCT job, sal+comm
      FROM emp
      ORDER BY sal;
  
------
  
# 2. '19.07.23


------

# 3. '19.07.24


