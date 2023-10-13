# 컴퓨터 구조와 운영체제 

<a href ='https://www.google.co.kr/books/edition/%ED%98%BC%EC%9E%90_%EA%B3%B5%EB%B6%80%ED%95%98%EB%8A%94_%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B5%AC%EC%A1%B0+%EC%9A%B4/OXmAEAAAQBAJ?hl=ko&gbpv=1&dq=%ED%98%BC%EC%9E%90+%EA%B3%B5%EB%B6%80%ED%95%98%EB%8A%94+%EC%BB%B4%ED%93%A8%ED%84%B0+%EA%B5%AC%EC%A1%B0+%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C&printsec=frontcover'>**혼자 공부하는 컴퓨터 구조 + 운영체제**</a>

## 프로세스와 스레드 차이는 ?

프로세스와 스레드 모두 운영체제에서 동작하는 실행 단위로 **프로세스**는 운영체제로부터 **‘자원을 할당받는 작업 단위’** 이고, **스레드**는 프로세스가 **‘할당 받은 자원을 이용하는 실행의 단위’** 입니다. 

프로세스와 스레드의 가장 큰 차이점은 **자원 공유 여부**입니다. 

**프로세스는 독립적으로 실행되고 자원을 공유하지 않지만, 스레드는 프로세스 내에서 실행되고 자원을 공유합니다.** 또한 프로세스 사이에는 **메모리 공간이 분리**되어 있지만, 스레드 사이에는 **메모리 공간을 공유**합니다. 

## 멀티프로세스와 멀티스레드 차이는 ?

멀티 프로세스는 **여러 개의 독립적인 프로세스를 동시에 실행하는 것이며 멀티 스레드는 하나의 프로세스 내에 여러 개의 스레드를 생성하여 동시에 실행하는 것**입니다.

**멀티 프로세스 환경**에서는 프로세스들이 독립적으로 실행되기 때문에 하나의 프로세스에 오류가 발생해도 다른 프로세스들에게 영향을 주지 않습니다. 
또한 프로세스들 끼리 자원을 공유하지 않기 때문에 새로운 PCB를 적재하는 과정에서 문맥교환의 오버헤드가 크게 발생합니다.

반면, **멀티 스레드 환경**에서는 스레드들끼리 프로세스 내의 자원을 공유하기 때문에 하나의 스레드에 문제가 발생하면 다른 스레드들에게도 영향을 주게됩니다. 또한 멀티스레드는 멀티 프로세스보다 더 작은 메모리 공간을 자치하며 문맥교환의 오버헤드가 적습니다.

- 오버헤드: 오버헤드란 프로그램의 실행 흐름에서 나타나는 현상 중 하나로 예를 들어 , 프로그램의 실행 흐름 도중에 동떨어진 위치의 코드를 실행시켜야 할 때 , 추가적으로 시간,메모리,자원이 사용되는 현상입니다.

## 교착상태란 무엇인가 ?

**교착상태(DeadLock)** 두 개 이상의 프로세스나 스레드가 각자 가지고 있는 자원을 서로 얻기 위해 기다리고 있는 상황에서 작업을 더 이상 진행하지 못하는 상태를 말합니다.

## 교착 상태의 4가지 조건에 대해 설명해보세요.

교착 상태의 4가지 조건에는 상호배제, 점유와 대기, 비선점, 원형 대기가 있습니다.

1. **상호 배제 / Mutual Exclusion** 
    - 자원은 한 번에 한 프로세스 또는 스레드만 사용할 수 있어야 합니다.
2. **점유 대기 / Hold and Wait** 
    - 프로세스나 스레드가 할당된 자원을 가진 상태에서 다른 자원을 기다리고 있어야 합니다.
    - 자원을 보유한 채 다른 자원을 기다렸기 때문에 발생합니다.
3. **비선점 / No Preemption**
    - 프로세스가 자원을 비선점 하는 경우 발생합니다
    - 즉 어떤 프로세스도 다른 프로세스의 자원을 강제로 빼앗지 못했기 때문에 교착 상태가 발생했다고 볼 수 있습니다.
4. **원형 대기 / Circular Wait** 
    - 프로세스들과 프로세스가 요청 및 할당받은 자원이 원의 형태를 이루었기 때문에 발생합니다.

