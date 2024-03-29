- enumerate
```
for entry in enumerate(['A', 'B', 'C']):
...     print(entry)
...
(0, 'A')
(1, 'B')
(2, 'C')

for i, letter in enumerate(['A', 'B', 'C'], start=101):
...     print(i, letter)
...
101 A
102 B
103 C

```
- pip install requests
- from 상위 폴더 import 하위폴더
- map(,)
```
user_list = []

def create_user(name, age, address):
    user_info = {}
    user_info['name'] = name
    user_info['age'] = age
    user_info['address'] = address
    user_list.append(user_info)
    print(f'{name}님 환영합니다!')
    return user_info

name = ['김시습', '허균', '남영로', '임제', '박지원']
age = [20, 16, 52, 36, 60]
address = ['서울', '강릉', '조선', '나주', '한성부']

user_info_list = list(map(create_user, name, age, address))

print(user_info_list)
```

- 여러명의 데이터 수집
```
import requests
from pprint import pprint as print

dummy_data = []

for i in range(1,11):
    # 무작위 유저 정보 요청 경로
    API_URL = f'https://jsonplaceholder.typicode.com/users/{i}'
    # API 요청
    response = requests.get(API_URL)
    # JSON -> dict 데이터 변환
    parsed_data = response.json()
    dummy_data.append(parsed_data['name'])

print(dummy_data)
```

reversed 로 문자열 거꾸로 출력하기
```
# # def reverse_string(stri):
#     sum = ''
#     for char in reversed(stri):
#         sum += char
#     return sum


# result = reverse_string("Hello, World!")
# print(result)  # !dlroW ,olleH

def reverse_string(stri):
    talk = ''.join(reversed(stri))
    return talk

result = reverse_string(list("Hello, World!"))
print(result)  # !dlroW ,olleH
```

반복문에서도 한줄로 출력하기
```
예시코드
arr = [1, 2, 3, 4, 5]
for num in arr:
    print(num, end='')
출력결과 : 12345
```

- list.sort() vs sorted(list)
    - sort는 리스트에만 사용가능, 원본 리스트 자체를 오름차순으로 정렬
    - sorted는 다른 시퀀스에도 적용가능, 리스트를 오름차순으로 정렬한 복제본을 만든다
```
# tuple 정렬하기 sol1) 
def sort_tuple(origin_tuple):
    sorting = sorted(origin_tuple) # 오름차순하고 리스트로 반환
    new_tuple = tuple(sorting)  # 다시 튜플 씌우기
    return new_tuple

result = sort_tuple((5, 2, 8, 1, 3))
print(result)

# sol2)
def sort_tuple(origin_tuple):
    new_list = []
    new_list.extend(origin_tuple)  # extend로 인해 튜플이 벗겨진 채로 리스트에 추가
    new_tuple = tuple(sorted(new_list))
    return new_tuple

result = sort_tuple((5, 2, 8, 1, 3))
print(result)
```
대문자 소문자 바꾸기
```
def capitalize_words(stri):
    word = stri.title() # 문자열 내 띄어쓰기 기준으로 각 단어의 첫글자는 대문자로, 나머지는 소문자로 변환한다.
    word = stri.capitalize() # 첫 글자만 대문자
    return word

result = capitalize_words("hello, world!")
print(result)

# title 안쓰고 풀기
'''
def capitalize_words(stri):
    text = stri
    text = text.replace(text[0],text[0].upper())
    for i in range(1,len(stri)):
        if stri[i-1] == ' ':
            text = text.replace(text[i],text[i].upper())
    return text

result = capitalize_words("hello, world!")
print(result)
'''
```

dict value 값 얻기
```
dict.get(key)  # key 값 없으면 None 반 // dict.get(key, 'Unknown') -> Key 없을때 Unknown 반환
# or
dict[key]
```

객체 클래스 예외처리 문제
```
class UserInfo:
    def __init__(self):
        self.user_data = {}
    
    def get_user_info(self):
        try:
            name = input("이름을 입력하세요: ")
            age = int(input("나이를 입력하세요: "))
            self.user_data['이름'] = name
            self.user_data['나이'] = age
        except ValueError:
            print('나이는 숫자로 입력해야 합니다.')

    def display_user_info(self):
        if not self.user_data:
            print('사용자 정보가 입력되지 않았습니다.')
        else:
            # print('사용자 정보:')
            # print('이름:', self.user_data['이름'])
            # print('나이:', self.user_data['나이'])
            print(f'사용자 정보:\n이름: {self.user_data['이름']}\n나이: {self.user_data['나이']}')
            # print('사용자 정보:')
            # for k, v in self.user_data.items():
            #     print(f'{k} : {v}')

user = UserInfo()
user.get_user_info()
user.display_user_info()
```

SWEA View 문제 코드
```
for tc in range(10):
    N = int(input())
    height = list(map(int, input().split()))

    result = 0

    for index in range(2, N - 2):
        near_height_list = [height[index - 2], height[index - 1], height[index + 1], height[index + 2]]
        temp = max(near_height_list)

        if height[index] > temp:
            result += height[index] - temp

    print(f'#{tc + 1} {result}')
```

버블 정렬
```
N = 6
arr = [7, 2, 5, 3, 1, 4]

for i in range(N-1):
    for j in range(i+1, N):
        if arr[i] > arr[j]:
            arr[i], arr[j] = arr[j], arr[i]

print(arr)


for i in range(N-1,0,-1):
    for j in range(0,i):
        if arr[j] > arr[j+1]:
            arr[j], arr[j+1] = arr[j+1], arr[i]

print(arr)
```
