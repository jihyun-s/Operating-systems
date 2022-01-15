# Operating Systems (쉽게 배우는 운영체제) 
* ## [Chapter3 프로세스와 스레드](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#chapter3-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%8A%A4%EB%A0%88%EB%93%9C-1)
  + ### [요약](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%9A%94%EC%95%BD-1)
  + ### [연습문제](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%97%B0%EC%8A%B5%EB%AC%B8%EC%A0%9C-1)
* ## [Chapter4 CPU 스케줄링](https://github.com/jihyun-s/Operating-systems#chapter4-cpu-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81-1)
  + ### [요약](https://github.com/jihyun-s/Operating-systems#%EC%9A%94%EC%95%BD-3)
  + ### [연습문제](https://github.com/jihyun-s/Operating-systems#%EC%97%B0%EC%8A%B5%EB%AC%B8%EC%A0%9C-3)
* ## [Chapter5 프로세스 동기화](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#chapter5-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EB%8F%99%EA%B8%B0%ED%99%94-1)
  + ### [요약](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%9A%94%EC%95%BD-6)
  + ### [연습문제](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%97%B0%EC%8A%B5%EB%AC%B8%EC%A0%9C-6)
* ## [Chapter6 교착 상태](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#chapter6-%EA%B5%90%EC%B0%A9-%EC%83%81%ED%83%9C-1)
  + ### [요약](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%9A%94%EC%95%BD-7)
  + ### [연습문제](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%97%B0%EC%8A%B5%EB%AC%B8%EC%A0%9C-7) 
* ## [Chapter7 물리 메모리 관리](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#chapter7-%EB%AC%BC%EB%A6%AC-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B4%80%EB%A6%AC-1)
  + ### [요약](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%9A%94%EC%95%BD-9)
  + ### [연습문제](https://github.com/jihyun-s/Operating-systems/blob/main/README.md#%EC%97%B0%EC%8A%B5%EB%AC%B8%EC%A0%9C-9)
+ ## [Chapter8 가상 메모리의 기초]()
  + ### [요약]()
  + ### [연습문제]()
+ ## [Chapter9 가상 메모리 관리]()
  + ### [요약]()
  + ### [연습문제]()

***
## Chapter3 프로세스와 스레드
### 요약 
1. 프로그램과 프로세스 
    - 프로그램은 저장장치에 저장되어 있는 정적인 상태이고, 프로세스는 실행을 위해 메모리에 올라온 동적인 상태이다.


2. 프로세스의 상태 
    - 생성 상태 : 프로그램을 메모리에 가져와 실행 준비가 완료된 상태이다. 
    - 준비 상태 : 실행을 기다리는 모든 프로세스가 자기 차례를 기다리는 상태이다. 실행될 프로세스를 CPU 스케줄러가 선택한다. 
    - 실행 상태 : 선택된 프로세스가 타임 슬라이스를 얻어 CPU를 사용하는 상태이다. 프로세스 사이의 문맥 교환이 일어난다. 
    - 대기 상태 : 실행 상태에 있는 프로세스가 입출력을 요청하면 입출력이 완료될 때까지 기다리는 상태이다. 입출력이 완료되면 준비 상태로 간다.
    - 완료 상태 : 프로세스가 종료된 상태이다. 사용하던 모든 데이터가 정리된다. 정상 종료인 exit와 비정상 종료인 abort를 포함한다. 


3. 프로세스 제어 블록
    - 프로세스를 실행하는 데 필요한 중요한 정보를 보관하는 자료 구조로, 모든 프로세스는 고유의 프로세스 제어 블록을 가진다. 프로세스 제어 블록은 프로세스 생성 시 만들어져서 프로세스가 실행을 완료하면 폐기된다. 


4. 문맥 교환 (context switching)
    - 두 프로세스의 제어 블록 및 이와 관련된 값들을 교환하는 작업을 말한다. 일반적으로 문맥 교환은 한 프로세스가 자신에게 주어진 시간을 다 사용하면 발생하고, 인터럽트가 걸렸을 때도 발생한다. 


5. 프로세스의 복사와 전환 
    - fork() 시스템 호출 : 실행 중인 프로세스로부터 새로운 프로세스를 복사하는 함수이다.
    - exec() 시스템 호출 : 기존의 프로세스를 새로운 프로세스로 전환하는 함수이다. 


6. 프로세스의 계층 구조 
    - 부모 프로세스를 복사하여 자식 프로세스를 만드는 방법으로 프로세스끼리 계층 구조를 갖는 것을 말한다. 부모 프로세스는 자신의 자원을 자식 프로세스에 상속하고 자식 프로세스가 종료되면 그 자원을 회수한다.  


7. 스레드 
    - CPU 스케줄러가 CPU에 전달하는 일 하나를 스레드라고 하며, 하나의 프로세스에는 여러 개의 스레드가 존재하기도 한다. 


8. 스레드 관련 용어 
    - 멀티스레드 : 멀티스레드는 프로세스 내 작업을 여러 개의 스레드로 분할함으로써 작업의 부담을 줄이는 프로세스 운영 기법이다.
    - 멀티태스킹 : 운영체제가 CPU에 작업을 줄 때 시간을 잘게 나누어 배분하는 기법이다.
    - 멀티프로세싱 : CPU를 여러 개 사용하여 여러 개의 스레드를 동시에 처리하는 작업 환경을 말한다. 
    - CPU 멀티스레드 : 한 번에 하나씩 처리해야 하는 스레드를 파이프라인 기법을 이용하여 동시에 여러 스레드를 처리하도록 만든 병렬 처리 기법이다. 


9. 멀티스레드의 장점
    - 응답성 향상 : 한 스레드가 입출력으로 인해 작업이 진행되지 않더라도 다른 스레드가 작업을 계속하여 사용자의 작업 요구에 빨리 응답할 수 있다. 
    - 자원 공유 : 한 프로세스 내에서 독립적인 스레드를 생성하면 프로세스가 가진 자원을 모든 스레드가 공유하게 되어 작업을 원활하게 진행할 수 있다. 
    - 효율성 향상 : 불필요한 자원의 중복을 막음으로써 시스템의 효율이 향상된다. 
    - 다중 CPU 지원 : 2개 이상의 CPU를 가진 컴퓨터에서 멀티스레드를 사용하면 다중 CPU가 멀티스레드를 동시에 처리하여 CPU 사용량이 증가하고 프로세스의 처리 시간이 단축된다. 


10. 멀티스레드 모델
    - 사용자 스레드(1 to N 모델) : 사용자 레벨에서 관련 라이브러리를 사용하여 구현하며, 라이브러리는 커널이 지원하는 스케줄링이나 동기화 같은 기능을 대신 구현해준다. 
    - 커널 스레드 (1 to 1 모델) : 커널이 멀티스레드를 지원하는 방식이다.
    - 멀티레벨 스레드 (M to N 모델) : 사용자 스레드와 커널 스레드를 혼합한 방식으로 하이브리드 스레드라고도 한다. 

### 연습문제 
1. 프로그램이 프로세스가 되려면 운영체제로부터 무엇을 받아야 하는가? 
    - 프로세스 제어 블록 (PCB) 


2. 프로세스의 상태 중 CPU를 할당받기 위해 기다리는 상태는 무엇인가? 
    - 준비 상태 (ready status)


3. 프로세스의 상태 중 입출력 작업을 하기 위해 이동하는 상태는 무엇인가? 
    - 대기 상태 (blocking status)


4. CPU 스케줄러가 준비 상태에 있는 프로세스 중 하나를 골라 CPU를 할당하는 작업을 무엇이라고 하는가? 
    - 디스패치 (dispatch)


5. 유닉스에서 Ctrl+Z 키를 눌러 프로세스가 중단되면 프로세스는 어떤 상태로 바뀌는가? 
    - 휴식 상태 (pause status)


6. 실행 상태에서 하나의 프로세스가 나가고 새로운 프로세스가 들어오는 상황을 무엇이라고 하는가? 
    - 문맥교환 (context switching) 


7. 실행 중인 프로세스로부터 새로운 프로세스를 복사하는 시스템 호출은 무엇인가? 
    - fork() 시스템 호출 (system call)


8. 프로세스의 골격은 그대로 둔 채 코드 영역만 바꾸는 시스템 호출은 무엇인가? 
    - exec() 시스템 호출 (system call)


9. 부모 프로세스가 기다리지 않아 자원이 회수되지 못하고 계속 살아 있는 프로세스는 무엇인가? 
    - 고아 프로세스 (orphan process) 


10. 프로세스의 코드에 정의된 절차에 따라 CPU에 작업 요청을 하는 실행 단위로서 가벼운 프로세스라고 불리는 것은 무엇인가? 
    - 스레드 (Thread) 


11. 고아 프로세스를 방지하기 위해 부모 프로세스는 어떤 시스템 호출을 사용하는가? 
    - wait() 시스템 호출 (system call)


12. 작업이 끝난 프로세스의 자원을 회수하는 행위를 무엇이라고 하는가? 
    - garbage collection 


13. 모든 프로세스를 부모-자식 관계로 만들어 자원 회수를 용이하게 하는 프로세스의 구조는 무엇인가? 
    - 프로세스의 계층 구조


### 심화문제 
1. 다섯 가지 프로세스 상태도를 그리시오 
    - <img src="https://github.com/jihyun-s/Operating-systems/blob/main/IMG_0125.JPG" width="50%" height="50%" title="프로세스 상태도" alt="Process status"></img>


