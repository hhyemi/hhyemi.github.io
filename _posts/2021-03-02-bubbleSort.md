---
title: Algorithm - 버블정렬(Bubble Sort)
tags: Algorithm TIL
key: page-202103021852
summary : 서로 인접한 두 원소를 검사하여 정렬하는 알고리즘
---

## 버블정렬이란?
**두 인접한 데이터를 비교**하여, 앞에 있는 데이터가 뒤에 있는 데이터보다 크면, 자리를 바꾸는 알고리즘
<br/><br/>

![Image Alt 텍스트](/assets/images/bubble-sort.png)

[https://visualgo.net/ko/sorting](https://visualgo.net/ko/sorting)을 참고하면 영상으로 볼 수 있다.

 맨 앞에 두 수를 비교하여 앞에 데이터가 크면 뒤에랑 바꾸면서 한 칸씩 뒤로 가는 알고리즘이다.<br/>
 회전을 한번씩 끝내면 마지막 비교했던 끝에 수는 제일 큰 수가 된다. <br/>
 즉, **n번째 회차가 끝나면 뒤에서 n번째 자리의 데이터가 확정**된다. 마지막 비교한 수는 다음 회전에 비교하지 않아도 된다.<br/>

## JavaScript
```javascript
function bubbleSort (arr) {
  const length = arr.length;
  let temp;

  for (let i = 0; i < length - 1; i++) {
    for (let j = 0; j < length - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) { // 앞의 수가 뒤에 수보다 크면
        temp = arr[j]; // 두 수를 바꿔준다
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }

    if (!temp) {
        break;
    }
  }
  return arr;
}

console.log(bubbleSort([6,4,3,1,2])); // 1,2,3,4,6
```
- 첫 번째 for문은 배열의 값을 순차적으로 비교하기 위한 for문이다.<br/>
- 두 번째 for문은 첫번째 for문의 숫자와 나머지 숫자를 비교하기 위한 for문이다.<br/>
- ```length - 1 - i```에서 ```-i```를 해주는 이유는 마지막 숫자는 확정이 되어서 비교할 필요가 없기 때문에 첫번째 for문의 i 만큼 빼주는 것이다.<br/>
- ```if (!temp)```를 통해 바꿔준 게 없으면 break하여 끝내준다. (완전정렬)<br/>

## 시간복잡도
- 최악의 경우 : 정렬이 하나도 안 되어있는 경우 **O(n^2)**
- 최선의 경우 : 완전 정렬되어있는 경우 **O(n)**

## 장점, 단점
**:heavy_check_mark: 장점**
- 구현이 쉽다.
- in place 알고리즘이기 때문에 메모리가 절약된다.
> "in place"라는 것은 자료를 정렬할 때 추가적인 메모리 공간이 필요한 것이 아니고 데이터가 저장된 그 공간 내에서 정렬을 한다는 뜻

**:heavy_check_mark: 단점**
- 최악의 경우 O(n^2)이 소요되기 때문에 성능이 떨어진다. (비효율)


<br/><br/><br/><br/>
참고자료 : [https://im-developer.tistory.com/133](https://im-developer.tistory.com/133) <br/>
참고자료 : [https://gmlwjd9405.github.io/2018/05/06/algorithm-bubble-sort.html](https://gmlwjd9405.github.io/2018/05/06/algorithm-bubble-sort.html)
<br/>
<br/>
