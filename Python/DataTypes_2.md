# list :star:
## 시퀀스로서의 리스트
- 여러 개의 값을 순서대로 저장하는 **변경 가능한** 시퀀스 자료형
### 특징
- 대괄호 [ ] 
- 모든 종류의 데이터(숫자, 문자열, 다른 리스트,...) 담을 수 있음
- 값 **추가, 수정, 삭제** 자유!
- 인덱싱, 슬라이싱, 길이 확인, 반복 등 모두 가능!
## 중첩 리스트
- 다른 리스트를 값으로 가진 리스트
- 인덱스 연속 사용으로 안쪽 리스트 값 접근 가능!
```
my_list=[1,2,3,'Python',['hello!','world!','!!!']]

print(len(my_list)) #5
print(my_list[4][-1]) #!!!
print(my_list[-1][1][0]) #w
```
## 리스트의 가변성
### 인덱싱으로 값 수정하기
```
my_list=[1,2,3,4,5]
my_list[1]='two'
print(my_list) #[1,'two',3,4,5]
```
### 슬라이싱으로 여러 값 한 번에 바꾸기
```
my_list=[1,2,3,4,5]
my_list[2:4]=['three','four']
print(my_list) # [1,2,'three','four',5]
```

# tuple
## list와 공통점
- 여러 개의 값을 순서대로 저장함 
- 모든 종류의 데이터를 담을 수 있음
- 인덱싱, 슬라이싱, 길이 확인, 반복 등 가능!
## list와 차이점
- 소괄호 ( ) 사용 (없이도 만들 수 있음)
- **불변성**: 값 추가, 수정, 삭제 **절대 불가능!**
  - 내부 동작과 안전한 데이터 전달에 사용 -> 안정성과 무결성 보장
  - 다중 할당, 값 교환, 함수 다중 반환 값 등 
- 단일 요소 튜플을 만들 때는 **반드시 후행 쉼표** 사용해야 함 

# range
- **연속된 정수 시퀀스**를 생성하는, **변경 불가능한** 자료형
- 주로 *반복문*과 함께 사용 -> 특정 횟수만큼 *코드를 반복 실행할 때* 매우 유용!
- 모든 숫자를 메모리에 저장 X '규칙'만 기억해 메모리를 효율적으로 사용 O
## 기본 구문
- 1개, 2개, 또는 3개의 **매개변수(인자)**를 가질 수 있음
### range(stop)
- 매개변수가 하나면 stop으로 인식
- **기본값: start = 0, step = 1**
### range(start, stop)
- 매개변수가 두 개면 start와 stop으로 인식
- **기본값: step = 1**
### range(start, stop, step)
- 모든 매개변수를 직접 지정 
```
my_range_1 = range(5) # 0, 1, 2, 3, 4
my_range_2 = range(1, 10) # 1,2,3,4,5,6,7,8,9,10
my_range_3 = range(5, 0, -1) # 5,4,3,2,1 

print(my_range_1)  # range(0, 5)
print(my_range_2)  # range(1, 10)
print(my_range_3)  # range(5, 0, -1)

# 리스트로 형 변환 시 데이터 확인 가능
print(list(my_range_1))  # [0, 1, 2, 3, 4]
print(list(my_range_2))  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(list(my_range_3))  # [5, 4, 3, 2, 1]
```
## 규칙
### 1. 값의 범위 규칙
- stop 값은 생성되는 시퀀스에 절대 포함 X
- range(1,5)는 1부터 5 **전까지의(stop 값 바로 앞에서 시퀀스 끝)** 숫자를 의미하므로 1,2,3,4가 생성
### 2. 증가/감소 값(step) 규칙
- step 값은 숫자 시퀀스의 간격과 방향을 결정함
- step 값이 양수일 때 (기본값: 1)
  - 숫자가 start부터 stop을 향해 **증가**
```
# 시작 값이 끝 값보다 작은 경우 (정상)
print(list(range(1, 5)))  # [1, 2, 3, 4]
print(list(range(1,10,2))) # [1,3,5,7,9]
# 시작 값이 끝 값보다 큰 경우
print(list(range(5, 1)))  # []
```
- step 값이 음수일 때 
  - 숫자가 start부터 stop을 향해 **감소**
  - **이 경우, start 값은 stop보다 반드시 커야 함!!**
```
# 시작 값이 끝 값보다 큰 경우 (정상)
print(list(range(5, 1, -1)))  # [5, 4, 3, 2]
print(list(range(10,1,-2))) # [10,8,6,4,2]
# 시작 값이 끝 값보다 작은 경우
print(list(range(1, 5, -1)))  # []
```
- 주로 반복문과 함께 활용 예정 
```
for i in range(1, 10):
    print(i)  # 1 2 3 4 5 6 7 8 9

for i in range(1, 10, 2):
    print(i)  # 1 3 5 7 9
```

