# 14-Patterns-for-Algorithm
14-Patterns-for-Algorithm + Dynamic Programming

# 1.滑动窗口  
---
*  #### 适用范围：  
通常为寻找数组中的一个满足要求的最长或最短**连续**子数组， 同时满足（或不满足）这个要求的数组的任何一个子数组也一定满足（或不满足）这个要求。

*  #### 原理及特点：  
因为满足（或不满足）要求的数组的子数组也一定满足（或不满足）要求，同时因为是求最长或最短连续子数组，所以无需再继续遍历其子数组，即滑窗的左右指针每次只需向右移动，这样保证了数组的每个元素最多被访问2次，所以时间复杂度为O(n)。  

*  #### 通用解法：  
使用双指针滑动窗口，初始化目标值以及窗口两边的指针l, r=0, 1，滑动窗口可以直接用原数组切片表示。  (可以直接初始化一个空窗口两端都为0，然后每次右移判断，初始化0，1相当于先单独初始化了一个0到1的窗口，同时还要单独判断这个窗口，没有整合到while中去）
构造一个while循环体
对右指针从1到最后的每一个位置判断当前窗口是否满足要求，满足要求则更新目标值, 同时根据情况更新指针以及辅助变量。（**注意如果右指针在最后一个位置时，要防止右指针继续向右移动**） 
循环结束后返回目标值

*  #### 例题：  
1. [Maximum Sum Subarray of Size K (easy) -- GeeksforGeeks](https://www.geeksforgeeks.org/find-maximum-minimum-sum-subarray-size-k/)(leetcode上未找到)
2. [Smallest Subarray with a given sum (medium) -- LeetCode](https://leetcode-cn.com/problems/minimum-size-subarray-sum/)
3. [Longest Substring with K Distinct Characters (medium, google) -- LintCode](https://www.lintcode.com/problem/longest-substring-with-at-most-k-distinct-characters/description)
4. [Fruits into Baskets (medium) -- LeetCode](https://leetcode-cn.com/problems/fruit-into-baskets/)
5. [No-repeat Substring (medium) -- LeetCode](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)
6. [Longest Substring with Same Letters after Replacement (medium, amazon) -- GeeksforGeeks](https://practice.geeksforgeeks.org/problems/maximum-sub-string-after-at-most-k-changes/0)
7. [Longest Subarray with Ones after Replacement (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/longest-subsegment-1s-formed-changing-k-0s/)(leetcode上未找到)
8. [Sliding Window Maximum (hard) -- LeetCode](https://leetcode-cn.com/problems/sliding-window-maximum/)

# 2.双指针模式  
---
*  #### 适用范围：  
通常为寻找数组中满足要求的目标值，而且主要是针对排序好的数组。

*  #### 原理及特点：  
双指针通常指一个数组左右两端的指针，根据题目的要求结合数组本身的特点（比如说已排序），能够控制**左指针右移**或**右指针左移**来满足题目要求，直至满足条件（通常是左右指针重合时）结束同时得到题目答案。由于数组中的每个元素只会被访问一次，所以时间复杂度为O(n)。  
需要注意的题目一般不会让你直接套用双指针，通常需要先经过一定转换，这也是该类问题的难点。  
比如说#15三数之和，首先需要将原数组排序，然后再遍历数组元素，将每次得到的值做为第一个数，再对该数右侧的子数组使用双指针来寻找和为该值相反数的两个元素，找到则返回对应元素在原数组中的索引。
还比如说#75颜色分类，则无需排序好的数组，而是利用数组的特性即其中元素只有‘0，1，2’三个值，同时结合题目的要求（相当于要进行排序），同样也可以转换为双指针问题，即将左右指针理解为‘0’元素和‘2’元素插入的位置，同时再引入一个游标指针来遍历数组元素（可以理解为二指针拓展为三指针），每次判断当前元素的值，根据情况交换元素位置以及移动左右指针。

*  #### 通用解法（单指双指针模式部分）：  
初始化指向数组左右的两个指针l, r = 0, len(nums) - 1  
根据题目要求计算当前的情况同时控制左指针右移或右指针左移，直至遍历完所有可能的情况后得到问题的解。

*  #### 例题：
1. [Pair with Target Sum (easy) -- LeetCode](https://leetcode-cn.com/problems/two-sum/)
2. [Remove Duplicates (easy) -- LeetCode](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)
3. [Squaring a Sorted Array (easy) -- LeetCode](https://leetcode-cn.com/problems/squares-of-a-sorted-array/)
4. [Triplet Sum to Zero (medium) -- LeetCode](https://leetcode-cn.com/problems/3sum)
5. [Triplet Sum Close to Target (medium) -- LeetCode](https://leetcode-cn.com/problems/3sum-closest/)
6. [Triplets with Smaller Sum (medium, google) -- LintCode](https://www.lintcode.com/problem/3sum-smaller/description)
7. [Subarrays with Product Less than a Target (medium) -- LeetCode](https://leetcode-cn.com/problems/subarray-product-less-than-k/)
8. [Dutch National Flag Problem (medium) -- LeetCode](https://leetcode-cn.com/problems/sort-colors/)

# 3.快慢指针 
---
*  #### 适用范围：  
通常为在链表结构中判断是否有环，也可以来获取单链表中的特定位置

*  #### 原理及特点：  
快慢指针是指一对移动速度不同的指针，通常是初始化为链表的头部，快指针每次移动2个位置，慢指针每次移动一个位置。
由于两个指针速度不同，如果链表中有环的话那么在某一时刻两个指针一定会相遇。所以可以用来判断链表中是否有环如#141环形链表，还有#202快乐数也是该类问题的变体。
同时还可以利用两者的速度关系，来获取单链表中指定位置的节点如#876链表的中间结点。
较为复杂一点的有#142环形链表 II，根据相交时的速度关系建立等式，找到题目中的隐含条件，最后再求解。
快慢指针算法在时间复杂度上与其他容易想到的算法基本没啥区别都是O(n)，它的优点主要在于其使用的额外空间的复杂度为O(1)。

*  #### 通用解法：  
初始化快、慢两个指针为链表头部 f = s = head  
每次移动快指针移动两步(注意判断f.next以及f.next.next是否为空）：f=f.next.next
慢指针移动一步（注意判断s.next是否为空）：s=s.next
根据题目要求来利用快慢指针求解

*  #### 其他：  
python默认库中没有链表结构，可以手动实现，通常（leetcode中）是这样表示：
```
#Definition for singly-linked list.
class ListNode:
  def __init__(self, x):
	  self.val = x
	  self.next = None
```

*  #### 例题：
1. [LinkedList Cycle (easy) -- LeetCode](https://leetcode-cn.com/problems/linked-list-cycle/)
2. [Middle of the LinkedList (easy) -- LeetCode](https://leetcode-cn.com/problems/middle-of-the-linked-list/)
3. [Happy Number (medium) -- LeetCode](https://leetcode-cn.com/problems/happy-number/)
4. [Start of LinkedList Cycle (medium) -- LeetCode](https://leetcode-cn.com/problems/linked-list-cycle-ii/)

# 4.区间合并  
---
*  #### 适用范围：  
基本上都是和区间相关的，包括合并区间、找交集、插入区间、使区间无重叠等

*  #### 原理及特点：  
感觉没有什么特别的原理及特点，通常就是按照区间的关系及题目逻辑进行解题，可能有两种思路，一个是在原区间上修改满足题目要求，另一个是新建一个空间将满足题目要求的区间放进去。两种方法时间复杂度都是O(n)，但是前一个通常需要在原空间上来查找删除某些元素速度肯定是比第二个方法更慢，但是它所需的额外空间复杂度未O(1)，而第二个是O(n)。

*  #### 通用解法：  
没有什么特别通用的解法，就是根据区间之间的逻辑关系，依照题目要求，遍历整个空间上的区间进行相应的修改，主要注意要考虑到各种可能的情况，不要遗漏就行了。

*  #### 例题：
1. [Merge Intervals (medium) -- LeetCode](https://leetcode-cn.com/problems/merge-intervals/)
2. [Insert Interval (medium) -- LeetCode](https://leetcode-cn.com/problems/insert-interval/)
3. [Intervals Intersection (medium) -- LeetCode](https://leetcode-cn.com/problems/interval-list-intersections/)
4. [Conflicting Appointments (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/given-n-appointments-find-conflicting-appointments/)（leetcode上未找到）
5. [Non-overlapping Intervals (medium) -- LeetCode](https://leetcode-cn.com/problems/non-overlapping-intervals/)

# 5.循环排序  
---
*  #### 适用范围：  
一种排序方法，用于元素的值和其应对应正确位置的值有固定关系的数组中

*  #### 原理及特点：  
比如给出一个含有1到n每个数字都会出现一次的长度为n的数组nums，现要对数组从小到大排序，通常的排序方法需要nlog(n)的时间复杂度，但是由于其元素的值与其位置存在特殊的关系，比如说元素的值为1，那么它一定是要放在数组中的第一个位置，也就是nums[0]，同理元素nums[i]就一定是要放在nums[nums[i]-1]的位置。那么通过这个特性我们就可以从头开始遍历数组，只要当前元素不是在它正确的位置上就进行替换，直到正确为止，再访问以下一个元素，遍历完毕后数组排序也就完成了，这就是循环排序，由于每个元素最多访问两次所以时间复杂度为O(n)，同时它也是就地排序无需额外空间，空间复杂度为O(1)。

*  #### 通用解法（单指排序部分）：  
遍历数组，只要当前元素不是在它正确的位置上就将其与那个位置上的元素进行替换，注意替换前先用临时变量来保存被替换的值，直到当前元素位置正确后再访问下一个元素。

*  #### 备注：
循环排序只是一种排序方法，相关题目一般是先使用循环排序得到一个顺序（或部分顺序）数组，再利用这个顺序（或部分顺序）数组来满足题目要求。 

*  #### 例题：
1. [Cyclic Sort (easy) -- Wikipedia](https://en.wikipedia.org/wiki/Cycle_sort)
2. [Find the Missing Number (easy) -- LeetCode](https://leetcode-cn.com/problems/missing-number/)
3. [Find all Missing Numbers (easy) -- LeetCode](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/)
4. [Find the Duplicate Number (medium) -- LeetCode](https://leetcode-cn.com/problems/find-the-duplicate-number/)
5. [Find all Duplicate Numbers (medium) -- LeetCode](https://leetcode-cn.com/problems/find-all-duplicates-in-an-array/)

# 6.原地链表翻转  
---
*  #### 适用范围：  
链表反转

*  #### 原理及特点：  
使用两个指针，一个当前指针，一个先前指针。先保存当前指针的下一个节点，然后将当前指针的下一个节点指向先前的指针，再将先前指针更新为当前指针，将当前指针更新为之前保存的下一个节点，当前指针遍历完所有节点，链表完成反转。每个节点只会访问两次，所以时间复杂度为O(n)，同时没有使用额外空间，额外空间复杂度为O(1)。

*  #### 通用解法（单指排序部分）：  
初始化当前指针 c = head，先前指针p = None
只要c不为None则
tmp = c.next 
c.next = p
p = c
c = tmp
完成反转，最后返回新的头节点

*  #### 例题：
1. [Reverse a LinkedList (easy) -- LeetCode](https://leetcode-cn.com/problems/reverse-linked-list/)
2. [Reverse a Sub-list (medium) -- LeetCode](https://leetcode-cn.com/problems/reverse-linked-list-ii/)
3. [Reverse every K-element Sub-list (hard) -- LeetCode](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/) 

# 7.树上的BFS  
---
*  #### 适用范围：  
需要层序遍历二叉数时

*  #### 原理及特点：  
广度优先搜索，一层一层的遍历二叉树。  

*  #### 通用解法：  
需要利用辅助队列，以python为例，引入collections中的deque，首先初始化deque，再将根节点压入（根节点为None的情况通常需要单独判断），只要队列不为空，则循环n次
（n等于当前队列的长度，也即是当前层的节点数），每次弹出队列左端一个节点（即为当前层的节点，对其进行相应操作以满足题目要求），同时加入该节点的左右字节点（如果有的话），循环完毕即该层节点遍历完毕，最后直到队列为空时表示二叉树的最后一层遍历完毕。

*  #### 例题：
1. [Binary Tree Level Order Traversal (easy) -- LeetCode](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)
2. [Reverse Level Order Traversal (easy) -- LeetCode](https://leetcode-cn.com/problems/binary-tree-level-order-traversal-ii/)
3. [Minimum Depth of a Binary Tree (easy) -- Leetcode](https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/)
4. [Level Averages in a Binary Tree (easy) -- LeetCode](https://leetcode-cn.com/problems/average-of-levels-in-binary-tree/)
5. [Level Order Successor (easy) -- GeeksforGeeks](https://www.geeksforgeeks.org/level-order-successor-of-a-node-in-binary-tree/)(leetcode上没有)
6. [Zigzag Traversal (medium) -- LeetCode](https://leetcode-cn.com/problems/binary-tree-zigzag-level-order-traversal/)
7. [Connect Level Order Siblings (medium) -- LeetCode](https://leetcode-cn.com/problems/populating-next-right-pointers-in-each-node/)

# 8.树上的DFS
---
*  #### 适用范围：  
需要深度遍历二叉数时

*  #### 原理及特点：  
深度优先搜索，从左到右遍历二叉树。  

*  #### 通用解法：  
创建一个递归函数，其内容为传入一个节点，如果其左子节点存在，继续调用递归函数传入其左子节点，如果其右子节点存在，继续调用递归函数传入其右子节点。
给递归函数传入根节点即可完成对整个二叉树的深度遍历。
在每次访问节点时进行相应的操作以满足题目要求（还可以根据需要增加递归函数的参数）。

*  #### 例题：
1. [Binary Tree Path Sum (easy) -- LeetCode](https://leetcode-cn.com/problems/path-sum/)
2. [All Paths for a Sum (medium) -- LeetCode](https://leetcode-cn.com/problems/path-sum-ii/)
3. [Sum of Path Numbers (medium) -- LeetCode](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/)
4. [Path With Given Sequence (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/check-root-leaf-path-given-sequence/)(leetcode上未找到)
5. [Count Paths for a Sum (medium) -- LeetCode](https://leetcode-cn.com/problems/path-sum-iii/)

# 9.双堆模式
---
*  #### 适用范围：  
寻找中位数，最小、最大值或调度问题

*  #### 原理及特点：  
双堆主要是指用两个优先队列，一个最小优先队列，一个最大优先队列来解决问题，比如#295数据流中的中位数、#480滑动窗口中位数，即通过将较小的一半数放在最大优先队列，较大的一半数放在最小优先队列来快速寻找中间值。还比如 #502IPO，也是通过先将成本放入最小优先队列，然后将能够满足的成本的对应利润放入最大优先队列，从而来获取整体的最大利润。优先队列通常是用二叉树来实现，其插入和查找一个元素的时间复杂度都是O(log(n))。

*  #### 通用解法：  
以寻找数据流中的中间数来举例，先初始化两个列表，一个是放较小的那一半数的最大优先队列lo，一个是放较大那一半数的最小优先队列hi。
每次插入元素时，先将元素插入lo（需要注意的是由于python只有最小优先队列，所以为了达到最大优先队列的效果，需要插入元素的相反值），然后再弹出lo中元素（即最大值），再将其插入hi，这样就保证了lo始终放较小的那一部分元素，hi总是放较大的那一部分元素。
最后由于要保持两个列表元素个数平衡，需要判断hi中的元素是否有比lo中的元素多两个或以上，如果是则需要弹出hi中的元素（即最小值）插入到lo中。
满足了这样的插入要求后，如果要取中位数，则只需判断当前插入的元素个数是偶数还是奇数，如果是奇数则中位数就是hi[0]（即hi中的最小值），如果是偶数那么中位数就是hi[0]（hi中的最小值）与lo[0]（lo中的最大值，注意符号）的平均值。

*  #### 例题：
1. [Find the Median of a Number Stream (medium) -- LeetCode](https://leetcode-cn.com/problems/find-median-from-data-stream/)
2. [Sliding Window Median (hard) -- LeetCode](https://leetcode-cn.com/problems/sliding-window-median/)
3. [Maximize Capital (hard) -- LeetCode](https://leetcode-cn.com/problems/ipo/)

# 10.子集问题模式
---
*  #### 适用范围：  
寻找数字的组合或是排列

*  #### 原理及特点：  
使用回溯算法，即通过深度优先搜索的递归函数，根据题意给定相应的终止条件，每次搜索时进行判断，满足时添加至解集，此外在递归完毕返回上一个节点时，还可以相应的还原变量的状态。

*  #### 通用解法：  
本质就是深度优先搜索，主要就是写递归函数，每次递归时先进行判定看是否满足要求，然后根据题意进行相应的改变，此外注意每次递归完毕，也就是回溯时也可能要进行相应的改变。

*  #### 例题：
1. [Subsets (easy) -- LeetCode](https://leetcode-cn.com/problems/subsets/)
2. [Subsets With Duplicates (easy) -- LeetCode](https://leetcode-cn.com/problems/subsets-ii/)
3. [Permutations (medium) -- LeetCode](https://leetcode-cn.com/problems/permutations/)
4. [String Permutations by changing case (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/permute-string-changing-case/)
5. [Minimum Remove to Make Valid Parentheses (medium) -- LeetCode](https://leetcode-cn.com/problems/minimum-remove-to-make-valid-parentheses/)
6. [Balanced Parentheses (hard) -- LeetCode](https://bradfieldcs.com/algos/stacks/balanced-parentheses/)(leetcode上没有)
7. [Unique Generalized Abbreviations (hard) -- LintCode](https://www.lintcode.com/problem/generalized-abbreviation/)

# 11.二分变种
---
*  #### 适用范围：  
排序好的数组，当需要用logn的时间复杂度解决问题时，通常就是用二分法。适用于寻找某一元素的位置或是寻找第k个位置的元素。

*  #### 原理及特点：  
原理简单来说就是二分法，只不过要根据题意进行相应的变化，比较灵活。需要注意边界条件。比如想要查找某个元素在数组中该插入的位置的索引，就有固定解法，如#744寻找比目标字母大的最小字母，这种甚至有python的函数库bisect.bisect(letters, target)直接可以返回索引值。
*  #### 通用解法：  
取整个区间的中间数，根据题目要求丢弃一半或另一半，直到达到终止条件返回结果。

*  #### 例题：
1. [Bitonic Array Maximum (easy) -- GeeksforGeeks](https://www.geeksforgeeks.org/maximum-sum-bitonic-subarray/)（leetcode上无）
2. [Order-agnostic Binary Search (easy) -- Medium Blog](https://medium.com/better-programming/three-smart-ways-to-use-binary-search-in-coding-interviews-250ba296cb82)（leetcode上无）
3. [Ceiling of a Number (medium) -- LeetCode](https://github.com/openset/leetcode/tree/master/problems/minimize-rounding-error-to-meet-target)
4. [Next Letter (medium) -- LeetCode](https://leetcode-cn.com/problems/find-smallest-letter-greater-than-target/)
5. [Number Range (medium) -- LeetCode](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
6. [Search in a Sorted Infinite Array (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/find-position-element-sorted-array-infinite-numbers/)
7. [Kth Smallest Element in a Sorted Matrix (medium) -- LeetCode](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/)
8. [Median of Two Sorted Arrays (hard) -- LeetCode](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)

# 12.前K大的数模式
---
*  #### 适用范围：  
任何让我们求解最大/最小/最频繁的K个元素的题，都遵循这种模式。

*  #### 原理及特点：  
先将所有元素放入堆（python中是最小优先队列），然后再一个个弹出，从而找到最大、最小的第K个元素

*  #### 通用解法（python）：  
nums = []
heapify(nums)
heappush(nums,i)
heappop()

*  #### 例题：
1. [‘K’ Closest Points to the Origin (easy) -- LeetCode](https://leetcode-cn.com/problems/k-closest-points-to-origin/)
2. [Connect Ropes (easy) -- LeetCode](https://leetcode-cn.com/discuss/interview-question/344677/Amazon-or-Online-Assessment-2019-or-Min-Cost-to-Connect-Ropes)
3. [Top ‘K’ Frequent Numbers (medium) -- LeetCode](https://leetcode-cn.com/problems/top-k-frequent-elements/)
4. [Frequency Sort (medium) -- LeetCode](https://leetcode-cn.com/problems/sort-characters-by-frequency/)
5. [Kth Largest Number in a Stream (medium) - LeetCode](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)
6. [‘K’ Closest Numbers (medium) -- LeetCode](https://leetcode-cn.com/problems/find-k-closest-elements/)
7. [Maximum Distinct Elements (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/maximum-distinct-elements-removing-k-elements/)
8. [Rearrange String (medium) -- LeetCode](https://leetcode-cn.com/problems/reorganize-string/)

# 13.K路归并  
---
*  #### 适用范围：  
解决那些涉及到多组排好序的数组的问题。

*  #### 原理及特点：  
多组排列好的数组通过归并可以整合成一个完整的排列好的数组，关键在于使用优先队列。

*  #### 通用解法：  
先将每一个数组中最小的元素推入优先队列，完成初始化，之后弹出队列中的元素（最小值）放入结果，然后再向优先队列中推入该元素所在原数组的下一个元素（如果没有下一个元素则跳过），循环直至队列为空，得到的结果即为整合后排列好的数组。

*  #### 例题：
1. [Merge K Sorted Lists (hard) -- LeetCode](https://leetcode-cn.com/problems/merge-k-sorted-lists/)
2. [Kth Smallest Number in M Sorted Lists (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/find-m-th-smallest-value-in-k-sorted-arrays/)（leetcode上无）
3. [Kth Smallest Number in a Sorted Matrix (medium) -- LeetCode](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/)
4. [Smallest Number Range (Hard) -- LeetCode](https://leetcode-cn.com/problems/smallest-range-covering-elements-from-k-lists/)

# 14.拓扑排序模式  
---
*  #### 适用范围：  
拓扑排序模式用来寻找一种线性的顺序，这些元素之间具有依懒性。比如，如果事件B依赖于事件A，那A在拓扑排序顺序中排在B的前面。

*  #### 原理及特点：  
通过又向无环图来理解，不断移除入度为0的节点，每次移除时更新图中剩余节点的度，直到无法移除为止。

*  #### 通用解法：  
需要两个字典（如果是简单的0到n的数组也可以用数组表示），一个字典存每个节点的入度，另一个字典存每个节点对应的依赖其的所有节点。
令n为当前节点个数， 然后初始化一个队列，将当前所有入度为0的节点压入，接着开始循环只要队列不为空，则弹出队列中的一个节点，同时令n -=1，然后去找依赖这个节点的其它节点，将其入度-1，如果其入度变为0则将其压入队列，直到队列为空时循环结束。
只有当n==0时才表示可以形成拓扑排序。

*  #### 例题：
1. [Topological Sort (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/topological-sorting/)(leetcode无，就是个介绍）
2. [Tasks Scheduling (medium) -- LeetCode](https://leetcode-cn.com/problems/course-schedule/)
3. [Tasks Scheduling Order (medium) -- LeetCode](https://leetcode-cn.com/problems/course-schedule-ii/)
4. [All Tasks Scheduling Orders (hard) -- GeeksforGeeks](https://www.geeksforgeeks.org/find-the-ordering-of-tasks-from-given-dependencies/)(the same as "Tasks Scheduling Order")
5. [Alien Dictionary (hard) -- LintCode](https://www.lintcode.com/problem/alien-dictionary/description)

# 15.动态规划
---
*  #### 适用范围：  
题目的解满足两个条件1.最优子结构，2.重叠子问题
最优子结构：问题的解可以被分解为子问题的解，这是动态规划的必要条件。
重叠子问题：在不断分解过程中，多次出现同一子问题，这样可以直接使用之前计算过的答案，而不必重复计算，这是保证动态规划有较高解题效率的必要条件。

*  #### 原理及特点：  
关键在于如何分解得到状态转移方程（可能是单一维度的分解，也可能是多维度的分解）。找到状态转移方程后又两种解题思路，一种是正向思维使用递归从上往下，另一种是逆向思维使用填表从下往上。填表可以看情况只保存需要的k个数，而递归要保存所有n个数，更耗空间。我统一都使用从下往上填表的解决方式。

*  #### 通用解法：  
理解题意，找到状态转移方程，初始化可直接求解的简单情况，保存到dp表中，从下往上根据状态转移方程求解填表。填表完毕得到最终结果。

*  #### 例题：
#### 1. 0/1 Knapsack (0/1背包类型)
1. [0/1 Knapsack (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/)（leetcode无）
2. [Equal Subset Sum Partition (medium) -- LeetCode](https://leetcode-cn.com/problems/partition-equal-subset-sum/)
3. [Subset Sum (medium) -- GeeksforGeeks](https://www.geeksforgeeks.org/subset-sum-problem-dp-25/)（leetcode无）
4. [Constrained Subset Sum (hard) -- LeetCode](https://leetcode-cn.com/problems/constrained-subset-sum/)
5. [Minimum Partition (hard) -- LintCode](https://www.lintcode.com/problem/minimum-partition/description)（leetcode无）
6. [Minimum Subset Sum Difference (hard) -- GeeksforGeeks](https://www.geeksforgeeks.org/partition-a-set-into-two-subsets-such-that-the-difference-of-subset-sums-is-minimum/)（leetcode无）

#### 2. Unbounded Knapsack，无限背包
1. Unbounded Knapsack，无限背包
2. Rod Cutting，切钢条问题
3. [Coin Change，换硬币问题](https://leetcode-cn.com/problems/coin-change-2/)
4. [Minimum Coin Change，凑齐每个数需要的最少硬币问题](https://leetcode-cn.com/problems/coin-change/)
5. Maximum Ribbon Cut，丝带的最大值切法

#### 3. Fibonacci Numbers，斐波那契数列
1. [Fibonacci numbers，斐波那契数列问题](https://leetcode-cn.com/problems/fibonacci-number/)
2. [Staircase，爬楼梯问题](https://leetcode-cn.com/problems/climbing-stairs/)
3. Number factors，分解因子问题
4. Minimum jumps to reach the end，蛙跳最小步数问题
5. Minimum jumps with fee，蛙跳带有代价的问题
6. House thief，偷房子问题

#### 4. Palindromic Subsequence，回文子系列
1. Longest Palindromic Subsequence，最长回文子序列
2. Longest Palindromic Substring，最长回文子字符串
3. Count of Palindromic Substrings，最长子字符串的个数问题
4. Minimum Deletions in a String to make it a Palindrome，怎么删掉最少字符构成回文
5. Palindromic Partitioning，怎么分配字符，形成回文

#### 5. Longest Common Substring，最长子字符串系列
1. Longest Common Substring，最长相同子串
2. Longest Common Subsequence，最长相同子序列
3. Minimum Deletions & Insertions to Transform a String into another，字符串变换
4. Longest Increasing Subsequence，最长上升子序列
5. Maximum Sum Increasing Subsequence，最长上升子序列和
6. Shortest Common Super-sequence，最短超级子序列
7. Minimum Deletions to Make a Sequence Sorted，最少删除变换出子序列
8. Longest Repeating Subsequence，最长重复子序列
9. Subsequence Pattern Matching，子序列匹配
10. Longest Bitonic Subsequence，最长字节子序列
11. Longest Alternating Subsequence，最长交差变换子序列
12. Edit Distance，编辑距离
13. Strings Interleaving，交织字符串
