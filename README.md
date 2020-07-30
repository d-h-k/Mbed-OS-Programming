# Mbed-OS-Programming
- Mbed OS 프로그래밍 교육 2020.07.27~29
- 강사 : ARM 코리아 이동명 차장
- 너는 강사할때 늦지마라 늦는건 최악이다 증말
- 재직자과정이니만큼 질문을 많이 해 주시면 필요한걸 얻어갈 수 있습니다.
- ARM의 생태계를 확보하려고 일하고 있는 현직자, 디벨로퍼 이반젤리스트 개발자가 고민하고 있는 내용을 풀어내기 위해서
- kiot 재직자 대상은 두번째, 지난주에는 비전공자 광범위한 
- 과거에는 삼성전자에서 모바일 SOC랑 검증 진행했고, SDK 보드를 설계했고, 엑시노스 칩이 나오면 디바이스드라이버와 비디오코덱
- 노키아에서 스마트자켓 총괄
- 이번달을 마지막으로 ARM을 떠나기로 했습니다. 
- 슬라이드는 4개의 큰 테두리,
  - 환경셋업, 제반설명, 하루걸린다. : 물론 더 빨리할수 있지만, 현업에서 쓰실꺼기 때문에 적극적으로 답변을 드리도록 하겠습니다.
  - ARM의 공개가 가능한 범위 내에서의 
> 목차
  - 1일차 
    - 개발환경소개
    - 개발환경 구축
  - 2일차
    - 
  - 3일차
    - 
# Day1 오전 : 썰풀기
- A과 M 차이
  - 클럭스피드
  - 코어 성능자체가 다름
  - M은 마이크로컨트롤러
  - Arm v7  인스트럭션 셋은 같다(스킨? 스킴? 스키마?)
  - 멀티코어는 논시큐어/시큐어 트러스트펌웨어
    - 멀티코어는 시큐리티 때문에...
    - 설계 의도에 따라서 안정성(우주왕복선) : X
- IoT 디바이스, ARM프로세서로 빠른 프로토타이핑을 위해서 만드는 사업
- 소프트뱅크로 매각이 됬는데 이거 해야되냐????
- 리날로, 컴파일 GCC?? 리나로?? 오픈커뮤니티로 넘길계획이지않나?
- 코어를 위해서는 GCC가 계속 공개되서 사용될것이다.
- 라즈베리파이의 보안이슈 ###########

- sigfox 한국에서 안쓰는 이유 
  - 우리나라에서 sigfox를 못쓰는 이유는 자료가 있다. 
  - 그네들이 많든 디바이스를 써야한다. 
  - 서버가 개같은 프랑스에 있고 하루에 한번 200byte뿐이 못씀
  - 그래서 시그폭스 못쓴다
- zigbee 가 mbed에 없다.
  - iot 기기에서 사용하고 있는 
- 한국에서 LoRa 힘듬
  - 로라 단말인증 단말 펌웨어가 있어야 하는데, OS를 올릴만큼 여유가 많은데, 로라에 인증받은 펌웨어만 돌려, mcu를 외부에 붙어야되고, SKT독점이라서 쓰기 힘들다.
  - 우리끼리 이야기이지만, SKT는 로라에 별로 신경 안쓰고 있음. 게이트웨이를 하나 사신다음에, 게이트웨이에서 
  - 구단위 로라망은 되어있으나, 전국망은 없다.
  - 로라에 스텐다드 API 검증 중 
- 열한시까지 두시간은 이론강의하면서 놀아따
- (3시간쨰 시작, 9시시작, 11시시점에서)개발환경 구축 시작

- mbed config 명령어로 컴파일러 경로 선언해주는 기법
```
mbed config -G ARM_PATH "C:\Program Files\ARM"
```
```
mbed config -G ARM_PATH "C:\Program Files (x86)\GNU Tools ARM Embedded\gcc-arm-none-eabi-9-2019-q4-major\bin
"
```
- ARM이라는 회사는 아래 몇가지 사업부로 나뉘는데
  - 클라우드 사업부 : 뒤에서 쓰게될 펠리온
  - 데이터 비지니스 : 트레져데이터 라는 회사를 인수함
  - 프로세서 사업부 : 여기서 우리들이 아는 ARM프로세서들을 라이센싱하고 설계하는 사업부임
  - IOT 사업부 : 여기서 대부분 그걸 함
- 오픈소스 하드웨어 플랫폼은 3가지가 있음
  - 아두이노
    - 아두이노는 저렴하고 취미로써는 최강의 프로세서
    - 이제 서서히 32bit로 넘어가는 추세임
  - ARM MBED
    - 프리알티오에스
    - 제퍼알티오에스 
    - MBED 를 ESP32에 포팅하는 노력중에 있음
  - 라즈베리파이
    - 오드로이드 등등..
    - 라즈베리파이 칩을 살수 없는데, 이걸 대응하기 위해서는 컴퓨트 모듈같은거를 사다 써야함
- IoT 사업을 시작할때 고려해야 할 사항 4가지
  - 하드웨어 : 스펙선정 컴퓨팅파워, 메모리공간크기, 등등..
  - 소프트웨어 : 보안/디버깅/테스트/안정성
  - 디자인 : 제조, 양산, 인증, RF요소의 인증 제조 (로라 셀룰러..)
  - 서비스 : 어떤 서비스를 제공해야 하는가
- ARM의 개발 복잡도 (임베디드에서) 에서 80퍼샌트를 mbed가 대신해 줄 수 있음.
  - mbed는 빠른 프로토타이핑을 위한 소프트웨어 솔루션임.
  - mbed 솔루션의 장점으로는
    - 타임투 마켓
    - 설계위험 감소
    - 향상된 코드 재 사용성
    - 최첨단 기술에 대한 접근성
