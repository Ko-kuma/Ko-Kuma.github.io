---
layout: post
title: "[Python] 파이썬 제어문, for문과 range, 리스트 컴프리헨션"
date: 2026-01-17
categories: [Python_Basic, Study]
tags: [python, for, loop, range, list comprehension]
---
# 시작하기 전에..

`while`문이 "조건이 참인 동안" 반복한다면, **`for`문**은 "준비된 재료(리스트, 문자열 등)가 떨어질 때까지" 차례대로 반복합니다. 파이썬의 꽃이라고 불리는 `for`문에 대해 완벽하게 정리해 봅니다.

## 1. for문의 기본 구조

파이썬의 `for`문은 구조가 매우 직관적입니다.

```python
for 변수 in 리스트(또는 튜플, 문자열):
    수행할_문장1
    수행할_문장2

```

* **동작 원리:** 리스트의 **첫 번째 요소**부터 **마지막 요소**까지 차례대로 변수에 대입되어, 아래 문장들을 수행합니다.

## 2. 예제를 통해 for문 이해하기

### ① 전형적인 for문

리스트 안에 있는 이름을 하나씩 꺼내어 출력합니다.

```python
test_list = ['one', 'two', 'three'] 
for i in test_list: 
    print(i)

# 결과:
# one
# two
# three

```

### ② 다양한 for문의 사용 (튜플 언패킹)

리스트 안에 튜플이 들어있는 경우, 구조에 맞춰 변수를 여러 개 지정할 수 있습니다.

```python
a = [(1, 2), (3, 4), (5, 6)]
for (first, last) in a:
    print(first + last)

# 결과:
# 3 (1+2)
# 7 (3+4)
# 11 (5+6)

```

## 3. for문의 응용 (continue문)

`while`문과 마찬가지로 `for`문에서도 `continue`를 사용하여 특정 조건을 건너뛸 수 있습니다.

**예제: 60점 이상이면 합격, 아니면 무시하기**

```python
marks = [90, 25, 67, 45, 80]
number = 0 

for mark in marks: 
    number = number + 1 
    if mark < 60: 
        continue  # 점수가 60점 미만이면 아래 print를 실행하지 않고 다음으로 넘어감
    print(f"{number}번 학생 축하합니다. 합격입니다.")

```

## 4. for문과 함께 자주 사용하는 range 함수

`for`문은 숫자 리스트를 자동으로 만들어주는 `range` 함수와 함께 쓰일 때 진가를 발휘합니다.

### range 함수란?

* `range(시작_숫자, 끝_숫자)` 형태를 가집니다.
* **주의:** 끝 숫자는 포함되지 않습니다. (끝 숫자 - 1까지만 생성)

### range 함수의 예시 살펴보기

```python
# 1부터 10까지 더하기
add = 0 
for i in range(1, 11):  # 1부터 10까지 (11은 포함 안 됨!)
    add = add + i 

print(add)
# 결과: 55

```

## 5. for와 range를 이용한 구구단

이중 `for`문(중첩 루프)과 `range`를 이용하면 단 4줄로 구구단을 만들 수 있습니다.

```python
for i in range(2, 10):        # 2단부터 9단까지 (i)
    for j in range(1, 10):    # 각 단마다 1~9까지 곱하기 (j)
        print(f"{i} x {j} = {i*j}", end=" ") 
    print('')  # 한 단이 끝나면 줄 바꿈

```

## 6. 리스트 컴프리헨션 (List Comprehension)

파이썬만의 매우 강력하고 편리한 기능입니다. 리스트 안에 `for`문을 포함하여 한 줄로 새로운 리스트를 만들 수 있습니다.

### ① 기본 문법

`[표현식 for 항목 in 반복가능객체 if 조건문]`

### ② 사용 전 vs 사용 후 비교

**[일반적인 for문 사용]**
리스트 `a`의 각 항목에 3을 곱해 리스트 `result`에 담기

```python
a = [1, 2, 3, 4]
result = []
for num in a:
    result.append(num * 3)

print(result) # [3, 6, 9, 12]

```

**[리스트 컴프리헨션 사용]**
위 코드를 단 한 줄로 줄일 수 있습니다.

```python
a = [1, 2, 3, 4]
result = [num * 3 for num in a]

print(result) # [3, 6, 9, 12]

```

### ③ 조건을 추가한 예시

짝수에만 3을 곱하고 싶다면?

```python
a = [1, 2, 3, 4]
result = [num * 3 for num in a if num % 2 == 0]

print(result) # [6, 12] (2와 4에만 3이 곱해짐)

```

---

**이해하기**

* 반복 횟수가 정해져 있거나, 리스트 등을 순회할 때는 `while`보다 **`for`**가 유리합니다.
* 숫자 범위를 만들 때는 **`range()`**를 씁니다.
* 리스트를 만들 때 `for`문을 한 줄로 쓰는 것을 **리스트 컴프리헨션**이라고 합니다.
