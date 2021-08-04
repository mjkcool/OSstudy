# OSstudy 2021/7/21~
<쉽게 배우는 운영체제 - 한빛아카데미>
   
   
## 1-2 운영체제의 역사

   
### 일괄작업 시스템 : batch job system
1950년대. 아주 작은 논리회로인 ```IC칩```으로 컴퓨터가 만들어지면서 등장했다. 현대적인 프로그래밍과 컴퓨터의 시작(진공관&전선 탈출)!

CPU, 메인메모리가 있었고 입력장치로는 *천공카드 리더(OMR의 원조)를, 출력장치로는 *라인프린터를 사용했다.

> ###### *천공카드 리더: 구멍을 뚫어 문자와 숫자를 표현했다. 흔히 시험에 쓰이는 OMR카드에 까만 점을 칠하는 것과 비슷하다. 구멍을 뚫었다니 꼭 오르골을 사용하는 것 같기도.
> ![image](https://user-images.githubusercontent.com/53461080/126930582-cd5c9a65-d382-4139-b121-dc6b1a1bd6d3.png)
>   
> ###### *라인프린터의 '라인'은 한줄씩만 출력한다는 의미이다.

그러나 이러한 입출력 기기로 인해 일괄 처리 시스템(batch processing system)이다.
    
    
### 시분할 시스템 : time sharing system
1960년대 후반. 다중 프로그래밍 기술의 개발로 여러 작업을 동시에 실행할 수 있게 되었다. 다중 프로그래밍이란 하나의 CPU가 여러 작업을 동시에 수행하는 것인데, 일괄작업 시스템과 반대되는 개념이라고 볼 수 있다. 보다 효율성이 뛰어나다.

그렇다면 왜 '시분할' 시스템이라 부르는 것일까?

사실 CPU가 여러 작업을 정말 '동시에' 실행하는 것은 아니다. 여러 작업을 조금씩 나누어서 하는 것이다. 그 시간 분배의 속도가 아주 빨라서 우리에겐 동시에 작업을 실행하는 것처럼 보이게 되는 것이다. 멀티태스킹 시스템이라고도 불린다.   

![image](https://user-images.githubusercontent.com/53461080/126930888-e1fc8ee4-d6ec-48fd-927d-876886be607b.png)
###### 분할된 시간 단위의 명칭은 ```time slice``` 또는 ```time quantum```이다.
동시에 실행되는 작업의 개수를 ```멀티프로그래밍 수준/정도(level of multiprogramming)```라고 부른다. 위 그림에선 멀티프로그래밍 수준이 3이다.

시분할 시스템에선 ```다중 사용자 시스템(multi-user system)```이 가능하다. 여러 사용자가 동시에 작업을 할 수 있는 것이다. 시분할 시스템이 적용된 OS론 유닉스가 있다.

단점으론 이러한 멀티태스킹을 위해선 추가적인 작업이 필요하다는 것이다. 또한 중요한 작업을 우선 관리하는 게 어려울 수 있다. 중요한 작업을 일정 시간 내에 끝내기 위한 목적으론 더욱 안전한 ```실시간 시스템(real-time system)```을 사용한다.

   
### 분산 시스템 : distributed system
1970년대 후반. 네트워크 상에 분산되어 있는 여러 컴퓨터로 작업을 처리하고 그 결과를 상호 교환하도록 구성한 시스템이다. 개인용 컴퓨터와 인터넷의 등장 덕분에 가능했다. 저렴하고 크기가 작은 컴퓨터들을 하나로 묶어 대형 컴퓨터 못지않은 시스템을 만들 수 있게 되었다.

> ###### 1. 개인용 컴퓨터(스티브 잡스의 애플2)의 등장으로 소프트웨어가 급속도로 발전했다. 더 많은 사람들이 컴퓨터를 소유하고 사용할 수 있게 된 것이다. 개인용 컴퓨터의 운영체제로 매킨토시와 MS-DOS가 많이 사용되었다.
> <img src=https://user-images.githubusercontent.com/53461080/126931127-3d8ec1e4-281f-4081-bc47-42469a7ddab4.png width=300px></img> Apple II Personal Computer
> 
> ###### 2. 1960년대, ARPAnet(아르파넷)이 만들어졌다. 인터넷의 등장이다. 이것이 점점 대중화되며 컴퓨터 간의 네트워킹을 위해 TCP/IP 프로토콜이 정의되었다.


### 클라이언트/서버 시스템
분산 시스템의 단점을 개선하는 시스템이다. 분산 시스템은 모든 컴퓨터가 동일한 지위이기 때문에 상호 교환에 있어서 컴퓨터의 개수 변동에 따라 문제가 생기거나 번거로워 진다.

이 시스템은 작업을 요청하는 클라이언트와 응답을 받아 요청된 작업을 처리하는 서버의 이중구조로 이루어진다. 클라이언트와 서버 사이에 요청과 응답을 다루기 위한 네트워크가 존재한다. 우리가 잘 알고 있듯 웹 시스템에서 이용되며, 웹 시스템을 통해 대중화되었다.

단점으론 많은 요청으로 인해 서버 과부화가 발생할 수 있다. 많은 요청을 처리하기 위해선 그만큼 많은 서버와 큰 용량의 네트워크가 필요하기 때문이다. (서버터졌다, 유리서버, 서버 다운..., Yes24 티켓팅)
> ###### <데몬> 클라이언트/서버 시스템에서는 서버가 멈추지 않고 계속 작동하여 클라이언트의 요청을 처리한다. 이렇게 멈추지 않고 계속 작동하는 프로그램을 데몬(demon)이라고 한다. 종류는 웹데몬, FTP데몬 등 용도에 따라 여러가지가 있다.


### P2P 시스템 : peer-to-peer system
클라이언트/서버 시스템의 서버 과부화 문제를 개선하는 시스템이다. peer는 사용자의 컴퓨터(말단 노드)를, P2P는 서버를 거치지 않고 사용자 간을 직접 연결한다는 의미를 가지고 있다.   

<img src=https://user-images.githubusercontent.com/53461080/126931550-cf106712-1e9e-4ef7-b556-33cfda46c1e6.png width=500px></img>   

이 시스템에선 파일 검색만 서버가, 파일 전송은 사용자 간에 이루어져 서버 부하가 적다. 메신저 프로그램이 대표적이다.

대용량 파일 공유를 위한 P2P 시스템의 경우 (MP3 공유 등),
1. 같은 파일을 가진 여러 사람에게 해당 데이터를 일부씩 나누어 받는다. 퍼즐조각처럼.
2. 더 많은 사람에게 나누어 받을 수록 그 속도는 더욱 빨라진다.
3. 대용량의 데이터 전송 중 문제가 생겨 전송이 취소되면 곤란한데, 이 방법은 여러명에게 받기 때문에 모든 사람에게 문제가 생기지 않는 한 전송이 취소될 위험이 매우 적어 안전하다(누군가의 전송이 취소되도 그 양이 크지 않기에 다른 사람이 메꾸면 된다).

## 2-1 컴퓨터의 기본 구성

### 하드웨어의 구성
#### 필수장치
 -   ```중앙처리장치(CPU)```: 명령어를 해석하여 실행하는 장치이다.
 -   ```메인메모리(제1저장장치)```: 작업에 필요한 프로그램과 데이터를 저장한다. 바이트 단위의 주소 분할. 데이터를 영구적으로 저장할 수 없다(전원OFF시 소멸).
#### 주변장치
 -   ```입력장치```: 외부의 데이터를 컴퓨터에 입력하는 장치이다. 키보드, 마우스, 스캐너, 터치스크린 등이 있다.
 -   ```출력장치```: 컴퓨터의 처리결과를 사용자가 원하는 형태로 출력하는 장치이다. 프린터, 모니터, 스피커 등이 있다.
 -   ```저장장치(제2저장장치, 보조저장장치)```: 메인메모리와 달리 구동장치가 있어 속도가 느리지만, 저렴하고 용량이 크다. 데이터를 영구적으로 저장한다.
     -   ```자성 이용 저장장치```: 카세프테이프, 플로피디스크, 하드디스크 등
     -   ```레이저 이용 저장장치```: CD, DVD, 블루레이디스크 등
     -   ```메모리 이용 저장장치```: USB 드라이버, SD 카드, CF 카드 등

-   ```버스```: 각 장치를 연결하는 선의 집합, 데이터가 지나다니는 통로
-   ```메인보드```: CPU와 메모리 등 다양한 부품을 연결하는 커다란 판. 각종 부품을 꽂을 수 있는 단자들이 있다(CPU 단자, 마우스키보드 단자, 사운드 단자 등). 단자에 연결되는 카드들이 기본으로 장착되어 있기도 하다. 성능향상을 위해선 따로 장착한다. 메인보드에도 다양한 제품이 있는 듯 하다.   

<img src=https://user-images.githubusercontent.com/53461080/127269033-f1ea8ccf-b90c-43d8-9690-49d6287b8ec5.png width=600px></img> 

### 폰노이만 구조 von Neumann architecture

CPU, 메모리, 입출력장치, 저장창치가 버스로 연결된 구조이다. 하드웨어는 그대로 둔 채 작업을 위한 프로그램만 교체하여 메모리에 올리는 방식으로, 기존의 하드와이어링(전선 회로) 형의 전선 재연결과 같은 번거로움을 해결했다. 메모리를 이용하여 프로그래밍이 가능한 오늘날 컴퓨터 구조의 모습이다.

이 구조의 핵심은 **'운영체제를 포함한 모든 프로그램은 메모리에 올라와야 실행할 수 있다'** 는 것이다.    

<img src=https://user-images.githubusercontent.com/53461080/127269088-b5ffd1f3-10ac-4eb8-b1a5-3c19e94022bc.png width=600px></img> 

### 하드웨어 사양

-   ```클록(clock)```: CPU의 속도와 관련된 단위이다. 클록이 일정 간격으로 틱(tick)을 만들면 CPU가 이 박자에 맞춰 작업을 한다. 버스는 메인보드의 클록이 만드는 틱에 맞춰 데이터를 이동시킨다. 
    > ###### *틱은 펄스(pulse) 또는 클록틱(clock tick) 이라고도 부른다.
-   ```헤르츠(Hz)```: 클록틱이 발생하는 속도를 나타내는 단위로, 1초에 클록틱이 발생하는 횟수를 나타낸다. 3.5kHz는 3500Hz이고 1초에 3500번 클록틱이 발생함을 나타낸다.
-   ```시스템 버스```: ```전면 버스(FSB, Front-side bus)```라고도 한다. 메모리와 주변장치를 연결하는 버스이다. 헤르츠가 같은 메모리와 부품에 연결해야 제 속도를 낼 수 있으며 효과적이다.
-   ```CPU 내부 버스```: ```후면 버스(BSB, Back-side bus)```라고도 한다. CPU 내부 버스의 속도는 CPU 클록과 같아 시스템 버스보다 훨씬 빠르다(전면 버스와 후면 버스 사이에 속도차가 존재한다).    
    
## 2-2-1 CPU의 기본 구성

### 산술논리 연산장치(Arithmetic and Logic Unit, ALU)
데이터를 연산하는 장치로, 산술연산과 논리연산을 수행한다.   
### 제어장치(control unit)   
CPU에게 작업을 지시한다.
### 레지스터(register)   
CPU 내에 데이터를 임시로 보관하는 곳이다. 연산을 위해 필요한 데이터를 메모리에서 CPU로 가져와 임시로 보관하고, 연산 결과를 메모리에 저장하기 전 보관한다.
#### 사용자 가시 레지스터(user-visible register): 사용자에 의해 내용이 변경된다.
  -   ```데이터 레지스터(DR)```: 메모리에서 가져온 데이터를 임시로 보관한다. CPU에서 주로 사용되며, ```일반 레지스터``` 또는 ```범용 레지스터```라고 부른다.
  -   ```주소 레지스터(AR)```: 데이터 또는 명령어의 메모리 주소를 저장한다.
#### 사용자 불가시 레지스터(user-invisible register): 사용자가 임의로 변경할 수 없는 특수 레지스터이다.
  -   ```프로그램 카운터(PC)```: 다음에 실행할 명령어의 주소를 제어장치에게 알려주며, ```명령어 포인터(instruction pointer)```라고도 한다.
  -   ```명령어 레지스터(IR)```: 현재 실행중인 명령어를 저장하며, 제어장치는 이곳에 저장된 명령을 해석하여 제어 신호를 만든다.
  -   ```메모리 주소 레지스터(MAR)```: 메모리에 데이터를 저장하고 가져오기 위한 메모리 주소를 지정한다.
  -   ```메모리 버퍼 레지스터(MBR)```: 메모리에서 가져왔거나 저장할 데이터를 임시로 저장한다. MAR과 함께 동작한다.
  -   ```프로그램 상태 레지스터(PSR)```: 연산 결과에 대한 정보를 저장한다.
   
   
### + 버스
- ```제어 버스```: 다음 작업을 지시하는 제어 신호가 이동한다. CPU의 제어장치, 메모리, 주변장치와 양방향으로 정보를 주고받는다. CPU에겐 오류 신호와 작업 상태를, 메모리에겐 읽기/쓰기 신호를, 주변 장치에겐 동장 신호를 보낸다.
- ```주소 버스```: 사용할 메모리 위치의 정보(주소)가 이동한다. 단방향으로 정보를 주고받으며, CPU의 MAR에게 메모리 주소를 받고, 메모리와 주변장치에 주소를 전달한다.
- ```데이터 버스```: 데이터가 목적지로 이동한다. 양방향으로 정보를 주고받으며, CPU의 MBR에게 데이터를 받아 메모리와 주변장치로 전달한다.
> - ```대역폭(bandwidth)```: 버스에서 한번에 전달할 수 있는 데이터의 최대 크기를 말하며, *CPU가 한번에 처리할 수 있는 데이터의 크기와 같다.
> - ```워드(word)```: CPU가 한번에 처리할 수 있는 데이터의 최대 크기. 대역폭도 워드라고 볼 수 있다.   
   
## 2-2-2 메모리와 부팅
메모리에는 실행에 필요한 프로그램과 데이터가 존재하며, CPU와 협업하여 작업한다. 메모리 주소는 바이트 단위로, 데이터는 워드 단위로 움직인다.
종류로는 RAM과 ROM이 있다.
### RAM
Ramdom access memory, 읽기/쓰기만 가능하다.
-   휘발성 메모리(volatility memory)
    -   ```DRAM(Dynamic RAM)```: 일정 시간마다 데이터가 사라지기 때문에 재생이 필요하다. 주로 메인메모리에 사용한다.
    -   ```SRAM(Static RAM)```: 전력이 공급되는 동안에는 데이터를 보관할 수 있어 재생할 필요가 없다. 속도는 빠르나 가격이 비싸다. 주로 캐시와 같은 고속메모리에 사용한다.
    -   ```SDRAM(Synchronous Dynamic RAM)```: DRAM이 발전된 형태로, 클록틱이 발생할 때마다 데이터를 저장하는 동기식 DRAM이다. _자동 재생을 나타내는 것 같다!_
-   비휘발성 메모리
    -   ```플래시 메모리```: 전력이 없어도 데이터를 보관한다. 디지털카메라, MP3 플레이어, USB 드라이버 등에 사용하며, 메모리의 각 소자는 사용횟수 제한이 있어 언젠간 원래의 기능을 잃을 수 있다.
    -   대표적인 플래시 메모리만 설명했다. 요즘 많이 사용되는 SSD는 하드디스크 대용으로 만들어졌다. 고가이나 높은 속도와 내구성으로 많은 기기에 사용되고 있다.

### ROM
Read only memory, 전력이 끊켜도 데이터를 보관할 수 있으나 저장된 데이터는 읽기만 가능하다(수정이 불가). 때문에 수정하면 안되는 또는 수정이 필요없는 프로그램을 저장한다. ```BIOS```를 롬에 저장한다.
-   ```Mask ROM```: 공장에서부터 데이터가 입력이 되어 데이터를 지우거나 쓸 수 없다.
-   ```PROM(Programmable ROM)```: 전용 기계를 이용해 데이터를 1회만 저장할 수 있다.
-   ```EPROM(Erasable Programmable ROM)```: 데이터를 여러번 쓰고 지울 수 있다. 플래시 메모리와 유사하나 고가이다.

### 메모리 보호
일괄작업 시스템에선 메모리가 운영체제 영역과 사용자 영역으로 구분되어 있는데, 사용자 영역이 운영체제 영역을 접근하지 못하게 막음으로써 메모리를 보호한다. 시분할 기법에선 사용자 영역이 여러 작업공간으로 나누어져 메모리 보호가 더욱 중요하다.
> 바이러스: 운영체제 영역이나 다른 프로그램 영역으로 침범하는 악성 소프트웨어

CPU는 메모리 보호를 위해 ```경계 레지스터(bound register)```와 한계 ```레지스터(limit register)```를 사용한다. 이 두 레지스터를 통해 작업이 사용하는 메모리 범위를 저장하고, 사용자의 작업이 진행될 때 이 주소 범위를 벗어나는지 하드웨어적으로 점검한다. 주소 범위를 벗어나면 메모리 오류에 관련한 인터럽트가 발생한다.
   
### 부팅
컴퓨터를 켰을 때 운영체제를 메모리에 올리는 과정이다.

1.  컴퓨터 전원이 켜진다.
2.  롬에 저장된 바이오스가 실행된다.
    1.  주요 하드웨어의 정상작동을 확인한다.
    2.  이상이 없으면 하드디스크 내 ```마스터 부트 레코드(MBR)```의 부트스트랩을 실행시킨다.

> - 마스터 부트 레코드: 하드디스크의 첫번째 섹터(저장 단위)이다. 마스터 부트 레코드가 손상되면 운영체제를 실행할 수 없다.   
> - ```부트스트랩(bootstrap)```: 운영체제를 메모리로 가져와 실행하는 작은 프로그램. 운영체제마다 전용 부트스트랩을 가진다.

운영체제(부트스트랩)은 하드디스크에, 바이오스는 롬에 저장된다.
