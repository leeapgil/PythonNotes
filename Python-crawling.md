# 웹 크롤링, 파싱, 스크레핑

이 문서는 웹 크롤링, 파싱, 스크레핑의 개념과 그에 따른 주의사항에 대해 설명합니다.

## 웹 크롤링 (Web Crawling)

**정의**: 웹 크롤링은 인터넷 상의 웹 페이지들을 방문하고 내용을 자동으로 수집하는 과정을 말합니다.

- 사용 도구: 크롤러(Crawler) 또는 스파이더(Spider)라고 부릅니다.
- 주요 목적: 검색 엔진에서 웹 페이지의 최신 정보를 갱신하거나 웹 콘텐츠의 색인 생성 등의 작업을 위해 사용됩니다.

## 파싱 (Parsing)

**정의**: 파싱은 특정 정보를 추출하기 위해 문서나 데이터를 분석하는 과정을 의미합니다.

- 사용 도구: BeautifulSoup, lxml, xml 파서 등의 라이브러리가 주로 사용됩니다.
- 주요 목적: 크롤링을 통해 수집한 웹 콘텐츠에서 필요한 정보만을 추출하기 위해 사용됩니다.

## 웹 스크레핑 (Web Scraping)

**정의**: 웹 스크레핑은 웹 사이트의 데이터를 추출하는 행위입니다. 이때 웹 크롤링과 파싱을 함께 사용하는 경우가 많습니다.

- 사용 도구: Scrapy, BeautifulSoup, Selenium 등의 도구와 라이브러리가 있습니다.
- 주요 목적: 웹 사이트에서 데이터를 추출하여 다양한 용도로 활용하기 위함입니다.

## 주의사항

1. **이용 약관 확인**: 대부분의 웹 사이트는 이용 약관에 웹 크롤링 및 스크레핑에 대한 정책을 명시하고 있습니다. 반드시 해당 사이트의 약관을 확인하고 준수해야 합니다.
2. **robots.txt 확인**: 웹 사이트의 root 디렉터리에 위치한 `robots.txt` 파일은 웹 크롤러가 접근할 수 있는 영역을 지정합니다. 이 파일을 반드시 확인하고 지침을 따라야 합니다.
3. **서버 부하 주의**: 크롤링 시 너무 많은 요청을 빠르게 보내면 웹 사이트의 서버에 부하를 줄 수 있습니다. 적절한 간격을 두고 요청을 보내야 합니다.
4. **개인정보 보호**: 웹 스크레핑을 통해 수집한 데이터 중 개인정보가 포함될 수 있습니다. 이러한 정보는 적절한 방법으로 보호하며, 불법적으로 수집하거나 사용하지 않아야 합니다.
5. **저작권 문제**: 웹 사이트의 콘텐츠는 저작권이 존재할 수 있습니다. 무단으로 수집한 콘텐츠를 재배포하거나 상업적으로 이용하는 것은 법적 제재를 받을 수 있습니다.

웹 크롤링과 스크레핑은 많은 정보를 효율적으로 수집하는 도구로 활용될 수 있지만, 위의 주의사항을 반드시 지켜야 합니다.

# BeautifulSoup과 Requests를 사용한 Python 정적 웹 크롤링

## 설치

먼저 필요한 라이브러리를 설치해야 합니다.

```bash
pip install requests
pip install beautifulsoup4
```

## 기본 사용법

### Requests 사용

`requests.get(url)`를 사용하여 웹 페이지의 HTML을 가져옵니다.

```python
import requests

response = requests.get('https://www.example.com/')
```

### BeautifulSoup 사용

가져온 HTML을 `BeautifulSoup` 객체로 변환합니다.

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(response.content, 'html.parser')
```

### HTML 요소 찾기

`find`나 `find_all` 메서드를 사용하여 특정 태그나 속성을 가진 요소를 찾을 수 있습니다.

```python
# 첫 번째 <a> 태그를 찾습니다.
first_a_tag = soup.find('a')

