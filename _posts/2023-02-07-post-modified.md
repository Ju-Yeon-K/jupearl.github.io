---
title: "swea 함수로 구현"
last_modified_at: 2016-03-09T16:20:02-05:00
categories:
  - Algorithm
tags:
  - Post Formats
  - readability
  - standard
---


# swea 1211
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