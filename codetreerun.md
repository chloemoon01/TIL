```
n = int(input())

arr = [0] * 201   # 음수 대비해서 넉넉히
offset = 100     # 0을 중앙으로 만들기

cur = offset       # 시작 위치
cnt = 0

for _ in range(n):
    x, d = input().split()
    x = int(x)
    
    if d == 'R':
        for _ in range(x):
            arr[cur] += 1
            cur += 1
    else:  # L
        for _ in range(x):
            cur -= 1 # 순서 유의 좌측은 cur 먼저
            arr[cur] += 1

# 2번 이상 지난 구간 세기
for i in arr:
    if i >= 2:
        cnt += 1

print(cnt)
```
offset 설정해서 위치를 추가로 기록하는 것이 중요함

```
n = int(input())

SIZE = 200001
OFFSET = 100000

white = [0]*SIZE
black = [0]*SIZE
color = [0]*SIZE   # 0 없음, 1 흰색, 2 검은색, 3 회색

cur = OFFSET

for _ in range(n):
    x, d = input().split()
    x = int(x)

    if d == 'R':
        for i in range(x):
            pos = cur + i

            if color[pos] == 3:
                continue

            black[pos] += 1
            color[pos] = 2

            if white[pos] >= 2 and black[pos] >= 2:
                color[pos] = 3

        cur = cur + x - 1

    else:  # L
        for i in range(x):
            pos = cur - i

            if color[pos] == 3:
                continue

            white[pos] += 1
            color[pos] = 1

            if white[pos] >= 2 and black[pos] >= 2:
                color[pos] = 3

        cur = cur - x + 1

w = b = g = 0

for c in color:
    if c == 1:
        w += 1
    elif c == 2:
        b += 1
    elif c == 3:
        g += 1

print(w, b, g)
```
꺼져라 그냥
