# 0과 1로 숫자를 표현하는 방법

컴퓨터가 이해할 수 있는 정보의 단위와 그리고 이진법에 대해서 학습해보자

## 정보 단위

컴퓨터가 이해할 수 있는 가장 작은 정보의 단위는 0과 1을 나타낼 수 있는 비트(bite)이다.

- 전구의 off과 on에 비유하면 이해하기 편하다.
- $2^n$으로 정보를 표현할 수 있다.

### 정보 단위 표현

1. 1byte = 8 bite
2. 1kb = 1000byte
3. 1mb = 1000kb
4. 1GB = 1000mb
5. 1TB = 1000GB

### 참고

워드 : CPU가 한 번에 처리할 수 있는 데이터 크기. 현대 컴퓨터는 대부분 32bite or 64bite의 크기를 가진다.

## 이진법

0과 1만으로 숫자를 표현하는 방식

### 이진수의 음수 표현

2의 보수법을 사용한다.

- 어떤 수를 그보다 큰 $2^n$에서 뺀 값’
- 하지만 훨씬 쉬운 방법으로 이진법의 0과1을 뒤집고 1을 더해주기만 하면 완성된다.
- 2의보수를 음수로 나타내고 그 음수를 다시 보수법으로 바꿔주면 원래의 값이 된다.

하지만 1011을 표현한 음수 0101과 십진수 5를 표현하는 0101은 똑같다. 구분할 수가 없다. 그래서 컴퓨터 내부에서는 플래그를 사용한다.

## 십육진법

이진법만으로 모든 숫자를 표현하려면 너무나 길어진다는 단점이 있다.

그래서 십육진법을 사용하는데 그 이유는 십육진법과 이진법은 서로 변환하기 쉽기 때문이다.

### 십육진수를 이진수로 변환하기

예를들어 1A2B라는 16진수가 있다. 

각 16진수는 4비트를 차지하므로 각각을 2진수로 변환하면

0001 1010 0010 1011이 되는데 이것을 그저 붙여주기만 하면 이진수로 변환이 완료된다.

### 이진수를 십육진수로 변환하기

방금 전 변환된 0001101000101011을 네개씩 끊고, 각각을 16진수로 변환한 다음 붙여주면 완료된다.

# 0과 1로 문자를 표현하는 방법

## 문자 집합과 인코딩

문자 집합 : 컴퓨터가 인식할 수 있는 문자의 모음

문자 인코딩 : 문자 집합의 문자를 컴퓨터가 이해할 수 있게, 0과 1로 변환하는 작업

문자 디코딩 : 0과 1로 표현된 문자를 사람이 이해할 수 있게 변환하는 작업

## 아스키 코드

- 초창기 문자 집합 중 하나이다.
- 영어 + 아라비아 숫자 + 특수문자
- 총 7비트를 쓴다. (8비트를 쓰지만 그 중 1비트는 오류 검출을 위해 사용하는 패리티 비트)
- $2^7$인 128가지의 문자를 표현할 수 있다.
- 하나의 고유한 수에 각 문자가 대응된다.

### 단점

- 128개는 여러 언어를 표현하기에는 너무 적다. 이후 1비트를 추가한 확장 아스키가 나왔지만 여전히 적은 것은 동일하다.
- 그래서 각 나라는 0과 1로 표현할 수 있는 고유한 문자 집합과 인코딩 방식을 만들기 시작한다.

## EUC-KR

- 대표적인 완성형 인코딩 방식
- 초성, 중성, 종성이 결합되어 하나의 문자와 고유한 숫자가 대응
- 한 글자당 2Byte를 먹는다. 16비트이기에 4비트를 먹는 16진수 네개를 사용하여 표현한다.

### 단점

- 총 2,350개 정도의 한글 단어를 표현할 수 있지만, 한글을 표현하기에는 부족하다.
    - 한글이 깨진다던지, 은행, 학교등에서 피해를 보기 시작했다.
- 마이크로소프트의 CP949가 등장했지만, 여전히 한글을 표현하기에는 부족했다.

## 유니코드와 UTF-8

유니코드 : 각 나라의 언어 문자 집합이 통일된 것. 가장 많이 사용되는 표준 문자 집합

UTF-8 : 유니코드를 인코딩하는 방식 중 하나 

### UTF-8 방식

UTF-8은 통상 1바이트부터 4바이트까지의 인코딩 결과를 만들어 낸다. 1~4중 어느 것이 될지는 유니코드 문자에 부여된 값의 범위에 따라 결정된다.

- 대부분의 문자들은 3바이트에 있고 한글도 그렇다.
- 유니코드로 ‘한’ D55C ‘글’ AE00 이것들을 2진수로 변환한 다음 3바이트 유니코드를 인코딩 하는 3번째 공간의 XXXX에 붙여넣어주기만 하면 끝난다.