## 교착상태의 해결방법에 대해 설명해보세요.

교착 상태는 **시스템이 중요한 자원을 효율적으로 활용하지 못하게 하고, 시스템의 안정성을 저하**시킵니다. 

교착 상태를 해결하는 방법에는 예방, 회피, 검출 후 회복이 있습니다. <br>
예방은 교착상태가 발생하지 않도록 발생 조건에 부합하지 않게 자원을 분배하는 방법입니다. 즉 교착상태의 4가지 조건 중 하나를 충족하지 못하게 하는 방법입니다. <br>
회피는 교착 상태가 발생하지 않을 정도로 자원을 할당하다가 교착상태의 위험이 있다면 자원을 할당하지 않는 방법입니다.<br>

검출 후 회복은 자원을 제약 없이 할당하다가 교착 상태가 검출되면 교착 상태를 회복하는 방법입니다. 교착상태를 회복하는 방법에는 선점을 통한 회복과 프로 세스 강제 종료를 통한 회복이 있습니다.

1. **선점을 통한 회복**
    
    **선점을 통한 회복은 교착 상태가 해결될 때까지 한 프로세스씩 자원을 몰아주는 방식**입니다.
    
2. **프로세스 강제 종료를 통한 회복**
    
    **운영체제가 교착 상태에 놓인 프로세스를 모두 강제종료하는 것으로** 프로세스 강제 종료를 통한 회복은 가장 단순하면서 확실한 방식입니다.
    

## 메모리 계층에 대해서 예시를 들어 설명해보세요.

메모리 계층 구조는 **컴퓨터에서 사용되는 메모리를 계층적으로 구성하여 성능을 최적화하는 방식**입니다.
CPU에 가까운 순으로 레지스터, 캐시 메모리, 주 기억장치, 보조기억장치로 구조화 되어있습니다.

**레지스터**는 CPU 내부에 존재하는 임시 저장장치로 CPU가 가장 빠른 속도로 접근할 수 있습니다. 

**캐시 메모리**는 CPU와 주 기억장치 사이에 위치하며 레지스터 다음으로 접근 속도가 빠릅니다. CPU가 주 기억장치에 접근하는 시간을 최소화 하기 위해 일부 데이터를 캐시 메모리로 가져와서 사용합니다.

**주 기억장치**는 캐시메모리와 보조기억장치 사이에 위치하며 캐시 메모리 다음으로 접근 속도가 빠릅니다. 주 기억장치에는 프로그램이 실행되는데 필요한 모든 데이터를 저장합니다.

**보조기억장치**는 하드 디스크 드라이브와 같은 큰 용량을 가진 저장 장치 접근 시간이 매우 느립니다.

CPU는 실행과정에서 필요한 데이터나 명령어를 레지스터에 저장하여 사용합니다. <br>
추가적인 데이터가 필요할 경우, 캐시 메모리를 먼저 확인합니다. 만약 캐시메모리에 해당 데이터가 없을 경우, 주 기억장치에 접근하여 확인합니다. 
만약 주 기억장치에서 추가적으로 데이터를 가져와야하는경우 보조기억장치에서 데이터를 읽어와 주 기억장치에 저장합니다.

## 키보드에서 “A”를 입력하면, 어떤 과정을 통해 컴퓨터에 “A”라고 출력 되는지 설명해보세요.

키보드에서 “A”를 입력했을 때 키보드 컨트롤러는 키 입력 신호를 감지하고 CPU 인터럽트를 요청을 발생시킵니다.

CPU는 실행 중인 프로세스를 일시 중단하고 인터럽트 처리 루틴을 실행합니다. 운영체제는 키보드 드라이버를 통해 입력된 “A”를 인식하고 ”A” 아스키 코드에 해당하는 65번으로 변환합니다.

CPU는 출력하고자하는 프로세스를 찾아 해당 장치의 입출력 포트로 데이터를 전송합니다. 데이터는 전기 신호로 변환되어 출력 장치로 전달되고 출력장치는 데이터를 해석하여 화면에 “A”라는 문자를 출력합니다.

## 시스템 콜과 서브루틴의 차이는 ?

