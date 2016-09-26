# react理论知识


##  简介

- 是Facebook推出的一个用来构建用户界面的JavaScript库
- 开源
- 虚拟DOM（Virtual DOM）和组件化

##  优点

- 能够实现服务器端的渲染，便于搜索引擎优化。
- 因为一切都是component，所以代码更加模块化，重用代码更容易。（components 的存在让计算 DOM diff 更高效）
- 用了virtual dom，所以性能很好。（React不是全局刷新，而是通过它内部的 dom diff 算法计算出不同点，然后以最小粒度进行更新）
- 单向数据绑定（在冯诺依曼体系中，数据就是单向流动的）

##  认识

- React不是一个MVC框架，是一个纯view层。
- React是单向的从数据到视图的渲染，非双向数据绑定。
- react并不依赖jQuery，当然我们可以使用jQuery。
- React 有独有的 JSX 语法，跟 JavaScript 不兼容。
- React不使用模板。

##  Virtual DOM 虚拟DOM

- React为了尽可能减少对DOM的操作，提供了一种不同的而又强大的方式来更新DOM，代替直接的DOM操作。就是Virtual DOM,一个轻量级的虚拟的DOM，就是React抽象出来的一个对象，描述dom应该什么样子的，应该如何呈现。通过这个Virtual DOM去更新真实的DOM，由这个Virtual DOM管理真实DOM的更新。
- 为什么通过这多一层的Virtual DOM操作就能更快呢？ 这是因为React有个diff算法，更新Virtual DOM并不保证马上影响真实的DOM，React会等到事件循环结束，然后利用这个diff算法，通过当前新的dom表述与之前的作比较，计算出最小的步骤更新真实的DOM。
- 其实这里的原理和脏检查一样，会在改动过的地方标脏，然后在Event loop结束时会计算得出DOM树上标了脏的地方，然后对这些地方进行重新渲染。

##  Components 组件

- 在DOM树上的节点被称为元素，在这里则不同，Virtual DOM上称为commponent。
- Virtual DOM的节点就是一个完整抽象的组件，它是由commponents组成。

## State 和 属性 和 Render

- state和属性包含定义组件所需要的一些数据，当数据发生变化时，将会调用Render重现渲染，都是纯JS对象。
- state是和自己相关的，既不受父组件也不受子组件影响。
- 属性本身是不能自己去修改的，只能从父组件获取属性，父组件也能修改它的属性
- 属性和状态根本的区别：组件在运行时需要去修改维护的就是状态