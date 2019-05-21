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
- 프로그램 실행 과정에서 메소드 실행 시 임시로 할당되고 해당 메소드가 끝나면 바로 소멸되는 것들이 저장된다.
- Heap 영역에 생성된 Object 타입의 데이터의 참조값이 할당된다.

# Heap 영역
- Java에서 new 명령을 통해 생성된 인스턴스 변수가 놓인다.
- 모든 Object 타입(Integer, String, ArrayList, ...)은 heap 영역에 생성된다.
- GC에 의해 지위지지 않는 이상 Heap 영역에 계속 남아있다.

~~~java
public class Main {
    public static void main(String[] args) {
        int port = 4000;
        String host = "localhost";
    }
}
~~~
위와 같은 코드가 있다고 가정했을 때, 해당하는 Stack 영역과 Heap 영역은 다음과 같다.

![memory](/assets/images/memory.png)

- Stack 영역에는 Heap 영역에 생성된 Object 타입의 데이터 참조값이 할당된다.
- 만약, 여기서 host += :8080 이라는 코드를 추가하면, localhost에 값이 추가되는 것이 아니라 localhost:8080 라는 새로운 String Object가 할당되어 참조하게 된다.
- 즉, localhost는 unreachable 객체가 되어 GC에 의해 메모리에서 제거된다.

- 참고 : <https://yaboong.github.io/java/2018/05/26/java-memory-management/>