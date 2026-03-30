## **现象描述**

在 Vue.js 框架中通过 `npm run dev` 运行 Demo 时，报如下错误：

```
No mactching export in "node_modules/react-virtualized/dist/es/WindowScroller/WindowScroller.js" for improt "bpfrpt_proptype_WindowsScroller"
```

<img alt="image.png" src="https://yx-web-nosdn.netease.im/common/78fe781ee649c0d6697ed784f4992848/image.png" style="width:80%;border: 1px solid #BFBFBF;">

## **原因分析**

这个错误的原因是由于 `react-virtualized` 库引起的。具体来说，`react-virtualized` 库在某些版本中可能存在不兼容的问题，导致在导入 WindowScroller 时出现错误。具体步骤包括：

1. 导入必要的模块。
2. 修改 react-virtualized 模块中的某些路径。
3. 替换文件中的错误代码。

通过这种方式，可以绕过 react-virtualized 库中的问题，使得 Demo 能够正常运行。

## **解决方法**

将 `vite.config.ts` 文件中的代码替换为如下内容：

```JavaScript
import { fileURLToPath, URL } from "node:url";
import { defineConfig } from "vite";
import vue from "@vitejs/plugin-vue";
import vueJsx from "@vitejs/plugin-vue-jsx";
import * as path from 'path'
import * as fs from 'fs'

const WRONG_CODE = `import { bpfrpt_proptype_WindowScroller } from "../WindowScroller.js";`;

function reactVirtualized() {
  return {
    name: 'my:react-virtualized',
    configResolved() {
      const file = require.resolve('react-virtualized')
        .replace(
          path.join('dist', 'commonjs', 'index.js'),
          path.join('dist', 'es', 'WindowScroller', 'utils', 'onScroll.js')
        );
      const code = fs.readFileSync(file, 'utf-8');
      const modified = code.replace(WRONG_CODE, '');
      fs.writeFileSync(file, modified);
    },
  };
}

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue(), vueJsx(), reactVirtualized()],
  resolve: {
    alias: {
      "@": fileURLToPath(new URL("./src", import.meta.url)),
    },
  },
  css: {
    preprocessorOptions: {
      less: {
        javascriptEnabled: true,
      },
    },
  },
});
```