2. 프로세스의 상태 중 휴식 상태와 보류 상태에 대해 설명하시오 
    - 휴식 상태 : 프로세스가 작업을 일시적으로 쉬고 있는 상태이다. 사용하던 데이터가 메모리에 그대로 있고 프로세스 제어 블록도 유지되므로 프로세스는 멈춘 지점에서부터 재시작할 수 있다. 
    - 보류 상태 : 프로세스가 메모리에서 잠시 쫓겨난 상태로 휴식 상태와 차이가 있다. 보류 상태는 '일시 정지 상태'라고도 불리며, 보류 상태와 비교하여 일반적인 프로세스 상태를 활성 상태라고 한다. 대부분이 컴퓨터의 성능을 떨어뜨리거나 실행을 미루어도 큰 지장이 없는 프로세스이다. 다음과 같은 경우에 보류 상태가 된다. 
        * 메모리가 꽉 차서 일부 프로세스를 메모리 밖으로 내보낼 때 
        * 프로그램에 오류가 있어서 실행을 미루어야 할 때 
        * 바이러스와 같이 악의적인 공격을 하는 프로세스라고 판단될 때
        * 매우 긴 주기로 반복되는 프로세스라 메모리 밖으로 쫓아내도 큰 문제가 없을 때 
        * 입출력을 기다리는 프로세스의 입출력이 계속 지연될 때 
    - 보류 상태에 들어간 프로세스는 메모리 밖으로 쫓겨나 Swap 영역에 보관된다. 보류 상태는 스왑 영역에 있는 상태이고 휴식 상태는 프로세스가 메모리에 있으나 멈춘 상태이다. 보류 상태는 대기 상태에서 옮겨진 보류 대기 상태와 준비 상태에서 옮겨진 보류 준비 상태로 구분되며, 각 상태에서 재시작하면 원래의 활성 상태로 들어간다. 또한 보류 대기 상태에서 입출력이 완료되면 활성 상태가 아닌 보류 준비 상태로 옮겨 간다.
    
    
3. 프로세스 제어 블록의 구성에 대해 설명하시오
    - <img src="https://github.com/jihyun-s/Operating-systems/blob/main/IMG_0127.JPG" width="65%" height="65%" title="프로세스 제어 블록" alt="PCB"></img>

4. 문맥 교환에 대해 설명하시오 
    - 두 프로세스의 제어 블록 및 이와 관련된 값들을 교환하는 작업을 말한다. 일반적으로 문맥 교환은 한 프로세스가 자신에게 주어진 시간을 다 사용하면 발생하고, 인터럽트가 걸렸을 때도 발생한다. 


5. 프로세스를 구성하는 코드 영역, 데이터 영역, 스택 영역에 대해 설명하시오 
    - 코드 영역 : 프로그램의 본문이 기술된 곳으로 텍스트 영역(text area)이라고도 한다. (읽기 전용을 처리됨)
    - 데이터 영역 : 코드가 실행되면서 사용하는 변수나 파일 등의 각종 데이터를 모아놓은 곳 (읽기&쓰기) 
    - 스택 영역 : 운영체제가 프로세스를 실행하기 위해 부수적으로 필요한 데이터를 모아놓은 곳 (ex. 함수 호출시 되돌아올 위치를 저장) 사용자에게 보이지 않는 영역이다. 


6. fork() 시스템 호출의 장점을 설명하시오
    - 프로세스의 생성 속도가 빠르다. :: 하드디스크로부터 프로그램을 새로 가져오지 않고 기존 메모리에서 복사하기 때문
    - 추가 작업 없이 자원을 상속할 수 있다. :: 부모 프로세서가 사용하던 모든 자원을 추가 작업 없이 자식 프로세스에 상속할 수 있다 
    - 시스템 관리를 효율적으로 할 수 있다. :: 부모-자식 프로세스가 연결되어 있기 때문에, 자식 프로세스를 종료하면 자식이 사용하던 자원을 부모 프로세스가 정리할 수 있다.

7. exec() 시스템 호출을 사용하는 이유를 설명하시오 
    - exec() 시스템 호출은 기존 프로세스를 새로운 프로세스로 전환하는 함수이다. 프로세스의 구조체를 재활용하기 위해 사용한다. 이미 만들어진 프로세스 제어 블록, 메모리 영역, 부모-자식 관계를 그대로 사용할 수 있어 편리하다. 각종 프로세스 구분자(PID, PPID, CPID)만 남겨두고 프로세스의 나머지 내용을 새로운 것으로 바꾼다. 데이터 영역이 새로운 데이터로 채워지고 스택 영역이 리셋된다. 


8. 프로세스 계층 구조의 장점을 설명하시오 
    - 여러 작업의 동시 처리 가능 (프로세스 복사와 전환을 통해 동시 처리가 가능)
    - 용이한 자원 회수 (자식 프로세스가 작업을 마쳤을 때 사용하던 자원을 부모 프로세스가 회수)


9. 멀티스레드, 멀티태스킹, 멀티프로세싱, CPU 멀티스레드를 비교하여 설명하시오 
    - 멀티스레드 : 멀티스레드는 프로세스 내 작업을 여러 개의 스레드로 분할함으로써 작업의 부담을 줄이는 프로세스 운영 기법이다.
    - 멀티태스킹 : 운영체제가 CPU에 작업을 줄 때 시간을 잘게 나누어 배분하는 기법이다.
    - 멀티프로세싱 : CPU를 여러 개 사용하여 여러 개의 스레드를 동시에 처리하는 작업 환경을 말한다. 
    - CPU 멀티스레드 : 한 번에 하나씩 처리해야 하는 스레드를 파이프라인 기법을 이용하여 동시에 여러 스레드를 처리하도록 만든 병렬 처리 기법이다. 


***
## Chapter4 CPU 스케줄링 
### 요약 
1. CPU 스케줄링
    - CPU 스케줄러는 프로세스가 생성돈 후 종료될 때까지 모든 상태 변화를 조정하는 일을 하며, CPU 스케줄링은 CPU 스케줄러가 하는 모든 작업을 가리킨다. 


2. 스케줄링의 단계 
    - 고수준 스케줄링 : 시스템 내의 전체 프로세스 수를 조절하는 것이다. 
    - 중간 수준 스케줄링 : 전체 시스템의 활성화된 프로세스 수를 조절하여 과부하를 마근 것이다. 
    - 저수준 스케줄링 : 어떤 프로세스에 CPU를 할당할지, 어떤 프로세스를 대기 상태로 보낼지 등을 결정하는 것이다. 


3. 스케줄링의 목적 
    - 공평성 : 모든 프로세스가 자원을 공평하게 배정받아야 하며, 자원 배정 과정에서 특정 프로세스가 배제되어서는 안 된다. 
    - 효율성 : 시스템 자원이 유휴 시간 없이 사용되도록 스케줄링을 하고, 유휴 자원을 사용하려는 프로세스에서는 우선권을 주어야 한다. 
    - 안정성 : 우선순위를 사용하여 중요 프로세스가 먼저 작동하도록 배정함으로써 시스템 자원을 점유하거나 파괴하려는 프로세스로부터 자원을 보호해야 한다. 
    - 확장성 : 프로세스가 증가해도 시스템이 안정적으로 작동하도록 조치해야 한다. 또한 시스템 자원이 늘어나는 경우 이 혜택이 시스템에 반영되게 해야 한다. 
    - 반응 시간 보장 : 응답이 없는 경우 사용자는 시스템이 멈춘 것으로 가정하기 때문에 시스템은 적절한 시간 안에 프로세스의 요구에 반응해야 한다. 
    - 무한 연기 방지 : 특정 프로세스의 작업이 무한히 연기되어서는 안 된다. 


4. 스케줄링 시 고려사항
    - 우선순위가 높은 프로세스에 CPU를 먼저 할당한다. 우선순위가 높은 프로세스는 커널 프로세스, 전면 프로세스, 대화형 프로세스, 입출력 집중 프로세스이고, 우선순위가 낮은 프로세스는 일반 프로세스, 후면 프로세스, 일괄 작업 프로세스, CPU 집중 프로세스이다. 


5. 다중 큐
    - 프로세스를 효율적으로 관리하기 위해 큐를 여러 개 두어 관리하는 것을 말한다. 준비 상태에서는 우선순위에 따라 다중 큐를 운영하고, 대기 상태에서는 같은 입출력을 요구한 프로세스들을 모아 다중 큐를 운영한다. 


6. 스케줄링 알고리즘 
    - FCFS 알고리즘 : 준비 큐에 도착한 순서대로 CPU를 할당하는 비선점형 스케줄링 방식이다.
    - SJF 스케줄링 : 준비 큐에 있는 프로세스 중에서 실행 시간이 가장 짧은 작업부터 CPU를 할당하는 비선점형 방식이다. 
    - HRN 스케줄링 : CPU를 할당받기 위해 기다린 시간과 CPU 사용 시간을 고려하여 스케줄링을 하는 비선점형 방식이다. 
    - 라운드 로빈 스케줄링 : 한 프로세스가 할당받은 시간(타임 슬라이스) 동안 작업을 하다가 작업을 완료하지 못하면 준비 큐의 맨 뒤로 가서 자기 차례를 기다리는 선점형 방식이다. 
    - SRT 스케줄링 : 기본적으로 라운드 로빈 스케줄링을 사용하지만, CPU를 할당받을 프로세스를 선택할 때 남아 있는 작업 시간이 가장 적은 프로세스를 선택하는 선점형 방식이다. 
    - 우선순위 스케줄링 : 프로세스는 중요도에 따라 우선순위를 갖는데 이러한 우선순위를 반영하여 CPU를 할당하는 방식이다. 선점형 혹은 비선점형 방식으로 구현이 가능하다. 
    - 다단계 큐 스케줄링 : 우선순위에 따라 준비 큐를 여러 개 사용하는 비선점형 방식이다. 프로세스는 운영체제로부터 부여받은 우선순위에 따라 해당 우선순위 큐에 삽입되어 실행된다.
    - 다단계 피드백 큐 스케줄링 : 다단계 큐 스케줄링과 기본적인 형태가 같지만, CPU를 사용하고 난 프로세스가 원래의 큐로 되돌아가지 않고 우선순위가 하나 낮은 큐의 끝으로 들어간다. 


