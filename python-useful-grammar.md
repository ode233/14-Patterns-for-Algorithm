# 用python写算法题的一些常用语法总结

*  #### zip():  
```python 
list(zip(list1, list2)) # 将两个列表对应元素组合成元组形成新的列表 
list1, list2 = zip(*zip(list1, list2))  # 解压返回原列表
```

*  #### deque():
```python
# 双向队列，要使用队列的时候就用它
from collections import deque  
```

*  #### defaultdict():
```python
# 带默认值的字典
from collections import defaultdict
# 默认值为0
dic = defaultdict(int)  
```

*  #### heapq:
```python
# 是最小优先队列  
heapify(list)  # 将列表转化为heap，原地，线性时间内
heappush(heap, item)  
heappop(heap)  
# 如果需要最大优先队列，稍微处理下用最小优先队列存入原值的相反数即可。
```

*  #### lambda:
```python
# 匿名函数，可接受任意数量的参数，但只能有一个表达式。  
lambda arguments : expression   # 传入参数，执行表达式，返回表达式的结果  
# 排序时指定按元素中的哪一个对象来排序：  
list1.sort(key=lambda x: x[0])  # x表示列表中的元素，指定按x[0]来排序
```

*  #### bisect:
```python
bisect.bisect(list1, target)    # 使用二分搜索返回target在列表list1中应该插入的位置的索引（从小到大排列）
```

*  #### float("inf)":
```python
# 正无穷大和负无穷大
float("inf)"
float("-inf)"
```

*  #### nonlocal:
```python
# 递归函数中修改函数外的变量要用到，否则是当作函数内变量来操作
res = 0
def helper():
    nonlocal res
    res = 1
```

*  #### 列表元素的浅拷贝与深拷贝:
```python
# 这是对列表中的[]元素浅拷贝n次
list1 = [[]] * n
# 这是对列表中的[]元素深拷贝n次
list1 = [[] for _ in range(n)] 
# 另外对整个列表深拷贝是
list1 = []
list2 = list1.copy()
```

*  #### enumerate:
```python
# enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。
seq = ['one', 'two', 'three']
for i, element in enumerate(seq):
    print(i, element)
```

*  #### 反转:
```python
# 列表原地反转
list1 = [1，2，3，4]
list1.reverse()
# 字符串或列表拷贝反转
# 切片的参数分别是截取起始位置、截取终止位置、截取步长
s = "abcd"
new_s = s[::-1]
# 指定反转2到3位
new_s = s[2:0:-1]
```