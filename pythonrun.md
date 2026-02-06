```
a = float(input())
b = a*2.54
print(f'{a:.2f} inch => {b} cm')
```

옛날 방식 (쉼표 사용): `print(a, "inch =>", b, "cm")`

띄어쓰기가 제멋대로 들어가고 소수점 조절이 까다로움.

f-스트링 방식: `print(f"{a:.2f} inch => {b} cm")`



문장 전체를 미리 써놓고, 값이 들어갈 자리만 {}로 뚫어 놓는 식이라 가독성 굿

데이터 (a) 어떤 변수(또는 값)를 가져올 것인가?

구분자 (:) 이제부터 이 데이터를 어떻게 보여줄지 명령

형식 (.2f) 소수점 아래 둘째 자리까지 표시하라는 구체적인 방법

---

```
a = int(input())
count = 0

for i in range(1, a+1):
    if a % i ==0:
        print(f'{i}(은)는 {a}의 약수입니다.')
        count += 1
    if count ==2:
              print(f'{a}(은)는 1과  {a}로만 나눌 수 있는 소수입니다.')
```
약수의 조건은 나머지가 0이어야 하므로 if 문에서 사용

소수의 조건은 1과 자기 자신을 몫으로 가지므로 count 변수 추가해 2일 경우 소수

---
```
t = int(input()) 

for i in range(1, t + 1): # 1부터 t까지 반복
    s = input()
    if s.isupper():
        print(f'#{i} {s} 는 대문자 입니다.')
    else:
        print(f'#{i} {s} 는 소문자 입니다.')
```
#1, #2, #3 식으로 출력하려면 
for i in range(1, t+1) 필요 *그래야 {i}가 늘어남

---


