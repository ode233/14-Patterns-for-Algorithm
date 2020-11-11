# 用golang写算法题的一些常用语法总结

*  #### utf8.RuneCountInString()
```go 
import "unicode/utf8"
utf8.RuneCountInString(s) // 统计字符串中字符个数 
```

*  #### strings
```go 
import "strings"
strings.ReplaceAll(s, old, new string) // 字符串替换，返回新替换后的字符串
```

*  #### container/list
```go 
import "container/list" // 提供了双向链表的数据结构
list1 := list.New()
list1.PushBack(1)
list1.PushFront(1)
node := list1.Front()
node = list1.Back()
list1.Remove(node)
fmt.Print(node.Value)   // 打印元素的值
```