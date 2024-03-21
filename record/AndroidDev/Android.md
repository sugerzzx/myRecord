# Android 开发

## 工程结构

### 目录结构

在 Android Studio 中，项目可以使用两种不同的目录结构：Project 结构和 Android 结构。这两种结构在项目组织和管理方面有一些区别：

1. **Project 结构**：

   - 这种结构更接近传统的项目结构，通常用于更复杂的项目或多模块项目。
   - 根目录下包含了项目的配置文件和 Gradle 构建文件，如 settings.gradle 和 build.gradle。
   - 子目录包含了不同的模块，每个模块可能是一个应用程序模块、库模块或者测试模块。
   - 这种结构更加灵活，可以更好地管理多个模块、库和依赖关系。

2. **Android 结构**：
   - 这种结构更加简化，更适用于较小的项目或者初学者。
   - 根目录下直接包含了应用程序模块，通常是一个单一的模块。
   - 不同的资源（如布局、字符串、图像等）通常直接位于模块的特定目录中。
   - 这种结构对于小型项目或者只有一个应用程序模块的项目更加方便和简洁。

在实际使用中，你可以根据项目的规模和需求选择合适的项目结构。如果你的项目比较简单，只有一个应用程序模块，那么 Android 结构可能更适合你。但如果你的项目较大，包含多个模块或者库，那么 Project 结构可能更适合你，因为它提供了更好的模块化和组织管理能力。

### manifest 文件

AndroidManifest.xml 文件是 Android 应用程序的配置文件，它描述了应用程序的基本信息，如应用程序的包名、版本号、权限等。Android 系统会在安装应用程序时读取这个文件，以了解应用程序的基本信息。

### java 文件夹

java 文件夹是 Android 应用程序的源代码目录，它包含了应用程序的所有 Java 源代码文件。

### res/layout 文件夹

res/layout 文件夹是 Android 应用程序的布局文件目录，它包含了应用程序的所有布局文件。

## Intent

在 Android 中，`Intent` 类是一个用于在不同组件之间进行通信的重要类。它可以用于启动活动（Activity）、服务（Service）、发送广播（Broadcast）、启动外部应用等。以下是关于 `Intent` 类的一些重要概念和功能：

1. **Intent 的作用**：

   - `Intent` 用于在应用程序内或者不同的应用程序之间传递消息和执行操作。
   - 它允许开发者请求系统执行特定的操作，或者请求系统将数据传递给其他组件。

2. **Intent 的类型**：

   - 显式 Intent：指定了要启动的目标组件的类名，用于在同一应用程序内的组件之间进行通信。
   - 隐式 Intent：没有明确指定目标组件的类名，而是根据给定的动作、类别和数据等信息由系统来确定目标组件。用于在不同应用程序之间进行通信。

3. **Intent 的构造**：

   - 通过指定动作（Action）、数据（Data）、类别（Category）等信息来构造 Intent 对象。
   - 可以使用 `putExtra()` 方法向 Intent 中添加额外的数据。

4. **Intent 的使用场景**：

   - 启动活动：通过 `startActivity()` 方法启动新的活动。
   - 启动服务：通过 `startService()` 或 `bindService()` 方法启动服务。
   - 发送广播：通过 `sendBroadcast()` 或 `sendOrderedBroadcast()` 方法发送广播。
   - 启动外部应用：通过隐式 Intent 启动其他应用程序中的组件。
   - 传递数据：可以通过 Intent 在不同组件之间传递数据。

5. **Intent 过滤器**：
   - 用于在清单文件中声明组件（如活动、服务、接收器等）可以响应的 Intent 类型。
   - 通过 `<intent-filter>` 元素指定组件可以处理的动作、类别、数据等信息。

使用 `Intent` 类可以实现 Android 应用程序中各个组件之间的交互，包括启动活动、服务、发送广播等操作，从而实现应用程序的各种功能。

## Activity

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

### 生命周期

在 Android 开发中，每个 `Activity` 都有自己的生命周期，它包括了一系列的生命周期方法，用于处理活动的创建、启动、暂停、恢复、停止和销毁等过程。这些生命周期方法可以帮助你管理活动的状态和行为，以便在不同的阶段执行不同的操作。

以下是 `Activity` 的生命周期方法：

- `onCreate`：在活动创建时调用，用于初始化活动的布局、视图、数据等。

