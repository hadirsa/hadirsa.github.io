---
layout: post
title: Distinct java 8 list
---
```

...
public static <T> Predicate<T> distinctByKey(Function<? super T, Object> keyExtractor) {
    Map<Object, Boolean> map = new ConcurrentHashMap<>();
    return t -> map.putIfAbsent(keyExtractor.apply(t), Boolean.TRUE) == null;
}
...
//usage
...
List<Person> distinctElements = list.stream()
                                            .filter( distinctByKey(p -> p.getId()) )
                                            .collect( Collectors.toList() );
...

```
