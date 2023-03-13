### 메모리와 캐시 메모리

> **1. RAM의 특징과 종류**
> 
> - RAM의 **특징**
>     - RAM에는 실행할 프로그램의 명령어와 데이터가 저장된다.
>     - 하지만 전원을 끄면 RAM에 저장된 명령어와 데이터가 모두 날아간다.
>     - **전원을 끄면 저장된 내용이 사라지는 저장 장치**를 **휘발성 저장 장치**라고 한다.
>     - 반대로 **전원을 꺼도 저장된 내용이 유지되는 저장 장치**를 **비휘발성 저장 장치**라고 한다.
>         - 하드 디스크나 SSD, CD-ROM, USB 메모리와 같은 **보조기억장치**가 대표적인 비휘발성 저장장치이다.
>         - 보조기억장치는 전원을 거도 내용을 유지하지만, **CPU는 보조기억장치에 직접적으로 접근할 수 없다.**
>     - 보조기억장치인 **비휘발성 저장 장치에는 ‘보관할 대상’을 저장**하고, **휘발성 저장 장치인 RAM에는 ‘실행할 대상’을 저장**한다.
> - RAM의 **용량과 성능**
>     - CPU가 실행하고 싶은 프로그램이 보조기억장치에 있다면 이를 RAM으로 가져와야 하는데, **RAM 용량이 적다면 보조기억장치에서 실행할 프로그램을 가져와야하는 일이 잦아 실행 시간이 길어지게 된다.**
>     - **RAM 용량이 크면 많은 프로그램을을 동시에 빠르게 실행하는데 유리하다.**
>     - RAM 용량이 커지면 프로그램 실행 속도가 어느정도 증가하는 것은 맞지만, **용량이 필요 이상으로 커졌을 때 속도가 그에 비례하여 증가하지는 않는다.**
> - RAM의 **종류**
>     - **DRAM** / Dynamic RAM
>         - **데이터가 동적으로 변하는 RAM**
>         - DRAM은 **시간이 지나면 저장된 데이터가 점차 사라진다.**
>         - 데이터의 소멸을 막기 위해 **일정 주기로 데이터를 재활성화** 해야 한다.
>         - 소비 전력이 비교적 낮고, 저렴하고, 집적도가 높기 때문에 대용량으로 설계하기 용이하다.
>     - **SRAM** / Static RAM
>         - **저장된 데이터가 변하지 않는 RAM**
>         - SRAM은 시간이 지나도 **저장된 데이터가 사라지지 않는다.**
>             - **SRAM이 비휘발성 메모리인 것은 아니다.** SRAM도 전원이 공급되지 않으면 저장된 내용이 날아간다.
>         - SRAM은 DRAM보다 일반적으로 **속도가 더 빠르다.**
>         - SRAM은 DRAM에 비해 집적도가 낮고, 소비 전력도 크며, 가격이 더 비싸기 때문에 일반적으로 DRAM을 더 많이 사용한다.
>         - **SRAM은 메모리가 아닌 ‘대용랴응로 만들어질 필요는 없지만 속도가 빨라야하는 저장장치’인 캐시 메모리에서 사용된다.**
>     - **SDRAM** / Synchronous Dynamic RAM
>         - SDRAM은 **클럭 신호와 동기화** 된 형태의 DRAM이다.
>         - **클럭 타이밍에 맞춰 CPU와 정보를 주고 받을 수 있다.**
>     - **DDR SDRAM** / Double Data Rate SDRAM
>         - 최근 가장 많이 사용되는 RAM으로 **대역 폭을 넓혀 속도를 빠르게 만든 SDRAM**이다.
>         - 대역폭이란 ‘데이터를 주고 받는 길의 너비’를 의미한다.
>         - DDR SDRAM은 너비가 두배인 도로와 같다.
>         - SDRAM과 비교했을 때 DDR SDRAM의 **전송 속도가 두배가량 빠르다.**
>         - **한 클럭당 하나씩 데이터를 주고 받을 수 있는 SDRAM**을 **SDR SDRAM**이라고 부른다.

