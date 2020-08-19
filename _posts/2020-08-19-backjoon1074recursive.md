---
title: (윤성우 Chapter2)재귀(Recursion)
author: SSJ
date: 2020-08-08 19:00:00 +0800
categories: [Algorithm, exercise]
tags: [recursive, algorithm]
toc: false
math: true
---

## 백준 1074 재귀 문제풀이

***

### 코드

```ruby

import java.util.*;
import java.io.*;
 
class backjoon1074 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
 
        int N = sc.nextInt();
        int r = sc.nextInt();
        int c = sc.nextInt();
 
        System.out.println(search(N,r,c));
    }
 
    static int search(int N,int r, int c) {
       int result = 0;
       int mid = 0;
       if(N == 0)
          return 0;
       mid = (int)Math.pow(2,N-1)-1;
       if(r <= mid && c <= mid)
       {
       }else if(r <= mid && c > mid)
       {
          c -= (mid + 1);
          result += 1 * Math.pow(2, 2*(N-1));
       }else if(r > mid && c <= mid)
       {
          r -= (mid + 1);
          result += 2 * Math.pow(2, 2*(N-1));
       }else
       {
          r -= (mid + 1);
          c -= (mid + 1);
          result += 3 * Math.pow(2, 2*(N-1));
       }
       result += search(N-1,r,c);
       return result;
    }
}

```

### 풀이

- 재귀로 문제를 해결하기위해서는 두가지 조건이 필요하다.
- 1. 반복탈출 조건
- 2. 반복되는 패턴
- 위 문제를 풀기 위해 먼저 <span class="text-danger">재귀적으로 해결할 패턴</span>이 있는지를 먼저 확인해야 한다.
- 기본적으로 위 문제를 푸는 아이디어는 N배열을 네 등분을 한 뒤 (r,c) 위치에 따라 각 사분면에 있는 칸수를 더해주고 N을-1 해주고 재귀적으로 문제를 해결하는것이다.

- 따라서 반복의 탈출 조건은 N =0 일때이다.
- 그리고  반복되는 패턴은 mid를 구하고 mid를 기준으로 (r,c)의 위치와 비교하여 몇 사분면에 있는지 확인한 뒤,
  사분면에 따라 칸 수를 더해주고 (r,c)를 N-1일때의 위치로 초기화 해주는 패턴이다.
- 코드를 실행 해 보면 결과는 명확하다.