### 연습문제 
1. 시스템 내 전체 프로세스의 수를 조절하는 것으로, 장기 스케줄링 또는 작업 스케줄링이라 불리는 스케줄링 수준은 무엇인가? 
    - 고수준 스케줄링


2. 어떤 프로세스에 CPU를 할당하고 어떤 프로세스를 대기 상태로 보낼지 등을 결정하는 스케줄링 수준은 무엇인가? 
    - 저수준 스케줄링 


3. 어떤 프로세스가 CPU를 할당받아 실행 중이더라도 운영체제가 CPU를 강제로 빼앗을 수 있는 스케줄링은 무엇인가? 
    - 선점형 스케줄링 


4. 현재 입출력을 진행하는 프로세스로, 사용자와 상호작용이 가능하여 상호작용 프로세스라고도 불리는 것은 무엇인가? 
    - 전면 프로세스


5. 준비 큐에 도착한 순서대로 CPU를 할당하는 비선점형 스케줄링 알고리즘은 무엇인가? 
    - FCFS 스케줄링


6. 준비 큐에 있는 프로세스 중 실행 시간이 가장 짧은 작업부터 CPU를 할당하는 비선점형 스케줄링 알고리즘은 무엇인가? 
    - SJF 스케줄링 


7. SJF 스케줄링 알고리즘의 단점으로 크기가 큰 작업이 계속 뒤로 밀리는 현상을 무엇이라 하는가? 
    - 아사 starvation 


8. 아사 현상을 해결하는 방법을 설명하시오. 
    - 에이징(aging)으로 완화할 수 있다. 에이징은 프로세스가 양보할 수 있는 상한선을 정하는 방식이다. 즉 프로세스가 자신의 순서를 양보할 때마다 나이를 한 살씩 먹어 최대 몇 살까지만 양보하도록 규정하는 것이다. 하지만 에이징 값을 어떤 기준으로 정할 것인지가 문제라 에이징에도 한계가 있다. 


9. 서비스를 받기 위해 대기한 시간과 CPU 사용 시간을 고려하여 우선순위를 정하는 스케줄링 알고리즘은 무엇인가? 
    - HRN 스케줄링


10. 프로세스가 할당받은 시간(타임 슬라이스) 동안 작업하다가 작업을 완료하지 못하면 준비 큐의 맨 뒤로 가서 다음 자기 차례가 올 때까지 기다리는 선점형 스케줄링 알고리즘 중 가장 단순한 것은 무엇인가? 
    - 라운드 로빈 스케줄링 


11. 타임 슬라이스의 크기와 문맥 교환의 관계를 설명하시오. 
    - 라운드 로빈 스케줄링이 효과적으로 작동하려면 문맥 교환에 따른 추가 시간을 고려하여 타임 슬라이스를 적절히 설정해야 한다. 타임 슬라이스의 크기는 프로세스의 반응 시간에 영향을 미칠 뿐 아니라 시스템 전체의 성능에도 영향을 미친다.
        * 타임 슬라이스가 큰 경우 : 하나의 작업이 끝난 뒤 다음 작업이 시작되는 것처럼 보인다. 이 경우 FCFS 스케줄링과 다를게 없는데, 실제로 라운드 로빈 스케줄링에서 타임 슬라이스가 무한대이면 FCFS 스케줄링이 된다. 
        * 타임 슬라이스가 작은 경우 : 사용자는 여러 프로그램이 동시에 실행되는 것처럼 느낄 것이다. 그러나 타임 슬라이스를 너무 작게 설정하면 시스템의 전반적인 성능이 떨어진다. 문맥 교환이 너무 자주 일어나 문맥 교환에 걸리는 시간이 실제 작업 시간보다 상대적으로 커지며, 문맥 교환에 많은 시간을 낭비하여 실제 작업을 못하는 문제가 발생한다. 


12. 기본적으로 라운드 로빈 방식을 사용하지만, CPU를 할당받을 프로세스를 선택할 때 남아있는 작업 시간이 가장 적은 것을 선택하는 스케줄링 알고리즘은 무엇인가?
    - SRT 스케줄링 


13. 우선순위에 따라 준비 큐를 여러 개 사용하며 고정형 우선순위를 적용하는 스케줄링 알고리즘은 무엇인가?
    - 다단계 큐 스케줄링


14. 우선순위에 따라 큐를 여러 개 사용하며, 프로세스가 CPU를 사용한 후 우선순위가 낮아지는 특징을 가진 스케줄링 알고리즘은 무엇인가? 
    - 다단계 피드백 큐 스케줄링


15. 다단계 피드백 큐 스케줄링에서 마지막 큐에 있는 프로세스(우선순위가 가장 낮은 프로세스)의 타임 슬라이스 크기는 얼마인가? 
    - 무한대의 타임 슬라이스 (프로세스가 실행 상태에 들어가면 CPU를 빼앗기지 않고 끝까지 작업을 마친다.) 


16. 다단계 피드백 큐 스케줄링에서 우선순위게 낮아질수록 타임 슬라이스의 크기는 어떻게 변하는가?
    - 우선순위가 낮은 큐의 타임 슬라이스를 크게 설정한다. 


17. 다단계 피드백 큐 스케줄링에서 마지막 큐(우선순위가 가장 낮은 큐)는 어떤 스케줄링 알고리즘처럼 동작하는가? 
    - FCFS 스케줄링 


### 심화문제 
1. **스케줄링의 단계와 그 특징을 설명하시오.**
    - <img src="https://github.com/jihyun-s/Operating-systems/blob/main/IMG_0129.JPG" width="44%" height="44%" title="스케줄링 단계"></img>
    - 고수준 스케줄링 : 시스템 내의 전체 프로세스 수를 조절하는 것이다. 
    - 중간 수준 스케줄링 : 전체 시스템의 활성화된 프로세스 수를 조절하여 과부하를 마근 것이다. 
    - 저수준 스케줄링 : 어떤 프로세스에 CPU를 할당할지, 어떤 프로세스를 대기 상태로 보낼지 등을 결정하는 것이다. 

2. **스케줄링의 목적을 설명하시오.**
    - 공평성 : 모든 프로세스가 자원을 공평하게 배정받아야 하며, 자원 배정 과정에서 특정 프로세스가 배제되어서는 안 된다. 
    - 효율성 : 시스템 자원이 유휴 시간 없이 사용되도록 스케줄링을 하고, 유휴 자원을 사용하려는 프로세스에서는 우선권을 주어야 한다. 
    - 안정성 : 우선순위를 사용하여 중요 프로세스가 먼저 작동하도록 배정함으로써 시스템 자원을 점유하거나 파괴하려는 프로세스로부터 자원을 보호해야 한다. 
    - 확장성 : 프로세스가 증가해도 시스템이 안정적으로 작동하도록 조치해야 한다. 또한 시스템 자원이 늘어나는 경우 이 혜택이 시스템에 반영되게 해야 한다. 
    - 반응 시간 보장 : 응답이 없는 경우 사용자는 시스템이 멈춘 것으로 가정하기 때문에 시스템은 적절한 시간 안에 프로세스의 요구에 반응해야 한다. 
    - 무한 연기 방지 : 특정 프로세스의 작업이 무한히 연기되어서는 안 된다. 


3. **선점형 스케줄링과 비선점형 스케줄링을 비교하여 설명하시오.**
  
  
구분 | 선점형 | 비선점형
--|--|--
작업 방식 | 실행 상태에 있는 작업을 중단시키고 새로운 작업을 실행할 수 있다. | 실행 상태에 있는 작업이 완료될 때까지 다른 작업이 불가능하다.
장점 | 프로세스가 CPU를 독점할 수 없어 대화형이나 시분할 시스템에 적합하다. | CPU 스케줄러의 작업량이 적고 문맥 교환의 오버헤드가 적다.
단점 | 문맥 교환의 오버헤드가 많다. | 기다리는 프로세스가 많아 처리율이 떨어진다.
사용 | 시분할 방식 스케줄러에 사용된다. | 일괄 작업 방식 스케줄러에 사용된다.
중요도 | 높다. | 낮다.



4. **스케줄링 알고리즘의 선택 기준에 대해 설명하시오.**    
    - CPU 사용률 : 전체 시스템의 동작 시간 중 CPU가 사용된 시간을 측정하는 방법이다. 가장 이상적인 수치는 100%이지만 실제로는 90%에도 못 미친다.
    - 처리량 : 단위 시간당 작업을 마친 프로세스의 수로, 이 수치가 클수록 좋은 알고리즘이다.
    - 대기 시간 : 작업을 요청한 프로세스가 작업을 시작하기 전까지 대기하는 시간으로, 이 시간이 짧을수록 좋다.
    - 응답 시간 : 프로세스 시작 후 첫 번째 출력 또는 반응이 나올 때까지 걸리는 시간으로, 이 시간 역시 짧을수록 좋다.
    - 반환 시간 : 프로세스가 생성된 후 종료되어 사용하던 자원을 모두 반환하는 데까지 걸리는 시간이다. 반환 시간은 대기 시간과 실행 시간을 더한 값이다.


