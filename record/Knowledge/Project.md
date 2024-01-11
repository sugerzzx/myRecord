# JSProject

## Source Map

JavaScript Source Map（JS Source Map）是一个映射文件，它可以将压缩、混淆后的 JavaScript 代码映射回原始的源代码。这样，当在浏览器中调试代码时，即使 JavaScript 代码已经被压缩或混淆，开发者也可以看到原始的源代码，从而更方便地进行调试和错误定位。

在 JavaScript 文件中，通常会有一行注释指向 Source Map 文件，如：`//# sourceMappingURL=/path/to/file.js.map`。

Source Map 文件是一个 JSON 格式的文件，包含了源代码和生成代码之间的位置