- mbed5 -> mbed6로 넘어가면서 가장 큰 변경점은 : 트러스트존 추가(시큐리티 강화), 듀얼코어 아키텍쳐 고려됨
- 전통 RTOS와 mbedOS 의 차이
  - 전통 RTOS : 레고처럼 필요한 SW들을 쌓아 올라감
  - mbedOS : 다 들어가있고 뺴내기만 하면됨, 쌓는것보다는 훨씬 쉬움
# Day1 오후 : 썰풀면서 툴 설치하고 끝냄..
- mbed 툴 사용 1시간, + mbed sim
- mbed CLI 설치하기 2시간
- 주변장치 제어
  - mbed는 iot 디바이스를 만들기 위해 적합한 OS
  - 이를위해서 컴포넌트가 연결이 되어있어
  - 저전력
  - 타이머
  - 튜토리얼들 페리페럴들 공부!!! 그네들을 쓸려면 어떻게 
  - 삼축가속도 센서 
  - trustudio
  - CubeIDE에서 mbedRTOS  :: 하드웨어 (실리콘) 디펜던시 가 없어지므로 NXP쓰다가 내일바로 TI로 넘어갈수 있는 이런 상황임.
- 내일은  
> 리뷰
- 주변환경이 다른 RTOS 대비 도큐먼트 잘되어있음
- 덩치가 너무크고, 업데이트가 너무 자주있어서 불편함.
- ARM이라는 IP 설계회사에서 만든 운영체제라 좋은 기회가 될꺼라고 생각하고
- 온라인 컴파일러는 특별히 어려운거 없이 쓸수 있었다.
- OS 
- 컴파일속도를 빠르게 하기 위해서 온라인에서 컴파일한다.
- LED 깜박거리는거랑 mbed Stduio 까지 씀
- Mbed CLI 도 써봤음
- 어제 CLI 에서 -f (퓨징옵션) 으로 빌드된 이미지를 헥사로 복사할수 있었잖아요 6일전에 버그 리포트! , 롤백을 시도했지만, 잘 안됬어요 
- ARM 도 글로벌로 JIRA를 쓴다 ㅋㅋ
- f 옵션 쓰지말고 카피 명령어로 따로 쓰면 된단다.
- CLI 가지고 퓨징하는데 문제가 있었다는점

# Day2 오전
- APN 주소값(엑세스 포인트 네임) 
- 통신모듈 CAT M1 통신 진행하고 나면 코드는 별게 없다. 설정을 바꿔야지
- 스마트정부 ESP8266 들어감
- ESP8266 버려진거 -> 와이파이모듈 빌트인 -> 디버거가 붙나 해서 메모리가 다 보이는거에요 메모리에 고대로 남아있는거에요 임베디드 장치가 어떤식으로 움직이는지 안다면 누구든지 다 할수 있음.
- 중국에서 만드는 저렴이 MCU
- 텐실리카 ESP32가 몇천불짜리 장비를 이용하면 메모리또한 해킹당할 위험이 있다. 
- 트러스트 펌웨어등 듀얼코어로만들어서 쓰는 이유가 보안에 취약하지않기위함
- 용량을 줄이려면?
  - .git 폴더 삭제, - 브렌치를 따서 시작함.
  - target 
  - ST에서도 안쓰는거 삭제하고(M4 && L4 남기고 다 삭제)
  
- component : 글로벌 잘쓰는것들 넣어놓음 -> 블록디바이스 SD카드 등등등.. 
- 스토리지
  - components\storage\blockdevice ->> 누군가가 만들어놓은것들
  ```
  storage\blockdevice\COMPONENT_QSPIF\mbed_lib.json
  ```
  - 위 경로의 파일을 수정하면 쿼드SPI 
  - 쿼드 SPI 는 이따가 한번 보여드림 ㅎㅎ
  - ESP8266 글로벌 가성비 좋은 와이파이모듈, ESP8266 하나가지고 FreeRTOS 돌아감 ㅎㅎ! 마이크로콘트롤러가 이미 또 들어가있어용
- wifi\esp8266-driver
  - 와이파이에 대한 모든것들이 들어가있음
- mbed-os\features\cellular\framework\targets
  - 제조사 디펜던시한 부분
- \mbed-os\features 경로의 필요한 네트워크 프로토콜들
```
2020-07-27  오후 08:04    <DIR>          .
2020-07-27  오후 08:04    <DIR>          ..
2020-07-27  오후 08:04    <DIR>          cellular
2020-07-27  오후 07:37    <DIR>          cryptocell
2020-07-27  오후 07:37    <DIR>          deprecated_warnings
2020-07-27  오후 07:37    <DIR>          device_key
2020-07-27  오후 07:37    <DIR>          FEATURE_BLE
2020-07-27  오후 07:37    <DIR>          FEATURE_BOOTLOADER
2020-07-27  오후 07:37    <DIR>          FEATURE_EXPERIMENTAL_API
2020-07-27  오후 08:04    <DIR>          frameworks
2020-07-27  오후 07:37    <DIR>          lorawan
2020-07-27  오후 07:37    <DIR>          lwipstack
2020-07-27  오후 07:37    <DIR>          mbedtls
2020-07-27  오후 07:37    <DIR>          nanostack
2020-07-27  오후 08:04    <DIR>          netsocket
2020-07-27  오후 07:37    <DIR>          nfc
2020-07-27  오후 08:04    <DIR>          storage
```
- 그린틱 테스트
- 아이스티 테스트
- 반복해서 테스트 하는 테스트결과가 따로 있어요... 
- 온보트 테스트 : 그린티테스트
- 아이스티 테스트 : 외부연결 테스트 
- 핀에 정의된것
```
C:\Users\DHKim\Mbed Programs\mbed-os-example-blinky\mbed-os\targets\TARGET_STM\TARGET_STM32L4\TARGET_STM32L475xG\TARGET_DISCO_L475VG_IOT01A
```