**시스템 콜(System Call)과 서브루틴(Subroutine)은 프로그램이 실행될 때 다른 코드 블록으로 제어를 전환할 수 있는 방법**입니다.
그러나 이 두 가지 기술은 **목적과 사용 방법에서 차이**가 있습니다.

**시스템 콜**은 운영 체제에 내장된 함수를 호출하여 커널 레벨에서 실행되도록 하는 방법입니다. 
운영 체제에서 제공하는 서비스(파일 입출력, 네트워크 통신 등)를 호출하고, 시스템 콜 인터페이스를 통해 커널 레벨의 자원에 접근할 수 있습니다. 시스템 콜은 커널 모드로 전환하여 시스템 자원에 접근하므로, 사용자 모드에서 직접 접근할 수 없는 하드웨어 자원을 제어할 수 있습니다.

반면에, **서브루틴**은 프로그램 내에서 다른 코드 블록을 호출하여 재사용 가능한 함수를 구현하는 방법입니다. 
서브루틴은 일반적으로 유저 모드에서 실행되며, 사용자가 직접 작성한 코드에서 호출됩니다. 서브루틴은 프로그램 내에서 호출되어 동작하며, 서브루틴 호출 후에는 제어가 호출한 위치로 돌아옵니다.

따라서, 시스템 콜과 서브루틴은 기술적으로 유사하지만, 용도와 사용 방법에서 차이가 있습니다. 시스템 콜은 운영 체제에서 제공하는 자원에 접근하기 위해 사용되며, 서브루틴은 프로그램 내에서 재사용 가능한 함수를 구현하기 위해 사용됩니다.

## 동기와 비동기의 차이는 ?

**동기**는 요청과 그 결과가 한 쌍으로 이루어지며, 요청에 대한 처리가 완료될 때까지 결과를 기다리는 방식입니다. 
즉, **작업이 끝날 때까지 다음 작업을 진행하지 않습니다.** 
동기 방식은 간단하고 직관적이지만, 대기 시간이 발생할 수 있으며, 처리 시간이 길어지면 전체 시스템 성능에 영향을 미칠 수 있습니다.

반면에, **비동기**는 요청과 그 결과가 서로 다를 수 있으며, 요청을 보낸 후 결과를 기다리지 않고 다른 작업을 진행하는 방식입니다. 
즉, **작업이 끝나지 않아도 다음 작업을 진행할 수 있습니다.** 
비동기 방식은 대기 시간이 없고, 처리 시간이 길어져도 전체 시스템 성능에 영향을 미치지 않습니다. 그러나 복잡한 구현 방식이 필요하며, 작업 결과를 확인하기 위한 추가적인 코드가 필요합니다.

웹 서버에서 파일을 읽어서 반환하는 작업을 수행한다고 가정해보면, 동기 방식에서는 파일을 읽을 때까지 다른 작업을 수행하지 않으며, 비동기 방식에서는 파일을 읽는 동안 다른 요청에 대한 처리를 계속 수행할 수 있습니다.

동기와 비동기의 가장 큰 차이점은 **작업이 완료되는 시점에 대한 처리 방식입니다**. 
**동기 방식은 작업이 완료될 때까지 기다리며, 비동기 방식은 작업을 시작한 후 다른 작업을 계속 수행할 수 있습니다.**

## Race Condition이란무엇이고 왜 발생하는가 ?

**Race Condition은 동시에 두 개 이상의 프로세스나 스레드가 공유 자원에 접근할 때 발생하는 문제입니다.** <br>
이 때, 두 개 이상의 프로세스나 스레드가 동일한 자원에 접근하며, 각각의 프로세스나 스레드가 자원을 변경하려고 할 때 예측할 수 없는 결과가 발생할 수 있습니다. <br>
이러한 문제는 공유 자원을 사용하는 동안 발생할 수 있으며, 대개는 동기화 문제로 인해 발생합니다. <br>
여러 프로세스나 스레드가 동시에 공유 자원을 업데이트하려는 경우, 다음과 같은 문제가 발생할 수 있습니다.

1. 값의 불일치 : 두 개 이상의 프로세스나 스레드가 동시에 자원을 변경하면서 원치 않는 값을 얻을 수 있습니다.
2. 데드락 : 두 개 이상의 프로세스나 스레드가 서로의 작업이 끝날 때까지 기다리는 상황이 발생할 수 있습니다.
3. 잘못된 결과 : 두 개 이상의 프로세스나 스레드가 동시에 자원을 변경하면서 예상하지 못한 결과가 발생할 수 있습니다.

