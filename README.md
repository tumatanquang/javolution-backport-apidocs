# Javolution backport API docs

Based on [Javolution 5.5.1](https://mvnrepository.com/artifact/javolution/javolution/5.5.1) source code.

Since version 5.4, the public methods of [`FastTable`](https://tumatanquang.github.io/javolution-backport/javolution/util/FastTable.html) and [`FastList`](https://tumatanquang.github.io/javolution-backport-apidocs/javolution/util/FastList.html) have been marked as `final` and cannot be overridden.

This is inconvenient because although these two classes (according to the documentation) can use the [`shared()`](https://tumatanquang.github.io/javolution-backport-apidocs/javolution/util/FastCollection.html#shared--) method to make them thread-safe. However, it does not work and throws a compile error.

This project has removed `final` to allow overriding of the public methods of these two classes, so you can implement thread-safety in any way you want.

### WARNING:

- Since v5.6.6: The original `FastList` has been replaced with `FastChain`!

## Suggestions for use:

- `ArrayList` can be replaced with `FastTable`.
- `LinkedList` can be replaced with `FastChain`.
- Initialize `FastTable` / `FastChain`:

```java
FastTable table = new FastTable();
FastChain list = new FastChain();
FastList list = new FastTable();
FastList list = new FastChain();
```

## How to build?

Build using Ant with [build.xml](https://github.com/javolution/javolution/blob/V5_2/build.xml) file taken and modified from version 5.2.5.

To build use: `ant -Dexecutable=<javac path of jdk 5 or 6> compile-jdk<5 or 6>`.