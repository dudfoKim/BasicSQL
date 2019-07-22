# 1. '19.07.22

* DB 및 DBMS 기본내용

* SQL 기초(SELECT, WHERE절)

      @C:\create1.sql

      SELECT ROWNUM, ROWID
      FROM EMP;

      SELECT '직업 : ' ||emp.job  || ' / 이름 : ' || emp.ename || ' / 연봉 : ' || emp.sal as "내가 새로 만든거라구~"
      FROM emp;

      SELECT *
      FROM dept
      ORDER BY 1;

      SELECT distinct count(*)
      FROM emp;

      SELECT *
      FROM EMP;
      WHERE ROWNUM LIKE '2'; // Error
  
------
  
# 2. '19.07.23


------

# 3. '19.07.24


