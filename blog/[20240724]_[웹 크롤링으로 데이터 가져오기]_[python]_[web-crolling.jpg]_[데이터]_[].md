# 웹 크롤링 실습

## 목차
1. 크롤링 시 주의해야 할 점
2. GET 방식, POST 방식
3. Quotes To Scrape 크롤링 - find_all
4. Quotes To Scrape 크롤링 - select

### 크롤링 시 주의해야 할 점

- 무한 크롤링: 특정 웹 사이트의 페이지를 쉬지 않고 크롤링하는 행위로, 이로 인해 **타인의 사용을 막고** 웹 사이트에 부하를 줍니다.
- 저작권 문제: 신문기사, 책, 논문, 사진 등 저작권이 있는 자료를 통해 부당이득을 얻는 행위를 할 경우 **법적 제재**를 받을 수 있습니다.

### GET, POST

- GET 방식이란, 서버로부터 데이터를 요청하기 위해 URL에 필요한 정보를 담아 전송하는 방법입니다.

- POST 방식이란, 서버로 데이터를 제출하기 위해 HTTP Body에 데이터를 담아 전송하는 방법입니다.
    - POST 방식을 알려면 개발자 도구 -> Network -> Headers의 Request Method를 봐야 합니다.
    - POST 방식은 URL에 정보가 나오지 않기 때문에 위와 같은 방식으로 들어가면 Payload에 나와 있습니다.

###  Quotes To Scrape 페이지 크롤링하기 - find_all

[Quotes to Scrape](https://quotes.toscrape.com/) 크롤링

크롤링을 하기 위해선 내가 어떤 데이터를 가져올 것인지 개발자도구를 통해 태그의 위치를 찾아야 합니다.

```py
import requests as rq
```
이 사이트의 경우, 클릭 시 url이 바뀌는 것을 알 수 있습니다. 따라서, 이 페이지는 get 방식을 사용합니다.
따라서, 코드는 다음과 같습니다.
```py
url = 'https://quotes.toscrape.com/'
quote = rq.get(url)
quote
```
quote 실행 시 response 200이 나오게 되는데 200번대가 나왔다는 것은 정상적으로 작동했다는 것을 의미합니다.

```py
quote.content
```
를 실행 시 html 구조가 나오지만, 읽기 굉장히 힘든 것을 알 수 있습니다.

따라서 beautifulsoup를 이용해야 합니다.

```py
from bs4 import BeautifulSoup

quote_html = BeautifulSoup(quote.content)
```
quote.content가 html 구조를 담고 있기 때문에 이를 BeautifulSoup 안에 넣고 quote_html을 실행하면
![html](img/html-beautifulsoup.png)

일부분이긴 하지만 html 구조로 되어 있어 읽기 편하졌습니다. 이제 페이지에서 명언 부분만을 불러오기 위해

find_all을 활용합니다.

```py
# div 태그의 class가 quote인 부분
# class로 찾을 시 언더 바(_) 붙이기
quote_div = quote_html.find_all('div', class_ = 'quote')
```
그러면 quote_div의 첫번째 부분이 다음과 같이 나오는 것을 알 수 있습니다.
![quote_div[0]](img/quote_div[0].png)

quote_div에서 다시 한 번 첫번째 부분의 명언 text만 추출하기 위해서 find_all을 활용합니다.

```py
quote_div[0].find_all('span', class_='text')[0].text
```
“The world as we have created it is a process of our thinking. It cannot be changed without changing our thinking.”

이렇게 나오는 것을 확인할 수 있습니다.

이제 for문을 활용한다면 페이지에 있는 명언 부분 모두를 추출하여 list에 담을 수 있습니다.

```py
[i.find_all('span', class_='text')[0].text for i in quote_div]
```
결과 값:

['“The world as we have created it is a process of our thinking. It cannot be changed without changing our thinking.”',

 '“It is our choices, Harry, that show what we truly are, far more than our abilities.”',

 '“There are only two ways to live your life. One is as though nothing is a miracle. The other is as though everything is a miracle.”',

 '“The person, be it gentleman or lady, who has not pleasure in a good novel, must be intolerably stupid.”',

 "“Imperfection is beauty, madness is genius and it's better to be absolutely ridiculous than absolutely boring.”",

 '“Try not to become a man of success. Rather become a man of value.”',

 '“It is better to be hated for what you are than to be loved for what you are not.”',

 "“I have not failed. I've just found 10,000 ways that won't work.”",

 "“A woman is like a tea bag; you never know how strong it is until it's in hot water.”",

 '“A day without sunshine is like, you know, night.”']

### Quotes To Scrape 페이지 크롤링하기 - select

하지만, 여러 태그를 타고 들어가야 정보를 찾을 수 있다면 find_all을 여러번 사용해야 하는 번거로움이 있습니다.

따라서, 이를 해결하기 위해 select 함수를 통해 좀 더 쉽게 데이터에 접근할 수 있습니다.

```py
# class명이 quote인 div >(하부) class명이 text인 span
quote_text = quote_html.select('div.quote > span.text')
[i.text for i in quote_text]
```
그러면 위 결과 값과 동일한 값을 추출하게 됩니다.