5.  **FCFS, SJF, HRN 스케줄링의 특징을 설명하시오.**   
    - FCFS 알고리즘 : 준비 큐에 도착한 순서대로 CPU를 할당하는 비선점형 스케줄링 방식이다.
    - SJF 스케줄링 : 준비 큐에 있는 프로세스 중에서 실행 시간이 가장 짧은 작업부터 CPU를 할당하는 비선점형 방식이다. 
    - HRN 스케줄링 : CPU를 할당받기 위해 기다린 시간과 CPU 사용 시간을 고려하여 스케줄링을 하는 비선점형 방식이다. 


6. **라운드 로빈, SRT, 다단계 큐, 다단계 피드백 큐 스케줄링의 특징을 설명하시오.**
    - 라운드 로빈 스케줄링 : 한 프로세스가 할당받은 시간(타임 슬라이스) 동안 작업을 하다가 작업을 완료하지 못하면 준비 큐의 맨 뒤로 가서 자기 차례를 기다리는 선점형 방식이다. 
    - SRT 스케줄링 : 기본적으로 라운드 로빈 스케줄링을 사용하지만, CPU를 할당받을 프로세스를 선택할 때 남아 있는 작업 시간이 가장 적은 프로세스를 선택하는 선점형 방식이다. 
    - 우선순위 스케줄링 : 프로세스는 중요도에 따라 우선순위를 갖는데 이러한 우선순위를 반영하여 CPU를 할당하는 방식이다. 선점형 혹은 비선점형 방식으로 구현이 가능하다. 
    - 다단계 큐 스케줄링 : 우선순위에 따라 준비 큐를 여러 개 사용하는 비선점형 방식이다. 프로세스는 운영체제로부터 부여받은 우선순위에 따라 해당 우선순위 큐에 삽입되어 실행된다.
    - 다단계 피드백 큐 스케줄링 : 다단계 큐 스케줄링과 기본적인 형태가 같지만, CPU를 사용하고 난 프로세스가 원래의 큐로 되돌아가지 않고 우선순위가 하나 낮은 큐의 끝으로 들어간다. 


7. **아사 현상과 에이징에 대해 설명하시오.**
    - 작업이 계속해서 연기되는 것이 아사(starvation)이며 (-> cpu 할당을 받지 못함) 이를 완화하기 위해 에이징(aging)을 사용한다. 에이징은 프로세스가 양보할 수 있는 상한선을 정하는 것이다. 프로세스가 자신의 순서를 양보할 때마다 나이를 한 살씩 먹어 최대 몇 살까지만 양보하도록 규정하는 것이다. 하지만 에이징 값을 어떤 기준으로 정할 것인지가 문제라 에이징에도 한계가 있다.


8. **타임 슬라이스의 크기를 정하는 것과 시스템 효율성에 대해 설명하시오.**
    - 타임 슬라이스를 너무 작게 설정하면 시스템의 전반적인 성능이 떨어진다. 문맥 교환이 너무 자주 일어나 문맥 교환에 걸리는 시간이 실제 작업 시간보다 상대적으로 커지며, 문맥 교환에 많은 시간을 낭비하여 실제 작업을 못하는 문제가 발생한다. 
    - 타임 슬라이스가 너무 크면 하나의 작업이 끝난 뒤 다음 작업이 시작되는 것처럼 보인다. 
    - 문맥 교환에 따른 추가 시간을 고려하여 타임 슬라이스를 적절히 설정해야 한다. 타임 슬라이스의 크기는 프로세스의 반응 시간에 영향을 미칠 뿐 아니라 시스템 전체의 성능에도 영향을 미친다. 따라서 타임 슬라이스는 되도록 작게 설정하되 문맥 교환에 걸리는 시간을 고려하여 적당한 크기로 하는 것이 중요하다. (유닉스 운영체제에서는 10~200밀리초 사이에서 조정)


***
## Chapter5 프로세스 동기화 
### 요약 
1. 프로세스 간 통신의 개념 
    - 프로세스가 다른 프로세스와 데이터를 주고받는 것을 말하며 프로세스 내부 데이터 통신, 프로세스 간 데이터 통신, 네트워크를 이용한 데이터 통신이 있다.

2. 프로세스 간 통신의 분류 

종류 | 예
--|--
양방향 통신 | 일반적 통신, 소켓 
반양방향 통신 | 무전기
단방향 통신 | 전역 변수, 파일, 파이프
대기가 있는 통신(동기화 통신) | 파이프, 소켓 
대기가 없는 통신(비동기화 통신) | 전역 변수, 파일 

3. 프로세스 간 통신의 종류 
    - 전역 변수를 이용한 통신 : 공동으로 관리하는 메모리를 사용하여 데이터를 주고받는 것이다.
    - 파일을 이용한 통신 : 저장장치에 파일을 읽고 쓰는 방법으로 데이터를 주고받는 것이다. 
    - 파이프를 이용한 통신 : 운영체제가 제공하는 동기화 통신 방식으로, 파이프에 쓰기 연산을 하면 데이터가 전송되고 읽기 연산을 하면 데이터를 받는다. 
    - 소켓을 이용한 통신 : 여러 컴퓨터에 있는 프로세스와 프로세스를 소켓으로 연결하면 데이터를 주고받는 것이다. 소켓에 쓰기 연산을 하면 데이터가 전송되고 읽기 연산을 하면 데이터를 받는다. 


4. 공유 자원
    - 여러 프로세스가 공동으로 이용하는 변수, 메모리, 파일 등을 말한다. 공유 자원은 공동으로 이용되기 때문에 누가 언제 데이터를 읽거나 쓰느냐에 따라 그 결과가 달라질 수 있다. 


5. 임계구역
    - 공유 자원 접근 순서에 따라 실행 결과가 달라지는 프로그램의 영역을 말한다.


6. 임계구역 해결 조건 
    - 상호 배제 : 한 프로세스가 임계구역에 들어가면 다른 프로세스는 임계구역에 들어갈 수 없다. 
    - 한정 대기 : 어떤 프로세스도 무한 대기하지 않아야 한다.
    - 진행의 융통성 : 한 프로세스가 다른 프로세스의 진행을 방해해서는 안 된다. 


7. 임계구역 해결 방법
    - 피터슨 알고리즘, 데커 알고리즘 : 임계구역 해결 조건을 모두 만족하는 소프트웨어적인 해결 방법이다. 
    - 세마포어 : 임계구역에 진입하기 전에 스위치를 사용 중으로 놓고 임계구역으로 들어가는 방법으로, 피터슨 알고리즘이나 데커 알고리즘보다 간단하고 사용하기 쉽다. 
    - 모니터 : 세마포어 알고리즘을 자동으로 처리하도록 설계한 코드이다. 보호할 자원을 임계구역으로 숨기고 임계구역에서 작업할 수 있는 인터페이스만 제공하여 자원을 보호한다. 



### 연습문제 
1. 프로세스 간 통신에서 데이터를 양방향으로 전송 가능하지만 동시 전송은 불가능하고 특정 시점에 한쪽 방향으로만 전송할 수 있는 통신 방식은 무엇인가?
    - 반양방향 통신

2. 상태 변화를 살펴보기 위해 반복문을 무한 실행하며 기다리는 것을 무엇이라 하는가?
    - 바쁜 대기 (busy waiting) 

3. 프로세스 간 통신에서 대기가 없는 통신과 대기가 있는 통신의 예를 각각 제시하시오. 
    - 대기가 있는 통신 : 동기화를 지원하는 통신 방식. 데이터를 받는 쪽은 데이터가 도착할 때까지 자동으로 대기 상태에 머물러 있다. (파이프, 소켓) 
    - 대기가 없는 통신 : 동기화를 지원하지 않는 통신 방식. 데이터를 받는 쪽은 바쁜 대기를 사용하여 데이터가 도착했는지 여부를 직접 확인한다. (전역 변수, 파일) 

4. 파이프를 이용하여 통신할 때 파이프를 2개 사용하는 이유는 무엇인가? 
    - 기본적으로 단방향 통신이며, 양방향 통신을 하려면 파이프 2개를 사용해야 한다. 

5. 공유 자원을 병행적으로 읽거나 쓰는 상황을 무엇이라 하는가? 
    - 경쟁 조건 (race condition) 

6. 공유 자원의 접근 순서에 따라 실행 결과가 달라지는 프로그램의 영역은 무엇인가?
    - 임계구역 (critical section) 

7. 임계구역 해결 조건 중 한 프로세스가 임계구역에 들어갔을 때 다른 프로세스는 임계구역에 들어갈 수 없는 조건을 무엇이라 하는가? 
    - 상호 배제 (mutual exclusion) 

8. 임계구역 해결 조건 중 한 프로세스가 다른 프로세스의 진행을 방해해서는 안 된다는 조건을 무엇이라 하는가? 
    - 진행의 융통성 (bounded waiting) 

9. 임계구역 문제를 하드웨어적으로 해결한 방식으로, 하드웨어의 지원을 받아 명령어를 실행하는 도중에 타임아웃이 걸리지 않도록 하는 방식을 무엇이라 하는가? 
    - 검사와 지정(test-and-set) 코드 사용 
    - 편하긴 하지만 바쁜 대기를 사용하여 검사하기 때문에 자원 낭비가 있다. 

10. 세마포어의 Semaphore(n)에서 n은 무엇을 가리키는가?
    - 공유 가능한 자원의 수 

11. 세마포어에서 내부 변수를 RS라고 할 때 세마포어 P()의 내부 코드를 쓰시오. 
```
if RS > 0 then RS = RS-1; 
else block();          // uutil RS > 0 
```

12. 세마포어에서 내부 변수를 RS라고 할 때 세마포어 V()의 내부 코드를 쓰시오. 
```
RS = RS + 1;
wake_up();
```

