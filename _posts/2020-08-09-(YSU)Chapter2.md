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

### 재귀함수의 디자인 사례

- 재귀함수는 <span class="text-danger">어려운 문제를 단순화</span> 하는데 사용되는 중요한 무기이다.
- 재귀함수가 있기에 재귀적인 수학적 수식을 코드로 그대로 옮길 수 있다. 다음을 보면 이를 확인할 수 있다.

$$ n! = n * (n - 1) * (n - 2) * (n - 3) * . . . * 2 * 1 $$
이를 함수로 나타내면 다음과 같이 나타낼 수 있다.
$$ f(n) = n * f(n-1)  ... n >= 1 $$
$$ f(n) = 1 ... n = 0 $$

이를 
### 재귀의 활용

### 이진 탐색 알고리즘의 재귀적 구현

## 02-2 하노이 타워(The Tower of Hanoi)

***

### 하노이 타워의 문제 이해

### 하노이 타워의 반복패턴 연구

### 하노이 타워 문제의 해결