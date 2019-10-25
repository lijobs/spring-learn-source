# Lambda表达式的学习笔记

### 常见的lambda表达式汇总

#### 没有参数的情况

* 没有参数且美誉返回值

  ```java
  () -> {}                   // No parameters; result is void
  ```

* 没有参数但有表达式体,有两种情况，一种是直接返回某个类型的值，一种则是返回null

  ```java
  () -> 42                    // No parameters, expression body
      () -> null              // No parameters, expression body
  ```

* 没有参数带有返回块体，有两种情况一是无参返回块体的情况，另一种则是返回执行复杂的块体

  ```java
  () -> { return 42; }        // No parameters, block body with return
  () -> {                     // Complex block body with returns
    if (true) return 12;
    else {
      int result = 15;
      for (int i = 1; i < 10; i++)
        result *= i;
      return result;
    }
  }  
  ```

* 没有参数返回体为空

  ```java
  () -> { System.gc(); }      // No parameters, void block body
  ```

### 带有参数的情况

#### 单个声明类型的参数

* 有括号的情况

  ```java
  (int x) -> x+1              // Single declared-type parameter
  (int x) -> { return x+1; }  // Single declared-type parameter
  ```

* 没有括号的情况

  ```java
  (x) -> x+1                  // Single inferred-type parameter
  x -> x+1                    // Parentheses optional for
                              // single inferred-type parameter
  ```

#### 多个声明类型的参数

* 声明参数类型的情况

  ```java
  (int x, int y) -> x+y       // Multiple declared-type parameters
  ```

* 推断参数类型的情况

  ```java
  (x, y) -> x+y               // Multiple inferred-type parameters
  ```

#### 非法参数情况

* 没有带推断类型的修饰符

```java
(x, final y) -> x+y  // Illegal: no modifiers with inferred types
```

* 无法混合推断类型和声明类型

  ```java
  (x, int y) -> x+y    // Illegal: can't mix inferred and declared types
  ```

  