# 모든 <a> 태그를 찾습니다.
all_a_tags = soup.find_all('a')
```

## 속성으로 요소 찾기와 값 가져오기

### 요소에서 속성 값 가져오기

```python
# 요소에서 href 속성을 가져옵니다.
link = element['href']

# 요소에서 class 속성을 가져옵니다.
classes = element['class']
```

### 특정 속성으로 요소 찾기

```python
# class가 'my-class'인 div 요소를 찾습니다.
element = soup.find('div', attrs={'class': 'my-class'})
```

## CSS 선택자 사용

### select 메서드

`select` 메서드는 CSS 선택자에 일치하는 모든 요소를 리스트로 반환합니다.

```python
elements = soup.select('div.my-class')
```

### select_one 메서드

`select_one` 메서드는 CSS 선택자에 일치하는 첫 번째 요소를 반환합니다.

```python
element = soup.select_one('div.my-class')
```

## 예제

```python
from bs4 import BeautifulSoup

# 예시 HTML 페이지
html_content = '''
<!DOCTYPE html>
<html>
<head>
    <title>Test Page</title>
</head>
<body>
    <div class="container">
        <a href="https://www.example1.com" class="my-link" id="link1">Example 1</a>
        <a href="https://www.example2.com" class="my-link" id="link2">Example 2</a>
    </div>
</body>
</html>
'''

# BeautifulSoup 객체 생성
soup = BeautifulSoup(html_content, 'html.parser')

# class가 'my-link'인 모든 a 태그를 선택하고 href 값을 출력합니다.
for a_tag in soup.select('a.my-link'):
    print(a_tag.get('href'))

## 동적 웹 크롤링 Selenium과 Python 사용법
이 문서는 최신 Selenium 라이브러리를 사용하여 XPath를 활용한 웹 요소 선택 및 상호작용 방법에 대해 설명합니다. 최신 Selenium 버전에서는 요소를 찾을 때 `find_element_by_xpath`와 같은 메서드 대신 `find_element` 메서드에 `By.XPATH`를 사용합니다. 이 변경은 코드의 가독성을 높이고, Selenium API의 일관성을 개선하기 위해 도입되었습니다.
## 설치

필요한 라이브러리를 설치합니다. Selenium을 사용하기 위해 `selenium` 패키지를 설치해야 합니다.

```bash
pip install selenium
```

사용하는 브라우저에 맞는 WebDriver도 설치해야 합니다. 예를 들어, Chrome을 사용한다면 ChromeDriver를 설치해야 합니다.

## 기본 사용법

### WebDriver 설정

Chrome WebDriver를 사용하는 예시입니다. WebDriver의 경로는 시스템에 따라 다를 수 있으므로 적절히 조정해야 합니다.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome('/path/to/chromedriver')
```

### 웹 페이지 접근

`get` 메서드를 사용하여 웹 페이지에 접근합니다.

```python
driver.get('https://www.example.com/')
```

### XPath를 이용한 요소 선택

최신 Selenium 버전에서 요소를 선택하는 방법입니다.

```python
# 첫 번째 <a> 태그를 선택합니다.
first_a_tag = driver.find_element(By.XPATH, '//a')

# 모든 <a> 태그를 선택합니다.
all_a_tags = driver.find_elements(By.XPATH, '//a')
```

## 예제

아래의 예제는 `class`가 'my-link'인 모든 `<a>` 태그를 선택하고, 각 태그의 텍스트를 출력하는 방법을 보여줍니다.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

# WebDriver 객체 생성
driver = webdriver.Chrome('/path/to/chromedriver')
driver.get('https://www.example.com/')

# class가 'my-link'인 모든 a 태그를 선택하고, 각 태그의 텍스트를 출력합니다.
a_tags = driver.find_elements(By.XPATH, '//a[@class="my-link"]')
for a_tag in a_tags:
    print(a_tag.text)

# 브라우저 닫기
driver.quit()
```