# dict :star:
## 딕셔너리 표현
- **key-value 쌍**으로 이루어진 **순서와 중복이 없는 변경 가능한** 자료형
- 중괄호 { }
- Key(키)
  - 값을 식별하기 위한 고유한 '이름표' **(중복 불가)**
  - **Key를 통해 접근함**
- Value(값)
  - 키에 해당하는 실제 데이터
  - 각 값에는 **순서가 없음** 
```
my_dict_1 = {}
my_dict_2 = {'key':'value'}
my_dict_3 = {'apple':12, 'list':[1,2,3]}

print(my_dict_1)  # {}
print(my_dict_2)  # {'key': 'value'}
print(my_dict_3)  # {'apple': 12, 'list': [1, 2, 3]}
```
## 규칙
### Key의 규칙
- 고유해야 함
  - Key는 중복 불가
- 변경 불가능한 자료형에만 사용 가능
  - **O(가능): str, int, float, tuple**
  - X(불가능): list, dict
### Value의 규칙
- 어떤 자료형이든 자유롭게 사용 가능
## 딕셔너리 값 접근
- Key를 사용해 해당 Value를 꺼내올 수 있음
- Key에 접근시 대괄호 [] 사용
```
my_dict = {'name': '홍길동', 'age': 25}
print(my_dict['name'])  # '홍길동'
print(my_dict['test'])  # KeyError: 'test'
```
- 존재하지 않는 Key로 접근하면 KeyError 발생
## 값 추가 및 변경
```
my_dict = {'apple': 12, 'list': [1, 2, 3]}
# 추가
my_dict['banana'] = 50
print(my_dict)  # {'apple': 12, 'list': [1, 2, 3], 'banana': 50}

# 변경
my_dict['apple'] = 100
print(my_dict)  # {'apple': 100, 'list': [1, 2, 3], 'banana': 50}
```
- 데이터에 순서가 필요 없고, 각 데이터에 의미 있는 이름(Key)를 붙여 관리하고 싶을 때 사용
  - (예: 사람의 인적 정보, 게임 캐릭터의 능력치 등)
- API를 다룰 때 사용

# set
## 세트 표현
- *순서와 중복이 없는 변경 가능한* 자료형
- 중괄호 { } 
- 수학에서의 집합과 동일한 연산 처리 가능
- 비어 있는 딕셔너리와의 혼동을 피하기 위해, 비어 있는 세트는 반드시 set() 함수로 만들어야 함
## 핵심 특징
1. **중복을 허용하지 않음**
  - 똑같은 값은 단 하나만 존재할 수 있음
  - 중복된 값이 있는 리스트의 중복 값을 제거할 때: set()
2. 순서가 없음
  - **인덱싱이나 슬라이싱 사용 불가**
## 집합 연산
- 세트는 수학의 ‘집합’ 개념을 그대로 가져와, 두 데이터 그룹 간의 관계를 파악하는 데 매우 효과적
```
my_set_1 = {1, 2, 3}
my_set_2 = {3, 6, 9}

# 합집합
print(my_set_1 | my_set_2)  # {1, 2, 3, 6, 9}

# 차집합
print(my_set_1 - my_set_2)  # {1, 2}

# 교집합
print(my_set_1 & my_set_2)  # {3}
```

# Other Types
## None
```
# 아직 아무 값도 할당하고 싶지 않을 떄
my_variable = None
print(my_variable)  # None
```
- **‘값이 없음’**을 표현하는 특별한 데이터 타입
- 내용물이 없는 ‘빈 상자’와 같음
- 숫자 0이나 빈 문자열(’ ‘)과는 다른, **‘값이 존재하지 않음’** 또는 **‘아직 정해지지 않음’**이라는 상태를 나타내기 위해 사용됨
- N 대문자
## Boolean
```
is_active = True
is_logged_in = False

print(is_active)  # True
print(is_logged_in)  # False
print(10 > 5)  # True
print(10 == 5)  # False
```
- **‘참(True)’과 ‘거짓(False)’ 단 두 가지 값**만 가지는 데이터 타입
- 비교/논리 연산의 평가 결과로 사용됨
- 주로 조건/반복문과 함께 사용됨
- T F 대문자

# Collection
- **여러 개의 값을 하나로 묶어 관리**하는 자료형들을 통칭하는 말
- str, list, tuple, range, set, dict 데이터 타입이 해당
## 불변과 가변
- 컬렉션 타입은 생성 후 내용 변경 가능 여부에 따라 '불변'과 '가변' 두 그룹으로 나뉨
- 불변: str, tuple, range
- 가변: list, dict, set

