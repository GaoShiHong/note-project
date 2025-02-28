# nrm和nvm的详解

## nrm 使用详解

### 背景
npm 默认镜像源是 https://registry.npmjs.org/，在国内访问可能会很慢。后来，淘宝做了一个镜像网站（npmmirror），以便国内开发者访问。

使用 npm 命令，可以这样设置镜像源：

``` sh
 $ npm config set registry https://registry.npmmirror.com/ 
```
但有点长，特别是源地址，不好记。下文将会介绍使用 nrm 来快速切换。

```
原淘宝 npm 域名即将停止解析，请切换至新域名 npmmirror.com。http://npm.taobao.org和 http://registry.npm.taobao.org 将在 2022 年 6 月 30 日正式下线和停止 DNS 解析。
```

### 安装与使用
nrm（NPM registry manager）是 npm 的镜像源管理工具之一。

### 全局安装

`$ npm i nrm -g`

### 查看所有源

```
$ nrm ls

* npm -------- https://registry.npmjs.org/
  yarn ------- https://registry.yarnpkg.com/
  cnpm ------- http://r.cnpmjs.org/
  taobao ----- https://www.npmmirror.com/
  nj --------- https://registry.nodejitsu.com/
  npmMirror -- https://skimdb.npmjs.com/registry/
  edunpm ----- http://registry.enpmjs.org/
```
其中 * 号表示当前使用的源。

也可使用 nrm current 命令查看当前源。

### 切换源
相比之下，nrm use taobao 简直不要太方便了。

`$ nrm use <registry>`
注意切换源之后，我们安装依赖仍使用 npm i <name> 的方式来进行安装。

其中 <registry> 就是上面命令所列出来的名称。

### 添加源
适用于企业内部定制的私有源，<registry> 表示源名称，<url> 表示源地址。

`$ nrm add <registry> <url>`
比如使用 Verdaccio 在本地搭了一个 NPM 平台，然后通过 nrm add local http://localhost:4873/ 来指定源。

### 删除源
`$ nrm del <registry>`
测试源的响应时间
`$ nrm test <registry>`
### References
[NPM registry manager](https://github.com/Pana/nrm)

[一个可同时切换 npm 和 yarn 镜像源的工具](https://github.com/toFrankie/blog/issues/91)

[一个极简的 npm/yarn registry 切换管理器](https://www.yunyoujun.cn/posts/nnrm-new-nrm)




## nvm使用详解