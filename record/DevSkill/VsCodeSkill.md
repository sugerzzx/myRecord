# 如何使用 VSCode

## 自定义用户代码片段

`文件` ==> `首选项` ==> `配置用户代码片段` ==> 选择一种语言 ==> 输入代码片段

```json
// 以typescriptreact.json为例
{
  "Typescript React Function Component": {
    "prefix": "fc",
    "body": [
      "import { FC } from 'react'",
      "",
      "interface ${TM_FILENAME_BASE}Props {",
      "  $1",
      "}",
      "",
      "const $TM_FILENAME_BASE: FC<${TM_FILENAME_BASE}Props> = ({$2}) => {",
      "  return <div>$TM_FILENAME_BASE</div>",
      "}",
      "",
      "export default $TM_FILENAME_BASE"
    ],
    "description": "Typescript React Function Component"
  }
}
```

效果为：当输入`fc`时，会自动补全代码片段

```tsx
import { FC } from "react";

interface pageProps {}

const page: FC<pageProps> = ({}) => {
  return <div>page</div>;
};

export default page;
```
