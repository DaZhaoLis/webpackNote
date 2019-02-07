# npm 和 package.json 复习
## packageJson 介绍  
**bin** 指定各个内部命令对应的可执行文件的位置
> "bin": {
  "someTool": "./bin/someTool.js"
}
**config** config字段用于添加命令行的环境变量
> {
  "name" : "foo",
  "config" : { "port" : "8080" },
  "scripts" : { "start" : "node server.js" }
}
npm config set foo:port 80 
## Semantic versioning
- 补丁版本：解决了 Bug 或者一些较小的更改，增加最后一位数字，比如 1.0.1 
> ～ 表示只接受补丁版本的更新
- 小版本：增加了新特性，同时不会影响之前的版本，增加中间一位数字，比如 1.1.0
> ^ 表示接受小版本的更新
- 大版本：大改版，无法兼容之前的，增加第一位数字，比如 2.0.0
> *或x 表示更新大版本 
> @latest @">=1.1.0 <2.0.2" --depth 更新层次
## 常见命令
npm i --production
> 仅安装生产包 类似的还是有 npm update --production  

npm outdated  
> 查看包是否过期，其实不太建议经常更新，更新之前必须认真查看更新了什么，避免更新带来的不安全等问题。  

npm prune
> 删除在父依赖中没有找到的。在packageJson中找不到的moudle  

npm link/unlink
> 用于开发时进行调试。  [建立软link detail](https://docs.npmjs.com/cli/link.html)  

npm run
> 查看packageJson中的script可执行的内容。 npm run 会临时将node_modules/.bin加入PATH变量。本地的moudle就可直接运行。  
npm i eslint --save-dev
运行上面的命令以后，会产生两个结果。首先，ESLint被安装到当前目录的node_modules子目录；其次，node_modules/.bin目录会生成一个符号链接node_modules/.bin/eslint，指向ESLint模块的可执行脚本。  

pre- 和 post-
> 提供run 之前和之后的运行方式，若scripts有pretest posttest 和 test ，运行 npm run test 时会执行 pretest --> test --> posttest  [其中commit和push之前的钩子也可以用](https://segmentfault.com/a/1190000009048911)  
https://segmentfault.com/a/1190000009546913  

## 在script中可以使用 packageJson 变量
> npm_package_version packageJson中的version 而 npm_package_name 表示 packageJson中的名称