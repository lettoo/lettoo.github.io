----------

## 显示真实数据 ##

接下来我们需要使用一个真实的url来获取真实的数据，定义一个提供json数据的api url:

    var REQUEST_URL ='https://raw.githubusercontent.com/facebook/react-native/master/docs/MoviesExample.json';

看一下这个url返回的是什么数据：

![此处输入图片的描述][1]

这里我们需要引入一个react的数据概念：`state`，我们使用`state`来存储变化的数据，当`state`的数据发生变化时，react会引用`render()`方法来将变化的数据渲染到组件界面上。

所以，我们需要在`AwesomeProject`这个对象增加`state`的初始化方法：

    getInitialState: function() {
        return {
          movies: null,
        };
    },

在组件加载完成的时候，去获取真实的数据，更新state中的数据：

    componentDidMount: function() {
        this.fetchData();
    },
    
这里使用了一个`fetchData()`的方法，看看是怎么定义这个方法的：

    fetchData: function() {
        fetch(REQUEST_URL)
          .then((response) => response.json())
          .then((responseData) => {
            this.setState({
              movies: responseData.movies,
            });
          })
          .done();
    },
    

> - 关于fetch API的使用，建议读一读这里：https://developer.mozilla.org/en/docs/Web/API/Fetch_API
> - 这里使用了ES6的箭头函数，`(response) => response.json()`的写法等同于`function(response) {return response.json();}`

    (responseData) => {
        this.setState({
          movies: responseData.movies,
        });
      }

上面代码的写法等同于：

    function(responseData) {
        this.setState({
          movies: responseData.movies,
        });
    }
    

> this.setState()方法更新了`state`的数据。

当`state`的数据发生变化的时候，React会调用组件的`render()`方法重新渲染组件界面。

    render: function() {
        if (!this.state.movies) {
          return this.renderLoadingView();
        }
    
        var movie = this.state.movies[0];
        return this.renderMovie(movie);
      },
    
      renderLoadingView: function() {
        return (
          <View style={styles.container}>
            <Text>
              Loading movies...
            </Text>
          </View>
        );
      },
    
      renderMovie: function(movie) {
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
      },

> - 当程序去调用fetch api去获取数据之前，`state`中的`movies`数据是空值，这里我们让界面显示一个"loading"
> - 当fetch api返回的数据，并将`state`中的`movies`数据更新时，这里我们将`movies`中的第一条记录显示在界面上。

ok，重新刷新模拟器，我们看到显示了一条真实的电影信息：

![此处输入图片的描述][2]


  [1]: content/20151218/real_json_url.png
  [2]: content/20151218/simulator_real_movie.png