# 형변환
## 암시적 형변환: 파이썬이 자동 처리
- 데이터 손실을 막기 위해 **더 정밀한 타입으로 자동 변환**
- 정수와 실수의 연산에서 정수가 실수로 변환됨
- **Boolean과 Numeric Type에서만 가능**
```
# 정수(int)와 실수(float)의 덧셈
print(3 + 5.0)  # 8.0
# 불리언(bool)과 정수(int)의 덧셈
print(True + 3)  # 4
# 불리언간의 덧셈
print(True + False)  # 1
```
## 명시적 형변환: 개발자가 직접 함수로 지정하여 변환
- 예시
```
# str -> int
# 형식에 맞는 숫자만 가능 
print(int('1'))  # 1
# ValueError: invalid literal for int() with base 10: '3.5'
# print(int('3.5'))
print(int(3.5))  # 3
print(float('3.5'))  # 3.5

# int -> str
# 모두 가능 
print(str(1) + '등')  # 1등
```

# 연산자
## 산술 연산자
- 수학적 계산을 위해 사용되는 연산자
- -(음수 부호), +, -(뺄셈), *, /, //(몫), %, **
## 복합 연산자
- 연산과 할당이 함께 이루어짐
```
y = 10
y -= 4
# y = y - 4
print(y)  # 6

z = 7
z *= 2
print(z)  # 14

w = 15
w /= 4
print(w)  # 3.75

q = 20
q //= 3
print(q)  # 6
```
## 비교 연산자
- 두 값을 비교해 그 관계가 맞는지 틀린지를 True 또는 False로 반환
- <, <=, >, >=, ==, !=, is, is not
### == 연산자
- 값(데이터)이 같은지 비교
- 동등성(Equality): 두 변수가 가리키는 객체의 내용, 즉 **값(Value)**이 같은지 확인
### is 연산자
- 객체 자체가 같은지, 즉 **완전히 동일한 메모리 주소인지** 확인
- 식별성(Identity)
- 주로 싱글턴 객체를 비교할 때 사용 
  - 싱글턴 객체: 특정 값에 대해 파이썬 전체에서 **단 하나의 객체만 생성되어 재사용**되는 특별한 객체
  - 예: None, True, False
## 논리 연산자
- 여러 개의 조건을 조합하거나, True/False 값을 반대로 뒤집을 때 사용
- and, or, not
```
# 논리 연산자 활용
print(True and False)  # False
print(True or False)  # True
print(not True)  # False
print(not 0)  # True


# 비교 연산자와 함께 사용 가능 
num = 15
result = (num > 10) and (num % 2 == 0)
print(result)  # False

name = 'Alice'
age = 25
result = (name == 'Alice') or (age == 30) # 앞에서 결과가 나오면 뒤를 버림 -> 단축 평가
print(result)  # True
```
### 단축 평가
- 논리 연산에서 **두 번째 피연산자를 평가하지 않고 결과를 결정**하는 동작
- 거짓으로 취급되는 값들
  - False, 숫자 0, 빈 문자열 “”, 빈 리스트[], None 등 ‘비어 있거나 없다’는 느낌의 값들
- 참으로 취급되는 것들
  - True 그리고 ‘거짓’이 아닌 모든 내용이 있는 값
- **and 연산자:** **하나라도 ‘거짓’**이면 바로 **‘거짓’**
  - 끝까지 갔는데 모든 값이 ‘참’이면 맨 마지막 ‘참’ 값을 반환
```
# 1
# 준비물 1: 내용이 있는 문자열
item1 = '지도'
# 준비물 2: 내용이 있는 문자열
item2 = '나침반'
result = item1 and item2
print(f'최종적으로 챙긴 물건: {result}')
# >> 최종적으로 챙긴 물건: 나침반

# 2
item1 = '지도'
# 준비물 2: 내용이 없는 빈 문자열
item2 = ''
result = item1 and item2
print(f'최종적으로 챙긴 물건: "{result}"')
# >> 최종적으로 챙긴 물건: ''


# 3
# 준비물 1: 내용이 없는 빈 문자열
item1 = ''
item2 = '나침반'
result = item1 and item2
print(f'최종적으로 챙긴 물건: "{result}"')
# >> 최종적으로 챙긴 물건: ''
```
- **or 연산자:** **하나라도 ‘참’**이면 바로 **‘참**’
  - 끝까지 갔는데 모든 값이 ‘거짓’이면 맨 마지막 ‘거짓’ 값을 반환
- 코드 실행 최적화, 불필요한 연산 피함, 코드 흐름 제어, 오류 방지, 간결 코드 작성

## 멤버십 연산자
- 특정 값이 시퀀스나 다른 컬렉션 안에 포함되어 있는지를 확인하는 연산자
- in, not in
```
word = 'hello'
numbers = [1, 2, 3, 4, 5]

print('h' in word)  # True
print('z' in word)  # False

print(4 not in numbers)  # False
print(6 not in numbers)  # True
```
## 시퀀스 연산자
- 시퀀스 자료형(문자열, 리스트, 튜플)에 특별한 의미로 사용되는 연산자
- '+':결합, '*':반복
```
print('Gildong' + ' Hong')  # Gildong Hong
print('hi' * 5)  # hihihihihi

print([1, 2] + ['a', 'b'])  # [1, 2, 'a', 'b']
print([1, 2] * 2)  # [1, 2, 1, 2]
```
