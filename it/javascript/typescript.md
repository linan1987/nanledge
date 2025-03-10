# TypeScript

## 99 配置文件 tsconfig.json

### ◉ include [Array]

指定要编译的文件或目录

```json
"include": ["src/**/*"]
```

### ◉ exclude [Array]

指定要排除的文件或目录，必须配合 `include` 使用，确保要排除的目录或文件属于include的某个目录范围内。

```json
"exclude": ["node_modules", "dist"]
```

### ◉ forceConsistentCasingInFileNames [boolean]

代码中要引入的模块文件名必须和文件系统中的文件名保持大小写一致

```javascript
// FileManager 必须和实际文件名大小写一致
import { getName } from './FileManager.ts';
```

### ◉ allowSyntheticDefaultImports [boolean]

有些模块（特别是用 CommonJS 规范编写的模块）没有默认导出，但你可能希望像使用默认导出一样导入它们。例如，使用 CommonJS 规范的模块通常使用 module.exports 导出：

```javascript
// CommonJS 模块
module.exports = {
  myFunction: function() {
    // ...
  }
};
```

在这种情况下，直接使用默认导入会导致错误：

```javascript
import myFunction from 'my-commonjs-module'; // 错误
```

设置 "allowSyntheticDefaultImports": true 后，将被允许。

这个选项不会改变模块的实际导出方式，只是在编译时进行处理。

如果你同时使用 Babel 进行编译，Babel 也有类似的配置项，可以实现相同的效果。