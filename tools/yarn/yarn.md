# Yarn的使用
## 一、yarn的简介：
Yarn是facebook发布的一款取代npm的包管理工具。
## 二、yarn的特点：
+ 速度超快。
  + Yarn 缓存了每个下载过的包，所以再次使用时无需重复下载。 同时利用并行下载以最大化资源 利用率，因此安装速度更快。
+ 超级安全。
  + 在执行代码之前，Yarn 会通过算法校验每个安装包的完整性。
+ 超级可靠。
  + 使用详细、简洁的锁文件格式和明确的安装算法，Yarn 能够保证在不同系统上无差异的工作。
## 三、yarn的安装:
`npm install -g yarn`  
`npm uninstall yarn -g  //yarn卸载`  
## 四、yarn的常用命令
### yran版本和源
1. yarn -v  // 查看yarn 版本
2. yarn config list  // 查看yarn配置
3. yarn config get registry   // 查看当前yarn源
4. yarn config set registry https://registry.npm.taobao.org  //修改yarn源（此处为淘宝的源）
###  yarn安装依赖
1. yarn add 包名          // 局部安装
2. yarn global add 包名   // 全局安装
###  yarn 卸载依赖
1. yarn remove 包名         // 局部卸载
2. yarn global remove 包名  // 全局卸载（如果安装时安到了全局，那么卸载就要对应卸载全局的）
###  yarn 查看全局安装过的包
1. yarn global list  
### yarn创建文件夹
1. md yarn   // 创建文件夹 yarn
2. cd yarn   // 进入yarn文件夹 
### 初始化项目
1. yarn init // 同npm init，执行输入信息后，会生成package.json文件
### yarn的配置项：
1. yarn config list // 显示所有配置项
2. yarn config get <key> //显示某配置项
3. yarn config delete <key> //删除某配置项
4. yarn config set <key> <value> [-g|--global] //设置配置项
### 安装包：
1. yarn install         //安装package.json里所有包，并将包及它的所有依赖项保存进yarn.lock
2. yarn install --flat  //安装一个包的单一版本
3. yarn install --force         //强制重新下载所有包
4. yarn install --production    //只安装dependencies里的包
5. yarn install --no-lockfile   //不读取或生成yarn.lock
6. yarn install --pure-lockfile //不生成yarn.lock
7. 添加包（会更新package.json和yarn.lock）：  
   + yarn add [package] // 在当前的项目中添加一个依赖包，会自动更新到package.json和yarn.lock文件中
   + yarn add [package]@[version] // 安装指定版本，这里指的是主要版本，如果需要精确到小版本，使用-E参数
   + yarn add [package]@[tag] // 安装某个tag（比如beta,next或者latest）
   + <font color=red>不太理解tag（待学习）</font>
8. 不指定依赖类型默认安装到dependencies里，你也可以指定依赖类型：
   + yarn add --dev/-D // 加到 devDependencies
   + yarn add --peer/-P // 加到 peerDependencies
   + yarn add --optional/-O // 加到 optionalDependencies
9. 默认安装包的主要版本里的最新版本，下面两个命令可以指定版本： 
   + yarn add --exact/-E // 安装包的精确版本。例如yarn add foo@1.2.3会接受1.9.1版，但是yarn add foo@1.2.3 --exact只会接受1.2.3版
   + yarn add --tilde/-T // 安装包的次要版本里的最新版。例如yarn add foo@1.2.3 --tilde会接受1.2.9，但不接受1.3.0
