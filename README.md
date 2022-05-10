####   knowledge
#### 知识学习

> - defineProperty
> 
>>> 虽然通过Object.defineProperty方法实现了对object数据的可观测，但是这个方法仅仅只能观测到object数据的取值及设置值，向object数据里添加一对新的key/value或删除一对已有的key/value时，它是无法观测到的，导致对object数据添加或删除值时，无法通知依赖，无法驱动视图进行响应式更新

> - 省份

> > >是通过地图，寻找价值的思路很容易存入的时间，放集合。
>-
>
>
#### this指向
> - 全局作用域下的this指向window。
> - 如果给元素的事件行为绑定函数，那么函数中的this指向当前被绑定的那个 元素。
> - 函数中的this，要看函数执行前有没有 . , 有 . 的话，点前面是谁，this就 指向谁，如果没有点，指向window。
> - 自执行函数中的this永远指向window。
> - 定时器中函数的this指向window。
> - 构造函数中的this指向当前的实例。
> - call、apply、bind可以改变函数的this指向。
> - 箭头函数中没有this，如果输出this，就会输出箭头函数定义时所在的作用域中的this.
