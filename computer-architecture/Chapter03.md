## 소스 코드와 명령어
- - -
### 고급언어와 저급언어
고급 언어로 작성된 코드가 실행되기 위해서는 반드시 저급언어로 변환돼야 합니다.
- 고급언어: 사람을 위한 언어로 대부분의 프로그래밍언어를 뜻합니다.
  - 컴파일 언어
    - `컴파일러`에 의해 소스 코드 전체가 저급언어로 변환되어 실행되는 고급언어입니다.
    - 소스코드 내에 오류를 하나라도 발견하면 컴파일은 실패합니다.
    - 컴파일을 통해서 저급언어로 변환되는 코드를 `목적코드`라고 합니다.
    - *컴파일러: 컴파일을 수행하는 도구 
  - 인터프리터 언어
    - `인터프리터`에 의해 소스코드가 한 줄씩 실행되는 고급언어 입니다.
    - 소스 코드 전체를 전급언어로 변환하는 시간을 기다릴 필요가 없습니다.
    - *인터프리터 :소스를 한 줄씩 저급언어로 바꿔주는 도구.
  - 속도 : 컴파일 언어 (가 더 빠름) > 인터프리터 언어
- 저급언어: 컴퓨터가 직접 이해하고 실행할 수 있는 언어로, 명령어로 이루어져 있습니다.  
    - 기계어: 0과 1의 명령어 비트로 이루어진 저급언어입니다.
    - 어셈블리어: 기계어는 오로지 컴퓨터만을 위해 만들어진 언어이므로, 사람이 보다 읽기 쉽게 만들어진 저급언어입니다.

## 명령어의 구조
- - -
### 연산코드와 오퍼랜드
명령어는 연산코드와 오퍼랜드로 구성되어 있습니다. 
- 연산코드(연산자): 명령어가 수행할 연산
- 오퍼랜드(=피연산자 =주소필드): 연산에 사용할 데이터 혹은 연산에 사용할 데이터가 저장된 위치

### 주소 지정 방식
주소 지정 방식은 `유효주소`를 찾는 방법입니다.  
*유효주소 : 데이터가 저장된 위치
- 즉시 주소 지정 방식: 오퍼랜드 필드에 데이터를 직접 명시하는 방법
  - 연산에 사용할 데이터를 메모리나, 레지트서로부터 찾이 않기 때문에 타 주소 지정방식 보다 빠름.
- 직접 주소 지정 방식: 오퍼랜드 필드에 `유효주소`를 직접 명시하는 방식
- 간접 주소 지정 방식: 오퍼랜드 필드에 `유효주소`의 `주소`를 명시하는 방식
- 레지스터 주소 지정 방식: 오퍼랜드 필드에 연산에 사용할 데이터를 저장한 `레지스터`를 직접 명시하는 방식
- 레지스터 간접 주소 지정 방식: 연산에 사용할 데이터를 메모리에 저장하고, 그 주소를 저장한 레지스터를 오퍼랜드 필으데 명시하는 방식
- 