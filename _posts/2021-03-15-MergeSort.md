---
title: Algorithm - 병합정렬(Merge Sort))
tags: Algorithm TIL
key: page-202103151950
summary : 리스트를 절반으로 잘라 재귀적으로 병합하는 알고리즘
---

## 병합정렬이란?
데이터 길이가 1개일때까지 절반으로 잘라 리스트를 앞뒤 두 개로 나누고 **재귀용법을 활용**하여 하나의 정렬된 리스트로 병합하는 정렬알고리즘
<br/><br/>

<img src="/assets/images/merge-sort-concepts.png" height="500"/>

[https://visualgo.net/ko/sorting](https://visualgo.net/ko/sorting)을 참고하면 영상으로 볼 수 있다.
- 리스트를 절반으로 잘라 비슷한 크기의 **두 부분 리스트로 나뉜다.**
- 각 부분 리스트를 **재귀적으로** 병합정렬을 이용하여 정렬한다.
- 두 부분리스트를 다시 **하나의 정렬된 리스트로 병합** 한다.


## JavaScript
```javascript
const merge = function (left, right) {
	const result = [];
	while (left.length !== 0 && right.length !== 0) {
		left[0] <= right[0] ? result.push(left.shift()) : result.push(right.shift());
	}
	return [...result, ...left, ...right];
}

const mergeSort = function (array) {
	if (array.length === 1) return array;

	const middleIndex = Math.floor(array.length / 2);
	const left = array.slice(0, middleIndex);
	const right = array.slice(middleIndex);

	return merge(mergeSort(left), mergeSort(right));
}
```
- ```merge```함수는 두 부분의 리스트를 합쳐주는 함수이다.
- ```while (left.length !== 0 && right.length !== 0) {``` 왼쪽 오른쪽 길이가 0이 될 때까지 반복문을 돌려서 작은쪽 값을 ```result```에 push한다.
- ```return [...result, ...left, ...right];``` 하나의 정렬리스트로 병합한다.
- ```if (array.length === 1) return array;``` 만약 리스트 개수가 하나이면 해당값을 리턴한다.
- 배열을 절반으로 잘라서(slice) ```merge(mergeSort(left), mergeSort(right));``` 재귀함수를 이용하여 정렬한다.


## 시간복잡도
- 최악의 경우 : **O(nlogn)**
- 최선의 경우 : **O(nlogn)**

## 장점, 단점
**:heavy_check_mark: 장점**
- 최선, 최악의 경우 모두 **O(nlogn)**이기 떄문에 데이터 분포에 영향을 덜 받는다.

**:heavy_check_mark: 단점**
- n place 알고리즘이 아니기 때문에 별도의 메모리 공간이 필요하다.
> "in place"라는 것은 자료를 정렬할 때 추가적인 메모리 공간이 필요한 것이 아니고 데이터가 저장된 그 공간 내에서 정렬을 한다는 뜻
- 데이터의 양이 많은 경우에는 이동 횟수가 많아지기 때문에 시간적인 낭비도 많아진다.

<br/><br/><br/>
참고자료 : [https://im-developer.tistory.com/134?category=846746](https://im-developer.tistory.com/134?category=846746) <br/>
참고자료 : [https://gmlwjd9405.github.io/2018/05/08/algorithm-merge-sort.html](https://gmlwjd9405.github.io/2018/05/08/algorithm-merge-sort.html) <br/>
<br/>