## 가상 메모리란 무엇인가요 ?

**가상 메모리(Virtual Memory)는 컴퓨터의 주기억장치(RAM)와 하드 디스크를 조합하여 하나의 큰 메모리 공간으로 인식하도록 하는 기술입니다**. <br>
실행하고자 하는 프로그램을 일부만 메모리에 적재하여 실제 물리 메모리 크기보다 더 큰 프로세스를 실행할 수 있습니다. 가상 메모리를 사용하면 외부 단편화 문제를 최소화 할 수 있으며 물리 메모리보다 더 큰 프로세스를 실행할 수 있게 됩니다. 가장 메모리 기법에는 페이징과 세그멘테이션이 있습니다. <br>
- 페이징 : 프로세스의 논리 주소공간을 페이지라는 일정한 단위로자르고, 메모리 물리주소 공간을 프레임이라는 페이지와 동일한 크기로 다른 뒤 페이지를 프레임에 할당하는 가상 메모리 관리 기법입니다.

**가상 메모리 사용 목적** 
1. 물리적인 메모리 용량을 넘어서는 대용량 데이터 처리 가능
    - 물리적인 메모리 용량이 부족한 상황에서도, 가상 메모리를 통해 대용량 데이터를 처리할 수 있다. <br>
2. 여러 프로그램 동시 실행 시 메모리 용량 문제 해결
    - 여러 개의 프로그램을 동시에 실행할 때, 물리적인 메모리 용량이 부족하면 프로그램이 정상적으로 실행되지 않는다.         
    하지만 가상 메모리를 사용하면 여러 개의 프로그램을 동시에 실행할 때도 메모리 용량 문제를 해결할 수 있다. <br>      
3. 프로그램 실행 속도 향상
    - 가상 메모리를 사용하면, 일부 데이터와 코드만 미리 메모리에 올리고, 나머지 부분은 하드 디스크에 저장해두므로, 메모리 사용량이 줄어들어 프로그램 실행 속도가 향상된다. <br>
4. 보안 강화
    - 가상 메모리를 사용하면, 프로그램이 사용하는 메모리 영역을 분리하여 다른 프로그램의 메모리 영역에 접근하는 것을 방지할 수 있습니다. 이는 보안에 매우 중요하다.

## Context Swiching(문맥교환)이란 ?

문맥 교환은 **CPU가 여러 프로세스나 스레드를 동시에 처리할 수 있는 멀티 태스킹 환경에서, 현재 실행 중인 프로세스나 스레드의 상태를 저장하고 다음 실행할 프로세스나 스레드의 상태를 저장하고 다음 실행할 프로세스나 스레드의 상태를 불러오는 작업**을 말합니다. 

문맥 교환이 자주 일어나면, 프로세스나 스레드 간의 전환에 필요한 시간이 증가하여 전반적인 시스템 성능이 저하될 수 있습니다. 

## 뮤텍스와 세마포어란 무엇이고 이 둘의 차이점은 무엇인가요 ?

**뮤텍스와 세마포어는 상호배제를 위한 동기화 기법**입니다. 여기서 상호배제란 한 프로세스가 임계구역에 진입했다면 다른 프로세스는 임계 구역에 들어올 수 없다는 원칙입니다. 두 기법은 **목적과 동작 방식에서 차이가 있습니다.**

**뮤텍스 락**은 동시에 접근해서는 안되는 한 가지 자원에 동시에 접근하지 못하도록 만드는 도구입니다. 즉, 상호배제를 위한 동기화 도구입니다. 임계구역에 진입하는 순간,  임계구역을 자신이 사용중임을 알릴 수 있고, 누군가 임계구역을 사용중이라면 임계구역에 진입할 수 있는 순간까지 대기하다 진입할 수 있습니다.  하지만 이처럼 임계 구역에 진입하기 위해서 계속해서 계속해서  사용여부를 확인해야 합니다. 이러한 대기 방식을 바쁜대기(busy wait)라고 합니다.

