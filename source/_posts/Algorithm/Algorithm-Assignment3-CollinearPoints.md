---
title: Algorithm-Assignment3-CollinearPoints
categories: Algorithm 
tags: Algorithm
description: 
show: true
date: 2021-12-27 04:16:28
---

原本以为 github 上 pull 下来的代码是 ok 的

结果一提交发现自己收到了来自两年前自己的背刺

当时混到了 40 分，那个版本没有 push……

在 26 分卡了一个小时，而且全是语言特性的坑

根本还没涉及到 merge sort 的算法

# BruteCollinearPoints

## 1. IllegalArgumentException

```
Test 1: points from a file
  * filename = input8.txt

    java.lang.IllegalArgumentException: both arguments to LineSegment constructor are the same point: (10000, 0)

    LineSegment.<init>(LineSegment.java:20)
    BruteCollinearPoints.<init>(BruteCollinearPoints.java:44)
```

给的 point 参数里面有重复的点，需要去判断这个情况抛异常

```java
Arrays.sort(points1);
for (int i = 0; i < points1.length; i++) {
    if (i > 0 && points[i].compareTo(points[i - 1]) == 0) {
        throw new IllegalArgumentException();
    }
}
```

### 2. NullPointerException

```
Test 1: points from a file
  * filename = input8.txt

    java.lang.NullPointerException

    BruteCollinearPoints.<init>(BruteCollinearPoints.java:47)
```

这里卡了一个小时

后来发现是在调用 `this.segments.add(segment)` 的时候忘了初始化 `this.segments` 

这时候还是用 `private List<LineSegment> segments` 偷懒的

### 3. ClassCastException

```
Test 1: points from a file
  * filename = input8.txt

    java.lang.ClassCastException: class [Ljava.lang.Object; cannot be cast to class [LLineSegment; ([Ljava.lang.Object; is in module java.base of loader 'bootstrap'; [LLineSegment; is in unnamed module of loader 'app')

    BruteCollinearPoints.segments(BruteCollinearPoints.java:63)
```

终究还是把 `segments` 声明成了 `LineSegment[]`

然后用一个 `ArrayList` 去存答案，最后转换过来

```java
List<LineSegment> ans = new ArrayList<>();

//...

LineSegment[] ls = new LineSegment[ans.size()];
this.segments = ans.toArray(ls);
```