13. 세마포어가 제대로 작동하지 않는 경우를 설명하시오. 
    - 프로세스가 세마포어를 사용하지 않고 바로 임계구역에 들어간 경우로 임계구역을 보호할 수 없다. 
    - P()를 두 번 사용하여 wake_up 신호가 발생하지 않은 경우이다. 프로세스 간의 동기화가 이루어지지 않아 세마포어 큐에서 대기하고 있는 프로세스들이 무한 대기에 빠진다.
    - P()와 V()를 반대로 사용하여 상호 배제가 보장되지 않은 경우로 임계구역을 보호할 수 없다.


14. 세마포어의 내부 코드도 타임아웃이 걸리면 문제가 발생할 수도 있다. 그래서 내부 코드는 무엇으로 보호받는가? 
    - 세마포어의 P()나 V()의 내부 코드가 실행되는 도중에 다른 코드가 실행되면 상호 배제와 한정 대기 조건을 보장하지 못한다. 그러므로 P()와 V()의 내부 코드는 검사와 지정을 사용하여 분리 실행되지 않고 완전히 실행되게 해야 한다. 


15. 공유 자원을 내부적으로 숨기고 공유 자원에 접근하기 위한 인터페이스만 제공함으로써 자원을 보호하고 프로세스 간에 동기화를 시키는 것으로, 세마포어의 단점을 해결하면서 임계구역 문제를 해결한 방식은 무엇인가?
    - 모니터 (monitor)


### 심화문제 
1. 프로세스 간 통신을 통신 방향에 따라 분류하여 설명하시오. 

종류 | 예
--|--
양방향 통신 | 일반적 통신, 소켓 
반양방향 통신 | 무전기
단방향 통신 | 전역 변수, 파일, 파이프


2. 대기가 있는 통신과 대기가 없는 통신의 의미를 설명하고 적절한 예를 제시하시오. 
    - 대기가 있는 통신 : 동기화를 지원하는 통신 방식. 데이터를 받는 쪽은 데이터가 도착할 때까지 자동으로 대기 상태에 머물러 있다. (파이프, 소켓) 
    - 대기가 없는 통신 : 동기화를 지원하지 않는 통신 방식. 데이터를 받는 쪽은 바쁜 대기를 사용하여 데이터가 도착했는지 여부를 직접 확인한다. (전역 변수, 파일) 


3. 실생활의 예를 들어 임계구역 문제를 설명하시오. 
    - 믹서는 공유가 불가능한 자원으로서 주방의 임계구역이다. 믹서를 사용할 때는 순서를 지켜야 한다. 


4. 다음 코드의 문제점을 설명하시오. (상호 배제 문제)
    - 프로세스 P1은 while(lock==true); 문을 실행한다. 임계구역에 프로세스가 없기 때문에 무한 루프를 빠져나온다. 이어서 다음 문장을 실행하려는 순간 자신에게 주어진 CPU 시간을 다 써서(타임아웃) 준비 상태로 옮겨진다. 문맥 교환이 발생하고 프로세스 P2가 실행 상태로 바뀐다. 
    - 프로세스 P2는 while(lock==true); 문을 실행한다. 아직 프로세스 P1이 잠금을 걸지 않았기 때문에 lock은 여전히 false이며 프로세스 P2는 임계구역에 진입할 수 있다. 
    - 프로세스 P1은 lock=true; 문을 실행하여 임계구역에 잠금을 걸고 진입한다. 
    - 프로세스 P2도 lock=true; 문을 실행하여 임계구역에 잠금을 걸고 진입한다. 결국 둘 다 임계구역에 진입하게 된다.
    - 또 다른 문제는 잠금이 풀리기를 기다리려면 빠쁜 대기를 한다는 것이다. 작업을 할 필요가 없는 시간에도 계속 무한 루프를 돌면서 시스템 자원을 낭비하게 된다. 


5. 다음 코드의 문제점을 설명하시오. (진행의 융통성 문제)
    - 한 프로세스가 두 번 연달아 임계구역에 진입하고 싶어도 그럴 수 없다. 프로세스의 우선순위에 상관없이 번갈아가며 임계구역에 진입한다. 
    - 프로세스 P1은 프로세스 P2가 임계구역에 진입했다가 나온 다음에야 다시 진입할 수 있으므로 프로세스 P2가 프로세스 P1의 진행을 방해하는 구조이다.
    - 프로세스의 진행이 다른 프로세스로 인해 방해받는 현상을 경직된 동기화(lockstep synchronization)라고 한다. 


6. 파일을 이용하여 Test라는 문자를 주고받는 코드를 작성하시오. 
```
#include <stdioh.h>
#include <unistd.h>
#include <fcnt1.h>

void main()
{
    int pid, fd; 
    char buf[5];
    
    fd = open("com.txt", 0_RDWR);     // Init
    pid = fork();
    
    if(pid < 0 || fd < 0) exit(-1); 
    
    else if(pid == 0) {               // Child
        write(fd, "Test", 5); 
        close(fd); 
        exit(0);    }
    
    else { wait(0) ;                  // Parent
        lseek(fd, 0, SEEK_SET); 
        read(fd, buf, 5); 
        prinft("%s", buf); 
        close(fd); 
        exit(0);    }
}
```

***
## Chapter6 교착 상태
### 요약
1. 교착 상태
    - 2개 이상의 프로세스가 다른 프로세스의 작업이 끝나기만 기다리며 작업을 더 이상 진행하지 못하는 상태를 말한다. 컴퓨터 시스템에서 교착 상태는 시스템 자원, 공유 변수(또는 파일), 응용 프로그램 등을 사용할 때 발생할 수 있다. 


2. 자원 할당 그래프 
    - 프로세스가 어떤 자원을 사용 중이고 어떤 자원을 기다리고 있는지를 방향성이 있는 그래프로 표현한 것이다. 자원 할당 그래프를 사용하면 자원의 할당과 대기 상태를 한눈에 파악할 수 있다. 


3. 교착 상태 필요조건 
    - 상호 배제 : 한 프로세스가 사용하는 자원은 다른 프로세스와 공유할 수 없는 배타적인 자원이어야 한다. 
    - 비선점 : 한 프로세스가 사용 중인 자원은 다른 프로세스가 빼앗을 수 없는 비선점 자원이어야 한다. 
    - 점유와 대기 : 프로세스가 어떤 자원을 할당받은 상태에서 다른 자원을 기다리는 상태여야 한다.
    - 원형 대기 : 점유와 대기를 하는 프로세스 간에 관계가 원을 이루어야 한다.


4. 식사하는 철학자 문제 
    - 철학자 4명이 둥그런 식탁에 둘러앉아 식사를 하는데, 왼쪽에 있는 포크를 잡은 뒤 오른쪽에 있는 포크를 잡아야만 식사가 가능하다는 조건이 있는 문제이다. 식사하는 철학자 문제는 교착 상태를 설명하기 위한 예로 오랫동안 사용되었다. 


5. 교착 상태 해결 방법
    - 교착 상태 예방 : 교착 상태를 유발하는 네 가지 조건이 발생하지 않도록 무력화하는 방식이다. 
    - 교착 상태 회피 : 자원 할당량을 조절하여 교착 상태를 해결하는 방식이다. 즉 자원을 할당하다가 교착 상태를 유발할 가능성이 있다고 판단되면 자원 할당을 중단하고 지켜본다. 
    - 교착 상태 검출과 회복 : 자원 할당 그래프를 모니터링하면서 교착 상태가 발생하는지 살펴보는 방식이다. 만약 교착 상태가 발생하면 교착 상태 회복 단계가 진행된다. 


6. 은행원 알고리즘
    - 교착 상태 회피를 구현하는 방법으로, 자원의 총수와 현재 할당된 자원의 수를 기준으로 시스템을 안정 상태와 불안정 상태로 나누고 시스템이 안정 상태를 유지하도록 자원을 할당한다. 


### 연습문제
1. 2개 이상의 프로세스가 서로의 작업이 끝나기만 기다리며 작업을 더 이상 진행하지 못하는 상태를 무엇이라 하는가?
    - 교착 상태 (dead lock)


2. 프로세스가 어떤 자원을 사용 중이고 어떤 자원을 기다리고 있는지를 나타내는 방향성이 있는 그래프를 무엇이라 하는가? 
    - 자원 할당 그래프 (resource allocation graph)

3. 네 가지 교착 상태 필요조건에 대해 설명하시오. 
    - 상호 배제 : 한 프로세스가 사용하는 자원은 다른 프로세스와 공유할 수 없는 배타적인 자원이어야 한다. 
    - 비선점 : 한 프로세스가 사용 중인 자원은 다른 프로세스가 빼앗을 수 없는 비선점 자원이어야 한다. 
    - 점유와 대기 : 프로세스가 어떤 자원을 할당받은 상태에서 다른 자원을 기다리는 상태여야 한다.
    - 원형 대기 : 점유와 대기를 하는 프로세스 간에 관계가 원을 이루어야 한다.

4. 교착 상태 해결 방법 중, 교착 상태를 유발하는 네 가지 조건을 무력화하는 방법은 무엇인가? 
    - 교착 상태 예방 : 교착 상태를 유발하는 네 가지 조건이 발생하지 않도록 무력화하는 방식이다.

5. 교착 상태 해결 방법 중, 교착 상태가 발생하지 않는 수준으로 자원을 할당하는 방법은 무엇인가? 
    - 교착 상태 회피 : 자원 할당량을 조절하여 교착 상태를 해결하는 방식이다. 즉 자원을 할당하다가 교착 상태를 유발할 가능성이 있다고 판단되면 자원 할당을 중단하고 지켜본다. 

6. 교착 상태 해결 방법 중, 자원 할당 그래프를 사용하여 교착 상태를 발견하는 방법은 무엇인가?
    - 교착 상태 검출과 회복 : 자원 할당 그래프를 모니터링하면서 교착 상태가 발생하는지 살펴보는 방식이다. 만약 교착 상태가 발생하면 교착 상태 회복 단계가 진행된다.

