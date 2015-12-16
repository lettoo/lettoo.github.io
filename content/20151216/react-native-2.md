# React Native 学习笔记(2)

标签（空格分隔）： 未分类

---

## 代码解析 ##
我们来看一下使用命令`react-native init`生成的代码。`react-native init`用于初始化生成一个项目。
![代码目录结构][1]

 - index.ios.js 是iOS app的主入口
 - index.android.js 是Android app的主入口

由此可见，React Native并不是“一次编写，到处运行”，而是“一次学习，分别编写”。

接下来我们来逐段分析代码。

### 严格模式 ###
----------

    'use strict';

"严格模式"（strict mode）。顾名思义，这种模式使得Javascript在更严格的条件下运行。

这样做的目的主要有以下几个：

 - 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为
 - 消除代码运行的一些不安全之处，保证代码运行的安全
 - 提高编译器效率，增加运行速度

### 引入组件 ###
----------

    var React = require('react-native');
    var {
      AppRegistry,
      StyleSheet,
      Text,
      View,
    } = React;
    
首先引入react-native。然后通过对象的解构赋值方法来批量获取对象的属性并一次赋值给多个变量。

### 定义主入口类 ###
----------

    var AwesomeProject = React.createClass({
      render: function() {
        return (
          <View style={styles.container}>
            <Text style={styles.welcome}>
              Welcome to React Native!
            </Text>
            <Text style={styles.instructions}>
              To get started, edit index.ios.js
            </Text>
            <Text style={styles.instructions}>
              Press Cmd+R to reload,{'\n'}
              Cmd+D or shake for dev menu
            </Text>
          </View>
        );
      }
    });
    
这段代码定义了一个AwesomeProject对象，使用了React.createClass方法来创建这个对象，并实现了这个对象的render方法。在render方法中，返回了一个类似XML语法结构的语句块，我们称之为JSX。

我们看到首先使用了一个`<View>`块，然后在这个View块中我们有三个`<Text>`块。顾名思义，`<View>`块代表一个容器，`<Text>`块分别显示三段文字。注意我们使用了`style={styles.container}`这样的方式，来定义样式，React Native并不能直接使用css来定义样式，而是使用了一个`StyleSheet`对象来定义样式。

### 定义样式 ###
----------

    var styles = StyleSheet.create({
      container: {
        flex: 1,
        justifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#F5FCFF',
      },
      welcome: {
        fontSize: 20,
        textAlign: 'center',
        margin: 10,
      },
      instructions: {
        textAlign: 'center',
        color: '#333333',
        marginBottom: 5,
      },
    });
    
在上段代码中，我们使用了`StyleSheet.create`来创建了一个`styles`，在这个`styles`样式中，我们定义了`container`，`welcome`和`instructions`三个样式，样式的定义和css语法差不多，注意第一个样式`container`我们使用了flexbox布局，详细的flexbox的布局语法请参考阮一锋老师的blog: http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html

### 注册组件 ###
----------

    AppRegistry.registerComponent('AwesomeProject', () => AwesomeProject);

注意`() => AwesomeProject`这是ES6的箭头函数定义方式，上面的语句也可以这样写：

    AppRegistry.registerComponent('AwesomeProject', function(){
            return AwesomeProject;
        }
    );

  [1]: content/20151216/sublime.png