---
title: Java - Coding Test 정리
tags: algorithm java
key: page-202010061836
summary : 자주 쓰이는 문법들 정리하기 + 계속 추가하기
aside:
  toc: true
---
# :heavy_check_mark: Coding Test Study Memo :pencil2::page_facing_up:
자주 쓰이는 문법들 정리하기 + 계속 추가하기
<br/>
<br/>

## 형변환
### int to String
```javascript
int i = 100;
String s = Integer.toString(i);
```

### char to String
```javascript
char c = 'A'
String s = Character.toString(c);
```

### String to int
```javascript
String s = "123";
int i = Integer.parseInt(s);
```

### String to double
```javascript
String s = "123";
double d = Double.parseDouble(s);
```

### Array to List
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

## HashSet
```javascript
HashSet<Integer> hs = new HashSet<>();
for (int i : nums) {
    if ( hs.contains(i)) {
        hs.remove(i);
        //hs.clear();//모든 값 제거
    } else {
        hs.add(i);
    }
}
return hs.iterator().next();
```
- hs.add(i) : 값 추가
- hs.remove(i) : 값 제거
- hs.clear() : 모든 값 제거
- hs.contains(i) : i 값이 있는 지 여부
- hs.iterator().next() :  Iterator iter = hs.iterator(); 사용, 값 출력

```javascript
HashSet<Integer> set = new HashSet<Integer>(Arrays.asList(1,2,3));//HashSet생성

System.out.println(set); //전체출력 [1,2,3]

Iterator iter = set.iterator();	// Iterator 사용
while(iter.hasNext()) {//값이 있으면 true 없으면 false
    System.out.println(iter.next());
}
```

## 문자열 찾기
### indexOf
```javascript
String text = 'hello world!';

text.indexOf("hello");
```
- 값이 없을때 -1 반환
- 값이 있을때 첫 index 반환

## 문자열 붙이기
String += 보다는 StringBuilder 와 StringBuffer 사용 <br/>
String의 주소값이 stack에 쌓이고 클래스들은 Garbage Collector가 호출되기 전까지 heap에 지속적으로 쌓이게 된다. <br/>
메모리 관리적인 측면에서는 비효울이다.
### StringBuilder
```javascript
StringBuilder sb = new StringBuilder();
stringBuilder.append("hello");
String s = sb.toString();
```
### StringBuffer
```javascript
StringBuffer sf = new StringBuffer();
stringBuilder.append("hello");
String s = sf.toString();
```
StringBuilder는 synchronization이 적용되지 않는다.

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

## 대소문자 변환
```javascript
String s = "Hello"
s.toLowerCase(); // 모두 소문자로
s.toUpperCase(); // 모두 대문자로
```

## 정규표현식
### 숫자와 영문 빼고 "" 처리
```javascript
String s = s.replaceAll("[^A-Za-z0-9]", "");
```
### 왼쪽에 붙은 0 제거
```javascript
String s = s.replace(/(^0+)/, "");
```

## XOR 연산자
배열에서 중복되는 숫자가 없는 값 return
```javascript
int res = 0;
for(int num : nums) {
    res ^= num;
}
return res;
```
<b>xor의 3 가지 속성</b> <br/>
1) 교환 연산 (즉 a xor b = b xor a). <br/>
2) xor 자체가 0이라는 것. a xor a = 0. <br/>
3) 0 xor a = a. <br/>

## ListNode


```
<br/><br/><br/><br/>
