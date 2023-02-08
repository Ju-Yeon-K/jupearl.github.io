---
title: "[SWEA] 11729 하노이의 탑"
last_modified_at: 
categories:
  - SWEA
tags:
  - Post Formats
  - readability
  - standard
---

### [SWEA] 11729 하노이의 탑
체감 난이도 : 🎈🎈🎈 **/5**   

문제에서 요구하는 출력값이랑 형식은 조금 다르게 작성하였음. (이해하기 쉽게)
```python
def hanoi(N, start, path, end):
    if N == 1:
        print(f'{1}번 블럭을 {start} 에서 {end}로 옮긴다. ')

    elif N > 1:
        hanoi(N-1, start, end, path)
        print(f'{N}번 블럭을 {start} 에서 {end}로 옮긴다. ')
        hanoi(N-1, path, start, end)

N = int(input())
print(2 ** N -1) 
# 총 이동 횟수 : 계산하여 수식으로 표시함. 
# 다만 재귀함수에서 변수 할당으로 hanoi함수의 리턴값으로도 받을 수 있음. 
hanoi(N, 1, 2, 3)
```


### 💭Idea들 
end point 를 픽스할 경우 (문제의 경우 3번 막대)
N 이 짝수일 경우와 홀수일 경우 첫번째 블럭이 이동하는 막대가 달랐음. 
이를 나누어 1차 시도하였으나 함수의 variable 에 내가 임의로 
end 에 해당하는 의미를 부여해 간결한 코드작성이 가능하였음. 

