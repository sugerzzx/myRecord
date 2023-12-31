# Android Layout

## 什么是 Android 布局

在 Android 开发中，布局（Layout）是指**定义应用程序中用户界面的方式**。Android 应用程序的用户界面通常由多个**控件**（Widget）组成，如按钮、文本框、图像等。布局管理器（Layout Manager）负责**决定这些控件在屏幕上的排列方式和位置**。

Android 提供了多种布局类型，每种都适用于不同的布局需求。以下是一些常见的 Android 布局类型：

1.  **线性布局（LinearLayout）：**

    - 线性布局是一种按照水平或垂直方向排列子元素的布局。你可以通过设置权重来调整子元素在布局中的分配空间。

2.  **相对布局（RelativeLayout）：**

    - 相对布局允许你相对于其他控件来定位每个控件。这意味着你可以根据其他控件的位置来布局界面元素。

3.  **帧布局（FrameLayout）：**

    - 帧布局是一种简单的布局，它将所有的子元素叠放在屏幕上，后添加的子元素会覆盖先添加的。

4.  **表格布局（TableLayout）：**

    - 表格布局将界面分割为行和列，每个单元格可以包含一个控件。这是一种复杂的布局，适用于需要以表格形式展示数据的情况。

5.  **约束布局（ConstraintLayout）：**

    - 约束布局是 Android Studio 中引入的一种强大的布局，它使用约束条件来定义控件之间的关系，使得布局适应不同屏幕大小和方向。

6.  **网格布局（GridLayout）：**

    - 网格布局将界面分割为网格，每个单元格可以包含一个控件。它类似于表格布局，但使用更直观的方式定义行和列。

布局是 Android 应用程序开发中关键的部分，良好的布局可以提高用户体验，确保应用在不同设备上都能够合适地显示和运行。选择合适的布局类型取决于应用程序的设计需求和用户界面的复杂性。
