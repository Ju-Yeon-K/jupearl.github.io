---
title: "[SWEA] 1210 Ladder1, 1211 Ladder2"
last_modified_at: 
categories:
  - SWEA
tags:
  - Post Formats
  - readability
  - standard
---

### [1] [SWEA] 1210 Ladder1
체감 난이도 : 🎈🎈**/5**   

```python
def move_of_dot(a:list,x:int,y:int):

    if (not area[x][y-1]) and (not area[x][y+1]):  # area[i][j] 양 옆이 0 일때 
        x -= 1  # area[i][j] -> area[i-1][j]
        
    elif area[x][y-1] and (not area[x][y+1]):  # area[i][j] 왼쪽 1 일때
        while area[x][y-1]: # area[i][j] -> area[i][j-1...] 0 될 때까지 탐색
            y -= 1
        x -= 1  # area[i][j-k] -> area[i-1][j-k]
    
    elif (not area[x][y-1]) and area[x][y+1]:  # area[i][j] 오른쪽 1 일때
        while area[x][y+1]: # area[i][j] -> area[i][j+1...] 0 될 때까지 탐색
            y += 1
        x -= 1  # area[i][j-k] -> area[i-1][j-k] 
    
    else: pass
    
    return (x,y)


for tc in range(10):
    N = int(input())
    area = [[0]+list(map(int,input().split()))+[0] for i in range (100)] 
    # index : (0,0) (0,1) ,,, (99,100) (99,101)
    
    y = area[-1].index(2)
    x = 99
    while x:
        x, y = move_of_dot(area, x, y)

    print(f'#{tc+1} {y-1}') # area 양옆에 0 추가해주었으니 보정

```

### 💭Idea들 
psudocode 꼼꼼하게 작성하니 의외로 손쉽게 풀렸음.   
다만 아래의 -1 때문에 고민하는 시간이 길었음. 
```python
print(f'#{tc+1} {y_result-1}') # area 양옆에 0 추가해주었으니 보정
```
index 다루는 연습 많이 할 필요 있음.




### [2] [SWEA] 1211 Ladder2
체감 난이도 : 🎈🎈**/5**   
1210 문제에서 구현한 move_of_dot 함수를 그대로 이용하였음.

```python
def move_of_dot(a:list,x:int,y:int):

    n = 0
    
    if (not area[x][y-1]) and (not area[x][y+1]):  # area[i][j] 양 옆이 0 일때 
        x += 1  # area[i][j] -> area[i-1][j]
        n += 1
        
    elif area[x][y-1] and (not area[x][y+1]):  # area[i][j] 왼쪽 1 일때
        while area[x][y-1]: # area[i][j] -> area[i][j-1...] 0 될 때까지 탐색
            y -= 1
            n += 1
        x += 1  # area[i][j-k] -> area[i-1][j-k]
        n += 1        
    
    elif (not area[x][y-1]) and area[x][y+1]:  # area[i][j] 오른쪽 1 일때
        while area[x][y+1]: # area[i][j] -> area[i][j+1...] 0 될 때까지 탐색
            y += 1
            n += 1
        x += 1  # area[i][j-k] -> area[i-1][j-k] 
        n += 1
            
    else: pass
    
    return (x,y,n)


for tc in range(10):
    N = int(input())
    area = [[0]+list(map(int,input().split()))+[0] for _ in range (100)] 
    # index : (0,0) (0,1) ,,, (99,100) (99,101)

    y_result = 0
    min_length = 10000

    for y in range(1,101):
        x = 0    
        length = 0        
        if area[0][y]:
            temp = y-1
            while x < 99:
                x, y, n = move_of_dot(area, x, y)
                length += n
            if length <= min_length:
                min_length = length
                y_result = temp

    print(f'#{tc+1} {y_result}') 
```

### 💭Idea들 
딱히 문제 없었음.