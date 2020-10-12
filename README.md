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


