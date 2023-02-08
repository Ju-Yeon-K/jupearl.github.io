---
title: "[SWEA] 11729 하노이의 탑 일반적인 풀이"
last_modified_at: 
categories:
  - SWEA
tags:
  - Post Formats
  - readability
  - standard
---


##  **[SWEA] 11729 하노이의 탑 일반적인 풀이**
<br>

```python
def hanoi(N, start, path, end):
    if N == 1:
        print(f'{1}번 블럭을 {start} 에서 {end}로 옮긴다. ')

    elif N > 1:
        hanoi(N-1, start, end, path)
        print(f'{N}번 블럭을 {start} 에서 {end}로 옮긴다. ')
        hanoi(N-1, path, start, end)

N = int(input())
print(2 ** N -1) # 
hanoi(N, 1, 2, 3)
```
머릿속 구현 단계를 정리한 그림 
![하노이그림](../photos/images/11729_image1.jpeg) {: width="30%" height="50%"0}

```
구현 중 생각했던 점
- round 때문에 계속 소수점 올려서 프린트 되었던 듯. 
  round(3.5) = 4 , round(4.5) = 4 

```
