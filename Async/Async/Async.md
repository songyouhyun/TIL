# 🤨 비동기 프로그래밍이란?
## 🧑🏻‍💻 데이터 처리 모델

비동기 처리란, 데이터 처리 모델의 한 종류이다.<br>
데이터 처리 모델이란, **데이터를 받는 방식**이라고 할 수 있다.<br>
이 방식에서는 <u>***동기식 처리 모델*** 과 ***비동기식 처리 모델***</u> 이 존재한다.


![image](https://user-images.githubusercontent.com/68471917/112572422-7c98e700-8e2d-11eb-81f0-c3574ed806b8.png)
<br><br>

### 🥇동기식 처리 모델(Synchronous process model)

동기식 처리 모델은 **직렬적**으로 태스크(task)를 수행한다.<br>
즉, 태스크는 순차적으로 실행되며 어떤 작업이 수행 중이면 다음 작업은 대기하게 된다.<br>

예를 들어 서버에서 데이터를 가져와서 화면에 표시하는 작업을 수행할 때,<br>
서버에 데이터를 요청하고 데이터가 응답될 때까지 이후 태스크들은 **블로킹**(blocking, 작업 중단)된다.<br>
![https://t1.daumcdn.net/cfile/tistory/99327B375BC7D7832A](https://t1.daumcdn.net/cfile/tistory/99327B375BC7D7832A)

> 동기식으로 처리되는 코드는, **순차적으로 실행**된다.

<br>

### 🥈비동기식 처리 모델(Asynchronous process model)

비동기식 처리 모델은 **병렬적**으로 태스크(task)를 수행한다.<br>
즉, 태스크가 종료되지 않은 상태라 하더라도 대기하지 않고 다음 태스크를 실행한다.

예를 들어 서버에서 데이터를 가져와서 화면에 표시하는 태스크를 수행할 때,<br>
서버에 데이터를 요청한 이후 서버로부터 데이터가 응답될 때까지 **대기하지 않고** 즉시 다음 태스크를 수행한다.<br>

이후 서버로부터 데이터가 응답되면 이벤트가 발생하고 이벤트 핸들러가 데이터를 가지고 수행할 태스크를 계속해 수행한다.

![https://t1.daumcdn.net/cfile/tistory/99194A365BC7D8223C](https://t1.daumcdn.net/cfile/tistory/99194A365BC7D8223C)
<br>
> 비동기식으로 처리되는 코드는, **순차적으로 실행되지 않는다.**

<br>

#### 📍 주로 비동기적으로 작업을 처리할 상황
- **Ajax Web API 요청**<br>
만약 서버쪽에서 데이터를 받아와야 할 때는, 요청을 하고 서버에서 응답을 할 때 까지 대기를 해야 되기 때문에 작업을 비동기적으로 처리한다.
<br>

- **파일 읽기**<br>
주로 서버 쪽에서 파일을 읽어야 하는 상황에는 비동기적으로 처리한다.
<br>

- **암호화/복호화**<br>
암호화/복호화를 할 때에도 바로 처리가 되지 않고, 시간이 어느정도 걸리는 경우가 있기 때문에 비동기적으로 처리한다.
<br>

- **작업 예약**<br>
단순히 어떤 작업을 몇초 후에 스케쥴링 해야 하는 상황에는, setTimeout을 사용하여 비동기적으로 처리한다.