> **2. 메모리의 주소 공간**
> 
> - CPU와 메모리에 저장되어 실행 중인 프로그램은 메모리 몇번지에 무엇이 저장되어 있는지 다 알지 못한다.
>     - 메모리에 저장된 정보는 시시각각 변하기 때문이다.
> - **CPU와 실행 중인 프로그램이 이해하는 주소**에는 메모리가 사용하는 **물리 주소**가 있고, CPU와 실행 중인 프로그램이 사용하는 **논리 주소**가 있다.
>     - **물리 주소**
>         - **메모리 하드웨어가 사용하는 주소**
>         - **정보가 실제로 저장된 하드웨어 상의 주소**이다.
>     - **논리 주소** 
>         - **CPU와 실행 중인 프로그램이 사용하는 주소**
>         - 실행 중인 프로그램 각각에게 부여된 **0번지부터 시작하는 주소**이다.
>             - 현재 메모리에 적재되어 있는 프로그램들은 다른 프로그램의 물리 주소가 무엇인지 알 필요 없다.
>             - 새로운 프로그램이 적재될 수 있고, 실행되지 않는 프로그램들은 메모리에서 언제든 사라질 수 있기 때문이다.
>             - 모두 물리주소가 아닌 0번지부터 시작하는 자신만을 위한 주소인 논리 주소를 가지고 있다.
>         - **CPU는 논리주소를 받아들이고, 해석하고, 연산한다.**
> - **CPU가 메모리와 상호작용**하려면 **논리 주소와 물리 주소간의 변환**이 이루어져야 한다.
> - **논리 주소와 물리 주소 사이의 변환**은 **CPU와 주소 버스 사이에 위치한 메모리 관리 장치**라는 하드웨어에 의해 수행된다.
> - **MMU**는 CPU가 발생시킨 **논리 주소에 베이스 레지스터 값을 더하여 논리 주소를 물리 주소로 변환**한다.
>     - **베이스 레지스터**
>         - 프로그램의 **가장 작은 물리 주소**
>         - 프로그램의 **첫 물리 주소를 저장**
>     - **논리주소**
>         - **프로그램의 시작점으로부터 떨어진 거리**
> - **메모리 보호 기법**
>     - **한계 레지스터**
>         - 다른 프로그램의 영역을 침범할 수 있는 명령어는 위험하기 때문에 **논리 주소 범위를 벗어나는 명령어 실행을 방지**하고, 실행 중인 프로그램이 **다른 프로그램에 영향을 받지 않도록 보호**할 방법이 필요하다.
>         - 한계 레지스터는 **주소의 최대 크기를 저장**한다.
>         - 프로그램의 물리 주소 범위는 **베이스 레지스터 값 이상, 베이스 레지스터 값 + 한계 레지스터 값 미만**이다.
>         - **CPU가 접근하려는 논리 주소는 한계 레지스터가 저장한 값보다 크면 안된다.**
>             - 한계 레지스터 보다 높은 주소 값에 접근하는 것은 곧 **프로그램의 범위에 벗어난 메모리 공간에 접근하는 것**이기 때문이다.
>         - 만약 CPU가 한계 레지스터보다 높은 논리 주소에 접근하려고 하면 **인터럽트를 발생시켜 실행을 중단한다.**
>         - 프로그램의 독립적인 실행 공간을 확보하고, 하나의 프로그램이 다른 프로그램을 침범하지 못하게 보호하기 위한 목적이다.

