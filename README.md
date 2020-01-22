# vue组件通信方式demo

### 安装依赖
```
npm install
```
### 启动服务
```
npm run serve
```

### 主要内容
组件之间通信方式

props： 父亲--》后代

$on;$emit 子--》祖先 兄弟（共同父亲）

$parent $children|$refs

provide inject  擅长隔代处理  子-》祖先

$listener  $attrs 擅长隔代处理 子-》祖先

### demo
![image](http://github.com/satomiyoyi/vue-component-communication-demo/vue-communication-demo.png)