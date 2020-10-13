# dig-into-protobuf

## 目录
protobuf的目录结构如下：
```
.
├── compiler   // 编译？
├── io         // io流
├── stubs      
├── testdata
├── testing
└── util       // 工具
```


## compiler

compiler的入口函数是"main.cc"，生成代码的时候会根据不同的语言加载不同的编译器，代码在以对应的语言命名的目录下，例如 c++是在目录"cpp"中。


## io

#### EpsCopyOutputStream
用来对齐字节？？？


## stubs

主要是一些工具之类的？？？


## util

一些工具

## encoding
关于各种类型的encoding方式，官方的文档有详细的介绍[doc](https://developers.google.com/protocol-buffers/docs/encoding#signed_integers
)。 主要包括一些常见类型的编码，其中改进了一些编码方式，使得压缩效率更高。  


## ParseFromString 和 SerializeToString
在message_lite.cc中，会根据类型生成不同的编解码代码，不同类型的编解码方式在上一节已经介绍过了，下面我们根据原理来分析下具体类型的代码实现。


## 为什么要序列化和反序列化
1. 直接用内存对象不行吗？
2. 比xml来说，空间占用更小

## protobuf格式
参考protobuf格式规范


## protobuf消息兼容性
修改protobuf消息之后，如何保证兼容性，这点在版本迭代过程中非常重要。
1. 删除之前的字段，需要保留字段号
2. 增加新的字段并不受影响

## protobuf的map字段

## protobuf的oneof字段

## protobuf的反射

## protobuf的自说明方法
google说内部从来没有使用这个方法，证明都是用grpc来处理消息，没有跨平台过？
如果需要说明则需要生成descript文件。

## protobuf重复利用消息
如果不停的生产消息，特别是小的消息，那么必然带来很多碎片，如何解决小碎片的问题呢？
1. 重复利用消息
2. 采用tmalloc申请内存，至于具体的原理是什么？？？

## protobuf的encoding说明

## protobuf的接口说明

## protobuf生成的接口说明
c++生成的消息类型有哪些接口？？

## protobuf的一些工具
protobuf打印对象信息DebugString

protobuf 二进制转为json，这里转换的是raw data也就是说数据都是编号，而没有具体的名称。
```
protoc --decode_raw < message.bin > message.txt
```

如果需要具体的名称，可以参考。
```
protoc --decode message message.proto < message.bin > message.txt
```

