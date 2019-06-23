### Java8常用操作


> stream常见操作

```java
List<String> list = Arrays.asList("abc", "", "bc", "efg", "abcd","", "jkl");

// 过滤
List<String> filtered
    = list.stream().filter(e -> !e.isEmpty()).collect(Collectors.toList());

// 合并字符串
String mergedString
    = list.stream().filter(e -> !e.isEmpty()).collect(Collectors.joining(", "));

// 聚合
Map<Integer, List<Apple>> groupBy
    = appleList.stream().collect(Collectors.groupingBy(Apple::getId))

// list转map
Map<Integer, String> result1
    = list.stream().collect(Collectors.toMap(Hosting::getId, Hosting::getName));
```


