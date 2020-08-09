---
title: (윤성우 Chapter1)자료구조와 알고리즘의 이해
author: SSJ
date: 2020-08-08 04:15:00 +0800
categories: [Algorithm, DataStructure]
tags: [자료구조]
toc: false
math: true
---

## 01-1 자료구조(Data Structure)에 대한 기본적인 이해

***

### 자료구조란 무엇인가?

"프로그램이란? <span class="text-danger">데이터를 표현</span>하고, 그렇게 표현된 <span class="text-danger">데이터를 처리</span>하는것이다."

- <span class="text-danger">'데이터 표현'</span> 은 <span class="text-danger">'데이터 저장'</span>을 포함하는 개념이다. 이 '데이터 저장'을 담당하는 것이 '자료구조' 이다.
- 넓은 의미에서 int형 변수와 구조체의 정의도 자료구조에 속한다.
![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/datastructure_category.jpg" | relative_url }})

### 자료구조를 왜 알아야 하나?

- 자료구조는 보통 라이브러리에 구현되어 있는 경우가 많이 있고 이를 <span class="text-danger">잘</span> 가져다 쓰면 되는 경우가 많다.
- <span class="text-danger">잘</span> 가져다 쓰려면 각각의 자료구조를 <span class="text-danger">잘</span> 이해하고 있어야 한다.
- 자료구조의 구현 경험은 프로그래밍 능력을 향상시켜 준다.(머리가 좋아진다.(<span class="text-secondary">개인적인 생각입니다</span>))

### 자료구조와 알고리즘

- <span class="text-danger">'자료구조'</span>가 '데이터의 표현 및 저장방법' 이라면, <span class="text-danger">알고리즘</span> 은 자료구조를 활용하여 
<span class="text-danger">문제를 해결하는 방법</span> 을 의미한다. 
```ruby
int arr[10] = {1,2,3,4,5,6,7,8,9,10};
```
- 이것은 <span class="text-danger">배열</span> 이라는 자료구조 이다.
```ruby
for(idx = 0; idx<10; idx++)
  sum+= arr[idx];
```
- 이것은 배열에 저장된 모든 값의 합을 구하는 <span class="text-danger">알고리즘</span>이다.

![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/cup.jpg" | relative_url }})
- 쌓여있는 상자안에 있는 머그컵이 있다고 가정하자
- 머그컵이 몇번째 상자에 있는지 찾기 위해서는 위에있는 상자부터 순서대로 내려가서 찾아야 한다.
- 여기에서 <span text-danger>쌓여있는 상자</span> 는 데이터를 저장하는 <span class="text-danger">자료구조</span> 이고 가장 위부터 순서대로 내려가면서 머그컵을 찾는 방법은 <span class="text-danger">알고리즘 이다.</span>
- 이 과정에서 두가지 사실을 알 수 있다.
- "자료구조에 따라서 알고리즘은 달라진다."
- "알고리즘은 자료구조에 의존적이다."
<h4><span class="text-danger">자료구조와 알고리즘은 많은 연관성이 있다.</span></h4>

## 01-2 알고리즘의 성능분석 방법
***
### 기본적으로 알아야 할 개념
- 지수식  $$ y =  2^x $$ 
- 로그식 $$ y = log_2 x $$

### 시간복잡도와 공간 복잡도

- 시간복잡도 : 얼마나 <span class="text-danger">빠른</span> 알고리즘이냐 를 평가하는 요소
- 공간복잡도 : 얼마나 메모리를 <span class="text-danger">적게</span> 쓰느냐 를 평가하는 요소
- 알고리즘의 수행 속도를 평가하는 방법

  "연산의 횟수를 센다."

  "처리해야 할 데이터의 수 n에 대한 연산횟수의 함수 T(n)을 구성한다."

  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/graph.jpg" | relative_url }})

- 이 그래프를 보면 데이터 수가 적으면 <span class="text-danger">알고리즘 B</span>가 더 빠르고 데이터의 수가 많으면 <span class="text-danger">A</span>가 빠르다.
- 데이터 수가 적을 경우에는 어차피 속도 차이가 얼마 나지 않기 때문에 알고리즘 A가 <span class="text-danger">더 좋은 알고리즘</span>이라 할 수 있다.
- 하지만 대게 알고리즘A가 알고리즘B보다 <span class="text-danger">구현 난이도</span>가 높아 데이터 수가 많지 않고 성능에 덜 민감한 경우 B와 같은 알고리즘을 선택하기도 한다.

### 순차 탐색(Linear Search)알고리즘과 시간복잡도 분석의 핵심요소

- LinearSearch.c

```ruby
#include <stdio.h>

int LSearch(int ar[], int len, int target)  // 순차 탐색 알고리즘 적용된 함수 //
{
	int i;
	for(i = 0; i <len; i++)
	{
		if(ar[i] == target)
			return i;
	}
	return -1;
}

int main(void)
{
	int arr[] = {3, 5, 2, 4, 9};
	int idx;

	idx =  LSearch(arr, sieof(arr)/sizeof(int), 4);
	if(idx == -1)
		printf("탐색 실패 \n");
	else
		printf("타갯 저장 인덱스: %d \n", idx);

	idx = LSearch(arr, sizeof(arr)/sizeof(int), 7);
	if(idx == -1)
		printf("탐색 실패 \n");
	else
		printf("타겟 저장 인덱스: %d \n", idx);

	return 0;
}
```

- 실행 결과 : LinearSearch.c

```console
타겟 저장 인덱스 : 3
탐색 실패
```

- 맨 앞부터 순서대로 탐색하기 때문에 순차탐색 이라 부른다.
- 알고리즘을 구현하는 코드

```ruby

for(i = 0; i <len; i++)
{
	if(ar[i] == target)
		return i;
}
```

- 시간복잡도함수T(n)을 구하는 방법 : 
  위 알고리즘에 사용된 연산자는 <,++,== 세개이다. 하지만 이 모든걸 다 비교하는것은 비효율적이다.
  따라서 핵심적인 연산만 비교한다

- 이 알고리즘에서 핵심은 동등비교를 하는 연산이다. 구조를 비교해보면 ==연산이 줄어들면 < 연산과 ++연산의 횟수도 줄어든다.
- 최선의 경우(best case) : 수행횟수  = 1(운이좋아서 배열의 맨 앞에서 찾았을 경우)
- 최악의 경우(worst case) : 수행횟수  = n(운이 나빠서 배열의 맨 마지막에서 찾았을 경우)
- 알고리즘을 평가하는데 있어서 '최악의 경우'만이 관심의 대상이다.
- 평균적인 경우가 가장 좋은것 아닌가? : 이는 어려운 일이라 '최악의 경우'를 알고리즘을 평가하는데 활용한다.

### 순차 탐색 알고리즘의 시간 복잡도 계산하기1: 최악의 경우(worst case)

"데이터의 수가 n개일 때, 최악의 경우에 해당하는 연산횟수는(비교연산의 횟수는)n 이다."

따라서 '데이터 수 n에 대한 연산횟수의 함수 T(n) = n 이다.'

### 이진 탐색(Binary Search) 알고리즘의 소개

- 앞서 설명한 순차 탐색보다 좋은 탐색 알고리즘이다.
- "배열에 저장된 데이터는 정렬이 되어 있어야 한다." 라는 조건을 만족해야한다.
- 다음과 같이 정렬된 배열이 있다고 가정하고 우리가 숫자 3을 찾고 있다고 하자.

  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/array.jpg" | relative_url }})

- 이진 탐색 알고리즘의 첫 번째 시도 : 
 1. 배열 의 첫번째 index와 마지막 index 를 더하여 2를 나눈 값을 구한다.((0+8)/2 = 4) 
 2. 그 값을 인덱스로 하여, 탐색하고 있는 값이 맞는지 확인한다. (arr[4] != 3)
- 이진 탐색 알고리즘의 두 번째 시도 : 
 1. arr[4] 에 저장된 값과 탐색대상의 대소를 비교한다.(9>3)
 2. 탐색 하고 있는 값보다 arr[4] 가 크다. 따라서 탐색의 범위를 0~3으로 제한한다.
 3. 0과 3을 더하여 그 결과를 2로 나눈다. 이 때 나머지는 버린다.((0+3)/2 = 1)
 4. 그 값을 인덱스로 하여, 탐색하고 있는 값이 맞는지 확인한다.arr[1] != 3

 - 이진 탐색 알고리즘의 세 번째 시도 : 
 1. arr[1] 에 저장된 값과 탐색대상의 대소를 비교한다.(2>3)
 2. 탐색 하고 있는 값이 arr[1] 보다 크다. 따라서 탐색의 범위를 2~3으로 제한한다.
 3. 2와 3을 더하여 그 결과를2로 나눈다. 이 때 나머지는 버린다.((2+3)/2 = 2)
 4.그 값을 인덱스로 하여, 탐색하고 있는 값이 맞는지 확인한다.(arr[2] == 3)

 - 이와 같은 패턴을 (탐색의 첫번째 인덱스 <= 탐색의 두번째 인덱스) 일때까지 반복하여 탐색한다.(같을 경우에도 탐색은 해야한다.)

  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/arr2.jpg" | relative_url }})

 - 위 그림을 보면 탐색 범위가 패턴이 반복될수록 반씩 줄어드는 것을 확인할 수 있다.
 - 이때 (탐색의 첫번째 인덱스 > 탐색의 두번째 인덱스) 일 경우 탐색에 실패한것이다.

### 이진 탐색(Binary Search) 알고리즘의 구현

 - BinarySearch.c

 ```ruby

 #include <stdio.h>

 int BSearch(int ar[], int len, int target)
 {
 	int first = 0;
 	int last = len-1;
 	int mid;

 	while(first <= last)
 	{
 		mid = (first+last) / 2;

 		if(target == ar[mid])
 		{
 			return mid;
 		}else
 		{
 			if(target < ar[mid])
 				last = mid - 1;
 			else
 				first = mid + 1;
 		}
 	}
 	return -1;
 }

 int main(void)
 {
 	int arr[] = {1, 3, 5, 7, 9};
 	int idx;

 	idx = BSearch(arr, sizeof(arr)/sizeof(int), 7);
 	if(idx == -1)
 		printf("탐색 실패 \n");
	else
		printf("타겟 저장 인덱스: %d \n", idx);

	idx = BSearch(arr, sizeof(arr)/sizeof(int), 4);
	if(idx == -1)
		printf("탐색 실패 \n");
	else
		printf("타겟 저장 인덱스: %d \n", idx);

	return 0;
 }

 ```

- 실행결과 BinarySearch.c

```console
타겟 저장 인덱스 : 3
탐색 실패
```

### 이진 탐색 알고리즘의 시간 복잡도 계산하기 :  최악의 경우(worst case) 를 기준으로

- 먼저 이진 탐색 알고리즘 에서 연산횟수를 대표하는 연산이 무엇인지 찾아야한다.

```ruby
while(first <= last)
{
	mid = (first+last) / 2;
	if(target == ar[mid])
	{
		return mid;
	}
	else
	{
		if(target < ar[mid])
 				last = mid - 1;
 			else
 				first = mid + 1;
	}
}

```

- 대표하는 연산은 <span class="text-danger">==</span> 이다.

- 그렇다면 데이터 수가 n개 일때, 최악의 경우에 발생하는 비교연산의 횟수는?

1. 데이터수가 n 개일 때 1회 비교연산 진행
2. n/2 일때 1회 비교연산 진행
3. n/4 일때 1회 비교연산 진행
4. n/8 일때 1회 비교연산 진행
...
5. 데이터 수가 1 개일 때 1회 비교연산 진행

- 이를 일반화하면
1. n이 1이 되기까지 2로 나눈 횟수 k회라 가정하면, 비교연산 k회 진행
2. 데이터가 1개 남았을 때, 비교연산 1회 진행

- 따라서 시간복잡도함수 <span class="text-danger">T(n)=k+1</span>이 된다.
- 하지만 이 식에서 k를 n에 대한 식으로 변환할 필요가 있다. 이를 위해 n과 k에 관한 식을 구하면
$$ n * (1/2)^k = 1 $$
이라는 식이 나온다.
이 식을 정리하면
<span class="text-danger">$$ n * 2^{-k} = 1 $$</span> => <span class="text-danger">$$ n=2^k $$</span> => <span class="text-danger">$$ log_2 n = k $$</span> 가 된다.
따라서 $$ T(n) = log_2 n + 1$$ 이된다. 하지만 데이터 수가 증가할때 1은 무시해도 되는 값이기 때문에
$$ T(n) = log_2 n $$ 이라 할 수있다.(사실 상수는 거의 무시하면 된다.)

### 빅-오 표기법(Big-Oh Notation)

- 빅오는 시간복잡도함수 T(n)에서 가장 영향력이 큰 부분이 어딘가를 따지는 것이다.
- 다음 함수를 보자
$$ T(n) = n^2 + 2n + 1 $$
- 위 함수에서 1은 작은 값이니 그냥 생략 한다고 치더라도 2n 까지 생략해도 될까? 이에 대한 해답을 내기위해 다음 표를 확인해보면된다.

|$$ n $$|$$ n^2 $$|$$ 2n $$|$$ T(n) $$ | $$ n^2 $$ 의 비율|
|:--|:----|:--|:----|--:|
|10 | 100 | 20 | 120 | 83.33% 
|100 | 10,000 | 200 | 10,200 | 98.04% 
|1,000 | 1,000,000 | 2,000 | 1,002,000 | 99.80%
|10,000 | 100,000,000 | 20,000 | 100,020,000 | 99.98%

- 위 표를 확인하면 알 수 있듯이 <span class="text-danger">최고 차항을 제외한 나머지 차수의 변수들은 무시</span>해도 상관없을정도로 작은 영향을 미친다.
- 따라서 함수 T(n) 에서 영향을 가장 많이 끼치는 부분만을 남겨 <span class="text-danger">O($$ n^2 $$)</span> 로 표현한다.
- <span class="text-danger">정리하자면</span> 함수 T(n) = $$ n^2+2n+1 $$ 의 빅오는 $$ n^2 $$ 이며, 이는 n의 증가 및 감소에 따른 T(n) 의 변화 정도가 $$ n^2 $$ 의 형태를 띰을 의미한다.

### 단순하게 빅-오 구하기

"T(n)이 다항식으로 표현이 된 경우, <span class="text-danger">최고차항의 차수</span>가 빅-오가 된다."

- $$ T(n) = n^2 + 2n + 9 $$ ▶ $$ O(n^2) $$
- $$ T(n) = n^4 + n^3 + n^2 + 1 $$ ▶ $$ O(n^4) $$
- $$ T(n) = 5n^3 + 3n^2 + 2n + 1 $$ ▶ $$ O(n^3) $$

정리하자면 다음과 같다.

- $$ O(logn) $$ 이 있다면 이는 데이터 수의 증가에 따른 연산횟수의 증가는 증가하는 추세가 둔화되는 <span class="text-danger">로그 그래프</span> 형태를 띈다는 것을 의미한다.

### 빅오의 성능비교

빅-오 표기들의 성능의 비교를 정리하면 다음 순으로 <span class="text-danger">성능이 좋은 알고리즘</span>과 같다.
$$ O(1) - O(logn) - O(n) - O(nlogn) - O(n^2) - O(n^3) - O(2^n) $$
이를 그래프로 정리해 보면 다음과 같다.

  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/bigograph.jpg" | relative_url }})

<출처 : http://media.photobucket.com/image/o%20notation/amit_9b/BIGO_GRAPH.jpg>
