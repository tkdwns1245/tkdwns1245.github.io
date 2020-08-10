---
title: (윤성우 Chapter2)재귀(Recursion)
author: SSJ
date: 2020-08-08 19:00:00 +0800
categories: [Algorithm, DataStructure]
tags: [자료구조]
toc: false
math: true
---

## 02-1 함수의 재귀적 호출의 이해

***

### 재귀함수의 기본적이해

- 재귀함수란 다음과 같이 함수 내에서 자기 자신을 다시 호출하는 함수를 의미한다.

```ruby

void Recursive(void)
{
	printf("Recuresive call! \n");
	Recursive();
}

```

- 그런대 위 처럼 재귀 함수를 선언하게 되면 함수 호출 시 무한으로 반복되어 실행될 것이다.
- 따라서 재귀함수에는 반드시 <span class="text-danger">함수를 탈출하는 조건 을 추가해야 한다. 다음이 조건을 추가한 함수이다.</span>

```ruby

void Recursive(int num)
{
	if(num <= 0)
		return;
	printf("Recursive call! %d \n", num);
	Recursive(num-1);
}

int main(void)
{
	Recursive(3);
	return 0;
}

```

이를 실행하면 다음과 같은 결과가 출력될 것이다.

```console

Recursive call! 3
Recursive call! 2
Recursive call! 1

```

- 재귀 함수에서 탈출 조건을 구성하는 것은 매우 중요한 일이다!!.

### 재귀의 활용(Factorial)

- 재귀함수는 <span class="text-danger">어려운 문제를 단순화</span> 하는데 사용되는 중요한 무기이다.
- 재귀함수가 있기에 재귀적인 수학적 수식을 코드로 그대로 옮길 수 있다. 다음을 보면 이를 확인할 수 있다.

$$ n! = n * (n - 1) * (n - 2) * (n - 3) * . . . * 2 * 1 $$
이를 함수로 나타내면 다음과 같이 나타낼 수 있다.

$$ f(n) = n * f(n-1)  ... n >= 1 $$

$$ f(n) = 1 ... n = 0 $$

여기서 f(n) 의 식을 잘 살펴보면 n이 계속 작아지다가 0이 될때는 고정값으로 1이된다는것을 알 수 있다. <span class="text-align">이것을 탈출조건으로 사용하면 되지 않을까?</span> 이 개념을 코드화하면 다음의 Factorial 함수와 같다.

-RecursiveFactorial.c

```ruby

#include<stdio.h>

int Factorial(int n)
{
	if(n == 0 )
		return 1;
	else
		return n * Factorial(n-1);
}

int main(void)
{
	printf("1! = %d \n", Factorial(1));
	printf("2! = %d \n", Factorial(2));
	printf("3! = %d \n", Factorial(3));
	printf("4! = %d \n", Factorial(4));
	printf("9! = %d ]n", Factorial(9));
	return 0;
}

```

```console

1! = 1
2! = 2
3! = 6
4! = 24
9! = 362880

```

### 재귀의 활용(피보나치 수열)

- 피보나치 수열이란? 다음과 같은 수열이다. 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55 . . . .
- 이 수열을 자세히보면 앞의 숫자 둘을 더해서 다음의 숫자가 만들어진다는 것을 알 수 있다.
- 이것을 함수로 표현하면 다음과 같다.

$$ fib(n) = 0   ...  n = 1 $$
$$ fib(n) = 1   ...  n = 2 $$
$$ fib(n) = fib(n-1) + fib(n-2)   ...   n > 2

- 어떻게 수열의 규칙에서 이와 같은 함수를 만들 수 있지? 라는 생각이든다면 수열을 함수로 변환하는 과정에 대해서 몇번 연습해 보는것이 좋을것 같다는 생각이 든다.

위와 같은 함수 규칙이 보였다면 다음 해야 할 일은 명확하다. 이를 코드화 해보자.

- FibonacciFunc.c

```ruby

#include <stdio.h>

int Fibo(int n)
{
	int(n == 1)
		return 0;
	else if(n ==2)
		return 1;
	else
		return Fibo(n-1) + Fibo(n-2);
}

int main(void)
{
	int i;
	for(i = 1; i < 15; i++)
		printf("%d ", Fibo(i));

	return 0;
}

```

```console

0 1 1 2 3 5 8 13 21 34 55 89 144 233

```

- Fibo 함수를 보고 필자는 그런 생각이 들었다. 아... 저게 된다고?.. 왜?... 그래서 하나하나 풀어서 결과가 정확하게 나오는지 확인 한 적이 있다. 궁금하면 고등학교 수열문제 풀듯이 하나하나 피라미드를 그려보라.. 물론 결과는 정확히 나오게 되어있다. 그런대 함수 호출 과정들이 머릿속에서 깔끔하게 그려지지 않아 답답했던 적이 있다. 아니나 다를까 윤성우의 열혈 알고리즘에서도 그런 이야기가 나온다. 재귀에 관해 설명하며 학부시절 교수님께서 하셨던 말씀이 생각난다. 이과정을 모두 이해하려 하지마세요 머리터집니다. 나는 재귀함수를 그렇게 받아들이기로 했다. 그냥 <span class="text-danger">이게되는구나...</span>

### 재귀의 활용(이진탐색)

