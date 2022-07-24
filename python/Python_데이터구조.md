# 데이터 구조(Data Structure)

### 컴퓨터(Computer)

- 선언적 지식(declaritive knowledge)
  - '사실에 대한 내용'
- 명령적 지식(imperative knowledge)
  - 'How-to'

### 변수와 타입

```python
word = 'happy!'
cnt = 0
for char in word:
    cnt += 1
```

### 시퀀스(순서가 있는 데이터 구조)

#### 문자열(String Type)

- 문자들의 나열(sequence of characters)
  - 모든 문자는 str 타입
- 문자열은 작은 따옴표(')나 큰 따옴표(")를 활용하여 표기
  - 문자열을 묶을 떄 동일한 문장부호를 활용
  - PEP8에서는 소스코드 내에서 하나의 문장부호를 선택하여 유지하도록 함

#### 문자열 탐색/ 검증

| 문법        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| s.find(x)   | x의 첫 번째 위치를 반환, 없으면 -1을 반환                    |
| s.index(x)  | x의 첫 번째 위치를 반환, 없으면, 오류 발생                   |
| s.isalpha() | 알파벳 문자 여부 *단순 알파벳이 아닌 유니코드 상 Letter(한국어도 포함) |
| s.isupper() | 대문자 여부                                                  |
| s.islower() | 소문자 여부                                                  |
| s.istitle() | 타이틀 형식 여부                                             |

#### 문자열 변경

| 문법                           | 설명                                       |
| ------------------------------ | ------------------------------------------ |
| s.replace(old, new[,count])    | 바꿀 대상 글자를 새로운 글자로 바꿔서 반환 |
| s.strip([chars])               | 공백이나 특정 문자를 제거                  |
| s.split(sep=None, maxsplit=-1) | 공백이나 특정 문자를 기준으로 분리         |
| 'separator'.join([iterable])   | 구분자로 iterable을 합침                   |
| s.capitalize()                 | 가장 첫 번째 글자를 대문자로 변경          |
| s.title()                      | 공백 이후를 대문자로 변경                  |
| s.upper()                      | 모두 대문자로 변경                         |
| s.lower()                      | 모두 소문자로 변경                         |
| s.swapcase()                   | 대 <->소문자 서로 변경                     |

- .replace(old, new[,count])

  - 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
  - count를 지정하면, 해당 개수만큼만 시행

  ```python
  print('coone'.replace('o','a'))
  # caane
  print('wooooowoo'.replace('o','!',2))
  # w!!ooowoo
  ```

- .strip([chars])

  - 특정한 문자들을 지정하면,
  - 양쪽을 제거하거나(strip), 왼쪽을 제거하거나(lstrip), 오른쪽을 제거(rstrip)
  - 문자열을 지정하지 않으면 공백을 제거함

  ```python
  print(' 와우!\n'.strip())
  # '와우!'
  print(' 와우!\n'.lstrip())
  # '와우!\n'
  print(' 와우!\n'.rstrip())
  # ' 와우!'
  print('안녕하세요????'.rstrip('?’))
  # '안녕하세요'
  ```

- .split(sep = None, maxsplit=-1)

  - 문자열을 특정한 단위로 나눠 리스트로 반환
    - sep이 None이거나 지정되지 않으면 연속된 공백문자를 단일한 공백문자로 간주하고, 선행/후행 공백은 빈 문자열에 포함시키지 않음
    - maxsplit이 -1인 경우에는 제한이 없음

  ```python
  print('a,b,c'.split('_’))
  # ['a,b,c']
  print('a b c'.split())
  # ['a', 'b', 'c']
  ```

- 'separator'.join([iterable])

  - 반복가능한(iterable) 컨테이너 요소들을 separator(구분자)로 합쳐 문자열 반환
    - iterable에 문자열이 아닌 값이 있으면 Type Error 발생

  ```py
  print(''.join(['3', '5’]))
  # 35
  ```

  

  