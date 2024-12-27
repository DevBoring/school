
### 解題思路：
1. 使用一個空的列表 `tails` 來存儲當前找到的最長不下降子序列的結尾元素。
2. 遍歷 `nums` 中的每個元素，使用 `bisect.bisect_right` 找到該元素在 `tails` 中應該插入的位置。
3. 如果該位置等於 `tails` 的長度，則將該元素添加到 `tails` 中；否則，更新該位置的元素為當前元素。
4. 最後，`tails` 的長度為最長不下降子序列的長度。

### 解答範例：
以下是這個題目的解答：

```python
from bisect import bisect_right

def length_of_lis(nums):
    if not nums:
        return 0
    
    tails = []
    
    for num in nums:
        pos = bisect_right(tails, num)
        if pos == len(tails):
            tails.append(num)
        else:
            tails[pos] = num
            
    return len(tails)

# 測試範例
print(length_of_lis([10, 9, 2, 5, 3, 7, 101, 18]))  # 輸出: 4
print(length_of_lis([0, 1, 0, 3, 2, 3]))            # 輸出: 4
print(length_of_lis([]))                             # 輸出: 0
print(length_of_lis([7, 7, 7, 7, 7, 7, 7]))         # 輸出: 1
```