- PeripheralPinMaps.h 파일을 보면, 핀맵을 바꿀수 있음
```cpp
MSTD_CONSTEXPR_OBJ_11 PinMap PinMap_I2C_SCL[] = {
//  {PB_6,       I2C_1, STM_PIN_DATA(STM_MODE_AF_OD, GPIO_NOPULL, GPIO_AF4_I2C1)}, // Connected to STDIO_UART_TX
    {PB_8,       I2C_1, STM_PIN_DATA(STM_MODE_AF_OD, GPIO_NOPULL, GPIO_AF4_I2C1)}, // Connected to ARD_D15 [I2C1_SCL]
    {PB_10,      I2C_2, STM_PIN_DATA(STM_MODE_AF_OD, GPIO_NOPULL, GPIO_AF4_I2C2)}, // Connected to INTERNAL_I2C2_SCL [VL53L0X_SCL]
    {PB_13,      I2C_2, STM_PIN_DATA(STM_MODE_AF_OD, GPIO_NOPULL, GPIO_AF4_I2C2)}, // Connected to ISM43362_WAKEUP [ISM43362_WKUP]
    {PC_0,       I2C_3, STM_PIN_DATA(STM_MODE_AF_OD, GPIO_NOPULL, GPIO_AF4_I2C3)}, // Connected to ARD_A5 [ADC]
    {NC, NC, 0}
};
```
- 제조사가 정해놓긴 했지만,바꿀수는 있다. 
- 우저메누얼 : 이칩을 사용하기위해 유저가 알아야할 정보들을 나열
- 데이터시트 : 모든 데이터가 정리되어있는거
- 레퍼런스 메뉴얼 :  기준이 되는 메뉴얼
  - 코드 레퍼런스 : 코드의 레퍼런스 등등..
  - 하드웨어 레퍼런스
- API 는 크게 4개
  - 플랫폼 API
  - Drivers API
  - RTOS API
  - 네트워크 API
  - 나머지 : 찾아봐라  
- RTOS : 단위시간(타임 슬라이스), 동시에 많은 일들을 처리, 멀티태스크 일의 단위
- 단위시간당 쓰루풋이 월등한 이유는 멀티테스킹이 돌아가고 있기때문에
- 쓰레드(태스크)를 많이 돌려야하는 이유는, 성능이 뛰어난데, 성능을 잘 활용하기 위해서 
- LED 하나두개 돌리는거쯤이야 그냥 돌리지만, LED로는 상태를 표시하면서, UART같은 통신으로 받
- 반대로, 여러분의 스마트폰이 대기상태에서 카카오톡이 오는걸 못받고, 게임을 돌리면 게임은 하는데, 게임하는도중에 전화오면 못받고, 전화하면서 카카오톡을 못하고.. ->> 노답이쥬?
- 리얼타임 :  실시간성 보장(일정시간 내 무적권 응답)
- 비선점형 커널이란 : 우선순위가 높은애가 무한정 자원을 처묵처묵 
- 비선점형 커널 : 아무리 우선순위가 높더라도 
- 컨텍스트 스위칭
- 네트워크 프로그래밍 -> 뒤에서 쓰레드가 돌아가고 있다(메세지 수신, 알람 팝업!)
- 쓰레드/스케쥴러/뮤텍스/세마포어
- 쓰레드
  - 일시킬때, 
  - MBED는 IDEL, MAIN TIMER
  - 
- 뮤텍스
  - 두개의 스레드가 하나의 공유자원을 쓸때, 문제를 일으키지 않도록, 기다려주는것
  - 자원을 해제하면, 그제서야 다른 스레드가 자원을 쓸수 있도록 권한을 넘겨받음(Release)
  - 대학과정에서 실시간운영체제 가장많은 예시가 화장실, 키가 있는 사람이 먼저들어갔다가, 먼저 쓰고있는사람이 나와야 들어갈수 있는 조건이 된다.
  - 스레드가 뮤텍스를 무한정 가질수 없게 쓰는 키워드도 있음
  - 일반 뮤텍스는 락/ 언락뿐인데, 쓰기직전에 뮤텍스락 다쓰고 뮤텍스 릴리즈
