## 6221

들여쓰기 주의
```
# ㅇㅋ
if a =='가위' and b =='보':
    print('Result : Man1 Win!')
elif a == '바위' and b == '가위':
    print('Result : Man1 Win!')
# ㄴㄴ
if a =='가위' and b =='보':
    print('Result : Man1 Win!')
    elif a == '바위' and b == '가위':
        print('Result : Man1 Win!')
```

리팩토링
```
# or 연산자로 그룹화

a = input()
b = input()

if a == b:
    print('Result : Draw')
# Man1이 이기는 모든 경우의 수를 한 번에 묶기
elif (a == '가위' and b == '보') or (a == '바위' and b == '가위') or (a == '보' and b == '바위'):
    print('Result : Man1 Win!')
else:
    # 비기지도 않았고 Man1이 이기지도 않았다면? 당연히 Man2가 이긴 것!
    print('Result : Man2 Win!')


# 리스트/튜플 활용하기

a = input()
b = input()

# Man1이 이기는 조합들
win_cases = [('가위', '보'), ('바위', '가위'), ('보', '바위')]

if a == b:
    print('Result : Draw')
elif (a, b) in win_cases:  # 입력받은 (a, b) 세트가 저 리스트 안에 있는가?
    print('Result : Man1 Win!')
else:
    print('Result : Man2 Win!')
```
---
## 6222
```
a = input() 
# 입력받은 문자가 알파벳인지 먼저 확인하면 더 정확
if a.isalpha(): 
    if a.isupper(): # 대문자라면
        result = a.lower()
    elif a.islower(): # 소문자라면
        result = a.upper()
    print(f"{a} (ASCII: {ord(a)}) => {result} (ASCII: {ord(result)})")
else:
    # 알파벳이 아닐 경우 그냥 출력
    print(f"{a} (ASCII: {ord(a)})")
```
Q1. 아스키코드 출력 어떻게?
ord(문자): 문자를 해당하는 **아스키코드(정수)**로 변환해줍니다. (Ordinal의 약자)

참고로 반대인 chr(숫자)는 숫자를 문자로 바꿔줍니다.

```
a = input()

# swapcase()는 대문자는 소문자로, 소문자는 대문자로, 나머지는 그대로 둡니다.
result = a.swapcase()

print(f"{a} 의 아스키코드: {ord(a)}")
print(f"변환된 결과: {result}")
```
```
a = input()

# swapcase()는 대문자는 소문자로, 소문자는 대문자로, 나머지는 그대로 둡니다.
result = a.swapcase()

print(f"{a} 의 아스키코드: {ord(a)}")
print(f"변환된 결과: {result}")
```
