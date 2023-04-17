# 프로세스와 스레드

## 프로세스 개요
- - -
- 포그라운드 프로세스(foreground process): 사용자가 보는 앞에서 실행되는 프로세스
- 백그라운드 프로세스(background process): 사용자가 보지 못하는 뒤편에서 실행되는 프로세스
  - 유닉스 체계의 운영체제에서 `데몬`
  - 윈도우 운영체제에서는 `서비스`

### 프로세스 제어 블록
운영체제는 번갈아가며 수행되는 프로세스의 실행 순서를 관리하고, 프로세스에 cpu자원을 배분합니다.
이를 위해 운영체제는 `프로세스 제어 블록(PCB:process control block)`을 이용합니다.
- PCB : 프로세스와 관련된 정보를 저장하는 자료구조
  - 메모리의 커널영역에 생성됨
  - 운영체제는 pcb로 특정프로세스를 식별하고 해당 프로세스를 처리하는 데 필요한 정보를 판단합니다.
  - PCB는 프로세스 생성시 만들어지고 실행이 끄타면 폐기됨

- PCB에 담기는 정보
  - 프로세스ID(PID) : 프로세스를 식별하기 위한 고유 번호
  - 레지스터 값 : 해당 프로세스가 실행하며 사용했던 프로그램 카운터 등 레즈스터의 값
  - cpu스케줄링 정보 : cpu를 할당받기 위한 순서
  - 메모리관리정보 : 프로세스가 어느 주소에 저장되어 있는지, 페이지 테이블 정보
  - 사용한 파일과 입출력장치 목록 : 어떤 입출력장치가 할당되었는지, 어떤 파일들을 열었는 지
  
### 문맥교환
기존 프로세스의 문맥을 PCB에 백업하고, 새로운 프로세스를 실행하기 위해 문맥을 PCB로부터 복구하여 새로운 프로세스를 실행하는 것
- *문맥 : 하나의 프로세스 수행을 재개하기 위해 기억해야할 정보 -> PCB에 기록되어있음

### 프로세스 메모리 영역
그렇다면 사용자 영역에는 크게 `코드영역`, `데이터 영역`, `힙 영역`, `스택 영역`으로 나뉘어 저장됨
- 정적 할당 영역
  - 코드 영역(code segment)
    - 데이터가 아닌 cpu가 실행할 명령어(기계어로 이루어진 명령어)가 담김
    - 읽기 전용(read-only), 쓰기 금지
  - 데이터 영역(data segment
    - 프로그램이 실행되는 동안 유지할 데이터 (ex 전역변수)
- 동적 할당 영역
  - 힙 영역(heap segment)
    - 프로그램을 만드는 사용자, 프로그래머가 직접할당할 수 있는 저장공간
    - 할당한 메모리를 반환해야함. -> 반환하지 않으면, 메모리 누수가 발생할 수 있음
  - 스택 영역(stack segment)
    - 데이터를 일시적으로 저장하는 공간(ex 매개변수, 지역변수)

## 프로세스 상태와 계층 구조
문맥교환 과정에서, 하나의 프로세스는 여러 상태를 거치며 실행됩니다. 운영체제는 프로세스의 상태를 pcb를 통해 인식하고 관리합니다.
- 생성상태(new)
  - 프로세스를 생성중인 상태로, 막 메모리에 적재되어 pcb를 할당받은 상태
  - 생성이 완료되면 `준비상태`가 됨
- 준비상태(ready)
  - cpu를 할당받기 위해 기다리는 상태
- 실행상태(runnung)
  - cpu를 할당받아 실행중인 상태
  - 실행 도중 입출력장치를 사용하는 경우 `대기상태`가 됨.
- 대기상태(blocked)
  - 입출력장치를 사용하는 경우, 입출력장치의 작업을 기다리는 상태
  - 입출력장치의 작업이 완료되면 `준비상태`가 됨.
- 종료상태(terminated)
  - 프로세스가 종료된 상태
  - 운영체제는 pcb와 프로세스가 사용한 메모리를 정리함.

### 프로세스 계층 구조
프로세스는 실행도중 시스템 호출을 통해 다른 프로세스를 생성할 수 있습니다. 
- 부모프로세스(parent process) : 새로운 프로세스를 생성하는 프로세스.
- 자식 프로세스(child process) : 부모프로세스에 의해 생성된 프로세스.  
부모프로세스와 자식프로세스는 각기다린 PID를 갖는다.

### 프로세스 생성 기법
fork와 excc는 `시스템 호출`로 부모프로세스는 `fork`를 통해 자신을 복사하고, 복사로 생성된 프로세스는 `exec`를 통해 메모리 공간을 다른 프로그램으로 교체합니다.
1. 복제(fork) : PID와 저장된 위치를 제외한 나머지가 복사되어 새로운 프로세스를 생성
2. 교체(exec) : 코드 영역과 데이터 영역의 내용이 실행할 프로그램으로 교체되고 나머지영역은 초기화됨

## 스레드
- - -
- 스레드: 프로세스를 구성하는 실행의 흐름 단위, 하나의 프로세스는 여러개의 스레드를 가질 수 있음.

### 프로세스와 스레드
스레드는 각기다른`스레드ID`, `프로그램 카운터를 비롯한 레지스터 값`, `스택`으로 구성됨
- 즉, 실행에 필요한 최소한의 정보만을 유지한 채, 프로세스 자원을 `공유(코드영역, 데이터영역,힙영역)`하며 실행한다.

### 멀티프로세스와 멀티스레드
- 멀티프로세스
  - 여러 프로세스를 동시에 실행하는 것
  - 멀티프로세스는 같은 프로그램을 실행하기 위해 메모리에동일한 내용들이 중복되는 메모리 낭비가 일어남.

- 멀티스레드
  - 여러 스레드로 프로세르를 동시에 실행하는 것.
  - 스레드마다 각기 다른 레지스터값, 스택을 가질뿐 나머지 자원을 공유하여, 메모리를 효율적으로 사용할 수 있음.
  - 자원을 공유하기 때문에 서로 협력과 통신에 유리함
  - 자원을 공유하기 때문에, 하나의 스레드에 문제가 생길 경우 프로세스 전체에 영향을 미침.