- 예제1번
```cpp
#include "mbed.h"
using namespace ThisThread;

DigitalOut l1(LED1);
DigitalOut l2(LED2);
DigitalOut l3(LED3);
//DigitalOut l4(LED4);

Thread mytrd1;
Thread mytrd2;

void led1_thread() {
    while(true) {
        l1 = !l1;
        sleep_for(100);
    }
}

void led2_thread() {
    while(true) {
        l2 = !l2;
        sleep_for(200);
    }
}

int main()
{
    // Initialise the digital pin LED1 as an output

    mytrd1.start(led1_thread);
    mytrd2.start(led2_thread);
    while (true) {
        l3 = !l3;
        sleep_for(400);
    }
}

```
- 에러가 나서 멈추는걸 보여주고 싶어 뮤텍스가 필요한걸 느껴야됭
### 예제2번
```cpp
#include "mbed.h"
using namespace ThisThread;

DigitalOut l1(LED1);
DigitalOut l2(LED2);
DigitalOut l3(LED3);
//DigitalOut l4(LED4);

Thread mytrd1;
Thread mytrd2;

void notify(const char* name, int state) {
    printf("%s : %d \r\n",name, state);
}

void test_tread(void const *args) {
    while(true) {
        notify((const char*)args, 0);
        //sleep_for(100);
        //wait(1);
        notify((const char*)args, 1);
        //sleep_for(100);
        //wait(1);
    }
}
int main()
{   
    do{
        // Initialise the digital pin LED1 as an output
        mytrd1.start(callback(test_tread, (void *)"TH2"));
        mytrd1.start(callback(test_tread, (void *)"TH3"));
        test_tread((void *)"TH1");
    }while(1);
    
}

```
- 이상하네 죽어야되는데 안죽네.... 이상하다
- 참고로
### 예제3(교안에 나와있는 뮤텍스 죽이기)
```cpp
#include "mbed.h"
Mutex stdio_mutex;
Thread t2;
Thread t3;
void notify(const char* name, int state) {
  stdio_mutex.lock();
  printf("%s: %d\n\r", name, state);
  stdio_mutex.unlock();
}
void test_thread(void const *args) {
  while (true) {
    notify((const char*)args, 0); wait(1);
    notify((const char*)args, 1); wait(1);
  }
}
int main() {
  t2.start(callback(test_thread, (void *)"Th 2"));
  t3.start(callback(test_thread, (void *)"Th 3"));
  test_thread((void *)"Th 1");
}
```
- 아이디가 어떤 쓰레드를 지칭하는지? 점심이후에 말해줌
> 세마포어
  - N개의 공유자원 엑세스 권한, 여러개의 키
  - 화장실 뮤텍스는 1인용이였다면 세마포어는 화장실 N개라는거임
  - 실제로, I2C가 4체널짜리라면, 체널을 할당받아서 HAL이 접근하는거라면, 세마포어가 필요함
