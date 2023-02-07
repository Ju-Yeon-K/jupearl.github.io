---
title: "[Algorithm] merge sort"
last_modified_at: 
categories:
  - Algorithm
tags:
  - Post Formats
  - readability
  - standard
---


##  **재귀를 통한 merge sort 구현**
<br>


```python

def partial_sort(arr:list):   #[   [  ]   ,   [   ]    ] 형태로 입력됨

    partial_sorted_list = []
    while len(arr[0]) or len(arr[1]):
        
        arr = list(filter(lambda x : bool(x), arr)) # 빈 리스트 있으면 삭제
        if len(arr) == 1:
            partial_sorted_list.extend(arr[0]) # 요소 여러개일수도 있으니까 append 가 아닌 extend
            break 
        elif arr[0][0] < arr[1][0]:
            partial_sorted_list.append(arr[0].pop(0))
        elif arr[0][0] > arr[1][0]:
            partial_sorted_list.append(arr[1].pop(0))
        elif arr[0][0] == arr[1][0]:
            partial_sorted_list.append(arr[1].pop(0))            
            partial_sorted_list.append(arr[0].pop(0))

    return partial_sorted_list


def merge_sort(lst):
    
    if len(lst) == 1:
        return lst
    elif len(lst) == 2:
        return partial_sort([[lst[0]],[lst[1]]])
    else:
        N = len(lst) // 2
        return partial_sort([merge_sort(lst[:N]), merge_sort(lst[N:])])

```
```
- 구현 중 했던 생각들
index error : 
 - partial_sort 함수 내부 에서 'while arr' ->  'while len(arr[0]) or len(arr[1])'

```