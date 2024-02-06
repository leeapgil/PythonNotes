# Python 기초

Python은 간단하면서도 표현력 있는 프로그래밍 언어입니다. 이 문서에서는 Python의 기초에 대한 이론과 예제를 다룰 것입니다.

## 식별자 (Identifiers)

식별자란 변수, 함수, 클래스, 모듈 등을 구별하기 위해 사용되는 이름입니다.

### 규칙
- 알파벳, 숫자, 언더스코어(_)로 구성
- 숫자로 시작할 수 없음
- 대소문자 구별
- 예약어를 사용할 수 없음 (ex. `for`, `while`, `if` 등)

```python
# 올바른 식별자 예
my_var = 10
VAR1 = "hello"
_var = True

# 잘못된 식별자 예
1var = 10  # 숫자로 시작
for = 20  # 예약어 사용
```

## 연산자 (Operators)

Python에서 사용되는 기본적인 연산자는 다음과 같습니다:

- 산술 연산자: `+`, `-`, `*`, `/`, `//`, `%`, `**`
- 비교 연산자: `==`, `!=`, `<`, `>`, `<=`, `>=`
- 논리 연산자: `and`, `or`, `not`

```python
# 산술 연산자 예
result = 3 + 2  # 더하기
result = 3 - 2  # 빼기
result = 3 * 2  # 곱하기
result = 3 / 2  # 나누기
result = 3 // 2  # 몫
result = 3 % 2  # 나머지
result = 3 ** 2  # 제곱

# 비교 연산자 예
result = (3 == 2)  # False
result = (3 != 2)  # True
result = (3 > 2)  # True

# 논리 연산자 예
result = (3 > 2) and (2 < 4)  # True
result = (3 > 2) or (2 > 4)  # True
result = not (3 == 2)  # True
```

## 자료형 (Data Types)

Python의 기본 자료형에는 `list`, `dict`, `tuple`, `set` 등이 있습니다.

### List

순서가 있는 컬렉션입니다.

```python
my_list = [1, 2, 3]
my_list.append(4)  # [1, 2, 3, 4]
my_list[0]  # 1
```

### Dict

키와 값의 쌍을 가지는 컬렉션입니다.

```python
my_dict = {'key': 'value', 'name': 'Alice'}
my_dict['age'] = 30  # {'key': 'value', 'name': 'Alice', 'age': 30}
my_dict['name']  # 'Alice'
```

### Tuple

순서가 있지만 변경 불가능한 컬렉션입니다.

```python
my_tuple = (1, 2, 3)
# my_tuple[0] = 4  # 에러 발생
```

### Set

순서가 없고 중복을 허용하지 않는 컬렉션입니다.

```python
my_set = {1, 2, 3, 3}
# my_set: {1, 2, 3}
```

## if 문

조건에 따라 코드를 실행합니다.

```python
x = 10
if x > 5:
    print("x는 5보다 큽니다.")
elif x == 5:
    print("x는 5입니다.")
elif x == 6:
    pass   #아무 처리 없을때 
else:
    print("x는 5보다 작습니다.")
```

## for 문

반복문을 수행합니다.

```python
for i in range(3):  # 0, 1, 2
    print(i)

for item in [1, 2, 3]:  # 1, 2, 3
    print(item)

for idx, val in enumerate(['a','b','c']):
    print('인덱스:', idx, '값:', val)

```

# 함수 (Functions)

함수는 특정 작업을 수행하는 코드의 묶음입니다. Python에서는 `def` 키워드를 사용해 함수를 정의합니다.

## 함수 정의 및 호출

기본 형태는 다음과 같습니다.

```python
def function_name(parameters):
    # 코드 블록
    return result
```

### 예시

```python
def add(a, b):
    return a + b

result = add(3, 4)  # 결과는 7
```

## 인자와 매개변수 (Arguments and Parameters)

- **매개변수 (Parameters)**: 함수를 **정의**할 때 사용되는 변수입니다.
- **인자 (Arguments)**: 함수를 **호출**할 때 전달하는 값입니다.

```python
# a, b는 매개변수
def multiply(a, b):
    return a * b

# 3, 4는 인자
result = multiply(3, 4)  # 결과는 12
```

## 기본값 매개변수 (Default Parameters)

함수의 매개변수에 기본값을 설정할 수 있습니다.

```python
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet("Alice"))  # "Hello, Alice!"
print(greet("Alice", "Hi"))  # "Hi, Alice!"
```

## 키워드 인자 (Keyword Arguments)

함수를 호출할 때 매개변수의 이름을 명시적으로 지정하여 인자를 전달할 수 있습니다.

```python
def divide(a, b):
    return a / b

result = divide(4, 2)  # 결과는 2
result = divide(b=4, a=2)  # 결과는 0.5
```

## 가변 인자 (Variable-length Arguments)

- `*args`: 임의의 개수의 위치 인자를 튜플로 받습니다.
- `**kwargs`: 임의의 개수의 키워드 인자를 딕셔너리로 받습니다.

```python
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3, 4))  # 결과는 10

def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=30)  
# name: Alice
# age: 30
```

## 람다 함수 (Lambda Functions)

익명 함수를 생성할 수 있습니다. 주로 간단한 연산에 사용됩니다.

```python
square = lambda x: x * x

print(square(5))  # 결과는 25
```

## 타입 힌트와 타입 주석

Python 3.5 이상에서는 타입 힌트(Type Hints)라는 기능을 제공합니다. 이를 사용하면 함수의 매개변수 타입과 반환 타입을 명시적으로 지정할 수 있습니다. 이는 코드의 가독성을 높이고, 개발자가 의도한 타입에 따라 코드가 작동할 것임을 미리 알려주는 역할을 합니다.

### 기본적인 타입 힌트

함수의 매개변수 타입과 반환 타입을 `->`를 사용하여 지정합니다.

```python
def add(a: int, b: int) -> int:
    return a + b
```

### 리스트, 딕셔너리, 튜플에 대한 타입 힌트

`from typing import List, Dict, Tuple`을 사용하여 컬렉션에 대한 타입 힌트를 지정할 수 있습니다.

```python
from typing import List, Dict, Tuple

def manipulate_data(numbers: List[int], options: Dict[str, bool]) -> Tuple[int, int]:
    total = sum(numbers)
    count = len(numbers)
    return total, count
```

### Optional 타입

값이 `None`일 수도 있는 경우에는 `Optional` 타입 힌트를 사용할 수 있습니다.

```python
from typing import Optional

def greet(name: str, title: Optional[str] = None) -> str:
    if title:
        return f"Hello, {title} {name}"
    else:
        return f"Hello, {name}"
```

### 가변 인자에 대한 타입 힌트

`*args`와 `**kwargs`에도 타입 힌트를 적용할 수 있습니다.

```python
from typing import Any

def foo(*args: int, **kwargs: Any) -> None:
    for arg in args:
        print(arg)
```

타입 힌트는 Python의 실행에는 영향을 미치지 않지만, 개발 도구나 linter에서 타입 관련 오류를 잡아주거나, 문서화 도구가 더 정확한 정보를 제공하는 등 다양한 이점이 있습니다.
