MMU

# 操作系统原理与Linux基本操作

## 操作系统基本原理

## linux基本原理

## linux常见命令
### sort 
Linux sort 命令用于将文本文件内容加以排序。sort 可针对文本文件的内容，以行为单位来排序。

**语法**
sort [-bcdfimMnr][-o<输出文件>][-t<分隔字符>][+<起始栏位>-<结束栏位>][--help][--verison][文件][-k field1[,field2]]

### uniq
Linux uniq 命令用于检查及删除文本文件中重复出现的行列，一般与 sort 命令结合使用。uniq 可检查文本文件中重复出现的行列。

**语法**
uniq [-cdu][-f<栏位>][-s<字符位置>][-w<字符位置>][--help][--version][输入文件][输出文件]

**参数：**
- -c或--count 在每列旁边显示该行重复出现的次数。
- -d或--repeated 仅显示重复出现的行列。
- -f<栏位>或--skip-fields=<栏位> 忽略比较指定的栏位。
- -s<字符位置>或--skip-chars=<字符位置> 忽略比较指定的字符。
- -u或--unique 仅显示出一次的行列。
- -w<字符位置>或--check-chars=<字符位置> 指定要比较的字符。
- --help 显示帮助。
- --version 显示版本信息。
[输入文件] 指定已排序好的文本文件。如果不指定此项，则从标准读取数据；
[输出文件] 指定输出的文件。如果不指定此选项，则将内容显示到标准输出设备（显示终端）。

## linux 面试题

### 字节:给一个文件有很多行，每个行都是ip地址，用Linux命令找出出线最多的三个ip地址
user case:
```bash
# a
# b
# c
# q
# d
# d
# a
# v
# v
# v
# b
# b
# b
# d

cat test.log | sort | uniq -c | sort -r | head -n 3
# 4 b
# 3 v
# 3 d
```
