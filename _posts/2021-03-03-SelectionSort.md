---
title: Algorithm - 선택정렬(Selection Sort)
tags: Algorithm TIL
key: page-202103031950
summary : 최소값을 찾아 교체를 반복하는 알고리즘
---

## 선택정렬이란?
주어진 데이터 중 **최소값을 찾아 데이터 맨 앞에 위치한 값과 교체**한다. 맨 앞 위치를 뺀 데이터를 동일 방법으로 반복하며 정렬하는 알고리즘
<br/><br/>

<img src="/assets/images/selection-sort.png"  height="600"/>

[https://visualgo.net/ko/sorting](https://visualgo.net/ko/sorting)을 참고하면 영상으로 볼 수 있다.

회전을 진행할때마다 최솟값을 탐색한다. 탐색한 최솟값은 정렬이 교체가 되지 않았던 맨앞의 숫자와 교체된다. <br/>
더이상 교체가 일어나지 않을때까지 반복한다.

## JavaScript
```javascript
function selectionSort(arr) {
  const length = arr.length;

  for (let i = 0; i < length; i++) {
    let min = i; // 최솟값
    for (let j = i + 1; j < length; j++) {
      if (arr[min] > arr[j]) min = j;
    }
    if (i !== min) {
      let temp = arr[i];
      arr[i] = arr[min];
      arr[min] = temp;
    }
  }
  return arr;
}

console.log(selectionSort([3, 5, 1, 2, 7, 6])); // [1, 2, 3, 5, 6, 7]
```
- 첫 번째 for문은 배열의 값을 순차적으로 비교하기 위한 for문이다.<br/>
- 두 번째 for문은 ```let j = i + 1```의 이유는 최솟값이 앞으로 교체했기 때문에 그 이후의 값부터 순회하기 위해서이다.
- ```if (arr[min] > arr[j]) min = j;```  j가 최솟값보다 작으면 min에 넣어준다.
- ```if (i !== min) ``` 최솟값이 맨 앞 숫자가 아니면 (j가 min이 되었으면) 두 수를 바꿔준다. 최솟값이 그대로면 바꿔주지 않아도 된다.


## 시간복잡도
- 최악의 경우 : **O(n^2)**
- 최선의 경우 : **O(n^2)**

## 장점, 단점
**:heavy_check_mark: 장점**
- 구현이 쉽다.
- in place 알고리즘이기 때문에 메모리가 절약된다.
> "in place"라는 것은 자료를 정렬할 때 추가적인 메모리 공간이 필요한 것이 아니고 데이터가 저장된 그 공간 내에서 정렬을 한다는 뜻
- 실행 전 자료의 이동 횟수를 알 수 있다.

**:heavy_check_mark: 단점**
- O(n^2)이 소요되기 때문에 성능이 떨어진다. (비효율)
- 현재 값이 최솟값임에도 불구하고 최솟값을 찾기 위한 순회 과정을 한다. (불필요)
- 배열 내에 동일한 값이 중복해 있다면 상대적인 위치가 변경될 수 있다.

<br/><br/><br/><br/>
참고자료 : [https://webruden.tistory.com/476](https://webruden.tistory.com/476) <br/>
참고자료 : [https://velog.io/@maintainker/algorithm%EC%A0%95%EB%A0%AC](https://velog.io/@maintainker/algorithm%EC%A0%95%EB%A0%AC)
<br/>
<br/>
