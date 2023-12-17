# Android 中的 Java

## 1. 工程结构

### manifest 文件

AndroidManifest.xml 文件是 Android 应用程序的配置文件，它描述了应用程序的基本信息，如应用程序的包名、版本号、权限等。Android 系统会在安装应用程序时读取这个文件，以了解应用程序的基本信息。

### java 文件夹

java 文件夹是 Android 应用程序的源代码目录，它包含了应用程序的所有 Java 源代码文件。

### res/layout 文件夹

res/layout 文件夹是 Android 应用程序的布局文件目录，它包含了应用程序的所有布局文件。

## activity

在 Android 开发中，`Activity` 是一种表示用户界面和用户交互的基本组件。每个 `Activity` 都对应于应用程序中的一个屏幕，它通常包含用户与应用程序进行交互的界面元素。例如，一个简单的应用可能有一个主活动，用于显示应用的主要用户界面，以及其他活动，用于执行不同的操作或显示不同的信息。

每个 `Activity` 都是 `android.app.Activity` 类的子类。一个简单的 `Activity` 可以通过继承 `Activity` 类并实现其中的方法来创建。以下是一个简单的 `Activity` 示例：

```java
import android.app.Activity;
import android.os.Bundle;

public class MyActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // 设置该活动的用户界面
        setContentView(R.layout.activity_main);

        // 在这里可以执行其他初始化操作
    }
}
```

在上述示例中，`onCreate` 方法是在活动创建时调用的，你可以在这里进行初始化设置，比如设置布局（通过 `setContentView` 方法）、绑定事件处理程序等。

活动之间可以相互启动，通过 `Intent` 对象传递数据。这种方式使得应用程序可以在不同的活动之间进行导航和交互。例如，通过点击按钮启动新的活动，或者从一个活动返回到上一个活动。

一个应用程序通常由多个活动组成，每个活动负责不同的任务或用户界面。Android 系统通过活动栈来管理活动的生命周期和用户导航。当用户与应用程序进行交互时，活动栈会根据用户的行为来调整活动的状态。

## onCreate 方法和 main 方法的对比

- **main()** 方法是 Java 程序的入口点，由 Java 虚拟机 (JVM) 调用。**onCreate()** 方法是 Android 活动的入口点，由 Android 系统调用。
- **main()** 方法是静态方法，不需要创建对象即可调用。**onCreate()** 方法是实例方法，需要创建活动对象才能调用。
- **main()** 方法的参数是字符串数组，用于接收命令行参数。**onCreate()** 方法的参数是 Bundle 对象，用于保存活动的状态。

以下是 **main()** 方法和 **onCreate()** 方法的对比表：

| 特性     | main()        | onCreate()                |
| -------- | ------------- | ------------------------- |
| 位置     | Java 程序     | Android 活动              |
| 访问权限 | public        | public                    |
| 返回值   | void          | void                      |
| 参数     | String[] args | Bundle savedInstanceState |
| 调用者   | JVM           | Android 系统              |

在 Android 开发中，**onCreate()** 方法是活动的生命周期方法之一，它在活动创建时被调用。**onCreate()** 方法通常用于初始化活动的布局、视图、数据等。
