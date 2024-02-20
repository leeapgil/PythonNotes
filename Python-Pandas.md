![image](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/pandas.png)

### 1. **DataFrame과 Series**
- `pandas`의 핵심 객체로, 대부분의 연산은 이 두 객체를 사용합니다.
    - **DataFrame**: 2차원 테이블 구조
    - **Series**: 1차원 배열 구조

### 2. **데이터 로드**
- 다양한 형식의 데이터를 쉽게 로드할 수 있습니다.
    ```python
    pd.read_csv('filename.csv')
    pd.read_excel('filename.xlsx')
    ```

### 3. **데이터 탐색**
- 데이터의 처음과 마지막 부분을 확인:
    ```python
    df.head()
    df.tail()
    ```

### 4. **선택과 필터링**
- 특정 열 선택: 
    ```python
    df['column_name']
    df[['col1', 'col2']]
    ```
- 조건에 따른 필터링: 
    ```python
    df[df['column_name'] > value]
    ```

### 5. **결측치 처리**
- 결측치 확인: 
    ```python
    df.isnull().sum()
    ```
- 결측치 제거:
    ```python
    df.dropna()
    ```
- 결측치 대체:
    ```python
    df.fillna(value)
    ```

### 6. **데이터 연산**
- 기초 통계량:
    ```python
    df.describe()
    ```
- 특정 열의 합, 평균 등:
    ```python
    df['column_name'].sum()
    df['column_name'].mean()
    ```

### 7. **데이터 병합**
- 데이터 프레임 결합:
    ```python
    pd.concat([df1, df2])
    pd.merge(df1, df2, on='key_column')
    ```

### 8. **그룹화**
- 데이터를 특정 열을 기준으로 그룹화:
    ```python
    df.groupby('column_name').mean()
    ```

### 9. **시계열 데이터 처리**
- 날짜 인덱스 설정 및 시계열 데이터 연산:
    ```python
    df['date'] = pd.to_datetime(df['date'])
    df.set_index('date', inplace=True)
    ```

### 10. **데이터 저장**
- 결과를 다양한 형식으로 저장:
    ```python
    df.to_csv('filename.csv')
    df.to_excel('filename.xlsx')
    ```

pandas`에서 자주 사용되는 방법 중, 반복문 사용과 `iloc`, `loc`에 관련된 주요 사용법 :

---

### 1. **DataFrame 순회하기**
- `iterrows()`: DataFrame의 각 행을 (index, Series) 쌍으로 반환합니다.
    ```python
    for index, row in df.iterrows():
        print(row['column_name'])
    ```

### 2. **iloc 사용법**
- 행과 열의 위치(정수 인덱스)를 사용하여 데이터에 액세스합니다.
    ```python
    df.iloc[0]  # 첫 번째 행 가져오기
    df.iloc[:, 0]  # 첫 번째 열 가져오기
    ```

### 3. **loc 사용법**
- 행과 열의 라벨을 사용하여 데이터에 액세스합니다.
    ```python
    df.loc[0, 'column_name']
    df.loc[0:4, 'column_name':'another_column']
    ```

### 4. **조건 필터링 with loc**
- `loc`를 사용하여 특정 조건에 따른 데이터 필터링:
    ```python
    df.loc[df['column_name'] > value]
    ```

### 5. **DataFrame에 새로운 열 추가**
- 새로운 열을 DataFrame에 추가하는 방법:
    ```python
    df['new_column'] = list_of_values
    ```

### 6. **apply 사용법**
- DataFrame의 열 또는 행에 함수 적용:
    ```python
    df['column_name'].apply(lambda x: function_of_x)
    ```

### 7. **map 사용법**
- Series의 각 요소에 함수나 딕셔너리를 매핑:
    ```python
    df['column_name'].map(mapping_dictionary)
    ```

### 8. **drop 사용법**
- 특정 열 또는 행 삭제:
    ```python
    df.drop('column_name', axis=1, inplace=True)
    df.drop(index, axis=0, inplace=True)
    ```

### 9. **set_index와 reset_index 사용법**
- 특정 열을 인덱스로 설정하거나 인덱스를 초기화:
    ```python
    df.set_index('column_name', inplace=True)
    df.reset_index(inplace=True)
    ```

### 10. **sort_values 사용법**
- 특정 열의 값에 따라 DataFrame 정렬:
    ```python
    df.sort_values(by='column_name', ascending=True)
    ```

물론입니다. 아래는 Python의 `lambda` 함수에 대한 기본 설명 및 상황별 사용법 10가지를 Markdown 형식으로 제공한 내용입니다:

---

## **Lambda 함수란?**
Lambda 함수는 Python에서 익명의 간단한 함수를 생성하기 위한 도구입니다. 주로 `filter()`, `map()`, `sorted()`와 같은 함수들과 함께 사용됩니다. Lambda 함수는 간결하게 코드를 작성할 수 있게 해주지만, 복잡한 로직을 구현하는 데는 적합하지 않습니다.

기본 구조: 
```python
lambda arguments: expression
```

## **상황별 사용법**

### 1. **리스트 아이템 제곱하기**
```python
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, numbers))
```

### 2. **리스트에서 짝수만 필터링하기**
```python
numbers = [1, 2, 3, 4]
evens = list(filter(lambda x: x%2 == 0, numbers))
```

### 3. **문자열 리스트 정렬하기**
- 문자열의 길이를 기준으로 정렬:
```python
words = ['apple', 'banana', 'cherry']
sorted_words = sorted(words, key=lambda x: len(x))
```

### 4. **딕셔너리 정렬하기**
- 딕셔너리의 값을 기준으로 정렬:
```python
data = {'apple': 10, 'banana': 5, 'cherry': 20}
sorted_data = sorted(data.items(), key=lambda x: x[1])
```

### 5. **함수의 인자로 사용하기**
```python
def math_operation(func, x, y):
    return func(x, y)
result = math_operation(lambda x, y: x * y, 5, 3)
```

### 6. **다수의 인자를 받는 Lambda 함수**
```python
result = (lambda x, y, z: x + y + z)(1, 2, 3)
```

### 7. **Lambda에서 조건 사용하기**
```python
numbers = [1, 2, 3, 4]
modified = list(map(lambda x: x**2 if x%2 == 0 else x, numbers))
```

### 8. **리스트 내의 리스트 정렬하기**
- 내부 리스트의 특정 인덱스 값을 기준으로 정렬:
```python
data = [[1, 2], [4, 5], [2, 0]]
sorted_data = sorted(data, key=lambda x: x[1])
```

### 9. **함수 리스트 사용하기**
```python
functions = [lambda x: x**2, lambda x: x**3]
results = [f(4) for f in functions]
```

### 10. **Lambda 함수 내에서 두 개의 리스트 조합하기**
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
result = list(map(lambda x, y: x + y, list1, list2))
```

