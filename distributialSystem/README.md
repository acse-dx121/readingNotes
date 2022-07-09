# Distrubuted System

***分布式系统可以抽象为一个由多个完成相同目的的实体组成的集合，集合中的每个实体都具有 autonomous, programmable, asynchronous 以及 failure-prone 的特点；不同实体之间可以依赖底层通讯介质互相通讯***[1].

### 一致性[1]

一致性由强到弱，一般可分为以下几种

1. [Linearizability (Strong consistency or Atomic consistency)](https://en.wikipedia.org/wiki/Linearizability)
2. [Sequential consistency](https://en.wikipedia.org/wiki/Sequential_consistency)
3. [Causal consistency](https://en.wikipedia.org/wiki/Causal_consistency)
4. [Eventual consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

### 线性一致性 (Linearizability)

Linearizability 要求系统表现的如同一个单一的副本，按照**实际的时间顺序**来串行的执行线程的读写操作，这也就是『线性』这个定义的由来。然而，满足线性一致性的系统不仅难于实现，更难于提供较高的性能。

### 顺序一致性 (Sequential consistency)

> A multiprocessor system is *sequentially consistent* if the result of any execution is the same as if the operations of all the processors were executed in some sequential order, and the operations of each individual processor appear in this sequence in the order specified by its program.

这个定义实际上对系统提出了两条访问共享对象时的约束：

1. 从单个处理器（线程或者进程）的角度上看，其指令的执行顺序以编程中的顺序为准；
2. 从所有处理器（线程或者进程）的角度上看，指令的执行保持一个单一的顺序；

相比于 linearizability，Sequential consistency 放松了一致性的要求。首先，其并不要求操作的执行顺序严格按照真实的时间序；其次，其对不同线程之间的读写操作执行先后没有任何要求，只需保证执行是原子性即可.

## References

[1]: [分布式系统一致性 - Kaiyuan's Blog | May the force be with me](http://kaiyuan.me/2018/04/21/consistency-concept/)

[2]:
