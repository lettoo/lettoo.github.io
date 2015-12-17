----------

> 本学习笔记是跟随React Native 官网文档和教程：https://facebook.github.io/react-native 学习过程中所记。

## React Native 介绍 ##

React Native 让开发者使用JavaScript和React技术，开发具备原生平台性能的app，与其他基于WebView的技术不同，React Native并不是让开发者开发一次便可以在多平台运行，而是让开发者学习和使用相同的技术来开发对应平台的app，从目前一些使用此技术开发出的app体验来看，运行效果已经能够媲美原生app的性能。

## 开发环境和开发工具 ##

开发iOS app需要有以下开发环境

 - Mac机
 - Mac OS X操作系统
 - [Homebrew][1]用于安装Watchman和Flow这2个工具
 - [Node.js][2]4.0以上版本
 - 安装Watchman: `brew install watchman`
 - 安装Flow: `brew install flow`
 - XCode 7.0以下版本

> 官网建议使用[nvm][3]来安装Node.js，同时建议使用npm 2.0版本，因为2.0版本比3.0版本速度快，使用这个命令来安装npm 2:`npm install -g npm@2`

## 开发第一个App ##

### 创建项目 ###

打开Terminal，在相应的路径下，执行`npm install -g react-native-cli`

以下是我执行命令的输出结果：

    $ npm install -g react-native-cli
    /Users/jeffrey/.nvm/versions/node/v5.2.0/bin/react-native -> /Users/jeffrey/.nvm/versions/node/v5.2.0/lib/node_modules/react-native-cli/index.js
    react-native-cli@0.1.7 /Users/jeffrey/.nvm/versions/node/v5.2.0/lib/node_modules/react-native-cli
    ├── semver@5.1.0
    ├── chalk@1.1.1 (supports-color@2.0.0, escape-string-regexp@1.0.3, ansi-styles@2.1.0, has-ansi@2.0.0, strip-ansi@3.0.0)
    └── prompt@0.2.14 (revalidator@0.1.8, pkginfo@0.3.1, read@1.0.7, winston@0.8.3, utile@0.2.1)
    
然后执行创建命令：`react-native init AwesomeProject`

以下是我的输出结果：

    $ react-native init AwesomeProject
    This will walk you through creating a new React Native project in /Users/jeffrey/project/ios/AwesomeProject
    Installing react-native package from npm...
    Setting up new React Native app in /Users/jeffrey/project/ios/AwesomeProject
    To run your app on iOS:
       Open /Users/jeffrey/project/ios/AwesomeProject/ios/AwesomeProject.xcodeproj in Xcode
       Hit the Run button
    To run your app on Android:
       Have an Android emulator running (quickest way to get started), or a device connected
       cd /Users/jeffrey/project/ios/AwesomeProject
       react-native run-android

> 这个过程有点慢，我开了vpn但仍然花费了大约10分钟的时间，所以请耐心等待。

### 运行项目 ###

打开XCode, open project，选择/Users/jeffrey/project/ios/AwesomeProject。
![在XCode中打开项目][4]

使用快捷键`⌘+R`来运行，这时会弹出React Native packager窗口。
![ Native packager][5]

然后在模拟器中我们可以看到这个app可以运行了。
![在模拟器中运行app][6]


----------


  [1]: http://brew.sh/
  [2]: https://nodejs.org/
  [3]: https://github.com/creationix/nvm#installation
  [4]: content/20151216/xcode.png "在XCode中打开项目"
  [5]: content/20151216/packager.png "React Native packager"
  [6]: content/20151216/simulator.png "在模拟器中运行app"
