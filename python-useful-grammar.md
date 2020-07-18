# 用python写算法题的一些常用语法总结

*  #### zip():  
list(zip(list1, list2))，将两个列表对应元素组合成元组形成新的列表  
list1, list2 = zip(*zip(list1, list2)) 解压返回原列表

*  #### deque():
from collections import deque  
双向队列，要使用队列的时候就用它

*  #### heapq:
是最小优先队列  
heapify(list)  将列表转化为heap，原地，线性时间内
heappush(heap, item)  
heappop(heap)  
如果需要最大优先队列，稍微处理下用最小优先队列存入原值的相反数即可。

*  #### lambda:
匿名函数，可接受任意数量的参数，但只能有一个表达式。  
lambda arguments : expression  传入参数，执行表达式，返回表达式的结果  
排序时指定按元素中的哪一个对象来排序：  
list1.sort(key=lambda x: x[0])  x表示列表中的元素，指定按x[0]来排序

*  #### bisect:
bisect.bisect(list1, target) 使用二分搜索返回target在列表list1中应该插入的位置的索引（从小到大排列）