7. 교착 상태 해결 방법 중, 타임아웃을 이용하여 해결하는 방법은 무엇인가?
    - 교착 상태 검출 

8. 교착 상태 해결 방법 중, 은행원 알고리즘을 사용하여 해결하는 방법은 무엇인가?
    - 교착 상태 회피 

9. 교착 상태 해결 방법 중, 모든 자원에 번호를 부여하고 낮은 번호의 자원을 사용할 수 없도록 하는 방법은 무엇인가? 
    - 원형 대기 예방 


10. 교착 상태 해결 방법 중, 프로세스가 시작 초기에 자신이 사용하려는 모든 자원을 한꺼번에 점유하거나, 그렇지 못할 경우 자원을 모두 반납하는 방법은 무엇인가? 
    - 점유와 대기 예방 : 전부 할당하거나 아니면 아예 할당하지 않는 방식을 적용 all or nothing 


11. 교착 상태 해결 방법 중, 교착 상태가 검출되면 교착 상태를 일으킨 모든 프로세스를 종료하는 방법은 무엇인가? 
    - 교착 상태 회복 

12. 자원 할당 그래프에서 무엇이 발견되면 교착 상태라고 판단할 수 있는가? 
    - 사이클


### 심화문제 
1. 교착 상태 해결 방법 중 프로세스가 시작 초기에 자신이 사용하려는 모든 자원을 한꺼번에 점유하거나, 그렇지 못할 경우 자원을 모두 반납하는 방법이 있다. 이 방법의 단점을 설명하시오.
    - 프로세스가 자신이 사용하는 모든 자원을 자세히 알기 어렵다. 
    - 자원의 활용성이 떨어진다.
    - 많은 자원을 사용하는 프로세스가 적은 자원을 사용하는 프로세스보다 불리하다. 
    - 결국 일괄 작업 방식으로 동작한다. 

2. 교착 상태 회피 방법인 은행원 알고리즘의 단점을 설명하시오. 
    - 프로세스가 자신이 사용할 모든 자원을 미리 선언해야 한다.
    - 시스템의 전체 자원 수가 고정적이어야 한다. 
    - 자원이 낭비된다.

3. 교착 상태 검출 시 타임아웃을 이용하는 방법의 장단점을 설명하시오. 
    - 일정 시간 동안 작업이 진행되지 않은 프로세스를 교착 상태가 발생한 것으로 간주하여 처리하는 방식. 교착 상태가 자주 발생하지 않을 것이라는 가정하에 사용하는 것으로, 특별한 알고리즘이 없어 쉽게 구현할 수 있다. 
    - 그러나 엉뚱한 프로세스가 강제 종료될 수 있으며 모든 시스템에 적용할 수 없다(ex. 분산 데이터베이스). 


***



## Chapter7 물리 메모리 관리 
### 요약 
1. 메모리 관리의 복잡성
    - 과거의 일괄 처리 시스템에서는 한 번에 한 가지 작업만 처리했기 때문에 메모리 관리가 어렵지 않았다. 그러나 오늘날의 시분할 시스템에서는 운영체제를 포함한 모든 응용 프로그램이 메모리에 올라와 실행되기 때문에 메모리 관리가 복잡하다. 


2. 컴파일러 
    - 컴파일러는 소스코드를 컴퓨터가 실행할 수 있는 기계어로 변역한 후 한꺼번에 실행할 수 있도록 해주는 언어 번역 프로그램이다. 오류를 발견하고 코드를 최적화하기 위해 컴파일러를 사용한다. 사용자가 소스코드를 작성하면 컴파일러는 컴파일→목적 코드와 라이브러리 연결→동적 라이브러리를 포함하여 최종 실행의 순서로 작동한다. 


3. 메모리 관리자의 정책 
    - 가져오기 정책 : 프로세스가 필요로 하는 데이터를 언제 메모리로 가져올지 결정하는 정책이다. 
    - 배치 정책 : 가져온 프로세스를 메모리의 어떤 위치에 올려놓을지 결정하는 정책이다. 
    - 재배치 정책 : 메모리가 꽉 찼을 때 메모리 내에 있는 어떤 프로세스를 내보낼지 결정하는 정책이다. 


4. 절대 주소와 상대 주소 
    - 절대 주소 : 실제 물리 주소를 가리키며 메모리 관리자 입장에서 바라본 주소이다. 
    - 상대 주소 : 사용자 영역이 시작되는 주소를 0번지로 변경하여 사용하는 주소이다. 


5. 메모리 오버레이 
    - 프로세스의 크기가 실제 메모리(물리 메모리)보다 클 때 전체 프로세스를 메모리에 가져오는 대신 적당한 크기로 잘라서 가져오는 기법이다. 


6. 스왑 
    - 메모리가 모자라서 쫓겨난 프로세스를 저장장치의 특별한 공간, 즉 스왑 영역에 모아두는 기법이다. 스왑 영역에서 메모리로 데이터를 가져오는 작업은 스왑인, 메모리에서 스왑 영역으로 데이터를 내보내는 작업은 스왑아웃이라고 한다. 


7. 메모리 분할 방식
    - 가변 분할 방식 : 프로세스의 크기에 따라 메모리를 나누는 것이다.
    - 고정 분할 방식 : 프로세스의 크기와 상관없이 메모리를 같은 크기로 나누는 것이다. 


8. 외부 단편화와 내부 단편화 
    - 외부 단편화 : 할당할 프로세스의 크기보다 메모리에 남아 있는 조각이 작아서 할당이 불가능한 현상을 말한다. 
    - 내부 단편화 : 각 메모리 조각에 프로세스를 배치하고 공간이 남는 현상을 말한다. 


9. 가변 분할 방식의 메모리 배치 방식 
    - 최초 배치 : 메모리에서 적재 가능한 공간을 순서대로 찾다가 첫 번째로 발견한 공간에 프로세스를 배치하는 방법이다. 
    - 최적 배치 : 메모리의 빈 공간을 모두 확인한 후 적당한 크기 가운데 가장 작은 프로세스를 배치하는 방법이다.
    - 최악 배치 : 최적 배치와 정반대로, 빈 공간을 모두 확인한 후 가장 큰 공간에 프로세스를 배치하는 방법이다. 


10. 조각 모음 
    - 단편화가 발생하면 이미 배치된 프로세스를 옆으로 옮겨 빈 공간들을 하나의 큰 덩어리로 만드는 것을 말한다. 




### 연습문제
1. 소스코드를 한 번에 번역하지 않고 한 행씩 번역하여 실행하는 방식을 무엇이라 하는가? 
    - 인터프리터 

2. 프로그래머가 C나 자바로 소스코드를 작성하여 컴파일하면 일차적으로 만들어지는 코드는 무엇인가? 
    - 목적 코드 

3. 컴파일할 때 코드에 라이브러리를 연결하지 않고 코드를 실행할 때 라이브러리를 가져와 실행하는 방식을 무엇이라 하는가? 
    - 동적 라이브러리 방식 

4. 메모리 관리 정책 중 메모리가 꽉 찼을 때 메모리에 있는 어떤 프로세스를 내보낼지 결정하는 것은 무엇인가? 
    - 재배치 정책

5. 32bit CPU를 사용하는 컴퓨터가 가질 수 있는 물리 메모리의 최대 크기는 얼마인가? 
    - 2의 32승 B (약 4GB)

6. 절대 주소는 실제 물리 주소로, 메모리 관리자 입장에서 바라본 주소이다. 절대 주소와 관계없이 사용자 입장에서 항상 0번지부터 시작하는 주소는 무엇인가? 
    - 상대 주소 

7. 상대 주소를 절대 주소로 변환할 때 사용하는 레지스터는 무엇인가? 
    - 재배치 레지스터

8. 프로세스의 크기가 물리 메모리보다 클 때 전체 프로세스를 메모리로 가져오는 대신 적당한 크기로 잘라서 가져오는 기법은 무엇인가? 
    - 메모리 오버레이 

9. 메모리 영역이 부족해서 쫓겨난 프로세스를 보관하는 저장장치의 특별한 공간은 무엇인가? 
    - 스왑 영역

10. 가변 분할 방식에서 사용하지 못하는 작은 메모리 공간이 발생하는 현상을 무엇이라 하는가? 
    - 외부 단편화

11. 고정 분할 방식에서 똑같이 나누어진 메모리 공간에 작은 조각이 발생하는 현상을 무엇이라 하는가?
    - 내부 단편화

12. 가변 분할 방식의 메모리 배치 방식 중 프로세스를 배치하기에 적당한 공간 가운데 가장 작은 공간에 배치하는 방식은 무엇인가? 
    - 최적 배치 best fit

13. 가변 분할 방식의 메모리 배치 방식 중 첫 번째로 발견한 빈 공간에 프로세스를 배치하는 방식은 무엇인가? 
    - 최초 배치 first fit

14. 가변 분할 방식의 메모리 배치 방식 중 가장 큰 공간에 프로세스를 배치하는 방식은 무엇인가? 
    - 최악 배치 worst fit

15. 가변 분할 방식에서 서로 떨어진 여러 개의 빈 공간을 합치는 작업을 무엇이라 하는가? 
    - 조각 모음 defragmentation

16. 메모리 분할 방식 중 프로세스의 크기에 맞도록 1/2 크기로 잘라가면서 메모리를 나누어주는 방식은 무엇인가? 
    - 버디 시스템 


