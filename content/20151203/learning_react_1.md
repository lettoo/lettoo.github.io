### 1. 什么是React
一个用于创建用户界面的JavaScript库。
* [官方网站](http://facebook.github.io/react/)
* [中文网站](http://reactjs.cn/)：从版本号来看，这个网站更新的不快。

### 2. 为什么要学习React
* 作为一个后端开发来说，了解并掌握一门新的前端技术，达成自己full-stack的目标。
* 作为后期使用[React Native](http://facebook.github.io/react-native/)的基础。

### 3. 学习React硬件环境准备
* 推荐使用Macbook Pro进行开发
* 找一个安静的地方，泡好茶，播放轻柔背景音乐
* 最好有一个完整的下午时间，关闭手机，进入免打扰模式

### 4. 学习React软件环境准备
> 前提环境，在电脑上安装好Node.js[^nodejs]和npm[^npm]。可以使用以下命令来验证是否安装，以下是我的电脑Node.js和npm版本：

```
$ node --version
v5.1.0

$ npm --version
3.3.12
```

官方推荐使用[browserify](http://browserify.org/)或者是[webpack](https://webpack.github.io/)来模块化React代码。但考虑到简单使用，我们这里可以直接使用React。

[直接下载React初学者开发包](http://facebook.github.io/react/downloads/react-0.14.3.zip)

以上为准备工作，接下来开始正式编程吧。

------

1. 解压缩上面下载的React初学者开发包，然后使用你喜欢的编辑器打开。
![react代码目录](content/20151203/react_code_dir.png)

2. 在代码根目录下，创建一个helloworld.html

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Hello React!</title>
    <script src="build/react.js"></script>
    <script src="build/react-dom.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
  </head>
  <body>
    <div id="example"></div>
    <script type="text/babel">
      ReactDOM.render(
        <h1>Hello, world!</h1>,
        document.getElementById('example')
      );
    </script>
  </body>
</html>
```
**代码分解如下**
1. `<script src="build/react.js"></script>`
引用react.js
2. `<script src="build/react-dom.js"></script>`
引用react-dom.js
3. `<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>`
引用babel的browser插件，Babel是一个广泛使用的ES6转码器，可以将ES6代码转为ES5代码，从而在浏览器或其他环境执行。这意味着，你可以用ES6的方式编写程序，又不用担心现有环境是否支持。
4. 下面这段代码使用ReactDom的render方法，输出Hello, world!。
```
<script type="text/babel">
  ReactDOM.render(
    <h1>Hello, world!</h1>,
    document.getElementById('example')
  );
</script>  
```
上面那段类似于XML语法的代码叫JSX[^JSX]，为了使浏览器能够运行这段代码，所以我们要使用`type="text/babel"`来将之转换成浏览器可以执行的代码。

运行一下：
![React Hello, World!](content/20151203/react_hello_world.png)

------

[^nodejs]: https://nodejs.org/en/

[^npm]: [npm](https://www.npmjs.com/) makes it easy for JavaScript developers to share and reuse code, and it makes it easy to update the code that you're sharing.

[^JSX]: 是一个看起来很像 XML 的 JavaScript 语法扩展。React 可以用来做简单的 JSX 句法转换。