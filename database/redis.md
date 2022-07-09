<!--
 * @Author: your name
 * @Date: 2021-08-27 11:07:27
 * @LastEditTime: 2021-08-27 11:31:43
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /Job/database/redis.md
-->

# Redis 设计与实现阅读笔记

## 基本数据结构及实现

redis中所有的数据结构都是由一个基本的object对象引申而来的。

### 简单字符串 Simple Dynamic String

```c
struct sdsdr {
    int len; // 已使用字节数量
    int free; // 未使用字节数量
    char buf[]; // 字节数组， 保存字符串
}
```

从上述结构定义来看，很容易类比到Golang 中的Slice的定义, 都是对基本的数据结构进行了一层封装。

```go

```

#### SDS 的优点

这层封装带来了一些好处，文中列举如下:

- **常数时间复杂度获取字符串长度**：结构体本身记录了已使用底层字符串的长度以及剩余可使用空间，因此可以在常数时间内返回字符串长度。

- **杜绝缓冲区溢出**：传统C中字符串不含有额外的长度信息，因此进行拼接时需要重新分配内存，且可能存在缓冲区溢出的问题。由于SDS存储了相关长度信息，因此在拼接前可以检查剩余空间是否足够，来决定是否需要分配内存，以此避免缓冲区溢出。

- **减少修字符串是带来的内存分配次数**：对C语言字符串进行append操作时，需要重新分配内存。
  
  - <u>空间预分配</u>：每当需要对SDS进行增长时，会额外分配一部分内存，减少后续内存分配次数。
  
  - <u>惰性释放</u>：当对SDS的长度进行缩减时，并不立即释放多余的内存，保留它们为了以后不时之需。

- **二进制安全**：C语言读取字符串时，按照ACSII编码读取，遇到'\0'即停止。而SDS根据len关键字读取长度，可以越过这一限制，因此可以存储除字符串外的其他数据。

### 链表 Link List

Redis 实现了自己的双向链表

```c
typedef struct listNode {
    // prev node
    struct listNode* prev;
    // next node
    struct listNode* next;
    // the value of node
    void * value;
}


typedef struct list {
    // head node
    listNode* head;
    // tail node
    listNode* tail;
    // the number of nodes 
    unsigned long len;
    // 节点值复制函数
    void *(*dup) (void *ptr);
    // 节点值释放函数
    void (*free) (void *ptr);
    // 节点值对比函数
    void (*match) (void *ptr, void *key);
}
```

## redis key很多

## 和memcache的区别