### 심화문제
1. 컴파일러와 인터프리터를 비교하여 설명하시오. 
    - 컴파일러 : 소스코드를 컴퓨터가 실행할 수 있는 기계어로 번역한 후 한꺼번에 실행한다. C언어, 자바 등이 이 방식으로 프로그램을 실행한다. 
    - 인터프리터 : 소스코드를 한 행씩 번역하여 실행한다. 자바스크립트, 베이직 등이 이 방식으로 프로그램을 실행한다.
    - 컴파일러는 실행 전에 소스코드를 점검하여 오류를 수정하고 필요 없는 부분을 정리하여 최적화된 실행 파일을 만든다. 복잡한 프로그램에는 컴파일러를 사용하고 간단한 프로그램에는 인터프리터를 사용한다. 

구분 | 자바(컴파일러) | 자바스크립트(인터프리터) 
--|--|--
변수 | 변수를 선언해야 한다. | 변수를 선언할 필요가 없다. 
실행 | 컴파일 후 실행된다. | 한 줄씩 실행된다. 
장점 | 오류 찾기와 코드 최적화, 분할 컴파일에 의한 공동 작업이 가능하다. | 실행이 편리하다. 
사용 프로그램 | 대형 프로그램 | 간단한 프로그램 


2. 컴파일 과정에 대해 설명하시오. 
    - 소스코드를 목적 코드로 변환한 후 라이브러리를 연결하고 최종 실행 파일을 만들어 실행하는 과정이다. 
    1) 소스코드 작성 및 컴파일 
    2) 목적 코드와 라이브러리 연결 
    3) 동적 라이브러리를 포함하여 최종 실행 


3. 메모리 관리자가 수행하는 세 가지 작업에 대해 설명하시오. 
    - 가져오기 작업 : 프로세스와 데이터를 메모리로 가져오는 작업. 요청이 없더라도 앞으로 필요할 것이라고 예상되는 데이터를 미리 가져오기도 한다. 
    - 배치 작업 : 가져온 프로세스와 데이터를 메모리의 어떤 부분에 올려놓을지 결정하는 작업. 배치 작업 전에 메모리를 어떤 크기로 자를 것인지가 매우 중요하다.
    - 재배치 작업 : 꽉 차 있는 메모리에 새로운 프로세스를 가져오기 위해 오래된 프로세스를 내보내는 작업


4. 절대 주소와 상대 주소에 대해 설명하시오. 
    - 절대 주소 : 실제 물리 주소를 가리키며 메모리 관리자 입장에서 바라본 주소이다. 
    - 상대 주소 : 사용자 영역이 시작되는 주소를 0번지로 변경하여 사용하는 주소이다. 


5. 가변 분할 방식의 장단점을 설명하시오. 
    - 장점 : 프로세스를 한 덩어리로 처리하여 하나의 프로세스를 연속된 공간에 배치한다. 
    - 단점 : 메모리 관리가 복잡하다. (추가적인 메모리 통합 작업이 필요함)


6. 고정 분할 방식의 장단점을 설명하시오. 
    - 장점 : 메모리를 일정한 크기로 나누어 관리하기 때문에 메모리 관리가 수월하다. 
    - 단점 : 쓸모없는 공간으로 인해 메모리 낭비가 발생할 수 있다. 


7. 버디 시스템에 대해 설명하시오. 
    - 가변 분할 방식과 고정 분할 방식의 중간 구조이다. 
    - 1) 프로세스의 크기에 맞게 메모리를 1/2로 자르고 프로세스를 메모리에 배치한다. 
    - 2) 나뉜 메모리의 각 구역에는 프로세스가 1개만 들어간다. 
    - 3) 프로세스가 종료되면 주변의 빈 조각과 합쳐서 하나의 큰 덩어리를 만든다.
    - 가변 분할 방식보다 효과적으로 공간을 관리할 수 있는 이유는 비슷한 크기의 덩어리가 서로 모여 있어 통합하기가 쉽기 때문이다.




***
## Chapter8 가상 메모리의 기초
### 요약 
1. 가상 메모리의 개념 
    - 물리 메모리의 크기와 상관없이 프로세스에 커다란 메모리 공간을 제공하는 기술이다. 프로세스는 운영체제가 어디에 있는지, 물리 메모리의 크기가 어느 정도인지 신경 쓰지 않고 메모리를 마음대로 사용할 수 있다. 


2. 가상 메모리의 크기 
    - 가상 메모리에서 메모리 관리자가 사용할 수 있는 메모리의 전체 크기는 물리 메모리와 스왑 영역을 합한 크기이다. 


3. 매핑 테이블 
    - 가상 주소가 물리 메모리의 어느 위치에 있는지 알 수 있도록 정리한 표이다. 페이징 기법에서는 페이지 매핑 테이블 또는 페이지 테이블이라고 부르며, 세그먼테이션 기법에서는 세그먼테이션 매핑 테이블 또는 세그먼테이션 테이블이라고 부른다. 


4. 페이징 기법 
    - 고정 분할 방식을 이용한 가상 메모리 관리 기법으로, 물리 주소 공간을 같은 크기로 나누어 사용한다. 가상 주소의 분할된 각 영역은 페이지라고 부르며, 물리 메모리의 각 영역은 가상 주소의 페이지와 구분하기 위해 프레임이라고 부른다. 


5. 페이지 테이블 매핑 방식 
    - 직접 매핑 : 페이지 테이블 전체가 물리 메모리의 운영체제 영역에 존재하는 방식이다. 
    - 연관 매핑 : 페이지 테이블 전체를 스왑 영역에서 관리하는 방식으로, 물리 메모리의 공간이 작을 때 사용한다. 
    - 집합-연관 매핑 : 연관 매핑의 문제를 개선한 방식으로, 페이지 테이블을 일정한 집합으로 자르고, 자른 덩어리 단위로 물리 메모리에 가져온다. 
    - 역매핑 : 위의 세 가지 매핑과 달리 물리 메모리의 프레임 번호를 기준으로 테이블을 구성한다. 


6. 세그먼테이션 기법 
    - 가변 분할 방식을 이용한 가상 메모리 관리 기법으로, 물리 메모리를 프로세스의 크기에 따라 가변적으로 나누어 사용한다. 


7. 세그먼테이션-페이징 혼용 기법 
    - 사용자 입장에서는 세그먼테이션 기법을 사용하고 메모리 관리자 입장에서는 페이징 기법을 사용하는 가상 메모리 관리 기법이다. 메모리 보호 및 중복 정보를 세그먼테이션 테이블에서 관리함으로써 메모리 관리를 효율적으로 할 수 있다. 



### 연습문제 
1. 가상 메모리에서 메모리 관리자가 사용할 수 있는 전체 크기는 어떻게 결정되는가? 
    - 물리 메모리(실제 메모리)와 스왑 영역을 합한 크기이다. 

2. 가상 주소에서 하나의 프로세스가 사용할 수 있는 최대 주소는 무엇과 연관이 있는가? 
    - CPU 비트 값


3. 가상 메모리에서 가상 주소를 물리 주소로 변환하기 위해 사용하는 자료구조를 무엇이라 하는가? 
    - 매핑 테이블 


4. 페이징 기법의 주소 변환 과정 식을 쓰시오. 
    - VA = <P, D> → PA = <F, D>


5. 페이지 테이블에서 각각의 한 줄을 무엇이라 하는가? 
    - 페이지 테이블 엔트리 PTE


6. 가상 주소를 <P, D>로 변환하는 공식을 쓰시오. 
    - P = "가상 주소/한 페이지의 크기"의 몫 
    - D = "가상 주소/한 페이지의 크기"의 나머지


7. 각 페이지 테이블의 시작 주소를 가지고 있는 레지스터는 무엇인가? 
    - 페이지 테이블 기준 레지스터 PTBR (Page Table Base Register) 


8. 페이지 테이블 매핑 방식 중, 모든 페이지 테이블을 스왑 영역에 저장하고 그 중 일부만 물리 메모리에 무작위로 가지고 있는 방식은 무엇인가? 
    - 연관 매핑 associative mapping 

9. 페이지 테이블 매핑 방식 중, 모든 페이지 테이블을 물리 메모리에 보관하는 방식은 무엇인가? 
    - 직접 매핑 direct mapping 

10. 페이지 테이블 매핑 방식 중, 모든 페이지 테이블을 스왑 영역에 저장하고 페이지 테이블을 일정한 집합 단위로 물리 메모리에 보관하는 방식은 무엇인가? 
    - 집합-연관 매핑 set-associative mapping 

11. 페이지 테이블 매핑 방식 중, 물리 메모리의 프레임 번호를 기준으로 테이블을 구성하는 방식은 무엇인가? 
    - 역매핑 invert mapping 

12. 연관 매핑에서 사용하는 테이블의 이름은 무엇인가? 
    - 변환 색인 버퍼 Translation Look-aside Buffer (TLB) 

13. 연관 매핑에서 원하는 데이터가 변환 색인 버퍼에 없는 상태를 무엇이라 하는가? 
    - TLB 미스 

14. 연관 매핑에서는 전체 매핑 테이블을 어디에 보관하는가? 
    - 스왑 영역 

15. 가상 메모리에서 메모리 관리자는 물리 메모리 영역과 스왑 영역을 합쳐서 프로세스가 사용하는 가상 주소를 실제 메모리의 물리 주소로 변환한다. 이러한 작업을 무엇이라 하는가? 
    - 동적 주소 변환

16. 사용자 프로세스가 자신의 크기보다 더 큰 주소에 접근하려고 하면 메모리 관리자는 그 프로세스를 강제 종료한다. 이때 발생하는 오류를 무엇이라 하는가? 
    - 트랩 trap

17. 세그먼테이션-페이징 혼용 기법에서는 접근 권한을 어디에서 관리하는가? 
    - 세그먼테이션 테이블 


