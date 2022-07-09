# Golang 常见面试问题

## go有哪些数据结构？

基本的数据结构有:slice, Map, String.

更多的数据结构定义在了一些标准库里面，例如: sync.Map, Container/List, Container/Heap, Container/ring.

## slice实现原理, 如何进行扩容，和Redis String之间的对比

slice是在原本的数组的基础上，加了一层封装。
```golang
type Slice struct {
    len, cap int
    data *Uintpoint
}
```
和Redis里面的string非常相似。


## map的实现原理

## sync.Map的实现原理

## 