10. yarn publish // 发布包
11. yarn remove <packageName>  // 移除一个包，会自动更新package.json和yarn.lock
12. yarn upgrade // 更新一个依赖: 用于更新包到基于规范范围的最新版本
13. yarn run   // 运行脚本: 用来执行在 package.json 中 scripts 属性下定义的脚本
14. yarn info <packageName> 可以用来查看某个模块的最新版本信息
### 更新一个依赖
1. yarn upgrade # 升级所有依赖项，不记录在 package.json 中
2. npm update # npm 可以通过 ‘--save|-D’ 指定升级哪类依赖
3. yarn upgrade 包名 # 升级指定包
4. npm update 包名
5. yarn upgrade --latest    忽略版本规则，升级到最新版本，并且更新 package.json
### 移除一个依赖
1. yarn remove 包名
2.  npm uninstall 包名
### 缓存
1. yarn cache
2. yarn cache list # 列出已缓存的每个包
3. yarn cache dir # 返回 全局缓存位置
4. yarn cache clean # 清除缓存
## 五、与npm的比较
### npm
1. 不用单独安装，它随 node 一起提供，node装好了npm就自动装好了【node是一个JS运行环境】
2. npm是一个包，这个包可以管理（下载、更新、删除）别的包
3. npm在下载包的时候有一个缓存的过程，我们一般不会使用npm默认下载缓存目录，而会自定义指定npm下载缓存目录
   执行 npm config set cache "C:\Program Files\nodejs\npm_cache"
4. npm下载包分为本地下载和全局下载，本地下载会下载到指定的文件夹，而全局下载会下载到默认的全局包保存路径，我们一般不会使用npm默认的全局包下载保存路径，而会自定义指定npm全局包下载路径。
   执行 npm config set prefix "C:\Program Files\nodejs\npm_global"

注意：npm自定义修改了全局包存放路径，还需要去设置环境变量，将自定义全局包路径加到环境变量中，否则全局装的包没法在命令行窗口中正常使用
### yarn：
Yarn是由Facebook、Google、Exponent 和 Tilde 联合推出了一个新的 JS 包管理工具（取代npm） ,是为了弥补 npm 的一些缺陷而出现。

1. 这个包默认没有，需要使用npm来进行安装
　　执行命令：npm install -g yarn
2. yarn在下载包的时候有一个缓存的过程，我们一般不会使用yarn默认下载缓存目录，而会自定义指定yarn下载缓存目录  
   执行 yarn config set cache-folder "C:\Program Files\nodejs\yarn_cache"
3. yarn下载包分为本地下载和全局下载，本地下载会下载到指定的文件夹，而全局下载会下载到默认的全局包保存路径，我们一般不会使用yarn默认的全局包下载保存路径，而会自定义指定yarn全局包下载路径。
   执行 yarn config set global-folder "C:\Program Files\nodejs\yarn_global"
   注意：yarn自定义修改了全局包存放路径，还需要去设置环境变量，将自定义全局包路径加到环境变量中，否则全局装的包没法在命令行窗口中正常使用

### Npm和Yarn优劣对比
#### Npm的劣势
+ npm install太慢。特别是新的项目拉下来要等半天，删除node_modules，重新install的时候依旧如此。
+ 同一个项目，安装的时候模块版本无法保持一致性。这是由于package.json文件中版本号的缘故。同一个项目，安装的时候无法保持一致性。由于package.json文件中版本号的特点，下面三个版本号在安装的时候代表不同的含义。 “5.0.3”表示安装指定的5.0.3版本，“～5.0.3”表示安装5.0.X中最新的版本，“^5.0.3”表示安装5.X.X中最新的版本。这就麻烦了，常常会出现同一个项目，有的同事是OK的，有的同事会由于安装的版本不一致出现bug。
+ 安装报错被覆盖。安装的时候，包会在同一时间下载和安装，中途某个时候，一个包抛出了一个错误，但是npm会继续下载和安装包。
#### Yarn的优势
+ 安装速度快 (服务器速度快 , 并且是并行下载)
+ 版本锁定，安装版本统一
+ 离线缓存机制，如果之前已经安装过一个软件包，用Yarn再次安装时从缓存中获取，就不用像npm那样再从网络下载了
+ 离线缓存，yarn 缓存了每个下载过的包，所以再次使用时无需重复下载。 同时利用并行下载以最大化资源利用率，因此安装速度更快。
+ 安装版本一致：在执行代码之前，Yarn 会通过算法校验每个安装包的完整性。并且为了防止拉取到不同的版本，Yarn 有一个锁定文件 (lock file) 记录了被确切安装上的模块的版本号。
+ 简洁语义：yarn改变了一些npm命令的名称，比如 yarn add/remove，感觉上比 npm 原本的 install/uninstall 要更清晰。
