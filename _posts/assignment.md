---
layout: post
title:  "assignment "
date:   2018-11-09 16:09:13
categories: Data_science
permalink: /archivers/python_lecture_08
---

# 2018-11-09-assignment.md

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

## 숫자 맞추기 게임(횟수제한)
	-숫자 맞추는 게임에 회수 제한이 있으면 재미있을것 같아서 추가했다.

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
	-숫자 맞추기 게임은 숫자가 랜덤으로 정해지기 때문에, 랜덤으로 숫자를 부여했다.

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
##Dict

```python
# -*- coding: utf-8 -*-

#dict
ab={'a' : '12456789',
   'b' : '456789123',
   'c' : '789456123'}

print ab

for key, number in ab.items():  
    print 'contact {} at {}' .format(key,number)   
print ab

for ab, number in ab.items():
    print 'contact {} at {}' .format(ab,number)  
print ab

```
#보충설명
	- 3개의 print ab 중에서 마지막 하나가 다르다. 
	- 차이는 for문에서 두번쨰 ab와 연결된 for 문에서 key를 사용했고, 차이가 있는 ab는 for 문에서 ab를 사용한 것 이다.


##전화번호부 만들기

```python
# -*- coding: utf-8 -*-

#전화번호부 
aa={'gamaro' : ['02-382-8295','dalcom','12:30~22:30'],
    'chipcken' : ['02-388-7006','banban', '24hr'],
    'bbq' : ['02-353-9393','golden_olive', '10:00~02:00'],
   }

for key in aa.keys():
    print(key, aa[key])

```

##랜덤스킬데미지
	-스킬 레벨이 1일 때, 파이어 볼 데미지는 30-60 사이의 랜덤값을 지니며, 라이트닝 데미지는 1-99 사이의 랜덤값을 지닌다. 각 스킬을 30까지 올렸을 때, 10000회 시행시 어떤 스킬의 평균 데미지가 높은지 구하시오.
	-스킬 레빌이 1올라갈 때, 데미지 최솟값, 최댓값이 1씩 증가한다.

```python
# -*- coding: utf-8 -*-

from random import *
fire_ball_1=0
Lightning_1=0
count = 1

while  True : 
    n=30 
    #스킬 래벨이 30높다.
    fire_ball = randint(30+n,60+n)
    Lightning = randint(1+n,99+n)
    if count == 1000 :
        print fire_ball_1/count
        print Lightning_1/count
        break
    elif count<1000 :
        count= count+1
        fire_ball_1=fire_ball_1+fire_ball
        Lightning_1=Lightning_1+Lightning

```

##duck_typing

```python
# -*- coding: utf-8 -*-

class pikachu:
    def cry(self) : print "pika pika"
    def signature_move(self) : print "pikachu has Thunderbolt"
class ditto:
    def cry(self) : print "meta meta"
    def signature_move(self) : print "Ditto has Transform"
        
def in_the_sunmoon(pikachu):
    pikachu.cry
    pikachu.signature_move()
    
def game() :
    pikachu1 = pikachu()
    ditto1 = ditto()
    in_the_sunmoon(pikachu1)
    in_the_sunmoon(ditto1)
    
def main():
    game()
    
if __name__=='__main__' :
    main()
    ```


##하이브리드 자동차 만들기
```python
# -*- coding: utf-8 -*-
# Car Class 

class car :
    def __init__(self, model_name):
        self.model_name = model_name

# Stop 
    def stop(self):
        # Engine Stop
        print "engine stop."
# Start 
    def start(self):
        # Engine Run
        print "engine start."
# Run
    def run(self):
        # drive
        print "drive."
# Break
    def break_pad(self):
        # break
        print "break_pad."
# Get Car name 
    def get_car_name(self):
        print self.model_name + "is running."

# ElectricCar Class
class ElectricCar():
    def __init__(self, model_name):
        self.model_name = model_name
#stop
    def stop(self):
#Motor Stop
        print "Motor Stop"
#start
    def start(self):
#Motor start
        print "Motro start"
#run
    def run(self):
#Drive
        print "Drive"
#break
    def break_pad(self):
#Break
        print"break_pad"
#Battery Charge
        print "battery Charge"
# Get Car name 
    def get_car_name(self):
        print self.model_name + "is running."

    
# HybridCar Class
class hybridCar(car, ElectricCar):
    def __init__(self, model_name):
        self.model_name = model_name
# Stop 
    def stop(self) :
        car.stop(self)
        ElectricCar.stop(self)
# Engine Stop
# Motor stop
# Start 
    def start(self) : 
        car.start(self)
        ElectricCar.start(self)
# Run
    def run(self) : 
        car.run(self)
        ElectricCar.stop(self)
# Run
# drive
# Break
    def break_pad(self) : 
        car.break_pad(self)
        ElectricCar.break_pad(self)
# break
# batteryCharge    
# Get Car name 
    def get_car_name(self):
        print self.model_name + "is running."    

def main():
    print "it is main."
    normal_car_1 = car("engine1")
    normal_car_1.get_car_name()
    normal_car_1.stop()
    normal_car_1.start()
    normal_car_1.run()
    normal_car_1.break_pad()
    
    Electric_car_1 = ElectricCar("ElectricCar1")
    Electric_car_1.get_car_name()
    Electric_car_1.stop()
    Electric_car_1.start()
    Electric_car_1.run()
    Electric_car_1.break_pad()


    hybrid_car_1 = hybridCar("HybridCar1")
    hybrid_car_1.get_car_name()
    hybrid_car_1.stop()
    hybrid_car_1.start()
    hybrid_car_1.run()
    hybrid_car_1.break_pad()
    
if __name__ == '__main__':
    main()
 ```
