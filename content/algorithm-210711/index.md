---
emoji: π€
title: BOJ, 1026 λ³΄λ¬Ό
date: '2021-07-11 18:00:00'
author: JChan
tags: Algorithm, BOJ
categories: Algorithm
---

# BOJ, 1026 λ³΄λ¬Ό

[λ³΄λ¬Ό](https://www.acmicpc.net/problem/1026)

## λ¬Έμ 

- μκ° μ ν : 2μ΄
- λ©λͺ¨λ¦¬ μ ν 128MB

μλ  μμ μ μνμ΄ ν­μ ν° κ³¨μΉ«κ±°λ¦¬μλ λλΌκ° μμλ€. μ΄ λλΌμ κ΅­μ κΉμ§λ―Όμ λ€μκ³Ό κ°μ λ¬Έμ λ₯Ό λ΄κ³  ν° μκΈμ κ±Έμλ€.

κΈΈμ΄κ° NμΈ μ μ λ°°μ΄ Aμ Bκ° μλ€. λ€μκ³Ό κ°μ΄ ν¨μ Sλ₯Ό μ μνμ.

S = A[0]ΓB[0] + ... + A[N-1]ΓB[N-1]

Sμ κ°μ κ°μ₯ μκ² λ§λ€κΈ° μν΄ Aμ μλ₯Ό μ¬λ°°μ΄νμ. λ¨, Bμ μλ μλ μ¬λ°°μ΄νλ©΄ μ λλ€.

Sμ μ΅μκ°μ μΆλ ₯νλ νλ‘κ·Έλ¨μ μμ±νμμ€.

## μλ ₯

μ²«μ§Έ μ€μ Nμ΄ μ£Όμ΄μ§λ€. λμ§Έ μ€μλ Aμ μλ Nκ°μ μκ° μμλλ‘ μ£Όμ΄μ§κ³ , μμ§Έ μ€μλ Bμ μλ μκ° μμλλ‘ μ£Όμ΄μ§λ€. Nμ 50λ³΄λ€ μκ±°λ κ°μ μμ°μμ΄κ³ , Aμ Bμ κ° μμλ 100λ³΄λ€ μκ±°λ κ°μ μμ΄ μλ μ μμ΄λ€.

5

1 1 1 6 0

2 7 8 3 1

## μΆλ ₯

18

## μλ

'Bμ μλ μλ μ¬λ°°μ΄νλ©΄ μ λλ€.' λΌλ κΈμ΄ μμ΄μ μ λ ¬μ νμ§ μκ³  μ΄λ»κ² ν μ μμκΉ κ³ λ―Όνλ€ ν΄κ²°μ±μ΄ μλ μ¬λΌ A, B μ λΆ `Arrays.sort()`λ₯Ό μ΄μ©ν΄ νμλ€.
μμ  μλ ₯μ ν΅ν΄ μΆλ ₯λ μ λλ‘ λμμ μ μΆνλλ° κ³μ **νλ Έλ€**κ³  λ¨κΈΈλ λ­μ§ μΆλλ λ¬Έμμ΄λ‘ λ λ°°μ΄μ μ λ ¬ν΄μ νλ Έλ€λ κ±Έ μμμ± μ μμλ€.
ν μλ¦¬ μ«μμ λ¬Έμμ΄μ λΉκ΅κ° λ  μ μμ΄λ λ μλ¦¬ μ«μλ ν μλ¦¬ μ«μκ° λ ν΄ μ μλ€.
String λ°°μ΄μ λ€μ ν λ² intλ‘ μΊμ€ννκ³  λ λ€ μ μΆνλ μ μμ μΌλ‘ μ μΆν  μ μμλ€

```java
// 1026 λ³΄λ¬Ό
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Arrays;

public class Main {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

    int testCase = Integer.parseInt(br.readLine());
    int sum = 0;

    String[] A = br.readLine().split(" ");
    String[] B = br.readLine().split(" ");

    int[] intA = new int[testCase];
    int[] intB = new int[testCase];

    for(int i = 0 ; i < testCase; i++) {
      intA[i] = Integer.parseInt(A[i]);
      intB[i] = Integer.parseInt(B[i]);
    }

    Arrays.sort(intA);
    Arrays.sort(intB);

    for(int i = 0; i < A.length; i++) {
      sum += (intA[i] * intB[testCase - i - 1]);
    }

    bw.write(sum + "\n");
    bw.flush();

    br.close();
    bw.close();
  }
}
```
