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
