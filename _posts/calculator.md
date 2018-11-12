---
layout: post
title:  "2주차 계산기"
date:   2018-11-09 16:09:13
categories: Data_science
permalink: /archivers/python_lecture_04
---

# 2018-11-09-calculator.md

## raw_input 예제 활용 

	- raw_input()은 문자열 포맷 코드로 숫자나 문자를 입력 받을 수있는 함수이다.
	- 파이썬 3의 경우는 input를 사용하지만, 파이썬 2에서는 raw_input사용
	

## 곱셈 계산기 만들기

```python
# -*- coding: utf-8 -*-

#multipli calculator

first=int(raw_input("first "))
second=int(raw_input("second "))

print first*second

```
	

	-위의 방법 처럼 print 이후의 연산자를 바꾸는 것으로 사측연산이 가능한 계산기를 만들 수 있다.


##일반 계산기 만들기

```python
# -*- coding: utf-8 -*-

#calculator

first=int(raw_input("first "))
second=int(raw_input("second "))

oper=(int(raw_input("odd:1, minus:2, mul:3, div:4 ")))

if oper==1: 
    print first+second
    
elif oper==2:
    print first-second
    
elif oper==3:
    print first*second

elif oper==4:
    print first/second

```

	- if문을 활용해서 간단한 계산기를 만들었다. 