### 심화문제 
1. 가상 메모리가 이론적으로 가질 수 있는 크기와 실제 운영되는 크기는 어떤 차이가 있는지 설명하시오. 
    - 이론적으로는 무한대이나, 컴퓨터 시스템이 가진 물리 메모리의 최대 크기로 한정되며 CPU의 비트에 따라 정해진다. 


2. 페이징 기법의 주소 변환 과정을 그림으로 그리고 설명하시오. 
    - ex) 가상 주소 18번지에 접근 
    - 1) 가상 주소 18번지가 어느 페이지에 있는지 찾는다. 18번지는 페이지 1의 8번째 위치에 있다. 
    - 2) 페이지 테이블의 페이지1로 가서 해당 페이지가 프레임 3에 있다는 것을 알아낸다. 
    - 3) 프로세스가 저장하려는 값을 프레임 3의 8번 위치에 저장한다. 


3. 연관 매핑의 동작을 설명하시오. 
    - 메모리에 접근하기 위해 먼저 TLB를 찾아본다. 원하는 페이지 번호가 TLB에 있는 경우는 TLB 히트라고 하며, 곧바로 물리 주소로 변환된다. 원하는 페이지 번호가 TLB에 없는 경우는 TLB 미스라고 하며, 스왑 영역에 저장된 직접 매핑 테이블을 사용하여 프레임 번호로 변환한다. 
    - 메모리를 절약할 수 있지만, TLB 미스가 빈번하게 발생할 경우 시스템의 성능이 떨어진다. TLB 미스를 알게 되는 시점이 TLB를 모두 검색하고 난 후이므로 TLB 미스인 경우 주소 변환이 느려진다. 


4. 집합-연관 매핑의 동작을 설명하시오.
    - 프로세스가 특정 주소를 요구하면 VA=<P1, P2, D>로 변환되고, P1을 이용하여 디렉터리 테이블에서 주소를 찾는다. 만약 I(Invalid)라고 표시되어 있으면 TLB 미스가 발생한 것이다. 반대로 원하는 테이블이 물리 메모리에 있으면 묶음 테이블의 시작 주소가 명시되어 있으며 P2를 이용하여 묶음 테이블에서 원하는 프레임 번호를 얻게 된다. 
    - 직접 매핑과 연관 매핑의 장점을 합한 방식 
    - 연관 매핑은 TLB 미스가 발생할 경우 TLB 전체를 검색하는 데 시간을 낭비하지만 집합-연관 매핑은 이러한 낭비가 발생하지 않는다. 
    - 집합-연관 매핑은 직접 매핑과 달리 일부 페이지 테이블만 메모리에서 관리하여 물리 메모리를 낭비하지 않는다. 


5. 역매핑의 동작을 설명하시오. 
    - 물리 메모리가 어떤 프로세스의 어떤 페이지를 가지고 있는지를 테이블 형태로 구성한다. <프레임 번호, 프로세스 아이디, 페이지 번호>
    - 메모리 관리자는 주소 변환을 해야 하는 프로세스의 아이디와 페이지 번호가 물리 메모리에 있는지 역매핑 테이블에서 검색한다. 현재 테이블에 원하는 데이터가 없으면 스왑 영역에서 가져온다. 
    - 페이지 테이블을 다 검사한 후에야 저장장치에 접근하기 때문에 검색 시간을 낭비하는 단점이 있다.
    - 페이지 테이블의 행 수는 실제 프레임의 수와 같다. 프로세스의 수와 상관없이 항상 일정 크기의 페이지 테이블을 유지하여 테이블의 크기가 매우 작다.  


6. 세그먼테이션-페이징 혼용 기법을 사용하는 이유를 설명하시오. 
    - 순수 페이징 기법을 사용하면 중복되는 데이터(권한 비트)로 페이지 테이블이 커지기 때문에 중복되는 데이터를 세그먼테이션 테이블로 옮겨서 테이블의 크기를 줄일 수 있다. 



*** 

## Chapter9 가상 메모리 관리
### 요약 
1. 요구 페이징
    - 사용자가 요청할 때 해당 페이지를 메모리로 가져오는 것을 말한다. 


2. 페이지 테이블 엔트리의 플래그 비트 
    - 접근 비트 : 페이지가 메모리에 올라온 후 사용한 적이 있는지 알려주는 비트
    - 변경 비트 : 페이지가 메모리에 올라온 후 데이터의 변경이 있었는지 알려주는 비트
    - 유효 비트 : 페이지가 실제 메모리에 있는지 나타내는 비트 
    - 읽기, 쓰기, 실행 비트 : 페이지에 대한 읽기, 쓰기, 실행 권한을 나타내는 비트 


3. 페이지 부재
    - 프로세스가 페이지를 요청했을 때 그 페이지가 메모리에 없는 상황을 말한다. 


4. 지역성 
    - 기억장치에 접근하는 패턴이 메모리 전체에 고루 분포되는 것이 아니라 특정 영역에 집중되는 성질을 말한다. 지역성은 크게 공간의 지역성, 시간의 지역성, 순차적 지역성으로 나뉜다. 


5. 페이지 교체 알고리즘 
알고리즘 | 특징
--|--
무작위 | 무작위로 대상 페이지를 선정하여 스왑 영역으로 보낸다.
FIFO | 처음 메모리에 올라온 페이지를 스왑 영역으로 보낸다.
최적 | 미래의 접근 패턴을 보고 대상 페이지를 선정하여 스왑 영역으로 보낸다. 
LRU | 시간적으로 멀리 떨어진 페이지를 스왑 영역으로 보낸다.
LFU | 사용 빈도가 적은 페이지를 스왑 영역으로 보낸다. 
NUR | 최근에 사용한 적이 없는 페이지를 스왑 영역으로 보낸다. 
FIFO 변형 | FIFO 알고리즘을 변형하여 성능을 높인다.


6. 스레싱
    - 하드디스크의 입출력이 너무 많아져서 잦은 페이지 부재로 작업이 멈춘 것 같은 상태를 말한다. 


7. 프레임 할당 방식
    - 정적 할당 : 프로세스 실행 초기에 프레임을 나누어준 후 그 크기를 고정하는 방식이다.
    - 동적 할당 : 프로세스를 실행하는 중에 프레임을 나누어주기도 하고 회수하기도 하는 방식이다. 


### 연습문제
1. 메모리 가져오기 정책 중, 사용자가 요구할 때 해당 페이지를 메모리로 가져오는 방식은 무엇인가? 


2. 요구 페이징과 반대로 앞으로 필요할 것이라고 예상되는 페이지를 미리 가져오는 방식은 무엇인가? 


3. 페이지 테이블 엔트리의 구조 중, 페이지가 실제 메모리에 있는지 나타내는 비트는 무엇인가? 


4. 페이지 테이블 엔트리의 구조 중, 페이지가 메모리에 올라온 후 사용한 적이 있는지 알려주는 비트는 무엇인가? 


5. 페이지 테이블 엔트리의 구조 중, 페이지가 메모리에 올라온 후 데이터의 변경이 있었는지 알려주는 비트는 무엇인가? 


6. 프로세스가 페이지를 요청했을 때 해당 페이지가 메모리에 없는 상황을 무엇이라 하는가? 


7. 기억장치에 접근하는 패턴이 메모리 전체에 고루 분포되는 것이 아니라 특정 영역에 집중되어 있는 성질을 무엇이라 하는가? 


8. 처음으로 메모리에 올라온 페이지를 스왑 영역으로 보내는 페이지 교체 알고리즘은 무엇인가? 


9. 미래의 접근 패턴을 기준으로 대상 페이지를 선정하여 스왑 영역으로 보내는 방식으로, 실제로 구현이 불가능한 페이지 교체 알고리즘은 무엇인가? 


10. 시간적으로 멀리 떨어진 페이지를 스왑 영역으로 보내는 페이지 교체 알고리즘은 무엇인가? 


11. 사용 빈도가 적은 페이지를 스왑 영역으로 보내는 페이지 교체 알고리즘은 무엇인가? 


12. 최근에 사용한 적이 없는 페이지를 스왑 영역으로 보내는 페이지 교체 알고리즘은 무엇인가? 


13. FIFO 변형 페이지 교체 알고리즘 중, 성공한 페이지를 큐의 맨 뒤로 옮김으로써 기회를 한 번 더 주는 페이지 교체 알고리즘은 무엇인가? 


14. FIFO 변형 페이지 교체 알고리즘 중, 대상 페이지를 가리키는 포인터를 사용하여 포인터가 큐의 맨 바닥으로 내려가면 다음에 다시 큐의 처음을 가리키게 하는 페이지 교체 알고리즘은 무엇인가? 


15. 하드디스크의 입출력이 많아져서 잦은 페이지 부재로 작업이 거의 멈춰버린 상태를 무엇이라 하는가? 


16. 동적 프레임 할당 방식 중, 최근 일정 시간 동안 참조된 페이지를 집합으로 유지하고 이 집합에 있는 페이지들을 물리 메모리에 유지하는 것은 무엇인가? 


17. 동적 프레임 할당 방식 중, 페이지 부재 비율의 상한선과 하한선을 설정하고 페이지 부재 비율이 상한선을 초과하면 할당 프레임을 늘려주는 것은 무엇인가? 



### 심화문제
1. 요구 페이징의 의미와 효과를 설명하시오. 


2. 세그먼테이션 오류와 페이지 부재의 차이를 설명하시오. 


3. 지역성의 의미를 설명하시오. 


4. LRU 페이지 교체 알고리즘의 동작을 설명하시오. 


5. NUR 페이지 교체 알고리즘의 동작을 설명하시오. 


6. 프레임 할당 방식 중 정적 할당에 대해 설명하시오. 


7. 프레임 할당 방식 중 동적 할당에 대해 설명하시오. 



***