- `onStart`：在活动启动时调用，用于准备活动的用户界面。

- `onResume`：在活动恢复时调用，用于恢复活动的状态和用户交互。

- `onPause`：在活动暂停时调用，用于暂停活动的用户交互和数据操作。

- `onStop`：在活动停止时调用，用于停止活动的用户界面和数据操作。

- `onDestroy`：在活动销毁时调用，用于释放活动的资源和数据。

- `onRestart`：在活动重新启动时调用，用于重新启动活动的用户界面和数据操作。

例如，你可以在 `onCreate` 方法中初始化活动的布局和视图，然后在 `onStart` 方法中准备活动的用户界面，最后在 `onResume` 方法中恢复活动的状态和用户交互。

#### 生命周期回调

在 Android 开发中，`Activity` 的生命周期方法是由 Android 系统自动调用的，你可以重写这些方法来处理活动的状态和行为。例如，你可以在 `onCreate` 方法中初始化活动的布局和视图，然后在 `onStart` 方法中准备活动的用户界面，最后在 `onResume` 方法中恢复活动的状态和用户交互。

以下是一个简单的 `Activity` 示例，演示了如何重写生命周期方法：

```java
import android.app.Activity;

public class MyActivity extends Activity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        // 初始化活动的布局和视图
    }

    @Override
    protected void onStart() {
        super.onStart();
        // 准备活动的用户界面
    }

    @Override
    protected void onResume() {
        super.onResume();
        // 恢复活动的状态和用户交互
    }

    @Override
    protected void onPause() {
        super.onPause();
        // 暂停活动的用户交互和数据操作
    }

    @Override
    protected void onStop() {
        super.onStop();
        // 停止活动的用户界面和数据操作
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        // 释放活动的资源和数据
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        // 重新启动活动的用户界面和数据操作
    }
}
```

在上述示例中，我们重写了 `Activity` 的生命周期方法，用于处理活动的状态和行为。这些方法可以帮助你管理活动的生命周期，以便在不同的阶段执行不同的操作。

#### onCreate 方法和 main 方法的对比

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

## Service

在 Android 中，Service（服务）是一种用于执行长时间运行操作而不需要用户界面的组件。Service 可以在后台运行，并且即使用户切换到其他应用程序或者退出应用程序，Service 仍然可以继续运行。以下是关于 Service 组件的一些重要概念和用途：

1. **服务的作用**：

   - 服务主要用于执行后台任务，例如下载文件、播放音乐、处理网络请求等。
   - 服务通常用于那些不需要用户交互界面或者需要长时间运行的操作。

2. **服务的生命周期**：

   - `onCreate()`: 当服务被创建时调用，只会在服务第一次创建时调用。
   - `onStartCommand(Intent intent, int flags, int startId)`: 当另一个组件通过 startService() 方法启动服务时调用。在此方法中，你可以执行你想要在服务中处理的操作。
   - `onBind(Intent intent)`: 当另一个组件通过 bindService() 方法绑定到服务时调用。
   - `onDestroy()`: 当服务不再被使用且将要被销毁时调用。在此方法中，你可以清理资源或者执行其他必要的清理操作。

3. **服务的类型**：

   - 前台服务（Foreground Service）：会在通知栏显示一个持久通知，用于用户可以看到服务正在运行的情况。通常用于执行用户需要立即知晓的操作，如播放音乐。
   - 后台服务（Background Service）：在后台执行任务，不会给用户显示通知。通常用于执行不需要用户知晓的操作，如数据同步、网络请求等。

4. **服务与线程**：

   - Service 默认在主线程中运行，因此如果需要执行耗时操作，需要在 Service 中创建新线程或使用 Handler 等机制。
   - 也可以使用 IntentService 类来简化在后台执行耗时操作的流程，因为 IntentService 会自动创建工作线程来处理任务。

5. **服务的启动与绑定**：
   - 启动服务：通过 `startService()` 方法启动服务，服务会一直运行，直到调用 `stopService()` 或者服务自行停止。
   - 绑定服务：通过 `bindService()` 方法绑定服务，使得其他组件可以与服务进行交互，服务会随着绑定组件的生命周期而启动或停止。

服务是 Android 开发中一个重要的组件，它使得开发者可以在后台执行长时间运行的任务，同时保持应用程序的响应性和用户体验。
