---
title: Java - Coding Test 정리
tags: algorithm java
key: page-202010061836
summary : 자주 쓰이는 문법들 정리하기 + 계속 추가하기
aside:
  toc: true
---
# :pencil2:  Coding Test 알아두면 좋은 문법! 정리 :thumbsup::sparkles:
자주 쓰이는 문법들 정리하기 + 계속 추가하기
<br/>
<br/>

## int to String
```javascript
int i = 100;
String s = Integer.toString(i);
```

## String to int
```javascript
String s = "123";
int i = Integer.parseInt(s);
```

## String to double
```javascript
String s = "123";
double d = Double.parseDouble(s);
```

## Array to List
```javascript
import java.util.Arrays;
import java.util.List;

Integer[] result = {0,8,0,1};
List<Integer> relist = Arrays.asList(result);
```
## sort
### array
```javascript
Arrays.sort(arr);
```

## reverse
### List
```javascript
import java.util.Arrays;
import java.util.Collections;

Integer[] result = {0,8,0,1};
Collections.reverse(Arrays.asList(result));
```

### 문자열
```javascript
String s = "abcd"
s = new StringBuilder(s).reverse().toString();
```

## Stack
```javascript
import java.util.Stack;

Stack stack = new Stack<>();

stack.push(0);
stack.pop();

while(!stack.empty()){
    stack.pop();
}
```

## Map
```javascript
import java.util.HashMap;
import java.util.Map;

Map<Character, Character> map = new HashMap<>();
map.put('key', 'value');

if (map.containsKey('key')) {
    map.get('key');
}
```
- map.containsKey('key') : 키 값('key')이  있는 지 여부

## 문자열 찾기
### indexOf
```javascript
String text = 'hello world!';

text.indexOf("hello");
```
- 값이 없을때 -1 반환
- 값이 있을때 첫 index 반환


## 문자열 자르기

### substring
```javascript
String str = "HAPPYCODING";

str.substring(2) // 결과 : PPYCODING
str.substring(2,6) // 결과 : PPYCO
```
- str.substring(start) : start부터 끝까지  자르기
- str.substring(start,end) : start부터 end까지만 빼고 자르기
- index는 0부터시작

### charAt
```javascript
String str = "HAPPYCODING";

char c1 = str.charAt(0); // 결과 : H
char c2 = str.charAt(3);  // 결과 : P
```
- str.charAt(index) : index위치에 있는 값 반환
- char 타입으로 반환
- index는 0부터시작

## 이분탐색 (Arrays API)
```javascript
int x = Arrays.binarySearch(nums, target);
```
- 배열에 존재하는 숫자는 해당 위치를 양수로 반환 (0부터)
- 배열에 존재하지 않는 숫자는 아닌배열에서 자기위치를 찾아 음수로 반환 (-1 부터)

```javascript
Arrays.sort(arr);
```
- 오름차순으로 정렬된 배열에만 사용 가능
https://code0xff.tistory.com/68

## 숫자 비교
```javascript
Math.max(10, 20); // 결과 : 20
Math.min(10, 20); // 결과 : 10
```
- Math.max : 두 값 중 큰 숫자 반환
- Math.min : 두 값 중 작은 숫자 반환


## ListNode


```
<br/><br/><br/><br/>