```cpp
#include "mbed.h"
Semaphore one_shot(1);

Thread t2;
Thread t3;

void test_thread(void const * name) {
    while(true) {
        one_shot.wait();
        printf("%s \n\r",(const char *)name);
        printf("hi\n\r");
        wait(1);
        one_shot.release();
    }
}


int main(void) {
    t2.start(callback(test_thread,((void *)"THREAD 2")));
    t2.start(callback(test_thread,((void *)"THREAD 3")));

    test_thread((void *)"THREAD 1");
}
```
- 무슨 의도인지 모르겠다..
# Day2 오후
- Platform API는 범용 MCU 관리 인프라, 공통 데이터 구조 및 다양한 표준 라이브러리, 그리고 툴 체인에서 필요
한 일관된 사용자 환경을 제공
- Mbed statistics : 엠베드 사용하는데 필요한 통계정보 : 메모리, 쓰레드정보(아이디 등등..)
### 예제4
```cpp
#include "mbed.h"
#if !defined(MBED_THREAD_STATS_ENABLED)
#error "Stats not enabled"
#endif

#define MAX_THREAD_STATS 0x8

int main(){
    mbed_stats_thread_t *stats = new mbed_stats_thread_t[MAX_THREAD_STATS];
    int count = mbed_stats_thread_get_each(stats, MAX_THREAD_STATS);


    for(int i=0 ; i<count ; i++) {
        printf("ID : 0x%x \n", stats[i].id);
        printf("Name %s \n",stats[i].name);
        printf("State: %d \n",stats[i].state);
        printf("Priority %d \n",stats[i].priority);
        printf("StatckSize %d \n",stats[i].stack_size);
        printf("Stack Space %d \n",stats[i].stack_space);
        printf("\n");
    }
}   
```
- mbed_app.json 파일 추가하고 내용
```json
{
    "target_overrides": {
        "*": {
            "platform.all-stats-enabled":true
        }
    }
}
```
- \mbed-os\platform\mbed_lib.json
- 메모리 통계 예제
```cpp
//Memory statistics example

/*
 * Copyright (c) 2017 - 2020 Arm Limited and affiliates.
 * SPDX-License-Identifier: Apache-2.0
 */

#include "mbed.h"

#define MAX_THREAD_INFO 10

mbed_stats_heap_t heap_info;
mbed_stats_stack_t stack_info[ MAX_THREAD_INFO ];
int main()
{
    debug("\nThis message is from debug function");
    debug_if(1, "\nThis message is from debug_if function");
    debug_if(0, "\nSOMETHING WRONG!!! This message from debug_if function shouldn't show on bash");

    printf("\nMemoryStats:");
    mbed_stats_heap_get(&heap_info);
    printf("\n\tBytes allocated currently: %ld", heap_info.current_size);
    printf("\n\tMax bytes allocated at a given time: %ld", heap_info.max_size);
    printf("\n\tCumulative sum of bytes ever allocated: %ld", heap_info.total_size);
    printf("\n\tCurrent number of bytes allocated for the heap: %ld", heap_info.reserved_size);
    printf("\n\tCurrent number of allocations: %ld", heap_info.alloc_cnt);
    printf("\n\tNumber of failed allocations: %ld", heap_info.alloc_fail_cnt);

    mbed_stats_stack_get(&stack_info[0]);
    printf("\nCumulative Stack Info:");
    printf("\n\tMaximum number of bytes used on the stack: %ld", stack_info[0].max_size);
    printf("\n\tCurrent number of bytes allocated for the stack: %ld", stack_info[0].reserved_size);
    printf("\n\tNumber of stacks stats accumulated in the structure: %ld", stack_info[0].stack_cnt);

    mbed_stats_stack_get_each(stack_info, MAX_THREAD_INFO);
    printf("\nThread Stack Info:");
    for (int i = 0; i < MAX_THREAD_INFO; i++) {
        if (stack_info[i].thread_id != 0) {
            printf("\n\tThread: %d", i);
            printf("\n\t\tThread Id: 0x%08lX", stack_info[i].thread_id);
            printf("\n\t\tMaximum number of bytes used on the stack: %ld", stack_info[i].max_size);
            printf("\n\t\tCurrent number of bytes allocated for the stack: %ld", stack_info[i].reserved_size);
            printf("\n\t\tNumber of stacks stats accumulated in the structure: %ld", stack_info[i].stack_cnt);
        }
    }

    printf("\nDone...\n\n");
}

```
- 스위치 입력을 받는 예제
```cpp
#include "mbed.h"

DigitalIn mypin(USER_BUTTON);
DigitalOut myled(LED1);

int main() {
    if(mypin.is_connected()) {
        printf("OK");
    }

    mypin.mode(PullNone);

    while(1){
        printf("MyPin Valyue : %d \r\n",mypin.read());
        myled = mypin;
        ThisThread::sleep_for(0.25);
    }
}
```
- 복잡한 연산을 ISR에서 한다던가, Delay나 wait를 ISR에서 이런 미친짓을 해버린다면????
답이없다 ..
- LCD 돌리다 실패함
```cpp
#include "mbed.h"
#include "C12832.h"

// Using Arduino pin notation
C12832 lcd(D11, D13, D12, D7, D10);

DigitalIn mypin(USER_BUTTON);
DigitalOut myled(LED1);

int main() {
    int j=0;
    lcd.cls();
    lcd.locate(0,3);
    lcd.printf("mbed application shield!");

    if(mypin.is_connected()) {
        printf("OK");
    }

    mypin.mode(PullNone);

    while(1){
        printf("MyPin Valyue : %d \r\n",mypin.read());
        myled = mypin;
        ThisThread::sleep_for(0.25);
    }
}


int main()
{
    int j=0;
    lcd.cls();
    lcd.locate(0,3);
    lcd.printf("mbed application shield!");

    while(true) {   // this is the third thread
        lcd.locate(0,15);
        lcd.printf("Counting : %d",j++);
        wait(1.0);
    }
}
```
- ADC 예제(with 스택보드)
- https://os.mbed.com/components/mbed-Application-Shield/
```cpp
#include "mbed.h"
// Initialize a pins to perform analog input and digital output fucntions
AnalogIn ain(A0);
DigitalOut dout(LED1);
int main(void)
{
while (1) {
// test the voltage on the initialized analog pin
// and if greater than 0.3 * VCC set the digital pin
// to a logic 1 otherwise a logic 0
if(ain > 0.3f) {
dout = 1;
} else {
dout = 0;
}
// print the percentage and 16 bit normalized values
printf("percentage: %3.3f%%\n", ain.read()*100.0f);
printf("normalized: 0x%04X \n", ain.read_u16());
wait(0.2f);
}
}
```
- 틱타이머 예제 동작
```cpp
#include "mbed.h"
Ticker flipper;
DigitalOut led1(LED1);
DigitalOut led2(LED2);

void flip() {
    led2 = !led2;
}

int main() {
    led2 = 1;
    // the address of the function to be attached (flip) and the
    // interval (2 seconds)
    flipper.attach(&flip, 2.0);
    // spin in a main loop. flipper will interrupt it to call flip
    
    while(1) {
        led1 = !led1;
        wait(0.2);
    }
}

```
- 일랩스드 타임  : 얼마나 시간이 지났는지
```cpp
#include "mbed.h"
Timer t;
int main() {
t.start();
printf("Hello World!\n");
t.stop();
/* 5.15 */
// printf("The time taken was %f seconds\n", t.read());
/* 5.16 */
printf("The time taken was %lld \n\r", t.elapsed_time().count()); //micro seconds
}
```
- 안돌아가네 ㅅㅂ..
```cpp
#include "mbed.h"

I2C i2c(I2C_SDA,I2C_SCL);

const int addr7bit = 0x48;
const int addr8bit = 0x48<<1;

int main() {
    char cmd[2];

    while(1) {
        cmd[0] = 0x01;
        cmd[1] = 0x00;

        i2c.write(addr8bit, cmd, 2);

        wait(0.5);
        cmd[0] = 0x00;
        i2c.write(addr8bit, cmd, 1);
        i2c.read(addr8bit, cmd, 2);

        float tmp = (float((cmd[0] << 8) | cmd[1]) / 256.0);
        printf("Temp : %.2f\n",tmp);
    }
}
```
- 위 예제는 센서가 없어어 안돌아가는 I2c 온도센서 예제
```cpp
#include "mbed.h"

//I2C i2c(I2C_SDA,I2C_SCL);
I2C i2c(PB_11,PB_10);

int main() {
    char cmd = '0';
    bool flag = 1;

    printf("I2C scan test \r\n");
    int addr = 0x00;

    for(int addr=0x00 ; addr<0xff ; addr++) {
        int ack = i2c.write(addr<<1,&cmd,1);
        if(ack == 0 ) {
            if(flag == 1) {
                printf("=> Found addr! \r\n");
                flag = 0;
            }
            printf(" > HEX(8bit):0x%x,  HEX(7Bit):0x%x \r\n",addr,addr>>1);
        }
        thread_sleep_for(100);
    }
    printf("Test Done \r\n");

}
```
- 반토막성능 8비트 스캐너
- 아래는 7비트 스캐너 (정석 굿굿!)
```cpp
#include "mbed.h"

//I2C i2c(I2C_SDA,I2C_SCL);
I2C i2c(PB_11,PB_10);

int main() {
    char cmd = '0';
    bool flag = 1;

    printf("I2C scan test \r\n");
    int addr = 0x00;

    for(int addr=0x00 ; addr<0x7f ; addr++) {
        //int ack = i2c.write(addr<<1,&cmd,1);
        int ack = i2c.read(addr<<1,&cmd,1);
        if(ack == 0 ) {
            if(flag == 1) {
                printf("=> Found addr! \r\n");
                flag = 0;
            }
            printf(" > HEX(8bit):0x%x,  HEX(7Bit):0x%x \r\n",addr,addr>>1);
        }
        thread_sleep_for(77);
    }
    printf("Test Done \r\n");

}
```
- 스캐닝 프로그램에서 Write보다는 Read가 더 안정적임
- 



