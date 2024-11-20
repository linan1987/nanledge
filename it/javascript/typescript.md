# TypeScript

## 99 配置文件 tsconfig.json

### ◉ forceConsistentCasingInFileNames [boolean]

代码中要引入的模块文件名必须和文件系统中的文件名保持大小写一致

```javascript
# FileManager 必须和实际文件名大小写一致
import { getName } from './FileManager.ts';
```