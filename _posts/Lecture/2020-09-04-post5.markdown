---
layout: post
title: Embedded Software 실습
date: 2020-09-04 11:00:00 +0900
category: Lecture
---

# EMBEDDED SOFTWARE 실습 :)

> ### 개요
* low level에서 bit 조작을 하기 위함
  * device driver 작성
  * 픽셀 레벨의 그래픽 프로그래밍
* high-level programmer는 해당 프로그래밍 기술을 사용하지 않지만, device driver는 필요

> ### Bit-wise operators
* AND(&) : 두 개의 비트가 모두 1일 때 1, 하나라도 0이면 0
  * 1. testing bit
    * ```ruby
if (*pTimerstatus & 0x08) {
    0이 아닌 수가 나오면, 세번째 bit가 1
    0인 수가 나오면, 세번째 bit가 0
} ```
  * 0x08 = 00001000
  * 2. Clearing bit
    * ```ruby
    *pTimerstatus &= ~(0x04) ```
    * 두 번째 비트만 0으로 세팅
* OR(|) : 두 개의 비트가 모두 0일 때 0, 하나라도 1이면 1
  * 어떤 bit를 1로 셋팅할 때 사용
    * ```ruby
    *pTimerstatus |= 0x10; ```
    * 어떤 비트 C|1000000 이면 7번째 비트가 무조건 1로 바뀌며, 나머지 비트는 어떤 값이든 상관 없이 그대로 유지
    * C | 0x80 과 동일
* Exclusive OR(^) : 두 비트가 다른 경우 1, 같은 경우 0
  * 어떤 비트를 토글링
  * 0과 토글링하면 원래의 수 유지!
    * 1^0=1 0^0=0
* Complement(~) :  한 비트를 토글링
* Shift operator
  * Left Shift operator(<<)
  * Right Shift operator(>>)

> ### Bit value
* 해당 비트를 1로 표현하는 것
* 대체로 16진수로 변환해줌

> ### Bit manipulation
* 임베디드 프로세서는 peripheral device에 내장된 register를 통해 통신
* register는 memory-mapping이 되어 있음
  * 포인터 변수처럼 다룰 수 있는 수단
  * 각 레지스터는 그것의 주소를 가지고 있음
  * 각 레지스터가 갖고 있는 주소를 포인터 변수를 사용하여 해당 레지스터에 접근(읽고 쓰기) 가능
1. testing bit
  * ```ruby
if (*pTimerstatus & 0x08) {
    0이 아닌 수가 나오면, 세번째 bit가 1
    0인 수가 나오면, 세번째 bit가 0
} ```
  * 0x08 = 00001000
2. Setting bit
    * ```ruby
    *pTimerstatus |= 0x10; ```
3. Clearing bit
  * ```ruby
  *pTimerstatus &= ~(0x04) ```
  * 두 번째 비트만 0으로 세팅
4. Toggling bit
   * ```ruby
  *pTimerstatus ^= 0x80; ```
  * 일곱 번째 비트를 토글링
  *  ~(0x80) = 1000000
5. Bitmask : bitwise 연산자와 함께 사용하기 위해 도입이 된 함수
  * 가독성을 높이기 위함
6. Bitmask Macro


> ### Programming exercise
