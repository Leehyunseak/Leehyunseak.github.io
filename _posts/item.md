---
layout: post
title:  "4주차 item"
date:   2018-11-09 16:09:13
categories: Data_science
permalink: /archivers/python_lecture_06
---

# 2018-11-09-Item.md

## 재귀함수

	- 재귀함수는 다시 자신을 불러서 계산하는 함수이다.

## 재귀함수를 활용한 팩토리얼 계산 

```python
# -*- coding: utf-8 -*-

#팩토리얼
def factorial(a) :
    if a == 1:
        return 1
    else :
        return a*factorial(a-1)
print factorial(4)

```

##List
	- 순서대로 정리된 비정적 mutable 자료구조이다.
	- List 초기화시 []를사용하며, append,sort,del을 사용한다.

```python
# -*- coding: utf-8 -*-

#list 
shoplist = ['chocopie', 'meat', 'trash_bonge', 'IPA']

print 'I have', len(shoplist), 'items to purchase'

print 'these items are:',
for item in shoplist:
    print item,
shoplist.append('red_dead_redemption')

shoplist.sort()
print shoplist

print 'the first item i will buy is ', shoplist[0]
del shoplist[0]
print shoplist[0]
```

##Tuple
	- 여러 개의 객체를 모아 담는 정적mutable 자료구조, 순서가있음.
	-new_x[n][n] 인덱싱 연산자 
	-tuple은 초기화 시 ()

```python
# -*- coding: utf-8 -*-

#tuple
ps4 = ('uncharted','monter_hunter','horizon')
print len(ps4)
print  ps4

new_ps4 ='red_dead_redemption',ps4
print len(new_ps4)
print new_ps4 

print new_ps4[1]
print new_ps4[1][1]

```

##Dict
	-Ditctionary 초기화 시 {}사용, key:value의 쌍으로 이루어진다. 
	-1개의 키에 여러개의 value가 있을 수있다.

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

##SET
	-집합은 정렬되지 않은 단순 객체의 묶음, 중복을 허용하지 않음.
	-멤버십 테스트를 수행할 수 있으며, 한 집합이 다른 집합의 부분집합인지 알 수 있으며, 교집합을 구할 수 있음.

```python
# -*- coding: utf-8 -*-

#set

chicken = set(['bbq', 'bhc', 'gobne', 'gamaro'])
print chicken

print 'bbq' in chicken
print 'nene' in chicken
chicken.add('chipcken')
chicken.remove('bhc')
print chicken
```


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
	-스킬 레벨이 1일 때, 파이어 볼 데미지는 30-60 사이의 랜덤값을 지니며, 라이트닝 데미지는 1-99 사이의 랜덤값을 지닌다. 각 스킬을 30까지 올렸을 때, 10000회 시행시 어떤 스킬의 평균 데미지가 높은지 구하시오
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