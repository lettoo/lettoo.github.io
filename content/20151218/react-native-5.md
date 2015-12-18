----------

## 显示列表 ##

上一篇我们将真实的电影数据显示在界面上，我们只是显示其中一条数据，接下来我们需要将整个列表的数据都显示在界面上。

首先，我们要使用一个新的控件，`ListView`

引入`ListView`：

    var {
      AppRegistry,
      Image,
      ListView,
      StyleSheet,
      Text,
      View,
    } = React;
    
在`AwesomeProject`组件初始化`state`的方法中，初始化2个数据，一个是表示数据是否load完成状态的，一个是供`ListView`使用的`DataSource`

    getInitialState: function() {
        return {
          dataSource: new ListView.DataSource({
            rowHasChanged: (row1, row2) => row1 !== row2,
          }),
          loaded: false,
        };
      },

> 创建一个`ListView.DataSource`对象，并指定这个对象的`rowHasChanged`的方法具体实现方式。

需要更新fetchData方法：

    fetchData: function() {
        fetch(REQUEST_URL)
          .then((response) => response.json())
          .then((responseData) => {
            this.setState({
              dataSource: this.state.dataSource.cloneWithRows(responseData.movies),
              loaded: true,
            });
          })
          .done();
      },

> 这里更新了`dataSource`数据，并将`loaded`设置为**true**

在`render()`方法中，我们根据`loaded`来判断是否数据加载完成，如果没有完成，我们显示一个loading界面，如果完成，我们显示一个列表。

    render: function() {
        if (!this.state.loaded) {
          return this.renderLoadingView();
        }
    
        return (
          <ListView
            dataSource={this.state.dataSource}
            renderRow={this.renderMovie}
            style={styles.listView}
          />
        );
      },
    
最后，注意我们给`<ListView>`设置了一个**listView**的样式，定义如下：

     listView: {
        paddingTop: 20,
        backgroundColor: '#F5FCFF',
      },
      
OK，最终结果如下：

![此处输入图片的描述][1]

> 我们使用了`ListView`控件，并将`state`中的`dataSource`数据传进去，同时调用`renderMovie`来渲染显示数据。


  [1]: content/20151218/simulator_read_movies.png