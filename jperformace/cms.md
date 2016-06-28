-XX:+UseParNewGC -XX:+UseConcMarkSweepGC

### two kind of failures
1. concurrent mode failure
2. promotion failure

*concurrent mode failure* made by no enough enough memory,```-XX:CMSInitiatingOccupancyFraction=30 -XX:+UseCMSInitiatingOccupancyOnly```

*promotion failure* is caused by fragment
