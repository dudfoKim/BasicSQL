# 1. '19.07.22

* DB 및 DBMS 기본내용

      * 쿼리 문법순서
      SELECT                          - 1
      FROM                            - 2
      WHERE                           - 3
      GROUP BY                        - 4
      HAVING                          - 5
      ORDER BY                        - 6
      
      * 쿼리 문법순서
      FROM                            - 1
      WHERE                           - 2
      GROUP BY                        - 3
      HAVING                          - 4
      SELECT                          - 5
      ORDER BY                        - 6

* 자주 쓰는 기본쿼리

      * 접속가능한 모든 테이블 목록조회
      SELECT *
      FROM tab; 

      * 해당 테이블 구조조회
      DESC dept; 
      
* SQL 기초1

      @C:\create1.sql
      
      SELECT 1 AS "1"
      FROM dual;
      
      SELECT '직업 : ' ||emp.job  || ' / 이름 : ' || emp.ename || ' / 연봉 : ' || emp.sal as "내가 새로 만든거라구~"
      FROM emp;
      
      /* Output 결과
      내가 새로 만든거라구~                                                                     
      -------------------------------------------------------------------------------- 
      직업 : CLERK / 이름 : SMITH / 연봉 : 800                                          
      직업 : SALESMAN / 이름 : ALLEN / 연봉 : 1600                                      
      직업 : SALESMAN / 이름 : WARD / 연봉 : 1250                                       
      직업 : MANAGER / 이름 : JONES / 연봉 : 2975                                       
      직업 : SALESMAN / 이름 : M%%ARTIN / 연봉 : 1250                                   
      직업 : MANAGER / 이름 : BLAKE / 연봉 : 2850                                       
      직업 : MANAGER / 이름 : CLARK / 연봉 : 2450                                       
      직업 : ANALYST / 이름 : SCOTT / 연봉 : 3000                                       
      직업 : PRESIDENT / 이름 : KING / 연봉 : 5000                                      
      직업 : SALESMAN / 이름 : TURNER / 연봉 : 1500                                     
      직업 : CLERK / 이름 : ADAMS / 연봉 : 1100                                         
      직업 : CLERK / 이름 : JAMES / 연봉 : 950                                          
      직업 : ANALYST / 이름 : FORD / 연봉 : 3000                                        
      직업 : CLERK / 이름 : MILLER / 연봉 : 1300
      */
      
      SELECT distinct count(*)
      FROM emp;
      
      /* Output 결과
      COUNT(*)               
      ---------------------- 
      14
      
* SQL 기초2

      SELECT *
      FROM EMP;
      where ROWNUM = 2;
      
      SELECT *
      FROM EMP;
      where ROWID = 2;
      
      SELECT *
      FROM emp A
      WHERE A.sal>=
            (
              SELECT AVG(B.SAL)
              FROM emp B
            );
            
* SQL 기초3
      
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

* SQL 기초 4
      
      /*
      정상 쿼리 : DISTINCT는 Alias 가능
      쿼리 순서 : From - Where - Select - Order By
      */
      SELECT DISTINCT job, sal+comm as "정렬쓰"
      FROM emp
      ORDER BY "정렬쓰";

      // 에러발생 : DISTINCT 키워드를 사용했을 때는 SELECT절에 있는 칼럼으로만
      SELECT DISTINCT job, sal+comm  
      FROM emp
      ORDER BY sal;
  
------
  
# 2. '19.07.23

* 단일 행 함수

      1. 인자(Parameter)를 받아들여 행 1개를 결과로 반환한다.
      2. SELECT, WHERE, ORDER BY 절에 사용한다.
      3. 중첩사용이 가능하고 데이터 타입을 변경할 수 있다.
          
      cf. DB Character Set 확인
          
      SELECT parameter, value
      FROM nls_database_parameters
      WHERE parameter = 'NLS_CHARACTERSET';
      
* 단일 행 함수 - 문자함수

      1. LOWER, UPPER, INITCAP, CONCAT
      
      SELECT CONCAT(ename, ', JOB : ') as "NAME", LOWER(job), UPPER(job), INITCAP(job)
      FROM emp
      WHERE deptno = 10;
     
      /* Output 결과
      NAME               LOWER(JOB) UPPER(JOB) INITCAP(JOB) 
      ------------------ ---------- ---------- ------------ 
      CLARK, JOB :       manager    MANAGER    Manager      
      KING, JOB :        president  PRESIDENT  President    
      MILLER, JOB :      clerk      CLERK      Clerk   
      */
          
      2. LENGTH, SUBSTR, INSTR

      SELECT ename, job, INSTR(ename, 'K', length(ename)-1)
      FROM emp
      WHERE SUBSTR(ename, length(ename)-1, 1) = 'K';
         
      /* Output 결과
      ENAME      JOB       K index                
      ---------- --------- ---------------------- 
      BLAKE      MANAGER   4  
      */
          
      3. 
          
          

------

# 3. '19.07.24


