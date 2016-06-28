[tom white](http://www.tom-e-white.com/2007/11/consistent-hashing.html) though has bug of collide

hash *key* and *server*(add replicas for load balance), find the next hash of server that equals to hash of key, if we reach the end, choose the first one, in java we use SortedMap<Integer, String> to store hash ring

```
// [John Cormie], what about the hash of two server replicas are equal?
public void add(T node) {
    for (int i = 0; i < numberOfReplicas; i++) {
      circle.put(hashFunction.hash(node.toString() + i),
        node);
    }
  }
```
