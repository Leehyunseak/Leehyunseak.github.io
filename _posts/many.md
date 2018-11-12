---
layout: post
title:  "3주차 다양한 예제"
date:   2018-11-09 16:09:13
categories: Data_science
permalink: /archivers/python_lecture_05
---

# 2018-11-09-many.md

## iF 예제 

	- IF는 조건문으로 조건에 부합하면 if에 있는 것을 아니면 else문에 있는 답을 뱉는다.
	- if문에 해당하지 않을 때, elif로 다른 조건을 또 걸수 있다. 
	

## 숫자 맞추기 게임(IF)

```python
# -*- coding: utf-8 -*-

#if

number = 17
guess = (int(raw_input('guess number? ')))

if guess == number : 
    print 'congratulations'
    
elif guess > number :
    print 'it is lower than that'

else :
    print 'it is higher than that'

    
print 'done'

```
	
## while문
	-while문은 반복제어 문으로 반복문을 break로 깨기 전까지 반복한다.
	-while문은 True, False로 진행되고, 깨진다. 

## 숫자 맞추기 게임(While)
```python
# -*- coding: utf-8 -*-

#while 
number = 13
running = True

while running :
    guess = int(raw_input('enter guess :'))

    if guess == number :
        print 'congratulations'
        running = False
    elif guess < number : 
        print 'up'
    else  : 
        print 'down'
else : 
    print "the while loop is over"

```
## 숫자 맞추기 게임(횟수제한)
	-while문을 이용한 게임을 만들어 보고 회수 제한이 있으면 재미있을것 같아서 추가했다.

```python
# -*- coding: utf-8 -*-

# 횟수제한
number = 13
running = True
count = 0 

while running :
    guess = int(raw_input('enter guess :'))
    
    if count == 3 :
        print 'you lost chance'
        running = False

    elif guess == number :
        print 'congratulations'
        running = False
    elif guess < number : 
        print 'up'
        count = count+1
        print count 
    else  : 
        print 'down'
        count = count+1
        print count 
else : 
    print "the while loop is over"
```

## 숫자 맞추기 게임(횟수제한+랜덤)
	-이런 게임은 숫자가 랜덤으로 정해지기 때문에, 랜덤으로 숫자를 부여했다.

```python
# -*- coding: utf-8 -*-

#random game + 횟수제한
from random import *
number = randint(1, 20)
running = True
count = 0 

while running :
    guess = int(raw_input('enter guess :'))
    
    if count == 3 :
        print 'you lost chance'
        running = False

    elif guess == number :
        print 'congratulations'
        running = False
    elif guess < number : 
        print 'up'
        count = count+1
        print count 
    else  : 
        print 'down'
        count = count+1
        print count 
else : 
    print "the while loop is over"
```


## 자판기 만들기 
	- 콜라,사이다, 커피 각 재고가 10개 씩있는 자판기를 만들어라.

```python
# -*- coding: utf-8 -*-
#자판기

coke = 3
cider = 2
coffee = 1
cost=0
coke_ja=10
cider_ja=10
coffee_ja=10
item = 0

while True :
    if coke_ja==0 and cider_ja ==0 and coffee_ja ==0 :
        print "we don't have anything"
        break
    else :
        print '1.coke {} 2.cider {} 3. coffee {}'.format(coke_ja,cider_ja,coffee_ja)
        want = int(raw_input('what You want? '))
        number = int(raw_input('How many do you need?'))

    if want == 1 :
        print 'it is {}doller'.format((coke)*number)
        coke_ja = coke_ja-number
        item = 'coke'
        cost = 3*number
    elif want == 2: 
        print 'it is {}doller'.format((cider)*number)
        cider_ja=cider_ja-number
        item='cider'
        cost = 2*number
    else :
        print 'it is {}doller'.format((coffee)*number)
        coffee_ja=coffee_ja-number
        item='coffee'
        cost =1*number
    while True :   
        machl = int(raw_input('How much will it cost? '))
        if machl == cost :
            print 'You get {}'.format(item)
            print 'Thanks'
            break
        elif machl < cost : 
            print 'you must pay more'
        else : 
            print 'you get {} and {}'.format(machl-cost,item)
            print 'Thanks'
            break
```

##전역변수와 지역변수 

```python
# -*- coding: utf-8 -*-

#전역변수와 지역변수 
x=50

def func():
    global x
    print 'x is ', x
    x = 2
    print 'changed global x to ',x
    
func()

print 'value of x is',x

def func(x):
    print 'x is', x
    x = 50
    print 'changed local x to' ,x
    
func(x)
print 'x is still', x
```


#
x is  50
changed global x to  2
value of x is 2
x is 2
changed local x to 50
x is still 2
	
	- 위의 함수식의 결과는 이런식으로 나오게 되는데, global x는 function안의 로컬함수 x를 글로벌 x로 지정한 것이다. 이후 로컬 안에서 X를 2로 변형시키게 되어서 글로벌x가 50에서 2로 변화하였다. 이후에는 func(x)를 통해 지역변수만 50으로 변형시켜서 글로벌 x는 하직 2이다.