**세마포**는 공유자원이 여러 개인 경우 사용하는 동기화 도구입니다. 바쁜대기 방식처럼 cpu의 주기를 낭비하지 않습니다. 
큐를 사용한다는 것이 차이점입니다. 만약 사용할 수 있는 자원이 없다면 자원을 사용하기 위해서 대기중인 프로세르의 pcb를 세마포를 위한 대기큐 에 집어 넣고, 기존의 자원을 사용하던 프로세스가 사용을 마치면 **대기큐**에 있던 프로세를 **준비큐** 로 옮기게 됩니다.(signal함수)

## 페이징이란 ?

**페이징이란 메모리와 프로세스를 일정한 단위로 자르고 이를 메모리에 불연속적으로 할당하는 방법**입니다.

일정한 단위로 자른 프로세스와 메모리는 각각 페이지와 프레임이 됩니다. 일정한 단위로 프로세를 불연속적으로 할당하기 때문에 외부 단편화 문제를 해결할 수 있으며 메모리에 적재될 필요가 없는 페이지들을 보조기억장치로 스왑아웃하여 실제 메모리 크기보다 더 큰 프로세스를 실행할 수 있게 됩니다. <br>
하지만 프로세스 크기가 페이지 단위의 배수가 아닐 경우 마지막 페이지에 내부 단편화가 발생하게 되는 단점이 있습니다.

## 세그먼테이션이란 ?

세그먼테이션(Segmentation)은 **가상 메모리(Virtual Memory)를 구현하는 기술 중 하나**로, **프로세스의 주소 공간을 논리적인 논리적 단위인 세그먼트(Segment) 단위로 분할하여 사용하는 것**을 말합니다. <br>

세그먼트는 **논리적인 단위**이므로 프로그램의 코드, 데이터, 스택 등과 같은 **여러 영역을 별도의 세그먼트로 분할하여 사용할 수 있습니다.** <br>
세그먼트들의 크기가 서로 다르기 때문에 프로세스가 메모리에 적재될 때 빈공간을 찾아 할당합니다. 프로세스가 필요한 메모리 공간 만큼 메모리를 할당해주기 때문에 내부 단편화는 발생하지 않지만, 중간에 메모리를 해제하면 외부 단편화 문제가 발생할 수 있습니다.

## 외부 단편화란 내부 단편화란 ?

**외부 단편화(External Fragmentation)** <br>
프로세스를 메모리에 연속적으로 배치하는 연속 메모리 할당 방식에 의해 메모리가 낭비되는 문제점입니다. 프로세스를 메모리에 연속적으로 할당하는 환경에서 프로세스들은 실행되고 종료됩니다. 그렇게 되면 연속된 메모리들 사이 사이에 빈 공간이 생기게 됩니다. 이렇게 생성된 빈 공간에는 프로세스를 적재하기 어려운 상황이 생겨납니다.   즉, 프로세스를 할당하기 어려울 만큼 작은 메모리 공간들로 인해 메모리가 낭비되는 현상입니다.
     
**내부 단편화(Internal Fragmentation)** <br>
메모리를 할당할 때 **프로세스가 필요한 양보다 더 큰 메모리가 할당되어서 프로세스에서 사용하는 메모리 공간이 낭비되는 상황**을 내부 단편화라고 합니다.

## 페이지 교체 알고리즘에 따른 페이지 폴트 방식에 대해 설명해보세요.

페이지 교체 알고리즘은 메모리 공간은 유한하기 때문에 메모리에 위치한 페이지를 보조기억장치로 필연적으로 옮겨야 합니다. 이때 어떤 페이지를 보조기억장치로 옮길지 결정하는 방법을 말합니다.  
좋은 페이지 교체 알고리즘은 페이지 폴트의 발생을 최소화하는 알고리즘입니다.

1. **FIFO 페이지 교체 알고리즘** <br>
    메모리에 가장 먼저 올라온 페이지부터 스왑아웃시키는 알고리즘입니다. 하지만 특정 페이지에 계속해서 프로세스에서 사용되어야 하는 내용이 포함된 페이지가 존재하는 경우에는 부적합한 알고리즘입니다.

