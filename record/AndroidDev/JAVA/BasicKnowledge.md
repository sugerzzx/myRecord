# JAVA 基础知识

## Hello World

```java
public class HelloWorld { // 声明一个公共类
    public static void main(String[] args) { // main 方法是程序的入口点
        System.out.println("Hello, World!");
    }
}
```

这个简单的程序包含一个名为 `HelloWorld` 的类，其中有一个名为 `main` 的方法。在 Java 程序中，`main` 方法是程序的入口点。当你运行这个程序时，系统将首先查找 `main` 方法，并从那里开始执行。

解释一下代码的各个部分：

- `public class HelloWorld`: 定义了一个公共类，类名为 `HelloWorld`。**Java 程序的文件名应该与公共类的名字相同**，并以 `.java` 为文件扩展名。

- `public static void main(String[] args)`: 这是程序的主方法，是程序执行的起点。Java 程序总是从 `main` 方法开始执行。`public static void` 是方法的修饰符，表示这个方法是公共的、静态的，没有返回值。

- `System.out.println("Hello, World!");`: 这一行使用 `System.out.println` 方法在控制台输出文本 "Hello, World!"。`println` 表示输出并换行，将文本输出到控制台。

## JAVA 基本数据类型

Java 的基本数据类型，以及与 JavaScript 的对比：

1. **整数类型：**

   - Java: `byte`, `short`, `int`, `long`
   - JavaScript: `Number`类型表示所有数值，包括整数和浮点数

2. **浮点数类型：**

   - Java: `float`, `double`
   - JavaScript: `Number`类型，不区分整数和浮点数

3. **字符类型：**

   - Java: `char`, 用单引号表示（如 `'a'`）
   - JavaScript: JavaScript 中没有专门的字符类型，字符通常由单个字符的字符串表示（如 `'a'`）

4. **布尔类型：**

   - Java: `boolean`
   - JavaScript: `boolean`

5. **其他：**
   - Java: `String`（不是基本数据类型，但是非常常用,用双引号表示（如 `"Hello"`））
   - JavaScript: `String`

对比时需要注意的一些差异和注意事项：

- **变量声明：**

  - Java 中需要明确声明变量的类型，例如 `int x = 10;`。
  - JavaScript 中变量的类型由赋值决定，使用 `let x = 10;` 即可。

- **类型转换：**

  - 在 Java 中，进行不同类型之间的转换时需要显式地进行类型转换。
  - 在 JavaScript 中，由于是弱类型语言，可以更灵活地进行隐式类型转换。

- **null vs undefined：**

  - 在 Java 中，`null` 是一个特殊的引用类型，表示对象的引用缺失。
  - 在 JavaScript 中，`undefined` 表示变量声明但未赋值，而 `null` 表示空对象引用。

- **数组：**
  - Java 中数组是对象，需要明确定义数组的大小，并且数组元素类型必须一致。
  - JavaScript 中数组是动态的，可以容纳不同类型的元素，并且长度可以动态变化。

## 修饰符

Java 中的修饰符用于控制类、方法、变量等对象的**访问权限、可见性、作用域**等。

根据修饰符的功能，Java 中的修饰符可以分为以下两类：

- **访问控制修饰符**：用于控制**对象的访问权限**。
- **非访问控制修饰符**：用于控制**对象的其他属性，如可见性、作用域等**。

### **访问控制修饰符**

| 修饰符        | 可见性       |
| ------------- | ------------ |
| **private**   | 仅限当前类   |
| **protected** | 当前类和子类 |
| **public**    | 任何类       |

### **非访问控制修饰符**

- **abstract**：表示该类是抽象类，不能实例化。
- **static**：表示该成员是静态成员，属于类而不是对象。
- **final**：表示该成员是常量，不可修改。
- **transient**：表示该成员不会被序列化。
- **volatile**：表示该成员的值可能会在多个线程之间共享，需要使用同步机制来保证线程安全。
- **native**：表示该成员的实现由本地代码实现。

以下是一些常见的修饰符的使用示例：

```java
public class MyClass {

    private int a; // 仅限当前类可见

    protected int b; // 当前类和子类可见

    public int c; // 任何类可见

    public static void main(String[] args) {} // main必须包含public修饰符

    abstract void myMethod(); // 该类是抽象类，不能实例化

    static int myStaticField; // 该成员是静态成员，属于类而不是对象

    final int myFinalField = 10; // 该成员是常量，不可修改

    transient int myTransientField; // 该成员不会被序列化

    volatile int myVolatileField; // 该成员的值可能会在多个线程之间共享

    native void myNativeMethod(); // 该成员的实现由本地代码实现

}
```

在实际开发中，需要根据实际情况来选择合适的修饰符。

## 注解(Annotation)

注解是一种特殊的修饰符，它可以用于修饰类、方法、变量等对象。注解可以在编译时和运行时被读取，并执行相应的处理。

注解的语法格式如下：

```java
@注解名(参数名 = 参数值)
```

注解的参数可以是基本数据类型、字符串、枚举类型、注解类型、Class 类型以及以上类型的数组。

注解的参数可以有默认值，如果没有指定参数值，则使用默认值。

以下是一些常见的注解的使用示例：

```java
@Deprecated // 表示该方法已过时
public void myMethod() {}

@SuppressWarnings(value = "unchecked") // 表示忽略警告

@Override // 表示该方法是重写的父类方法

@Target(ElementType.TYPE) // 表示该注解只能用于类上

@Retention(RetentionPolicy.RUNTIME) // 表示该注解在运行时可见

public @interface MyAnnotation {} // 表示该注解是一个注解类型
```

`@Override` 用于告诉编译器，被注解的方法是重写（覆盖）父类中的一个方法。这个注解提供了一种机制，用于检查编译时是否真的覆盖了父类的方法。

在 Java 中，子类可以继承父类的方法，而有时子类可能会重写（覆盖）父类的某个方法。为了确保在子类中真的覆盖了父类中的方法，使用 `@Override` 注解可以让编译器进行检查，如果被注解的方法并没有覆盖父类中的方法，编译器将会产生一个编译错误。

例如：

```java
class Animal {
    void makeSound() {
        System.out.println("Some generic sound");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Bark");
    }
}
```

在上面的例子中，`Dog` 类继承自 `Animal` 类，并重写了 `makeSound` 方法。`@Override` 注解用于确保 `makeSound` 方法确实是在子类中覆盖了父类的方法。如果在 `Dog` 类中没有正确覆盖 `makeSound` 方法，编译器将会产生错误。

总而言之，`@Override` 注解是一种在代码中提供说明和安全检查的方式，用于确保子类正确地覆盖了父类中的方法。
