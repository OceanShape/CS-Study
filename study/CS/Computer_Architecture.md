**Computer Architecture**
[Computer Architecture](https://gyoogle.dev/blog/computer-science/computer-architecture/컴퓨터의%20구성.html)

# [컴퓨터의 구성 & 중앙처리장치(CPU) 작동 원리 (예빈)]

## 1)하드웨어가 어떻게 구성되어 있는지 설명해주세요. 

    하드웨어는 중앙처리장치(CPU), 기억장치, 입출력장치로 구성되어 있다.

    이들은 시스템 버스로 연결되어 있으며, 시스템 버스는 데이터와 명령 제어 신호를 각 장치로 실어나르는 역할을 한다.

## 2)데이터 버스, 주소 버스, 제어 버스에 대해 각각 설명해주세요. 

    # 데이터 버스
    중앙처리장치와 기타 장치 사이에서 데이터를 전달하는 통로

    기억장치와 입출력장치의 명령어와 데이터를 중앙처리장치로 보내거나, 중앙처리장치의 연산 결과를 기억장치와 입출력장치로 보내는 '양방향' 버스임

    # 주소 버스
    데이터를 정확히 실어나르기 위해서는 기억장치 '주소'를 정해주어야 함.

    주소버스는 중앙처리장치가 주기억장치나 입출력장치로 기억장치 주소를 전달하는 통로이기 때문에 '단방향' 버스임

    # 제어 버스
    주소 버스와 데이터 버스는 모든 장치에 공유되기 때문에 이를 제어할 수단이 필요함

    제어 버스는 중앙처리장치가 기억장치나 입출력장치에 제어 신호를 전달하는 통로임

    제어 신호 종류 : 기억장치 읽기 및 쓰기, 버스 요청 및 승인, 인터럽트 요청 및 승인, 클락, 리셋 등

    제어 버스는 읽기 동작과 쓰기 동작을 모두 수행하기 때문에 '양방향' 버스임

## 3)CPU의 동작 과정 대해 설명해주세요. 

    1. 주기억장치는 입력장치에서 입력받은 데이터 또는 보조기억장치에 저장된 프로그램 읽어옴

    2. CPU는 프로그램을 실행하기 위해 주기억장치에 저장된 프로그램 명령어와 데이터를 읽어와 처리하고 결과를 다시 주기억장치에 저장

    3. 주기억장치는 처리 결과를 보조기억장치에 저장하거나 출력장치로 보냄

    4. 제어장치는 1~3 과정에서 명령어가 순서대로 실행되도록 각 장치를 제어
    

# [캐시 메모리(수현)]
## 1. 캐시메모리는 뭐고 언제 활용할까요?
```
- 캐시메모리: 메인메모리와 CPU 간의 데이터 속도 향상을 위한 중간버퍼 역할을 하는 메모리
- CPU 코어와 메모리 사이의 병목 현상 완화
```

## 2. 캐시메모리는 어떤 원리로 작동될까요?
```
1. 시간 지역성: 한번 참조된 데이터는 잠시후 참조될 가능성 이있음
2. 공간 지역성: 연속젒근시, 근처데이터에 있는데이터가 참조될 가능성이 있음
```

## 3. 언제 캐시미스가나고 어떻게 해결할까요?
```
1. cold miss: 해당 메모리를 처음 불러스 나는 미스
2. conflict miss: 캐시 메모리의 같은 주소에 서로 다른 데이터가 있는 경우
3. 캐시 메모리 공간이 부족해서 나는 미스
```

# [고정소수점 & 부동소수점 (수현)]
## 1. 고정 소수점이 무엇일까요?
```
소수점이 찍힐 위치를 미리 정해놓고 소수를 표현하는 방식
표현 범위가 너무 적음
```

## 2. 부동 소수점이 무엇일까요?
```
지수에 값에따라 소수점이 움직이는 방식을 활용한 실수표현
수의 범위가 넓어지지만 오차가 발생할 수 있음
-133.623의 부동소수점 표현방식
1. 이진수 표현방식 
    - 부호부:1
    - 절대값을 이진법 으로 나타내면 :1110110.101
    - 소수점을 왼쪽으로 이동시키는경우: 1.110110101×2⁶
    - 가수(소수점 exp)의 부분에서 부족한 부분0으로 채움11011010100000000000000
    - 지수부분(2⁶에서 6) + bias (2^(K-1)-1)하면 133이므로 
    - 1,10000101,11011010100000000000000가됨
    - python에서도 부동소수점을 사용하고 있지만 실제로 정확한 값은 아님(거의 같지는 않음)
    >>> .1 + .1 + .1 == .3
        False
```

 # [패리티비트 & 해밍코드 (지안)]

## 1) 패리티비트란 무엇인가요?

    → 정보 전달 과정에서 오류가 생겼는 지 검사하기 위해 추가하는 비트
       전송하고자 하는 데이터의 각 문자에 1비트를 더하여 전송
       
## 2) 해밍코드란 무엇인가요?

    → 데이터 전송 시 1비트의 에러를 정정할 수 있는 자기 오류정정 코드
     패리티비트를 보고, 1비트에 대한 오류를 정정할 곳을 찾아 수정할 수 있다. 
    (패리티 비트는 오류를 검출하기만 할 뿐 수정하지는 않기 때문에 해밍 코드를 활용)

    ```
    1비트의 에러를 정정할 수 있는 자기 오류 정정코드
    0111001 일때 홀수 패리티로 가정
    1,3,5,7: 0101 ==> 짝수로 에러 
    2,3,6,7: 1101 ==> 홀수로 OK
    4,5,6,7: 1001 ==> 짝수로 에러
    101 ==> 5 숫자 다섯번째가 에러난것음
    0111101 
    ```