2. **2차 기회 페이지 교체 알고리즘** <br>
    FIFO페이지의 문제를 어느정도 보완한 알고리즘으로, 메모리에 등록된 페이지를 쫓아낼때 한번의 기회를 더주는 방식입니다. 먼저 들어온 페이지를 쫓아내는 과정에서 참조비트를 확인합니다. 이떄 참조비트가 1인 경우, 0으로 만들고 쫓아내지 않고 메모리에 적재된 시간을 현재 시간으로 갱신합니다. 0인 경우 그대로 쫓아냅니다. 

3. **최적 페이지 교체 알고리즘** <br>
    cpu에 의해 참죄되는 횟수를 고려하는 페이지 교체 알고리즘입니다. 앞으로 사용 빈도 가장 낮은 페이지를 쫓아내는 방식입니다. 따라서 가장 낮은 페이지 폴트를 보장합니다. 하지만 앞으로 사용되지 않을 페이지를 예상한다는 점에서 어려움이 존재합니다. 이러한 특성 때문에 다른 페이지교체 알고리즘을 평가하기 위해 페이지 폴트의 하한선을 결정하기 위해사용됩니다.

4. **LRU 페이지 교체 알고리즘(Least Recently Used Page Replacement Algorithm)** <br>
    가장 오랫동안 사용되지 않은 페이지를 교체하는 알고리즘 입니다. 

## 운영체제의 운영 기법 중 동시에 프로그램을 수행할 수 있는 CPU를 두 개 이상 두고 각각 그 업무를 분담하여 처리할 수 있는 방식을 의미하는 것은 ?

**멀티프로세싱(multiprocessing)** <br>
멀티프로세싱은 **여러 개의 CPU를 사용하여 하나의 작업을 처리하는 방식**이다. 이는 여러 개의 프로세스를 동시에 실행하여 시스템의 성능을 향상시키고 작업을 더 빠르게 처리할 수 있다. 
멀티프로세싱은 대규모 컴퓨팅 시스템에서 많이 사용되며, 병렬 처리(parallel processing)에 적합한다. 또한 멀티프로세싱은 대규모 데이터베이스 시스템이나 서버 시스템에서도 사용된다.

## Critical Section(임계영역) 문제를 해결하기 위한 방법을 설명해보세요.

여러개의 프로세스나 스레드가 동시에 동유자원에 접근하면서 발생하는 문제를 해결하는 방법으로는 동기화가 필요합니다.

- **뮤텍스** <br>
뮤텍스는 상호 배제를 위한 동기화 메커니즘입니다. 즉, 뮤텍스를 이용하면 한 순간에 오직 한 개의 스레드만이 공유 자원을 사용할 수 있도록 보호할 수 있습니다. 뮤텍스는 lock과 unlock 두 개의 연산을 제공합니다. 하나의 스레드가 lock을 호출하면, 다른 스레드는 unlock이 호출될 때까지 대기해야 합니다.

- **세마포어** <br>
    세마포어는 뮤텍스와 유사한 역할을 수행하지만, 뮤텍스가 0 또는 1만 표현할 수 있는 상태를 가진 반면, 세마포어는 더 많은 상태를 가질 수 있습니다. 세마포어는 공유 자원에 대한 접근을 제한하기 위해 사용됩니다. 하나의 스레드가 세마포어를 획득하면, 다른 스레드는 해당 세마포어가 release 될 때까지 대기해야 합니다.
    
    세마포어는 counting semaphore와 binary semaphore로 나뉘는데, counting semaphore는 허용된 개수만큼 허용하고 binary semaphore는 뮤텍스와 같이 0 또는 1의 상태만을 가질 수 있습니다.
    
    뮤텍스와 세마포어는 모두 공유 자원의 동시 접근을 제한하는 데 사용되지만, 그 방법이 약간 다릅니다. 뮤텍스는 하나의 스레드/프로세스만이 임계 영역에 진입할 수 있도록 하는 반면, 세마포어는 지정된 수의 스레드/프로세만이 임계 영역에 진입할 수 있도록 하는 것입니다.
    
## 캐시의 지역성이란 무엇인가 ?

**캐시가 효율적으로 동작**하려면, 캐시의 **적중률을 극대화** 시켜야 한다. 캐시의 적중률을 극대화 시키기 위해서는 **캐시에 저장할 데이터가 지역성(Locality)을 가져야 한다.**

