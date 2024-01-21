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
