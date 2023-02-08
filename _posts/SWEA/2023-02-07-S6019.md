---
title: "[SWEA] 6019 기차 사이의 파리"
last_modified_at: 
categories:
  - SWEA
tags:
  - Post Formats
  - readability
  - standard
---


### [SWEA] 6019 기차 사이의 파리
체감 난이도 : 🎈**/5**   

```python
T = int(input())
for tc in range(1, T+1):
    D, A, B, F = map(int,input().split())
    crush_t = D/(A+B)
    print(f'#{tc} {F * crush_t:.10f}')
```
```python
# 실행시간을 줄이기 위한 리스트 append 방법
ans = []
T = int(input())
for tc in range(1, T+1):
    D, A, B, F = map(int,input().split())
    res = F * D/(A+B)
    ans.append(f'#{tc} {res}')
for _ in ans:
    print (_)
```

### 💭Idea들 
문제이해를 하니 빠르고 짧게 코드 작성이 가능했음.   
실행시간을 줄이는 방법에는 리스트 append 하여 한번에 프린트하는 방법이 있었음.
이것은 아마.. `print()` 가 인터프리터와의 상호작용을 통해 실행시간이 길게 걸리나.. 하는 추론이 가능하였음. 
이에 대한 공부가 추후 필요함. 
# 나중에 CS 폴더 내 정리해서 링크 걸어둘 것
