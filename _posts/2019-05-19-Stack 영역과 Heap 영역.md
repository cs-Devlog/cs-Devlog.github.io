---
title: Stack 영역과 Heap 영역
date: 2019-05-19- 17:00:00
description: Java에서 Stack 영역과 Heap 영역에 대해 알아보자
categories:
- Java
tags: 
- Java
- Stack Area
- Heap Area
---
# Stack 영역
- 메소드 지역 변수를 Stack 형식으로 임시 할당하고, 해당 메소드가 종료되면 Stack 에서 전부 제거된다.
- 원시타입 변수(byte, short, int, long, float, double, char, boolean)만 Stack에 저장된다.
- 원시타입을 제외한 참조 변수의 경우 Heap 영역에 생성된 Object 주소값이 저장된다.

# Heap 영역
- Java에서 new 명령을 통해 생성된 인스턴스 변수가 놓인다.
- 모든 Object 타입(Integer, String, ArrayList, ...)은 heap 영역에 생성된다.
- Stack에 참조변수로 저장되어 Heap 영역에 Real Value가 저장되고 Stack 영역에는 주소값만 저장된다.
- GC에 의해 지위지지 않는 이상 Heap 영역에 계속 남아있다.

~~~java
public class Main {
    public static void main(String[] args) {
        int port = 4000;            //원시타입 변수이므로 Stack 영역에 저장
        String host = "localhost";  //인스턴스 변수이므로 Heap 영역에 실질적인 값이 저장되고 Stack에 해당 주소값이 저장
    }
}
~~~
위와 같은 코드가 있다고 가정했을 때, 해당하는 Stack 영역과 Heap 영역은 다음과 같다.

![memory](/assets/images/memory.png)

- Stack 영역에는 Heap 영역에 생성된 Object 타입의 데이터 참조값이 할당된다.
- 만약, 여기서 host += :8080 이라는 코드를 추가하면, localhost에 값이 추가되는 것이 아니라 localhost:8080 라는 새로운 String Object가 할당되어 참조하게 된다.
- 즉, localhost는 unreachable 객체가 되어 GC에 의해 메모리에서 제거된다.

- 참고 : <https://yaboong.github.io/java/2018/05/26/java-memory-management/>