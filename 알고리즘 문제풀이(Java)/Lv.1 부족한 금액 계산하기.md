# Lv. 1 부족한 금액 계산하기

[출처]<https://school.programmers.co.kr/learn/courses/30/lessons/82612>

## 문제

새로 생긴 놀이기구는 인기가 매우 많아 줄이 끊이질 않습니다. 이 놀이기구의 원래 이용료는 price원 인데, 놀이기구를 N 번 째 이용한다면 원래 이용료의 N배를 받기로 하였습니다. 즉, 처음 이용료가 100이었다면 2번째에는 200, 3번째에는 300으로 요금이 인상됩니다.
놀이기구를 count번 타게 되면 현재 자신이 가지고 있는 금액에서 얼마가 모자라는지를 return 하도록 solution 함수를 완성하세요.
단, 금액이 부족하지 않으면 0을 return 하세요.

## 내 풀이

```java
class Solution {
    public long solution(int price, int money, int count) {
        long sum = 0;
        long result = 0;
        for(int i=1; i<=count ; i++){
            sum += i * price;
        }
        if(sum>money) {
            result=sum-money;
        }else{
            result = 0;
        }
        return result;
    }
}
```

**문제점** : for문으로 누적 합을 구하게 되면 시간복잡도 **O(n)**  
count가 커질수록 반복 횟수가 많아짐

## 등차수열의 합 사용한 풀이

```java
class Solution {
    public long solution(int price, int money, int count) {
        long sum = 0;
        long result = 0;
        sum = (long)price * (count*(1+count))/2;

        if(sum>money) {
            result=sum-money;
        }else{
            result = 0;
        }
        return result;
    }
}
```

시간복잡도 : O(1);
어떤 count가 오더라도 **한 번**만 수행

## 다른 사람 풀이

```java
class Solution {
    public long solution(long price, long money, long count) {
        return Math.max(price * (count * (count + 1) / 2) - money, 0);
    }
}
```

Math.max( a , b )  
a와 b 중 더 큰 값을 반환
