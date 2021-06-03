---
title: Algorithm - 퀵정렬(Quick Sort)
tags: Algorithm TIL
key: page-202103111950
summary: 기준점을 정해서 왼쪽, 오른쪽으로 나누어서 정렬하는 알고리즘
---

## 퀵정렬이란?

**기준점(pivot)** 을 기준으로 왼쪽에는 그보다 작은 수, 오른쪽에는 큰 수만 남기는 방식으로
정렬하는 알고리즘이다.
<br/><br/>

<img src="/assets/images/quick-sort.png" height="600"/>

[https://visualgo.net/ko/sorting](https://visualgo.net/ko/sorting)을 참고하면 영상으로 볼 수 있다.

- **기준점(pivot)** 을 5로 정한다.
- 기준점보다 **작은 데이터는 왼쪽(left), 큰 데이터는 오른쪽(right)** 으로 나누어서 모으는 함수를 사용한다
- 나누어진 왼쪽, 오른쪽에서도 기준점을 정한 후 **재귀함수를 이용** 해서 작업을 반복한다.
- 함수는 **왼쪽(left) + 기준점(pivot) + 오른쪽(right)** 합친 것을 반환한다.

## JavaScript

```javascript
function quickSort(arr) {
  if (arr.length === 0) {
    return [];
  }
  const pivot = arr[0];
  let left = [],
    right = [];

  for (let i = 1; i < arr.length; ++i) {
    if (arr[i] < pivot) {
      left.push(arr[i]);
    } else {
      right.push(arr[i]);
    }
  }
  return quickSort(left).concat(pivot, quickSort(right));
}
```

- ` if(arr.length === 0 )` arr이 빈 값인 경우 []를 반환해준다.
- `const pivot = arr[0];` 기준점을 맨 앞으로 정해준다.
- **for문**을 배열의 길이만큼 돌려 기준점보다 작은 값은 `left.push(arr[i]);` 왼쪽 배열에 넣어주고 큰 값은 `right.push(arr[i]);` 오른쪽 배열에 넣어준다.
- `return quickSort(left).concat(pivot, quickSort(right));` 재귀함수를 호출하고 **_왼쪽(left) + 기준점(pivot) + 오른쪽(right) 합친 것_**을 반환한다.
  <br/>
  <br/>

**:white_check_mark: 참고하면 좋은 코드**

```javascript
function quickSort(arr, index = arr.length - 1, start = 0) {
  if (arr.length < 2) return arr;
  const pivot = arr[index];
  const left = [];
  const right = [];

  while (start < index) {
    arr[start] < pivot ? left.push(arr[start]) : right.push(arr[start]);
    start++;
  }

  return [...quickSort(left), pivot, ...quickSort(right)];
}
```

- `if (arr.length < 2) return arr;` 배열이 0개 1개일 때는 그대로를 반환해준다.
- for문 대신 **while문** 을 이용한 코드이다. 방식은 동일하다.
- Spread 연산자를 사용하여 반환해준다.

## 시간복잡도

- 최악의 경우 : 기준점(pivot)이 가장 작거나 가장 큰 경우에는 모든 데이터를 비교하기 때문에 **O(n^2)**
- 최선의 경우 : **O(nlogn)**

## 장점, 단점

**:heavy_check_mark: 장점**

- 정렬알고리즘 중에 가장 속도가 빠르다.
- 추가 메모리 공간을 필요하지 않는다.

**:heavy_check_mark: 단점**

- 기준값에 따라서 시간복잡도가 크게 달라진다

<br/><br/><br/><br/>
참고자료 : [https://gmlwjd9405.github.ionLayer(68)'>io/2018/05/10/algorithm-quick-sort.html](<https://gmlwjd9405.github.ionLayer(68)'>io/2018/05/10/algorithm-quick-sort.html>) <br/>
참고자료 : [https://jeongw00.tistory.com/184](https://jeongw00.tistory.com/184) <br/>
참고자료 : [https://boycoding.tistory.com/74](https://boycoding.tistory.com/74)
<br/>
<br/>
