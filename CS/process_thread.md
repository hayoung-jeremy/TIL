## Process

일반적으로 프로그램은 하드디스크 등에 저장되어 있는 실행 가능한 코드를 의미하고
process 는 프로그램이 실행되고 있는 상태를 의미한다. 프로그램이 실행되려면 필요한 자원들이 메모리에 할당 되어야 한다.

### Code

실행 명령을 포함한 코드들이 기계어 형태로 저장됨

### Data

코드에서 선언한 전역 변수나 정적 변수가 있으며, 프로그램 생성시에 할당 되었다가, 종료되면 사라짐

### Stack

함수내에 선언된 지역 변수, 매개 변수, 리턴 값 등 일시적 데이터

### Heap

동적 메모리 공간으로, 프로그램 실행시에 사용될 메모리의 크기만큼 할당 되었다가, 사용이 끝난 후 반납된다.
<br>

## Thread

- Thread 는 프로그램 내에서, 특히 Process 내에서 실행되는 흐름의 단위를 말한다.

- 기본적으로 한 프로그램은 하나의 Process 를 가지고, 그 Process 에는 하나의 Thread (Main Thread) 가 있다.

- Thread 는 Process 내에서 Stack 영역만 별도로 할당 받고, 부모 Process 의 Code, Data, Heap 영역은 공유 한다.
  <br>

## Context Switching

CPU 가 하나의 process 를 수행하다가, 다른 process 를 처리하기 위해 이전 process 의 상태를 보관하고 새로운 process 를 처리하는 작업을 말한다.

CPU 는 한번에 하나의 명령어밖에 처리하지 못한다. 컴퓨터에서 여러 작업을 가능하게 하는 멀티 태스킹은 사실 동시에 실행되는 개념이 아니다. 여러개의 process 의 생성, 준비, 실행, 대기, 종료 상태를 매우 빠른 속도로 번갈아가며 처리하기 때문에 마치 동시에 여러 작업을 수행하는 것처럼 보일 뿐이다.
<br>

## Multi Process

하나의 응용 프로그램을 여러개의 Process 로 구성하여 하나의 Proecss 가 한개의 작업(task)을 처리하도록 한다.  
장점

- 안정성이 높다. 한개의 Process 에 문제가 생겨도, 다른 Process 들이 영향을 받지 않는다.
- 구현이 비교적 간단하다.

단점

- 메모리 사용량이 높다.
- Context Switching 비용이 비싸다. 캐시 메모리 초기화와 같은 무거운 작업들이 수행되며, 성능 저하의 우려가 있다.
- 각각의 Process 들은 독립된 메모리 영역을 할당 받았기 때문에, 서로의 메모리에 대해 접근할 수 없으며, IPC (Inter-Process Communication) 를 통해서만 가능하다.
  <br>

## Multi Thread

하나의 응용프로그램을 여러 개의 Thread 로 구성하고 각 Thread 로 하여금 하나의 작업(task)을 처리하도록 한다.

사용자 경험을 높이기 위해, DB 나 Network 작업처럼 시간이 오래 걸리는 긴 작업을 수행하면서, 동시에 사용자와 상호 작용 하기 위해 주로 사용된다.

ex) 웹 서버 — 대표적인 Multi Thread 응용 프로그램  
장점

각각 할당받은 Stack 외에 다른 메모리 자원들을 공유하기 때문에,

- 자원 공유가 쉽고
- Process 를 할당하는 것보다 비용이 적게 든다.
- 작업량이 작아 Context Switching 이 빠르다.
- 응답성이 높다.

단점

- 구현 및 테스트, 디버깅이 어렵다.
- 너무 많은 Thread 사용은 오버헤드를 발생시킨다.
- 자식 Thread 하나의 문제로인해 전체 Process 에 영향을 끼칠 수 있다.

### references

- [Process와 Thread 이야기](https://charlezz.medium.com/process%EC%99%80-thread-%EC%9D%B4%EC%95%BC%EA%B8%B0-5b96d0d43e37)

- [[OS] 프로세스와 스레드의 차이 - Heee's Development Blog](https://gmlwjd9405.github.io/2018/09/14/process-vs-thread.html)

- [[10분 테코톡] 🌷 코다의 Process vs Thread](https://www.youtube.com/watch?v=1grtWKqTn50&list=PLgXGHBqgT2TvpJ_p9L_yZKPifgdBOzdVH&index=19&t=309s)
