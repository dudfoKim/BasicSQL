# 1. 코드 실행 과정

  * Web API : 기다려야 하는 일과 일이 끝나면 실행시킬 콜백을 API를 통해 함께 등록한다.

  * Call Stack : 스택 형태로 함수 호출과 관련된 정보(execution context)를 관리한다.

  * Task Queue : 작업 큐에 있는 작업들은 호출 스택이 비워진 다음에 수행할 수 있다.
  
    => 호출 스택에 특정 작업이 실행되고 있을 경우 : API에서 대기 - Task Queue로 전달 - Call Stack으로 이동


------
 
# 2. 비동기처리
  
  * 정의 : 특정 코드의 연산이 끝날 때까지 실행을 멈추지 않고 다음 코드를 먼저 실행하는 특성. 서버에 요청을 한 후 멈추어 있는 것이 아니라 그 프로그램은 계속 동작하며 다며 다른 일을 수행하고 있다.
  
  * Ajax(Asynchronous JavaScript and XML) : HTML페이지 전체가 아니라 필요한 부분만을 갱신할 수 있도록 XMLHttpRequest 객체를 통해 요청한다. JSON이나 XML 형태로 최소한의 필요 데이터만 받아서 갱신하게 된다.
  
------

# 3. 콜백함수

  * 정의 : 특정 함수가 실행을 마친 후에 실행되는 함수로, 자바스크립트에서는 함수도 객체이기 때문에 인자로 전달된 함수를 콜백함수라고 한다.
  
  * 특징 : 비동기 데이터를 처리하기 위해 함수의 인자로 콜백함수를 넣고, 비동기처리가 끝나는 시점에 콜백함수를 실행시킨다. 비동기프로그래밍을 위해 비동기적으로 콜백함수를 호출하는 함수(setTimeout 등)와 비동기적으로 호출될 수 있는 콜백함수가 필요하다.
  
  * ex1) setTimeout 이용
  
        console.log('Hi');
 
        setTimeout(function ()
        {
         console.log('Hi2');
        },3000);
 
        console.log('Hi3');
 
        /*
        결과
        Hi
        Hi3
        Hi2
        */
  
  
  * ex2) 절대 호출될 수 없는 "호출 이후"
  
        function fn_newCallBack()
        {
         console.log("비동기 호출");
        }
        setTimeout(fn_newCallBack, 0); // 콜백이 언제 동작할지 예측해보자.

        console.log("-------  호출 이후 -------");

        //무한로프로 콘솔을 찍어낸다.
        while(true)
        {
          console.log("한국 일교차 너무해...");
        }
        
  * Call back hell : 비동기처리 로직을 위해 콜백 함수를 연속해서 사용할 때 발생하는 문제(가독성도 떨어지고 로직 변경도 어렵다.)
  
        $.get('url', function(response)
        {
          parseValue(response, function(id) 
          {
            auth(id, function(result) 
            {
              display(result, function() 
              {
                console.log(text);
               });
             });
          });
         });
         
         => Promise나 Async를 사용해서 해결하기!