# Day3 지각함 : 똑바로살아라
- 1시간의  빈칸
- mbed CLI 주요 명령어
  - mbed import mbed-os-example-blinky
  - mbed add https://github.com/ARMmbed/wifi-ism43362
  - mbed deploy
  - mbed sync
  - mbed --help
- printf에 스트링클래스가 쏼아있네!!!
- 
- 
- 
- 
- 
- 
- 
- 
> 2교시
- 네트워크
- 네트워크는 기본적으로 OSI 7계층임
  - 2계층 데이터링크 계층 : 물리계층 ISP 에서 물리적으로 게이트웨이를 만들고 // 네트워크 드라이버
  - 3계층 : ipv4, 6냐 이런거 계층
  - 4계층 : 
- mbed는 관점과 순서의 변화임
  - 과거에는 : A모듈 추가시 데이터시트부터 시작해서 마지막에 돌려 ->> 이걸 어떻게 돌리지?!?!??!?
  - 요즘에는 : 일단예제로 엠베드든 아두이노든 돌려보고 ->> 이게 왜 돌아가지????!?!?!?!?!?
- Wifi 정보
```
SSID

Kiotedu


PASSWORD

kiot1408

``` 
- wifi는 반경 50미터 이내에서만
- sigfox : 불가능
- LoRa망 : SKT에 인내심을 가지고 붙일수 있다? 가장 저렴하다. 글로벌 판매는 불가능
- Celluler : 글로벌 판매시에 가능
- 블루투스 : 
  - 노래방 무선마이크의 출력 주파수가 900mhz 인데 막쏜다-
  - 강남 한복판 가보면 
  - 인증받고나면 마음이 바뀌어서 출력을 최대한 빵빵
  - 블루투스 주파수랑 비슷하거나 체배 주파수대역은 피해를 볼 수 있다
  - 와이파이 체널간섭이 너무 심해서 BLE를 쓴다.
    - 반은 맞고 반은 틀리다
    - 와이파이가 많은곳이 BLE도 많음
    - 한정된 공간 안에 디지털 공간안에 
    - 불루투스랑 와이파이랑 간섭이 생겨 2.4GHz
- 비면허대역/ 면허대역
  - 지그비대역
  - 비면허대역끼리 연결되어있으면 난리가난다
  - 통신이 쉽지가 않아요, 소프트웨어가 난해하지만 무선통신은 거기에다가 물리적으로 해결이 안되는부분이 있어용
  - BLE랑 WiFi가 깔린 칩의 갯수로만 보면 맞다
  - 주류인지 아닌지 판단기준은 칩의 갯수
  - IOT정부지원사업도 많은데 트레커도 많고 많은데 사업이 이루어지는거같지 않거든요
  - 정부에서 밀고있는, 정부가 주도하고있는 국가가 필요한것들은 정부가 진행하지만 ->> 붐을 일으키기 위해서 투자를 하는 돈박아주는 역할이거든요
- 손정의회장이 IoT 팔아먹은거 맞쥬??
- 스마트폰하잖아요?

```

```



```성공했을때 결과
WiFi example
Mbed OS version 5.15.4

Scan:
Network: Kiotedu secured: WPA2 BSSID: 5C:E2:8C:63:34:ff RSSI: -58 Ch: 1
Network: U+Net76DB secured: WPA2 BSSID: 0:27:1C:58:76:d9 RSSI: -87 Ch: 1
Network: U+NetB69F secured: WPA2 BSSID: 0:27:1C:6a:b6:9d RSSI: -88 Ch: 1
Network:  secured: WPA BSSID: 0:27:1C:23:72:20 RSSI: -94 Ch: 1
Network: U+NetCBC3 secured: WPA2 BSSID: 0:27:1C:4a:cb:c1 RSSI: -91 Ch: 1
Network: U+Net7223 secured: WPA2 BSSID: 0:27:1C:23:72:21 RSSI: -91 Ch: 1
Network: Rogers secured: WPA2 BSSID: 70:5D:CC:33:6:c2 RSSI: -76 Ch: 2
Network: 봉군.iphone secured: WPA2 BSSID: 22:1:A8:66:d8:eb RSSI: -69 Ch: 6
Network: donghun's iPhone secured: WPA2 BSSID: AE:AF:57:db:e7:4b RSSI: -34 Ch: 6
Network: iPhone secured: WPA2 BSSID: 4E:F3:1F:99:8c:1e RSSI: -59 Ch: 6
Network: karus secured: WEP BSSID: 0:90:4B:e6:20:10 RSSI: -91 Ch: 6
Network: karus secured: WEP BSSID: 0:90:4B:e6:20:20 RSSI: -87 Ch: 6
Network: kjin_net secured: WPA2 BSSID: 52:77:5:bb:48:9e RSSI: -69 Ch: 11
Network:  secured: WPA2 BSSID: 12:23:AA:b8:65:52 RSSI: -93 Ch: 9
Network: U+Net8C9F secured: WPA2 BSSID: 88:3C:1C:dd:8c:9e RSSI: -85 Ch: 11
15 networks available.

Connecting to donghun's iPhone...
Success

MAC: C4:7F:51:94:24:13
IP: 172.20.10.2
Netmask: 255.255.255.240
Gateway: 172.20.10.1
RSSI: -4


Done
```
- Wifi를 바라보는 관점
  - 기존 사업에서 추가기능 : 
    - 사과모양의 패악질
  - 
