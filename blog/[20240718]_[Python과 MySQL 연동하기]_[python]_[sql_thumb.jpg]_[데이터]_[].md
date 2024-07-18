# Jupyter와 MySQL 연동하기
## 목차
1. SQL과 연동하면 좋은점
2. 연동 방법
3. 활용

### SQL과 연동하면 좋은점
SQL과 파이썬을 연동하면 좋은 점을 AI에게 물어본 결과,

1. 데이터 처리 효율성: SQL은 **대량의 데이터**를 효율적으로 쿼리하고 처리할 수 있고 파이썬과 연결하면 SQL의 이런 강점을 활용하면서 **파이썬의 유연성**도 활용할 수 있다는 장점이 있습니다.
2. 자동화: 데이터베이스 작업을 **파이썬 스크립트**로 자동화할 수 있습니다.
3. 데이터 분석: SQL로 데이터를 추출한 후 파이썬의 강력한 **데이터 분석 라이브러리(pandas, NumPy 등)**를 사용할 수 있습니다.
4. 웹 개발: 파이썬 웹 프레임워크(Django, Flask 등)와 SQL 데이터베이스를 연동해 풀스택 웹 애플리케이션을 개발할 수 있습니다.
5. 유연한 데이터 조작: SQL 쿼리 결과를 **파이썬 객체로 쉽게 변환하여 추가 처리**할 수 있습니다.

이 중에서 데이터를 불러와 **파이썬 스크립트와 데이터 분석 라이브러리**를 이용할 수 있는 것이 강점인 것 같습니다.

### 연동 방법
연동 방법은 다음과 같습니다.

#### 1. pymysql 설치
파이썬에는 pymysql 라이브러리가 있는데, 이를 아나콘다 Environments에서 설치해 줍니다.
![install_pymysql](Donggyu-Kim1/blog1/img/install_pymysql.png)

#### 2. import pymysql
그 다음 import pymysql 모듈을 추가합니다.
```py
import pymysql
```

### 활용

#### 1. MySQL과 연결하기
```py
# mysql 연결하기
conn = pymysql.connect(
    user = '유저명',
    passwd = '지정한 비밀번호',
    host = 'ip 주소', # 일반적으로 127.0.0.1 혹은 localhost
    db = 'DB명',
    charset = 'utf8'
)
```
connect로 불러올 DB의 정보를 입력하여 mysql 서버와 연결합니다.

#### 2. 커서 지정
```py
mycursor = conn.cursor()
```
DB 커서 객체를 지정합니다. 커서의 경우, 데이터 중 특정 위치를 가리킬 때 사용됩니다.

#### 3.SQL에서 테이블 불러오기
```py
query = """
select * from goods;
"""
```
query로 sql 구문을 작성하여 query로 데이터를 불러옵니다.

goods는 테이블명이고 '*'는 모든 칼럼을 불러옵니다.

```py
mycursor.execute(query)
```
지정한 커서명.execute(query)로 쿼리를 실행합니다.

```py
data = mycursor.fetchall()
# 서버로부터 모든 데이터를 받아옴
conn.close()
# 데이터베이터와의 연결 종료
```
fetch는 데이터를 받아오고 fetchall은 모든 데이터를 받아오게 됩니다.

이를 data에 저장해 줍니다.

데이터를 다 불러왔으면 close로 데이터베이스와 연결을 종료합니다.

#### 4. data 확인하기
![data](Donggyu-Kim1/blog1/img/dataset.png)
이를 통해, MySQL에 있는 테이블 불러 올 수 있습니다.

하지만, 사진처럼 튜플 형태로 되어 있고 칼럼명도 확인할 수 없어 상당히 불편합니다.

따라서, 이를 판다스 라이브러리를 통해 테이블을 다시 생성해줘야 합니다.

#### 5. 판다스 라이브러리를 통해 데이터 테이블 재생성

```py
import pandas as pd
from sqlalchemy import create_engine
```
판다스에서 sql을 연결할 때는 **SQLalchemy ORM**을 사용하게 되는데 

**ORM**이란 어플리케이션과 데이터 베이스를 연결할 때 **sql이 아닌 어플리케이션 개발 언어**로 데이터베이스를 접근할 수 있게 해주는 툴입니다.

```py
# engine = create_engine('mysql+pymysql://[사용자명]:[비밀번호]@[host:포트]/[데이터베이스명]')
engine = create_engine('mysql+pymysql://root:3406@localhost:3306/shop')

query = """select * from goods;"""
goods = pd.read_sql(query, con=engine)
# read_sql(쿼리, 연결정보)로 데이터 프레임 형태로 데이터를 불러옴
engine.dispose()
# dispose로 연결 종료
```
engine으로 DB를 불러오고 query를 통해 테이블을 생성해줍니다.

pandas 문법인 read_sql(쿼리, 연결정보)로 데이터 프레임 형태로 데이터를 불러옵니다.

마찬가지로 데이터를 다 불러왔으면 dispose로 연결을 종료해줍니다.

테이블을 확인해보면, 
![pandas_table](Donggyu-Kim1/blog1/img/table_sql.png)
깔끔한 테이블을 확인할 수 있습니다.

#### 6. 반대로 Python에서 SQL 데이터 테이블 생성
```py
import seaborn as sns

iris = sns.load_dataset('iris')
```
seaborn라이브러리로 테이블을 불러와 

```py
engine = create_engine('mysql+pymysql://root:3406@localhost:3306/shop')
iris.to_sql(name='iris', con=engine, index=False, if_exists='replace')
# name = 테이블명, con = 연결정보, index 번호 없이 생성할 시 False, if_exists='replace': 해당 테이블이 존재할 시 덮어씌움
```
위 코드를 작성하여 sql로 보냅니다.


이를 통해, SQL 데이터를 불러와 파이썬에서 분석하고 다시 SQL에 데이터를 저장할 수 있습니다.