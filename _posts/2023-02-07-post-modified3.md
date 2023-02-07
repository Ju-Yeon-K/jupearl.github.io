---
title: "[SWEA] 6019 기차 사이의 파리"
last_modified_at: 
categories:
  - Algorithm
tags:
  - Post Formats
  - readability
  - standard
---

##  **[SWEA] 6019 기차 사이의 파리**
<br>

```python
T = int(input())
for tc in range(1, T+1):
    D, A, B, F = map(int,input().split())
    crush_t = D/(A+B)
    print(f'#{tc} {F * crush_t:.10f}')



# 실행시간을 줄이기 위한 dp 방법
ans = []
T = int(input())
for tc in range(1, T+1):
    D, A, B, F = map(int,input().split())
    res = F * D/(A+B)
    ans.append(f'#{tc} {res}')
for _ in ans:
    print (_)
```

```
구현 중 생각했던 점
- round 때문에 계속 소수점 올려서 프린트 되었던 듯. 
  round(3.5) = 4 , round(4.5) = 4 

```