- 결국 Wifi로 돈버는게 잘 보이지않는게, Wifi스마트프린터를 산다고해서 
- 어셋트래커는 B2C보다는 B2B가 나오는데, 요쿠르트 아줌마
- 결국 iot 디바이스 꽁자로 주면서 구독형으로 하면
- 스마트폰없이는 살수없지만 Iot가 없어도 잘살고있어요
- 판로를 열려면 기업과기업의 
  - LG와 삼성도 풀지못하는 시장의 
- 센서붙여서 센서 모니터링
- 유비쿼터스에서 IOT 로 이름만 바꾼건데
- IOT에서 넘어가기 위해 구글에서 AI로 IOT에 인공호흡
- 기술트렌드 AIOT 요즘 트렌드는 AIOT입니다
- LED든 센서든 당연히 돌리는데 그걸 어디다 쓸껀데? 그런 생각을 전달해주는 
- 삼성이든 뭐든 AI를 탑재하는 방향이고, 인식해야 돈을 더 지불할꺼잖아요
- 로봇청소기 완젼필수품 
- 똑똑한에어컨 : 몇명있다 사람이 있다 
- 구글홈을 킨 계정에 데이터를 연결시켜서 많이한 이야기의 키워드를 뽑아서 유투브를 올려요, 광고수익으로 직결
- AWS 구글 MS 애플 천조4대장이 사활을 걸고 하고있어
- 쿠키 허락해주세요 
- 테슬라 모델 한번 띄워 줘 
- 유투브 네이버 다음 구글 등등등.. 너나할꺼없이 다 추적하고있어 위치정보 허락안해도 빽도어로 암암리에 
- 페이스북은 틱톡이 한느것보다 훨씬더많은걸 수집하고있어
- 서비스를 하고있는 기업의 나라를 뒷배삼아서 ㄱ 


- 
```
mbed compile --config | grep ISM43362
```
- mbed_config.h
```
```
> 셀룰러
- 아픔과 통곡의 셀룰러 : 셀룰러 맛을 봐야 좋다고 하는데, 쓸수있는환경을 개같이 만들어서 어렵다
- 어떤게 대세인지 모르겠으나, 판매량기준 블루투스가 대세임
- 벤더사들이 와이파이 블루투스 콤보 : 같은 하나의 안테나로 
- 거리와 쓰루풋 기준의 
- 와이파이 롱레인지/ 농촌에서 가리는게 없으면 100m까지는 도달할수 있지만, 이상적인 경우고
- 실사용 우리집 30평이 한계야
- 시그폭스 한국에서 할 생각 하지마라, 글로벌 선박 항공기정도는 가능
- 시그폭스는 프랑스업체에서 모든 권한을 가지고있어서 제품개발 불가능, 칩은 받을수있으나 인증은 받을수없다.
- NB IoT : 협대혁 내로우 아이이오티
- LTE M : LTE 막내격 
- LTE란 : 작은 소형기기에서 LTE는 혼자사는데, 20층 건물을 주는격
- 모듈로 시리얼로 네트워크 이그잼플 그대로 
- 왜 안보여드리는지는 통한의 자료
- 한국에서 쏴도 프랑스에 본사로 들어간다
- LoRa
  - 누구나 솔루션을 개발할수 있다는 ->> SKT가 원하는 그들만의 조건을 만족했을때 SKT님께서 간택해주셨을때만 가능
  - 약간의 주파수변환이 필요해요
  - 밴드위스는 125KHZ에서 8체널
  - 자전거 위치트레커 정도는 보낼수 있다
  - 한국에서 구로구 로라망이있고 금천구망이 있다(IOT업체들이 많아서) : 구디남 가디남..
  - 구로구 금천구 강남구망 쓰고싶으면 주소지를 
- NB IOT
  - LG 유쁠러스 단독
  - 모듈마다 다르지만 저렴하다(구매가 만원 이하, 1K기준)
- LTE CAT M1
  - LG유쁠, SKT
  - 보드를 드리겠지만, 만원이 넘어가요 
- 중요고려 
  - 가격
  - 속도(통신처리량 쓰루풋, 밴드위스)
  - 
- 통신구격
  - 안드로이드는 A R L I : 안드로이드(릴드 드라이버) : 릴드가 뭐냐?라디오 인터페이스
    - 타겟에 삼성이라고 적혀있는 mbed 소스를 참고하시면 릴드 드라이버 구조를 참조할 수 있다. 
  - AT 커맨드
  - PPP : 포인트 투 포인트