이 문서는 Selenium을 사용하여 웹 페이지의 요소를 클릭하고, 키보드 입력을 전송하며, 스크린샷을 저장하고, JavaScript 코드를 실행하는 방법에 대해 설명합니다. 이러한 기능들은 웹 자동화 및 테스팅에 있어서 매우 중요합니다.

## 클릭하기 (Click)

웹 페이지의 요소를 클릭하는 것은 사용자 인터랙션의 기본 형태 중 하나입니다. Selenium에서는 `click` 메서드를 사용하여 요소를 클릭할 수 있습니다.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome('/path/to/chromedriver')
driver.get('https://www.example.com/')

# 요소 클릭하기
clickable_element = driver.find_element(By.CSS_SELECTOR, 'button#submit')
clickable_element.click()
```

## 키보드 입력 전송하기 (Send Keys)

텍스트 입력 필드나 텍스트 영역에 문자열을 입력하는 경우, `send_keys` 메서드를 사용합니다.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome('/path/to/chromedriver')
driver.get('https://www.example.com/')

# 텍스트 입력 필드에 문자열 전송
input_field = driver.find_element(By.NAME, 'search')
input_field.send_keys('Selenium')
input_field.send_keys(Keys.ENTER)  # 엔터 키를 누름
```

## 스크린샷 저장하기 (Save Screenshot)

페이지의 현재 상태를 이미지 파일로 저장할 수 있습니다. 이는 디버깅 또는 문서화 과정에서 유용하게 사용됩니다.

```python
from selenium import webdriver

driver = webdriver.Chrome('/path/to/chromedriver')
driver.get('https://www.example.com/')

# 현재 페이지의 스크린샷을 저장
driver.save_screenshot('page_snapshot.png')
```

## JavaScript 실행하기 (Execute Script)

Selenium을 사용하면 JavaScript 코드를 웹 페이지에서 직접 실행할 수 있습니다. 이는 특정 스크립트 실행, 페이지의 동적 변경 사항 적용, 스크롤 조작 등에 사용됩니다.

```python
from selenium import webdriver

driver = webdriver.Chrome('/path/to/chromedriver')
driver.get('https://www.example.com/')

# 페이지의 제목을 JavaScript를 사용하여 가져오기
title = driver.execute_script("return document.title;")
print(title)

# 페이지 하단으로 스크롤
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
```

이 예제들은 Selenium과 WebDriver를 사용하여 웹 페이지와의 상호작용을 자동화하는 기본적인 방법들을 보여줍니다. 클릭, 키 입력 전송, 스크린샷 저장, JavaScript 실행 기능은 웹 테스팅 및 자동화에 광범위하게 활용됩니다.


## 주의사항

1. **암묵적 대기**: 웹 페이지의 모든 요소가 로드될 때까지 기다리는 데 사용됩니다. `implicitly_wait` 메서드를 사용하여 설정할 수 있습니다.
   ```python
   driver.implicitly_wait(10)  # 최대 10초 동안 대기
   ```
2. **명시적 대기**: 특정 조건까지 대기하는 것으로, `WebDriverWait`와 `expected_conditions`을 사용하여 설정합니다.
3. **WebDriver 경로**: `webdriver.Chrome()`을 사용할 때 WebDriver의 경로를 지정해야 합니다. 환경 변수에 WebDriver 경로를 추가하면 코드 내에서 경로를 직접 지정하지 않아도 됩니다.
4. **WebDriver 종료**: 작업 완료 후 `driver.quit()` 메서드를 사용하여 WebDriver 세션을 종료해야 합니다. 이는 시스템 리소스를 해제하고 메모리 누수를 방지합니다.

이 가이드는 Selenium을 사용하여 웹 페이지에서 XPath를 활용해 요소를 선택하고 상호작용하는 기본적인 방법을 설명합니다. XPath는 웹 페이지의 구조를 기반으로 요소를 정밀하게 선택할 수 있게 해주므로, 웹 자동화 및 테스팅에 매우 유용합니다.