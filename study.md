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
