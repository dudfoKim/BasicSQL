# 커서

  1. 오라클 서버에서는 SQL문을 실행할 때마다 처리를 위한 메모리공간을 사용한다.
  
   * 사용자가 요청하는 데이터를 DB버퍼에서 커서로 복사해 온 후 커서(Cursor area)에서 원하는 데이터를 추출한다.
   * 묵시적 커서와 명시적 커서로 나눌 수 있다.

  
  2. 종류
    
   * 묵시적 커서
  
        PL/SQL 블록 내에서 SELECT, DML문이 실행될 때마다 묵시적 커서가 선언된다.
        묵시적 커서에는 1행 데이터만 저장가능하며, 문장이 종료되면 동시에 정리된다.
        SQL% 접두어로, ROWCOUNT/FOUND/NOTFOUND/ISOPEN 4개의 속성을 사용할 수 있다.
    
    
  * 암시적 커서
  
        사용자가 선언하여 생성 후 사용하는 SQL커서로, 여러 개의 행을 처리하고자 할 때 사용한다.
        커서 이름을 접두어로 가지며, 역시 4개의 속성을 사용할 수 있다.
        
        CURSOR c IS  
          SELECT biz_cd, biz_nm
          FROM TB_STG1070; // (세미콜론 꼭 찍기!)

        BEGIN
          FOR DML IN c LOOP
    
          OPEN C_FCR_MST;
     
        LOOP
          FETCH c INTO c_cd, c_nm;
        
        END LOOP;
        CLOSE c;
     
        EXCEPTION
          WHEN OTHERS THEN // 에외처리          
          
        END;
        
        