> **3. 캐시 메모리**
> 
> - **저장 장치 계층 구조** / Memory Hirearchy
>     - 컴퓨터가 사용하는 저장 장치들은 **‘CPU에 얼마나 가까운가’를 기준**으로 계층적으로 나타낼 수 있고 이를 저장 장치 계층 구조라고 한다.
> - **캐시 메모리**
>     - **CPU와 메모리 사이에 위치, 레지스터보다 용량이 크고 메모리보다 빠른 SRAM 기반의 저장 장치**이다.
>         - CPU가 메모리에 접근하는 시간은 CPU의 연산 속도보다 느리다. 그럼에도 CPU는 프로그램을 실행하는 과정에서 메모리에 빈번하게 접근해야한다.
>         - CPU의 연산 속도가 빨라도 **메모리에 접근하는 속도가 이를 따라가지 못하면 의미가 없으므로 캐시 메모리라는 저장 장치를 사용**하는 것이다.
>         - CPU의 연산 속도와 메모리 접근 속도의 차이를 줄이기 위해 사용한다.
>     - 메모리에서 **CPU가 사용할 일부 데이터를 미리 캐시 메모리로 가지고 와 활용**한다.
>     - **CPU와 가까운 순서로 계층을 구성**하는데 코어와 가장 가까운 캐시 메모리를 **L1 캐시,** 그 다음 가까운 캐시 메모리를 **L2 캐시, L3 캐시, …** 라고 부른다.
>         - 캐시 메모리의 용량은 L1 < L2 < L3 순으로 커진다.
>         - 캐시 메모리의 속도는 L3 < L2 < L1 순으로 빨라진다.
>         - 캐시 메모리의 가격은 L3 < L2 < L1 순으로 비싸진다.
>     - CPU가 메모리 내에 데이터가 필요하다고 판단하면 **우선 L1 캐시에 해당 데이터가 있는지 알아보고, 없다면 L2, L3 캐시 순으로 데이터를 검색**한다.
>     - **L1 캐시와 L2 캐시는 코어마다 고유한 캐시 메모리로 할당**되고, **L3 캐시는 여러 코어가 공유하는 형태**로 사용된다.
>         - **분리형 캐시**
>             - 코어와 가장 가까운 L1 캐시는 조금이라도 접근 속도를 빠르게 만들기 위해 **명령어만을 저장하는 L1 캐시인 L1I 캐시**와 **데이터만을 저장하는 L1 캐시인 L1D 캐시**로 분리하는 경우를 **분리형 캐시**라고 한다.
> - **참조 지역성 원리**
>     - 메모리가 보조기억장치의 일부를 복사하여 저장하는 것처럼 **캐시 메모리는 메모리의 일부를 저장하여 복사**한다.
>     - 캐시 메모리는 **CPU가 사용할 법한 대상을 예측하여 저장**한다.
>         1. **캐시 히트**
>             - 자주 사용될 것으로 **예측한 데이터가 실제로 들어맞아 캐시 메모리 내 데이터가 CPU에서 활용될 경우이다.**
>         2. **캐시 미스**
>             - **예측이 틀려** 메모리에서 필요한 데이터를 직접 가져와야 하는 경우이다.
>         3. **캐시 적중률**
>             - 캐시가 **히트되는 비율**
>     - 캐시 메모리는 **참조 지역성 원리에 따라** **메모리로부터 가져올 데이터를 결정**한다.
>         - 참조 지역성의 원리란 **CPU가 메모리에 접근할 때 주된 경향**을 바탕으로 만들어진 원리이다.
>             1. CPU는 **최근에 접근했던 메모리 공간에 다시 접근**하려는 경향이 있다. 
>                 - 변수에 값을 저장하면 언제든 변수에 다시 접근해 저장된 값을 사용할 수 있다.
>                 - ‘CPU는 변수가 저장된 메모리 공간을 언제든 다시 참조할 수 있다.’는 것을 의미한다.
>                 - 그리고 저장된 값은 한 번만 사용 되지 않고 프로그램이 실행되는 동안 여러번 사용된다.
>                 - ‘CPU는 최근 접근했던 메모리 공간을 여러번 다시 접근할 수 있다’는 의미이다.
>                 - 이처럼 최근에 접근했던 메모리 공간에 다시 접근하려는 경향을 **시간 지역성**이라고 한다.
>             2. CPU는 **접근한 메모리 공간 근처를 접근**하려는 경향이 있다. 
>                 - CPU가 특정 프로그램을 실행할 때는 해당 프로그램이 모여있는 공간 근처를 집중적으로 접근한다.
>                 - 접근할 메모리 공간 근처를 접근하려는 경향을 **공간 지역성**이라고 한다.
>         - 캐시 메모리는 이렇듯 참조 지역성의 원리에 입각해 **CPU가 사용할 법한 데이터를 예측**한다.