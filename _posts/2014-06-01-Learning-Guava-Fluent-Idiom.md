---
layout: articles
title: Guava学习-Fluent idiom
tags: [java,Guava]
---
编写程序的最基本要求是要完成给定的需求。而代码的可读性往往是最容易被忽略但也是相当重要的。因为可读性往往决定着程序的可维护性和可扩展性。Guava包含着大量精心设计的API，凝聚着优秀的编程实践。学习和使用Guava可以促使写出更易读、更易扩展的代码。
<!--more-->
对象的比较是常见的任务，在java中提供了Comparator接口来统一比较对象的抽象。假设比较的过程比较复杂，然而Comparator接口又过于的抽象，那么编写出来的代码可能就不那么易读。Guava中提供了Ordering类，该类对Comparator接口进行了封装。主要的设计思想是SRP原则，然后提供链式的调用方式。使得能够很容易的构建出自己的比较器。

'''java
//利用Ordering自带的构造方法构建
Ordering<Foo> ordering = Ordering.natural().nullsFirst().onResultOf(new Function<Foo, String>() {
  public String apply(Foo foo) {
    return foo.sortedBy;
  }
});
//实现Ordering抽象类的构造方式
Ordering<String> byLengthOrdering = new Ordering<String>() {
  public int compare(String left, String right) {
    return Ints.compare(left.length(), right.length());
  }
};
//易读，易扩展。
assertTrue(byLengthOrdering.reverse().isOrdered(list));
assertTrue(ordering.isOrdered(list));
'''
**类似的还有ComparisonChain类**用来帮助实现compare/compareTo方法。

Guava里这样的方法随处可见。以下统计文件中单词出现个数的小程序参考[你应该更新的Java知识之常用程序库（一）](http://dreamhead.blogbus.com/logs/226738702.html)

'''java
  String content = Files.toString(new File(args[0]), Charset.defaultCharset());
  Iterable texts = Splitter.on(CharMatcher.WHITESPACE)
                                                 .omitEmptyStrings()
                                                 .trimResults()
                                                 .split(content);
  Multiset collection = HashMultiset.create(texts);
'''