지역성이란, 데이터 접근이 시간적 혹은 공간적으로 가깝게 일어나는 것을 의미한다. 지역성의 전제조건으로 프로그램은 모든 코드나 데이터를 균등하게 Access 하지 않는다는 특성을 기본으로 한다.

즉, **Locality란 기억 장치 내의 정보를 균일하게 Access 하는 것이 아닌 어느 한 순간에 특정 부분을 집중적으로 참조하는 특성인 것이다.**

**시간적 지역성(temporal locality)** 과 **공간적 지역성(spatial locality)** 의 두 가지 형태로 나뉜다. 

시간적 지역성은 어떤 데이터나 명령어가 한 번 사용된 후, 그 데이터나 명령어가 잠시 후 다시 필요할 가능성이 높다는 것을 의미한다. 
예를 들어, 반복문에서 배열의 각 요소를 접근하는 경우, 반복문의 실행 중 같은 배열 요소에 여러 번 접근하게 된다. 
이러한 경우, 이전에 접근한 배열 요소의 데이터가 캐시에 남아있어 다시 접근할 때 캐시에서 빠르게 가져올 수 있으므로 성능이 향상된다.

공간적 지역성은 어떤 데이터나 명령어에 인접한 데이터나 명령어가 함께 사용될 가능성이 높다는 것을 의미한다.
예를 들어, 배열의 인접한 요소를 연속적으로 접근하는 경우, 캐시가 이러한 데이터를 미리 가져와 놓을 수 있으므로 데이터에 빠르게 접근할 수 있다. 

이러한 지역성을 이용하여 **캐시 메모리에 자주 사용되는 데이터나 명령어를 미리 저장**하고, **메모리에서 데이터를 가져오는 횟수를 줄여 성능을 향상**시킬 수 있다.

## 하드웨어 스레드와 소프트웨어 스레드에 대해 설명해보세요.

하드웨어 스레드는 하나의 물리적인 코어에 여러 개의 스레드를 동시에 실행시키는 기술입니다.

소프트웨어 스레드란 프로세스를 구성하는 실행의 흐름 단위입니다. 하나의 프로세스는 여러 개의 스레드를 가질 수 있으며 스레드를 이용하면 하나의 프로세스에서 여러 부분을 동시에 실행할 수 있습니다.

## ARM이란 무엇인가? ARM의 장점에 대해 설명해보세요.

ARM이란 Adavanced RISC Machined의 약자로 CPU의 한 종류입니다. 
**ARM의 코어는 RICS 방식을 사용합니다.**

**RICS**란 명령어 집합 구조(ISA, CPU가 이해할 수 있는 명령어들의 모음)의 한 종류 입니다. 명령어가 짧고 규격화되어 있으며 1클럭 내외로 명령어를 수행하기 때문에 파이프라이닝에 최적화 되어있습니다. 고정된 명령어이기 때문에 디코딩 속도가 빠릅니다.

## 연속 메모리 할당 알고리즘에 대해 설명해보세요. (3가지)

**연속 메모리 할당(Contiguous Memory Allocation) 알고리즘은 프로세스가 필요한 메모리를 연속적으로 할당받는 방법**입니다. 
이 방법은 메모리를 빠르게 할당하고 접근할 수 있으며, 주소의 연속성을 활용하여 CPU가 메모리를 더 효율적으로 사용할 수 있습니다.

대표적인 연속 메모리 할당 알고리즘으로는 **최초 적합(First Fit), 최적 적합(Best Fit), 최악 적합(Worst Fit)** 등이 있습니다.
각 알고리즘은 고유한 장단점이 있으며, 사용되는 메모리 크기와 시스템 환경에 따라 적합한 알고리즘이 다를 수 있습니다.
따라서, 특정 시스템에 맞게 알고리즘을 선택하고 조합하여 사용하는 것이 좋습니다.

- **최초 적합(First Fit)**<br>
    **가용한 메모리 중에서 가장 먼저 발견되는 충분한 크기의 블록을 사용하여 할당**합니다. 가용한 메모리 공간을 처음부터 순서대로 검색하기 때문에 할당 속도가 빠르지만, 작은 조각이 발생하여 외부 단편화가 발생할 가능성이 있습니다.
    
