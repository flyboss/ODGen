# JS import knowledge
- ECMAScript (ES6)  
```js
import xxx from 'xxx.js'

export function foo(){}
```

## Nodejs support  CJS and ES6

### CJS
- CommonJS-style module system "CJS"
```js
function hello() {
  return "Hello";
}
module.exports = hello
// or
module.exports = {hello} // omit key
// or
module.exports = {hello:hello} // omit "" in key
// or
module.exports = {"hello": hello} // if key has 空格、破折号、以数字开头或包含特殊字符时, must add ""

const myModule = require('./mymodule');
```

### CJS and ES6 differ
- 文件扩展名
  - CommonJS 模块通常使用 .js 或 .cjs 扩展名。
  - ES6 模块通常使用 .mjs 扩展名。
- package.json 中的 "type" 字段 Node.js 通过 package.json 文件中的 "type" 字段来判断模块的类型。
  - 如果在 package.json 中设置了 "type": "module"，则文件会被当作 ES6 模块处理，默认使用 import/export 语法。
  - 如果没有设置 "type"，或者设置为 "type": "commonjs"，则默认使用 CommonJS 模块，且可以使用 require 和 module.exports。

## browser support ES6
- 以前没有 module 的概念，所有 script 都是全局 scope

```html
<script>
  var foo = "Hello";  // 全局
</script>

<script type="module"> // ES6
  let foo = "Hello"; // foo 是模块作用域内的
</script>
```

## odgen 一个最简单的例子，用于研究它的命令行参数
- nodejs version unknown，但222服务器上的 node-22 or node-16 应该有一个能用
```shell
conda activate ODGen

python odgen.py -t code_exec  -ma /mnt/disk2/liwei/01-code/ODGen/tests/packages/lw_test/arg_nodejs/hello.js 
```
- 必须同时加 ma，否则找不到Vulnerability