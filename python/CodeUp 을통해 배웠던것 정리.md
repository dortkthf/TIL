# CodeUp 을통해 배웠던것 정리

#6031

```python
c = int(input())
print(chr(c))  # c에 저장되어 있는 정수 값을 유니코드 문자(character)로 바꿔 출력한다.

# chr()는 정수값 -> 문자 
# ord()는 문자 -> 정수값 형태로 바꿔주는 서로 반대 방향으로 바꾸어주는 기능을 한다.
```

#6042

```python
#실수 1개를 입력받아
#소숫점 이하 두 번째 자리까지의 정확도로 반올림한 값을 출력해보자.


#예시
a=input()
a=float(a)
print( format(a, ".2f") )

#format(수, ".2f") 를 사용하면 원하는 자리까지의 정확도로 반올림 된 실수 값을 만들어 준다. 여기서 만들어진 값은 소수점 아래 3번째 자리에서 반올림한 값이다.
```

#6052

```python
bool( ) 을 이용하면 입력된 식이나 값을 평가해 불 형의 값(True 또는 False)을 출력해준다.

n = int(input())
print(bool(n)) ## python 언어에서 정수값 0은 False(거짓)로 평가되고, 그 외의 값들은 모두 True(참)로 평가된다.
```