- **최적 적합(Best Fit)** <br>
    **가용한 메모리 중에서 가장 작은 크기의 블록을 찾아 할당**한다. 외부 단편화를 최소화하기 위한 알고리즘이지만, 가용한 메모리 공간을 모두 검색해야 하므로 할당 속도가 느릴 수 있습니다.
    
- **최악 적합(Worst Fit)** <br>
    **가용한 메모리 중에서 가장 큰 크기의 블록을 사용하여 할당**합니다. 외부 단편화를 발생시키지 않고, 큰 메모리 블록이 할당되어 작은 블록이 발생할 가능성이 낮아져서, 중간 과정에서 메모리를 재조정할 필요가 없어서 효율적입니다. 하지만 가용한 메모리를 모두 검색해야 하므로, 최적 적합보다 할당 속도가 더 느립니다.
    

## 연속메모리 할당의 단점에 대해 설명해보세요.

메모리 공간을 연속적으로 할당하는 방식이기 때문에 아래와 같은 문제가 발생합니다. 

**외부 단편화(External Fragmentation)** <br>
연속 메모리 할당에서는 프로세스에게 할당되는 메모리 공간이 일정한 크기를 가져야합니다. 그러나 프로세스들이 메모리에서 할당과 해제를 반복하다 보면, 메모리 공간 사이에 남는 작은 조각들이 발생할 수 있습니다. 이렇게 발생한 작은 조각들을 외부 단편화라고 하며, 남은 메모리를 유용하게 사용하지 못하게 합니다.

**내부 단편화(Internal Fragmentation)** <br>
프로세스에게 할당된 메모리 공간은 프로세스가 요구한 크기와 일정한 크기를 가져야합니다. 그러나 요구한 크기보다 조금 더 큰 크기로 할당되는 경우, 그 차이만큼이 낭비되는데 이를 내부 단편화라고 합니다.

**메모리 공간 낭비** <br>
연속 메모리 할당에서는 프로세스가 사용하는 메모리 공간만큼을 미리 할당해야 합니다. 그러나 실제로는 프로세스가 사용하지 않는 공간도 함께 할당되기 때문에, 메모리 공간이 낭비될 수 있습니다.

**할당/해제 비용 증가** <br>
연속 메모리 할당에서는 메모리 공간이 일정한 크기로 할당되어야 하므로, 프로세스의 크기가 계속 변할 경우에는 메모리를 재할당하거나 해제하는 작업이 필요합니다. 이 때, 프로세스의 크기에 따라 할당/해제 작업이 반복될 수 있으며, 이는 시스템의 성능 저하로 이어질 수 있습니다.

따라서, 연속 메모리 할당을 사용할 때에는 이러한 단점들을 고려하여 적절한 알고리즘을 선택하고, 메모리 관리를 철저히 해야 합니다.

## fork()와 vfork()의 차이점은 ?

**fork()와 vfork()는 모두 새로운 자식 프로세스를 생성하는 시스템 콜** 입니다. fork()와 vfork()는 **프로세스를 생성하는 방식에서 차이**가 있습니다.

**fork()** 는 부모 프로세스의 복사본을 만들어 완전히 분리된 프로세스를 생성하며 부모프로세스와는 독립적으로 동작합니다.

**vfork()** 는 부모 프로세스와 자식 프로세스가 동일한 메모리 공간을 공유하는 방식으로 프로세스를 생성합니다. fork()와 달리 vfork()는 같은 메모리 공간을 공유하므로 부모 프로세스는 자식 프로세스가 실행을 완료 할 때까지 일시 중단 상태를 유지해야합니다.

## 커널스레드, 유저 스레드, 하드웨어적 스레드의 차이점에 대해 설명해보세요.

**커널 스레드**는 운영체제 커널에서 생성되고 관리되는 스레드입니다. 커널 스레드는 CPU에서 직접 스케줄링되며 하드웨어와 관련된 작업을 수행합니다.

**유저 스레드**는 프로그램 레벨에서 생성되는 스레드 입니다. 유저 스레드가 CPU에서 실행되기 위해서는 반드시 커널 스레드와 연결되어야합니다.

**하드웨어적 스레드**는 하나의 물리적인 코어에 여러 개의 스레드를 동시에 실행시키는 기술입니다.