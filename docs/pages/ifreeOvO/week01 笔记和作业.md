# week01 笔记和作业


#### 为什么全局安装@vue/cli后会添加命令vue
因为决定命令名称的是package.json的bin 里面的配置，与包名无关

```json
// package.json
"bin": {
  "vue": "bin/vue.js"
}
```

#### 全局安装@vue-cli时发生了什么
安装后，包会被下载在全局的node_modules里，然后解析`package.json`的`bin`，接着在安装node的主目录的bin文件下创建一个软链接，指向实际执行的文件

#### 为什么vue指向一个js文件，我们却可以直接通过vue命令直接取执行它
执行vue时，它等价于执行指向软链接对应的实际文件，系统会根据文件首行的`#! /usr/bin/env node`，去环境变量中找node命令，最后通过node命令执行实际文件