- 이쯤되면 똑똑한 친구들은 패턴이 보일 것이다. 동일한 패턴이 반복되는 조건이 있다면 이는 재귀적으로 표현 할 수 있을 가능성이 높다.
- 이진탐색이 어떤것이였는지 생각해보자
  1. 가운데 값이 탐색하는 값인지 비교하자
  2. 반으로 자르자
  3. 반으로 잘린것의 가운데 값을 탐색하자
  4. 반으로 자르자
  5. 반으로 잘린것의 가운데 값을 탐색하자
  6. 이를 first 가 last보다 클때까지 반복하자.
- 패턴이 명확히 보인다. 그리고 패턴을 빠져나가는 탈출조건까지 명확히 보인다.
- 그렇다면 다음으로 해야할 것은 이 과정을 하나하나 코드로 옮겨보자

```ruby

int BSearchRecur(int ar[], int first, int last, int target)
{
	int mid;
	if(first > last) 	 //탈출부분//
		return -1;
	mid = (first + last) / 2;		//가운데 부분을 정의하는 부분//

	if(ar[mid] == target)		//탐색하는 부분//
		return mid;
	else if(target < ar[mid])		//패턴 반복 조건//
		return BSearchRecur(ar, first, mid-1, target);
	else
		return BSearchRecur(ar, mid+1, last, target);
}


```

- 이 과정을 보고 드는 반응은 두가지 일것 같다. <span class="text-danger">와.. 개신기하다.. 저게 되는구나</span> 혹은 <span class="text-danger">어떻게 저렇게 함수가 만들어진거지?</span> 첫번째 반응은 기본적으로 알고리즘을 이해하는 능력이 좋은것이라 판단한다. 개인적으로 처음 이 과정을 접햇을때 드는 생각은 두번째 경우였다. 당시에는 그렇구나 하고 그냥 넘어갔던 기억이 난다. 시간이 지나 개발경력이 조금씩 쌓인 후 이 과정을 다시보았을때 결과는 명확해 보인다.
1. 탈출 조건을 처음 판별한다.
2. 반복되는 패턴을 단계적으로 코드화한다.

- 이 과정이 명확하게 그려지지 않을 경우, 그냥 그렇구나 하고 넘어가는걸 추천한다.
- 개인적인 경험으로 프로그래밍을 공부하면서 모든것을 한번에 다 이해하는것을 추천하지 않는다 (물론 가능하다면 그렇게 하는것이 좋다.) 기회가 닿아 다시보았을때 이전보다는 머리가 좋아져서 일까? 명확히 보이는 시점이 온다고 생각한다. 이것은 코딩을 공부하는 전반적인 과정에서 하게 되는 경험이다.(물론 검증된것은 아니다... 개인적인 경험이다. 물론 필자의 경험만은 아니고, 선배개발자님 분들과 같은 경험을 공유하였다.)

### 재귀의 활용(하노이타워)

- 하노이 타워 문제는 다음과 같다.


  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/hanoi1.jpg" | relative_url }})

- 위 그림처럼 세개의 기둥이 있고 A기둥에 크기순으로 원반이 놓여져있다.
- 원반 들을 A에서 C로 옮기는것이 목표이다.
- 원반을 옮기는대는 다음의 규칙을 지키며 옮겨야한다.
  1. 원반은 한 번에 하나씩만 옮길 수 있다.
  2. 옮기는 과정에서 작은 원반의 위에 큰 원반을 올릴 수 없다.

- A 에서 C로 옮겨지는 과정을 보면 다음과 같다.

  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/hanoi2.jpg" | relative_url }})
  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/hanoi3.jpg" | relative_url }})
  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/hanoi4.jpg" | relative_url }})
  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/hanoi5.jpg" | relative_url }})
  ![Desktop View]({{ "/assets/img/algorithm/YSU/datastructure1/hanoi6.jpg" | relative_url }})

- 이 문제를 보았을 때 패턴이 있음이 보인다면 재귀적으로 문제를 풀 수 도 있을것이다. 그렇다면 패턴은 무엇일까?
1. 가장 큰 원반을 C로 옮기기 위해서는 그보다 작은 원반들을 B로 옮긴다.
2. A에 있는 큰 원반을 C로 옮긴다.
3. B에 있는 작은 원반들을 C로옮긴다.

- 신기하게도 원반이 4개가되건 5개가되건 같은 패턴으로 문제를 해결 할 수 있다.

- 그렇다면 이 패턴을 일반화 해보자 일반화 한다면 다음과 같다.
1. 작은 원반 n-1개를 A에서 B로 이동
2. 큰 원반 1개를 A에서 C로 이동
3. 작은 원반 n-1 개를 B에서 C로 이동

- 다음으로 이를 코드로 옮겨보자.

```ruby

void HanoiTowerMove(int num, char from, char by, char to)
{
	if(num == 1)
	{
		printf("원반1을 %c에서 %c로 이동 \n", from, to);
	}else
	{
		HanoiTowerMove(num-1, from, to, by);
		printf("원반%d을 (를) %c에서 %c로 이동\n", num, from, to);
		HanoiTowerMove(num-1, by, from, to);
	}
}

int main(void)
{
	HanoiTowerMove(3, 'A', 'B', 'C');
	return 0;
}

```

- 코드를 실행해본다면 결과가 명확하다는 것을 알 수 있다.