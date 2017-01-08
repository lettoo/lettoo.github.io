Python多线程实例

使用`multiprocessing.Process`类

1. 首先创建一个类继承自`Process`
2. 在`__init__()`方法里，调用`Process`的`__init__()`方法
3. 实现具体的`run()`方法
4. 调用的时候，先实例化多个这个类，放到一个`list`里，然后在需要运行的时候，依次调用每个实例的`start()`方法

实例如下：

```
from multiprocessing import Process
import time
from random import randint


class Bot(Process):
    def __init__(self, name):
        super(Bot, self).__init__()
        self.name = name

    def run(self):
        print '%s start' % self.name
        sleep_seconds = randint(0, 9)
        time.sleep(sleep_seconds)
        print '%s run for %d seconds' % (self.name, sleep_seconds)
        print '%s end' % self.name


if __name__ == '__main__':
    bots = []
    for i in range(6):
        name = 'name-%d' % i
        bot = Bot(name)
        bots.append(bot)

    for bot in bots:
        bot.start()

```
