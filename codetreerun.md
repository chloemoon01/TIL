/code
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
            cur -= 1
            arr[cur] += 1

# 2번 이상 지난 구간 세기
for i in arr:
    if i >= 2:
        cnt += 1

print(cnt)
