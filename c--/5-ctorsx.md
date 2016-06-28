# copy constructor
[蓝色](http://zhihu.com/question/30726582/answer/49210382)对象没初始化用copy ctor，已初始化用copy assign ctor
```
Object x = Object(y) // copy ctor
x = Object(z) // copy assign ctor
```
用于：  
+ 方法non-reference参数传递，和non-reference return 
+ 数组{}初始化


[stackoverflow](http://stackoverflow.com/a/9178324)  why boost:noncopyable works   
the synthesized copy constructor performs full member-wise copy of **the object's bases** and non-static members

编译器也有可能直接把copy constructor移除为constructor, -f no-elide-constructors

# copy assign ctor
“It is crucially important for assignment operators to work correctly, even when an object is assigned to itself. A good way to do so is to copy the right-hand operand before destroying the left-hand operand.
 ”
Excerpt From: Lippman, Stanley B. “C++ Primer, 5/e.” iBooks.
