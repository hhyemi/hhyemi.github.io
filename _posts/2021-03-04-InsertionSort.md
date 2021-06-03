---
title: Algorithm - 삽입정렬(Insertion Sort)
tags: Algorithm TIL
key: page-202103041950
summary: 지정한 자리에 데이터를 삽입하여 정렬하는 알고리즘
---

## 삽입정렬이란?

**앞에요소들을 비교하여** 자신(key값)보다 큰 값을 만날때 큰 값을 뒤 index로 복사 후 **자신(key값)보다 작은 값을 만날때까지 반복**하는 알고리즘이다.
자신(key값)보다 **작은 값을 만났을때 바로뒤에 자신(key값)을 삽입**한다.
<br/><br/>

<img src="/assets/images/insertion-sort.png" />

[https://visualgo.net/ko/sorting](https://visualgo.net/ko/sorting)을 참고하면 영상으로 볼 수 있다.

- 두 번째 index부터 왼쪽 데이터와 비교한다.
- 1회전 : 5를 key값으로 두면 왼쪽데이터인 8과 비교를한다. 해당key값이 더 작기때문에 8은 뒤 index로 이동하게 되고 더 비교할 대상이 없으니 8앞에 5를 삽입하게 된다.<br/>
- 2회전 : 2회전도 똑같이 비교하는데 이번에는 8를 뒤로 이동하고 앞에 비교대상 5가 있으니 또 비교하게된다. <br/>
  이렇게 비교대상이 앞에 있을때 까지 비교하고 데이터를 삽입하는 것을 반복한다.<br/>
- 만약 삽입이 일어나면 앞에 데이터는 비교하지 않아도된다.<br/>

## JavaScript

```javascript
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    let j = i - 1;
    let temp = arr[i];
    while (j >= 0 && arr[j] > temp) {
      arr[j + 1] = arr[j];
      arr[j] = temp;
      j--;
    }
  }
  return arr;
}

console.log(insertionSort([5, 4, 3, 2, 1]));
```

- 첫번째 for문은 `let i = 1`인 이유는 두 번째 index부터 시작하기 때문이다.
- `let j = i - 1;` key의 왼쪽 전 index부터 시작한다.
- `let temp = arr[i];` temp의 key값을 넣어준다.
- `while (j >= 0 && arr[j] > temp) {` 여기서 `j>=0`은 index가 0인 곳 까지만 하기위함이고 `arr[j] > temp`은 key값이 비교대상보다 작을때 삽입을 하기위한 조건이다.
- `j--;` index를 줄여 앞으로 비교하게 한다.
  <br/>
  <br/>

**:white_check_mark: 참고하면 좋은 코드**

```javascript
function insertionSort(arr, length = arr.length) {
  for (let i = 1; i < length; i++) {
    let temp = arr[i];
    let j;
    for (j = i - 1; j > -1 && arr[j] > temp; j--) {
      arr[j + 1] = arr[j];
    }
    arr[j + 1] = temp;
  }
  return arr;
}

console.log(insertionSort([8, 5, 6, 2, 4])); // [2, 4, 5, 6, 8]
```

while문 대신 for문에 조건을 넣어서 이용한 코드이다. <br/>
for문동안 비교 반복을 한 후 for문이 끝나면 삽입해주는 코드이다. <br/>

## 시간복잡도

- 최악의 경우 : 정렬이 하나도 안 되어있는 경우 **O(n^2)**
- 최선의 경우 : 완전 정렬되어있는 경우 **O(n)**

## 장점, 단점

**:heavy_check_mark: 장점**

- in place 알고리즘이기 때문에 메모리가 절약된다.
  > "in place"라는 것은 자료를 정렬할 때 추가적인 메모리 공간이 필요한 것이 아니고 데이터가 저장된 그 공간 내에서 정렬을 한다는 뜻
- 최선의 경우 O(N)이라는 빠른 효율성을 가지고 있다.
- 성능이 좋아서 다른 정렬 알고리즘의 일부로 사용된다.
- 안정 정렬(Stable Sort)이다.

**:heavy_check_mark: 단점**

- 배열의 크기가 크면 시간이 오래걸리고 이동이 많다.

<br/><br/><br/><br/>
참고자료 : [https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html](https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html) <br/>
참고자료 : [https://yabmoons.tistory.com/250](https://yabmoons.tistory.com/250) <br/>
참고자료 : [https://jeongw00.tistory.com/187](https://jeongw00.tistory.com/187)
<br/>
<br/>
