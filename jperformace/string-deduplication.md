[after jdk8u20](https://blog.codecentric.de/en/2014/08/string-deduplication-new-feature-java-8-update-20-2/)
must be used with -XX:+UseG1GC
java -Xmx32m -XX:+UseG1GC -XX:+UseStringDeduplication -XX:+PrintStringDeduplicationStatistics StringDeduplication

```
public class LotsOfStrings {  private static final LinkedList<String> LOTS_OF_STRINGS = new LinkedList<>();  public static void main(String[] args) throws Exception { int iteration = 0; while (true) { for (int i = 0; i < 100; i++) { for (int j = 0; j < 1000; j++) { LOTS_OF_STRINGS.add(new String("String " + j)); } } iteration++; System.out.println("Survived Iteration: " + iteration); Thread.sleep(100); } }}
```
