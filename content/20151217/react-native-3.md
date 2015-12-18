---------

## 修改代码 ##

接下来修改index.ios.js这个文件，我们想在屏幕正中间显示一张图片。首先，定义一个数组，这个数组包括了一个电影对象。

    var MOCKED_MOVIES_DATA = [
      {title: 'Title', year: '2015', posters: {thumbnail: 'http://i.imgur.com/UePbdph.jpg'}},
    ];
    
然后将React.Image传值给Image变量。

    var {
      AppRegistry,
      Image,
      StyleSheet,
      Text,
      View,
    } = React;

接下来修改AwesomeProject对象的render方法。

    render: function() {
        var movie = MOCKED_MOVIES_DATA[0];
        return (
          <View style={styles.container}>
            <Text>{movie.title}</Text>
            <Text>{movie.year}</Text>
            <Image source={{uri: movie.posters.thumbnail}} />
          </View>
        );
      }
      
上面代码中，我们使用了`container`这个样式，我们这样定义它：

    var styles = StyleSheet.create({
      container: {
        flex: 1,
        justifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#F5FCFF',
      },
      thumbnail: {
        width: 53,
        height: 81,
      },
    });

> - justifyContent: 容器内元素水平居中
> - alignItems: 容器内元素垂直居中

在模拟器中运行app，但是并没有看到图片显示出来。

![模拟器中运行app但没有看到图片][1]

> **小贴士**： 在模拟器中使用快捷键`⌘+R`来刷新界面，不需要每次都重新在XCode中编译运行。

将render方法中的`<Image>`修改如下：

    <Image 
    source={{uri: movie.posters.thumbnail}}
    style={styles.thumbnail}
    />
    
Ok，这样我们看到图片显示出来了。

![模拟器中运行app显示图片][2]

接下来，我们想实现这样的布局：图片在左边，右边分两栏，第一栏是title，第二栏是年份。

    +---------------------------------+
    |+-------++----------------------+|
    ||       ||        Title         ||
    || Image ||                      ||
    ||       ||        Year          ||
    |+-------++----------------------+|
    +---------------------------------+

将render方法修改如下：
    
    return (
        <View style={styles.container}>
          <Image
            source={{uri: movie.posters.thumbnail}}
            style={styles.thumbnail}
          />
          <View style={styles.rightContainer}>
            <Text style={styles.title}>{movie.title}</Text>
            <Text style={styles.year}>{movie.year}</Text>
          </View>
        </View>
      );
      
对应的，需要修改样式：

    container: {
        flex: 1,
        flexDirection: 'row',
        justifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#F5FCFF',
    },

> - flexDirection: 'row' 表示容器内的元素将横向排列，默认是竖向排列。

    rightContainer: {
        flex: 1,
    },
    
> `rightContainer`是`container`的一个子元素，`flex: 1`表示这个子元素将占用`container`除了`<Image>`之外的剩余空间。

另外，我们还使用了`styles.title`和`styles.year`两个样式，定义如下：

    title: {
        fontSize: 20,
        marginBottom: 8,
        textAlign: 'center',
    },
    year: {
        textAlign: 'center',
    },
    
`⌘+R`来刷新模拟器，现在好看多了。

![此处输入图片的描述][3]


  [1]: content/20151217/simulator_no_image.png
  [2]: content/20151217/simulator_has_image.png
  [3]: content/20151217/simulator_one_movie.png
