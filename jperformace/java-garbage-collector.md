https://blogs.oracle.com/jonthecollector/entry/our_collectors

Using the -XX flags for our collectors for jdk6,

UseSerialGC is "Serial" + "Serial Old"
UseParNewGC is "ParNew" + "Serial Old"
UseConcMarkSweepGC is "ParNew" + "CMS" + "Serial Old". "CMS" is used most of the time to collect the tenured generation. "Serial Old" is used when a concurrent mode failure occurs.
UseParallelGC is "Parallel Scavenge" + "Serial Old"
UseParallelOldGC is "Parallel Scavenge" + "Parallel Old"

1. UseParNew and UseParallelGC both collect the young generation using multiple GC threads. Which is faster
ParallelScavenge可以自适应设置内存比例(Xmn, SurvivorRatio都不需要，-XX:+UseAdaptiveSizePolicy)
2. How do I use "CMS" with "Serial"?
－XX:+UseConcMarkSweepGC -XX:-UseParNew而不是-XX:+UseConcMarkSweepGC -XX:+UseSerialGC,这个会报冲突的
3. ParNew和Parallel Old不能配合是，设计方面的问题
ParNew只能cms和serial
