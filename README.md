# Faster_RCNN代码解读

1.关于import
---
把变量从内存中变成可存储或可传输的过程叫做序列化（在python中为pickling）  
序列化之后，就可以把内容写入磁盘进行存储，或者传递到别的机器上  
反之，将变量内容从序列化的对象重新读到内存里称之为反序列化  
python提供两个模块来实现序列化：cpickle和pickle  
这两个模块功能是一样的，区别在于cPickle是C语言写的，速度快，pickle是纯Python写的，速度慢，用的时候，先尝试导入cPickle，如果失败，再导入pickle  
```
#异常处理：先尝试导入cPickle，如果失败，再导入pickle 
try:
  import cPickle as pickle
except ImportError:
  import pickle
```

2.Train
---
首先调用vgg类创建一个网络对象self.net  
```
#
if cfg.FLAGS.network == 'vgg16':
    self.net = vgg16(batch_size=cfg.FLAGS.ims_per_batch)
```
