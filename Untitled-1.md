# 

- 我理解的1a的流程是这样的

```cpp
/**
class list_node {
    T data;
    list_node* pre, next;
}

class double_list {
    int length;
    const int max_len;
    list_node<T> head;

    // some member functions
    ...
    checker();
    inserter();
    deleter();

    insert(){
        if(checker() != pass) {
            deleter(last_one);
        }
        inserter();
    }
}

class measurement:
    double value
    long timestamp

class position:
    double lat
    double lon
    
    equal: == (...) {// 粗匹配}

class sensor:
    double_list<measurement> measurements // max_size = 1000
    position pos

    // member functions
    ...

region: // max_size 32
    double_list<sensor> sensors // max_size = 32;
    position low_left, hight_right 

    // member functions
    ...
*/


void ingestEvent(double value, double latitude, 
                    double longitude, int timestamp) {
    // step1
    // 判断在哪个region中

    // step2
    // 在对应region中寻找sensor，根据经纬度粗匹配
    // if 不存在 then 新增sensor并插入

    // step3
    // 在对应sensor中插入数据

    return;
}
```



问题在于, Region 的范围是如何确定的？自己设定一个范围?
