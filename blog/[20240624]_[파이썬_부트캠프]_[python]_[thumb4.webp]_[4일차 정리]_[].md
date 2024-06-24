# 4일차 정리

## 오늘의 상식

**AI 스타트업 창업 시 주의할 점**



[AI 스타트업을 구축하는 방법](https://www.news.aakashg.com/p/how-to-build-an-ai-startup)을 보고 참고했음


1. 아이디어는 쉽게 실행 가능해야 함
2. 스타트업을 위협하는 함정들이 존재함
   - 반짝이는 증후군
     * 새 모델 출시 시 방향을 바꾸고 싶은 유혹(피벗)
   - 실험실에선 작동해요
     * 인상적인 연구 결과가 항상 실제 제품과 같은 건 아님
     * 연구보다 제품화에 더 시간을 쏟을 것
   - 무책임한 배포
     * 데이터 개인 정보 보호, 보안, 공정성, 투명성 및 견고성에 신경쓸 것
   - 기능보다 우선 순위 지정을 중요시함
     * 사용자가 실제로 관심을 갖는 것이 무엇인지 잊어버리곤 함
     * problem과 solution에 집중할 것
   - 너무 많이, 너무 빨리 모금하기
     * 현금은 성공을 보장하지 않음
     * **PMF**란 Product/Market fit이라는 뜻으로 **기업의 제품이나 서비스가 시장의 요구와 잘 맞는 지**를 의미
     * PMF에 도달하기 위해 부트스트랩 또는 작은 시드 라운드로 시작할 것.
     * 이는 고객 가치에 부합하는 가격 책정 모델 검증에 도움을 줌

## 함수

**파라미터**

- 함수를 정의할 때 사용하는 변수

def my_function(x, y):  x, y는 파라미터

**아규먼트**

-  함수를 호출할 때 전달하는 실제 값

result = my_function(5, 10):  5, 10은 아규먼트

```
# 기본 값은 정하거나 바꿀 수 있음
# 기본 값 사용 시 아규먼트를 맞추지 않아도 됨

def f(a, b=20, c=10):   # 기본 값: b = 20, c = 10
    print(a, b, c)

f(100, 10) # 출력 값: 100 10 10
f(a=100, b=200, c=300) # 출력 값: 100 200 300
f(c=300, a=100, b=200) # 출력 값: 100 200 300
```

```
def f(a, b=20, c=30):
    print(a, b, c)

# print(f()) # error
print(f(100, 10)) # 출력 값: 100, 10, 30
print(f(a=100, b=200, c=300)) # 출력 값: 100 200 300
print(f(c=300, a=100, b=200)) # 출력 값: 100 200 300
# print(f(c=300)) # error

# a에는 기본값이 없으므로 반드시 a에 대하여 아규먼트를 적용해야 함
```

```
# 권장하지 않는 방법
def append_to_list(value, lst=[]):
    lst.append(value)
    return lst
# 리스트로 하는 경우, 수를 입력할 때마다 추가가 되어 과거 데이터들도 중복될 수 있음

# 권장하는 방법
def append_to_list(value, lst=None):
    if lst is None:
        lst = []
    lst.append(value)
    return lst
```

```
# 지역변수: 함수 내부에서만 정의되고 사용되는 변수

def f():
    a = 1
    print(locals()) # 출력 값: {'a': 1}

def f():
    a = 1
    b = 'hello'
    def ff():
        pass
    print(locals()) 
# 출력 값: {'a': 1, 'b': 'hello', 'ff': <function f.<locals>.ff at 0x7a46e99d2c20>}
f()

# 전역변수: 프로그램 전체, 어떤 함수에서도 접근 가능한 변수
a = 100

def f():
    global a
    a = a + 1

f()
print(a)  
# 출력 값: 101, 함수 f 내에서 전역 변수 a가 수정
```

```
# pass: Python에서 아무 것도 하지 않는 구문

def calculate():
    pass
```

### 함수 실습

1. 사용자로부터 이름을 입력받아 "안녕하세요, [이름]님!"을 출력하는 함수를 작성하세요.

```
def greeting(name):
    print(f"안녕하세요, {name}님!")

name = input("이름을 입력하세요: ")
greeting(name)
```

2. 상품 가격과 수량을 입력받고 총 금액을 산출하시오.

```
def total_price(price, quantity):
    t_price = price * quantity
    return t_price

price = int(input("상품 가격을 입력하세요: "))
quantity = int(input("상품 수량을 입력하세요: "))

print(f"총 금액은 {format(total_price(price, quantity),',')}원 입니다.")
# format 함수를 통해 금액에 , 표시
```

3. 전화번호를 입력받고 마지막 4자리를 출력하세요.

```
def tel(lst):
    ph_num_spl = lst.split('-')
    return ph_num_spl[-1]

phone_num = input("전화번호를 입력하세요. 양식은 000-0000-0000입니다.")

print(f"마지막 네자리는 {tel(phone_num)} 입니다.")
```

4. 주소를 입력 받고 시/도, 구/군을 분리하여 출력하시오.

```
adress = input("주소를 입력하세요: ex) 00시 00구")
def adr(adress):
    adr_list = adress.split()
    print(f"시/도: {adr_list[0]}, 구/군: {adr_list[1]}")

adr(adress)
```

### 빌트인 함수(Built-in Function)

Built-in functions 또는 내장 함수는 파이썬 언어에 기본적으로 포함되어 있는 함수들

요소 전체의 True, False 판별
  - all
  - any


숫자를 문자로 바꾸거나 문자를 숫자로 바꾸는 함수
  - chr
  - ord


함수와 순회할 수 있는 객체의 연산
  - map
  - filter


순회할 수 있는 객체의 묶음
  - zip


형식 변환
  - format


길이 반환
  - len


큰 값, 작은 값, 다 더한 값
  - max
  - min
  - sum


문자열, 대표 문자열, 문자열 출력
  - str
  - repr
  - print


순회할 수 있는 객체
  - enumerate
  - range


역순과 정렬
  - reversed
  - sorted


```
# map : 리스트, 튜플 객체들을 하나씩 계산할 수 있게 하는 함수
def 제곱(x):
    return x ** 2
list(map(제곱, [1, 2, 3, 4])) # 출력 값: [1, 4, 9, 16]

# 람다(lamda)
list(map(lambda x : x ** 2, [1, 2, 3, 4])) # 출력 값: [1, 4, 9, 16]
```
```
# filter(조건 함수, 리스트 또는 튜플)
list(filter(lambda x : x % 2 == 0, [1, 2, 3, 4])) # 출력 값: [2, 4]
```
```
# zip: 여러 개의 순회할 수 있는 객체의 요소를 묶어서 반환, 주소를 알려줌

list(zip([1, 2, 3], [4, 5, 6])) # 출력 값: [(1, 4), (2, 5), (3, 6)]
# list와 함께 활용하면 같은 자리에 있는 데이터들을 묶어줌
```
```
x = [2, 4, 8, 16, 32, 64, 128]
list(zip(x, x[1:], x[2:]))
# 출력 값
[(2, 4, 8), (4, 8, 16), (8, 16, 32), (16, 32, 64), (32, 64, 128)]

# 시계열 데이터 이동평균 값 구하는 방법
```
```
# format(값, '서식 지정자(format_spec)')

print(format(123.4567, '.2f')) #  출력 값: 123.46, 소수점 둘째자리까지
print(format('Hello', '^9')) #  출력 값: '  Hello  ', 9글자 지정
print(format(10000, ',')) #  출력 값: '10,000', 돈
```
```
students = [
    {'이름': '가', '국어': 90, '영어': 72, '수학': 95},
    {'이름': '나', "국어": 80, '영어': 90, '수학': 91},
    {'이름': '다', "국어": 95, '영어': 73, '수학': 92}
]

min(students, key=lambda student: student['수학'])
# 출력 값: {'이름': '나', '국어': 80, '영어': 90, '수학': 91}
```
```
import numpy as np

np.sum([[1, 2], [3, 101], [1, 20], [3, 100]]) # 출력 값: 231
```
```
# range(start, stop, step): 순회할 수 있는 숫자 객체를 만들어주는 함수

range(1, 10, 2) # 출력 값: range(1, 10, 2)
list(range(1, 10, 2)) # 출력 값: [1, 3, 5, 7, 9]
```
```
# enumerate: 반복할 수 있는 객체의 인덱스와 값을 함께 반환하며 주로 반복문에서 사용
values = ['A', 'B', 'C', 'D']
print(list(enumerate(values)))
print(list(enumerate(values, 1)))
print(list(enumerate(values, 100)))
# 출력 값:
# [(0, 'A'), (1, 'B'), (2, 'C'), (3, 'D')]
# [(1, 'A'), (2, 'B'), (3, 'C'), (4, 'D')]
# [(100, 'A'), (101, 'B'), (102, 'C'), (103, 'D')]

# 키 값을 지정해줄 수 있는 함수
```
```
# sorted

print(sorted([1, 5, 4, 100, 2, 3])) 
# 출력 값: [1, 2, 3, 4, 5, 100]

print(sorted(['hello world', 'hell', 'hello'])) 
# 출력 값: ['hell', 'hello', 'hello world']
```
```
list(reversed('hello world'))
# 출력 값: ['d', 'l', 'r', 'o', 'w', ' ', 'o', 'l', 'l', 'e', 'h']

list(reversed([1, 2, 3, 10, 5, 4])) # 역정렬 아님, 역순 o
# 출력 값: [4, 5, 10, 3, 2, 1]

list(reversed(sorted([1, 2, 3, 10, 5, 4])))
# 출력 값: [10, 5, 4, 3, 2, 1]
```

## Tkinter 위젯

이 위젯은 replit.com에서 사용 가능하다.

```
# Tkinter 생성
import tkinter as tk

# 기본 윈도우 생성
root = tk.Tk()

# 윈도우 타이틀 설정
root.title("Tkinker Install")

# 창 크기 설정
root.geometry("400x500")

# 레이블 위젯 추가
label = tk.Label(root, text = "Tkinker Install")
label.pack(padx = 20, pady = 20)

# 버튼 위젯 추가 - 동장에 대한 기능 구현
def on_click():
  print("click button")

def on_button_click():
  label.config(text = "bitton Clicked!")
  entry.text = entry.get()
  label.config(text = entry_text)

# 텍스트 입력을 위한 입력 필드 생성
entry = tk.Entry(root, show = "*", width = 50)
entry.pack(padx = 10, pady = 10)

# 입력 필드의 내용을 가져와서 출력하는 함수
def get_text():
  print(entry.get())

# 입력 내용을 출력하는 버튼
button1 = tk.Button(root, text = 'enter', command = get_text)
button1.pack()

# 동작을 수행하는 버튼
button = tk.Button(root, text = 'click', command = on_click)
button.pack(padx = 10, pady = 10)

# 메인 이벤트 루프 생성
root.mainloop()
```

```
import tkinter as tk

root = tk.Tk()
root.title("Pack 예제")

# 윈도우 크기 설정
root.geometry("300x100")

# 상단에 배치
top_label = tk.Label(root, text="up")
top_label.pack(side=tk.TOP)

# 하단에 배치
bottom_label = tk.Label(root, text="bottom")
bottom_label.pack(side=tk.BOTTOM)

# 왼쪽에 배치
left_label = tk.Label(root, text="left")
left_label.pack(side=tk.LEFT)

# 오른쪽에 배치
right_label = tk.Label(root, text="right")
right_label.pack(side=tk.RIGHT)
```

```
import tkinter as tk

root = tk.Tk()
root.title("Grid 예제")

# 행과 열로 배치
for i in range(3):  # 3행
    for j in range(3):  # 3열
        cell = tk.Label(root, text=f"line {i}, row {j}")
        cell.grid(row=i, column=j)

root.mainloop()
```

```
import tkinter as tk

root = tk.Tk()
root.title("Place 예제")

# 절대 위치 지정
label = tk.Label(root, text="place(x=50, y=100)")
label.place(x=50, y=100)

root.mainloop()
```

```
import tkinter as tk

def handle_click(event):
    print("Button Clicked")

root = tk.Tk()
button = tk.Button(root, text="Click")
button.pack()

# 버튼 클릭 이벤트 바인딩
button.bind("<Button-1>", handle_click)

root.mainloop()
```

```
import tkinter as tk

def handle_keypress(event):
    print(f"press_key: {event.char}")

root = tk.Tk()

# 키보드 이벤트 바인딩
root.bind("<Key>", handle_keypress)

root.mainloop()
```

### Tkinter 위젯 실습

**온도 변환기 만들기**

```
import tkinter as tk

def converter():
  cel = float(entry.get())  # 숫자형 주의
  fah = (cel * 9 / 5) + 32
  result_label.config(text=f"{cel} Celsius is {fah} Fahrenheit")

root = tk.Tk()
root.title("temperature Converter")
root.geometry("300x150")

# 입력필드와 레이블
entry = tk.Entry(root)
entry.pack(pady=10)

# 변환 버튼
convert_button = tk.Button(root, text="cel to fah", command=converter)
convert_button.pack(pady=5)

# 변환 결과
result_label = tk.Label(root, text="result show")
result_label.pack(pady=10)

# 메인 이벤트 루프 실행
root.mainloop()
```

# 마무리
오늘은 함수 정의, 파이썬에서 쓸 수 있는 만들어져 있는 함수, tkinter 위젯에 대하여 배웠다.

![사진](https://images.unsplash.com/photo-1718641731724-0b583a50df1f?q=80&w=2670&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)
