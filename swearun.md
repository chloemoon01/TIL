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
---
## 6224

input을 어디서 하느냐라는 문제에 봉착하다
그리고 import random은 해야하는 게 맞았음 ~~이게 왜 if문제야 ㅡㅡ~~

---
## 6226

7의 배수-5의배수

```
result = []

for i in range(1, 201):
    # 7의 배수이면서(and) 5의 배수는 아닌(!=) 경우
    if i % 7 == 0 and i % 5 != 0:
        result.append(str(i)) # join을 쓰기 위해 미리 문자열로 저장합니다.

# 리스트 안의 문자열들을 콤마(,)로 이어붙입니다. (띄어쓰기 없음)
print(",".join(result))
```

and i % 5 != 0: 리스트에 먼저 넣었다가 나중에 빼는 것보다, 처음부터 5의 배수가 아닌 것만 골라서 넣는 것이 훨씬 안전하고 빠름

",".join(result): 이 함수는 리스트 ['7', '14', '21']을 "7,14,21"이라는 하나의 문자열로 합쳐줍니다. 띄어쓰기 없이 딱 붙어서 출력

*주의: join을 쓰려면 리스트 안의 요소들이 반드시 **문자열(str)*이어야 합니다.

빡고수방식
`print(",".join([str(i) for i in range(1, 201) if i % 7 == 0 and i % 5 != 0]))`

---

# join
1. 기본 공식
"연결고리".join(리스트)

join은 특이하게 합쳐줄 '연결고리(구분자)'가 주인공이 되어 리스트를 불러오는 방식입니다.

2. 예시로 이해하기

```
fruits = ['사과', '바나나', '포도']

# 1. 쉼표(,)로 연결하고 싶을 때
print(",".join(fruits))  
# 출력: 사과,바나나,포도

# 2. 공백(띄어쓰기)으로 연결하고 싶을 때
print(" ".join(fruits))  
# 출력: 사과 바나나 포도

# 3. 줄바꿈(\n)으로 연결하고 싶을 때
print("\n".join(fruits))
# 출력:
# 사과
# 바나나
# 포도
```

3. 주의사항 (가장 중요!)
join()은 문자열 리스트에만 사용할 수 있습니다. 리스트 안에 숫자가 들어있으면 에러

❌ 안 되는 예: ",".join([1, 2, 3]) → TypeError 발생!

✅ 해결 방법: 숫자를 str()로 감싸서 문자열로 바꿔줘야 합니다.

` result.append(str(i))`

4. 왜 print(result)보다 좋은가요?
그냥 리스트를 출력하면 파이썬은 우리에게 "이건 리스트야!"라고 친절히(?) 알려주려고 여러 가지를 덧붙입니다.

print(result) → ['7', '14', '21'] (대괄호, 작은따옴표, 띄어쓰기 포함)

print(",".join(result)) → 7,14,21 (딱 우리가 원하는 알맹이만!)

요약하자면: 리스트에 담긴 데이터들을 사용자가 보기 좋게 한 줄로 예쁘게 출력해야 할 때 join을 쓰면 만점짜리 답안지가 됩니다.

