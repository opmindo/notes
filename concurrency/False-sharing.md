cpu每次操作都是以cache line(64k) 为单位，
如   long x, y内存相邻，那么x, y很有可能被读取到同一个cache line
2个不同core的线程t1, t2分别修改x, y
那么，可能出现t1修改x，导致t2对应的cache line失效, cpu reload value from memory， so false sharing is called "silent performance kill"

解决办法是像disruptor一样使用padding，
http://mechanical-sympathy.blogspot.co.uk/2011/08/false-sharing-java-7.html
http://mechanitis.blogspot.com/2011/07/dissecting-disruptor-why-its-so-fast_22.html
http://robsjava.blogspot.com/2014/03/what-is-false-sharing.html
Java8使用@Contended注解 http://budairenqin.iteye.com/blog/2048257
