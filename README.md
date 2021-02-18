# HttpServer
这个项目目的： 
- 学习高性能服务器的一般开发流程 
- 掌握epoll LT模式加非阻塞I/O在Linux平台的开发 
- 回顾C++11的语法 
- 利用线程池和多核CPU特性，避免线程频繁创建销毁的开销 
- 对象池和内存管理 其他详见项目


###关于C++的不可拷贝类
使用 boost::noncopyable，可以完成不可拷贝。在 <boost/noncopyable.hpp> 下提供了不可拷贝类的实现，使用起来也非常简单，让自己的类继承自 boost::noncopyable 即可：
~~~
class Matrix : boost::noncopyable
{
    // 类实现
}
~~~
如果不想用第三方库，自己实现呢？可以查看 Boost 源码看看是怎么做的：
~~~
private:  // emphasize the following members are private
    noncopyable( const noncopyable& );
    noncopyable& operator=( const noncopyable& );

private:  // emphasize the following members are private
    noncopyable( const noncopyable& );
    noncopyable& operator=( const noncopyable& );
~~~
