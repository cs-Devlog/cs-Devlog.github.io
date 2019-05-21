---
title: ArrayList와 LinkedList
date: 2019-05-21- 14:00:00
description: ArrayList와 LinkedList의 시간복잡도에 대해 알아보자.
categories:
- 자료구조
tags: 
- 자료구조
- ArrayList
- LinkedList
- 시간복잡도
---
# ArrayList와 LinkedList
ArrayList와 LinktedList 둘다 모두 Java에서 제공하는 List 인터페이스를 구현한 Collection 구현체이다.

하지만 내부적으로 작동하는 방식은 다르다.

~~~java
import java.io.*;
import java.util.*;
 
public class Main {
    public static void main(String[] args) throws Exception {
        ArrayList<String> alist = new ArrayList<>();
        alist.add(0,"First");           //O(1)
        alist.add("Third");             //O(1)
        alist.add(1, "Second");         //O(n)
        alist.remove(1);                //O(n)
 
        alist.get(1);                   //O(1)
 
        LinkedList<String> nlist = new LinkedList<>();
        nlist.addFirst("First");        //O(1)
        nlist.add("Second");            //O(1)
        nlist.addLast("Third");         //O(1)
        nlist.pollFirst();              //O(1)
        nlist.pollLast();               //O(1)
 
        nlist.get(0);                   //O(n)
    }
}
~~~

***

## ArrayList
알고리즘 문제를 풀면서 가장 중요한 ArrayList와 LinkedList의 차이점은 시간복잡도의 차이라고 볼 수 있다.

ArrayList는 동적으로 Array를 생성한다고 생각하면 배열과 비슷한 점이 많다.

ArrayList는 remove 시에 O(n)의 시간복잡도를 가진다.

i번째 배열을 지우고 최대 n만큼 앞으로 이동해야 하기 때문이다.


< ArrayList 중간 Insert >
![11st_result](/assets/images/ArrayList_insert.png){: width="500"}

< ArrayList 중간 Remove >
![11st_result](/assets/images/ArrayList_insert.png){: width="500"}

삽입 또한 맨 뒤에삽입과 중간삽입으로 나눌 수 있는데, 중간에 삽입하는 경우 O(n), 맨 뒤에 삽입하는 경우 O(1)의 시간복잡도를 가진다.

하지만 get 메소드는 해당 index를 바로 가져오기 때문에 O(1)의 시간복잡도를 가진다.

## LinkedList

< LinkedList 중간 add >
![11st_result](/assets/images/LinkedList_add.png){: width="500"}

이에 비해, LinkedList는 Node를 사용하기 때문에 add, poll 시에 O(1)의 시간복잡도를 가진다.

하지만 get 메소드 사용시에 앞에서부터 찾기 때문에 O(n)의 시간복잡도를 가진다.

***

# 정리

||ArrayList|LinkedList|
|:----:|:---:|:---:|
|삽입|add<br>O(1) or O(n)|add, addFirst, addLast<br>O(1)|
|삭제|remove<br>O(n)|poll, pollFirst, pollLast<br>O(1)|
|접근|get<br>O(1)|get<br>O(n)|