- NB_IOT 모듈중 : 
- 오퍼레이터 네트워크 : KT냐 SKT냐 LGU냐
- 셀룰러 모뎀이 진짜 궁극의 구조인데
- non-IP : 프로토콜 변환기, 트렌스레이터, 라즈베리파이가지고 Wifi랑  BLE 변환해주는거
- 어떻게 구현할지 기술적으로 구현하고 네트워크 연결 구조도(토폴로지)에 대한 이야기
- 금천구 지캠프에서 사업공고, 스타트업이나 교육목적으로 비지니스, CAT M1 디바이스 사업의 일환으로 만들어진게 이 보드얌
- SKT CAT.M1 디바이스 
- 수내역 여기가면 LoRa: https://www.sktiot.com/iot/support/openhouse/reservation/openhouseMain
- https://www.sktiot.com/iot/product/catm1/catm1Modem
- LM5 살려면 사업자등록징이 있어야됭, 대당6만원
  - USIM 월단위 금액 모듈가격 6만원
  - 지말토 / 쿽텔
- 글로벌통신사 
- 형상관리 머큐리얼, 젠킨스
- 노키아 스마트자켓
  - CAT M1망을 쓰는데, 이게 만들어지게 된 계기가 소방경찰관, 유조선 엔지니어 긴급구조신호
  - 배는 위성통신을 하는데, 긴급상황시에는 위성통신 배 내부에 Cat M1을 운영할수 있는 이동식 중계기를 
  - 배 내부에는 철판이니까 Cat M1 보다는 철판 통과가 쉬움
  - 배 내부에 음영지역을 없애고 해적공격시 
  - 배 내부에 세이프티룸 
  - 구축비용이 한사람 구조하는데 지출하는 비용보다는 훨씬 싸다
  - 위성통신을 쓰지않아도 되는 이유! Wifi 음영지역 해소하는데 
- 모뎀과의 통신을 디버깅할때 파서가 필요함 AT Paser!!!
- MCU가 제대로된 신호를 보내는지, 모뎀이 바보짓을 하는지 꼭 필요한게 AT 커맨드 파서
- NSAPI : 네트워크 스텍 API
- PLMN : 사업자번호, ISP 고유식별번호 서비스 프로바이더
```
"nsapi.default-cellular-apn": "\"lte-internet.sktelecom.com\"",
```
- PLMN란 사업자의 네트워크 식별번호를 말한다. 해외로밍 서비스 이용 시, 선호하는 사업자의 식별번호를 등록하면 해당 이동통신 사업자의 네트워크로 접속UserPLMn에 등록 가능하며, FPLMN은 이동통신 사업자가 휴대폰 개통 및 로밍시에 작성하여 사용자에게 공급한다
- dsfdsfsd
  ```cpp
  static void trace_wait()
  {
      trace_mutex.lock();
  }

  static void trace_release()
  {
      trace_mutex.unlock();
  }
  ```
- NB IOT 망 사용 규칙
  - NB-IoT 망을 사용하기 위해서는 통신사의 엄격한 단말 품질테스트를 통과하여야 합니다. 동일한 이유로 그동안, 대학 연구소에서 이동 통신망을 사용할 수 있는 기회나 방법이 없었습니다.
  - 이에, 대학 연구소의 순수 개발을 지원하기 위하여 이동통신사의 NB-IoT 상용망의 이용을 제한적으로 허가하는 방법을 마련하였습니다. 
  - 하지만, 개발목적이 아닌 수익사업에 이용하거나 과다 트래픽을 유발할 경우 사용이 제한될 수 있습니다.
  - 악용되는 사례가 많아 질 경우 이용 중단이 결정될 수 있으니 이용 조건을 숙지하시고 모쪼록 금번에 마련된 좋은 기회를 많은 대학 연구실에서 사용할 수 있도록 배려해 주시길 바랍니다. 
  - 사업을 진행하려면, LG U+에서 사업기획서를 보여줘야됨..
- LPWA : : Low Power Wide Area
- 객체지향 상속을 받는다는것
- OOP 객체지향형 프로그래밍 이식성 차이
> DAP Link 시간
- mbed랑 호환이 안되는 보드를 호환시키는 방법
- mbedls
- mbedls --mock 2410:EP_AGORA
- 
- serial_port_plotter : 데이터 비주얼라이제이션
- AWS를 너무쓰는이유 : 보안, 스토리지, 서버증설..., 서버유지보수... 등등-> 이런 고민을 줄여주는게 상용클라우드
  - 사업을 할때 필요한 리소스를 다 마련해놨어, 돈만주고 쓰기만 하면 됨 우왕굿
  - 책임소지에서도 자유로워 클라우드 서비스
  - 가장 큰 나쁜건 비싸요.. aws 의 과금체계 : 기하급수적으로 올라가 
  - 머신러닝 솔루션도 제공해주면 가져다 쓰면 됨
  - 펠리온은 간단해요 디바이스를 위해서만 존재함
  - 어떤 서비스를 구독하느냐에 따라 다름
    - 싸스 파스 이아스 온프라미스
> IOT 프로토콜
- ARM에서는 CoAP : UDP 계열
- 아마존이랑 MS는 MQTT : 아마존, 에저에서 MQTT를 쓰고 있다, TCP베이스
- M2M 계열
- XMPP : 아는바가 없음.., 실제 유즈케이스..?
- MQTT : 살짝 오버헤드가 있음.., 과금의 덧에 걸릴수 있지만, Wifi같은 과금문제가 없으면 .. ㅋ..
  - 브로커, 퍼블리셔, 서스크립션
  - IPSO
- lwM2M : 
- CoAP는 프로토콜을 맞춰줘야 됨
- LWM2M은 프로토콜이 정해져있음.
- IoT 설정을
  - 와이파이설정