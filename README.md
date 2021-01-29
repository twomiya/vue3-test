# vue3-2

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### 知识点
* setup和ref
* reactive
* 声明周期和钩子函数
  * setup()：开始创建组件之前，在beforeCreate和created之前执行，创建的是data和methods
  * onBeforeMount()：组件挂载到节点之前执行的函数
  * onMounted()：组件挂载完成后执行的函数
  * onBeforeUpdate()：组件更新之前执行的函数
  * onUpdated()：组件更新完成之后执行的函数
  * onBeforeUnmount()：组件卸载之前执行的函数
  * onUnmounted()：组件卸载完成之后执行的函数
  * onActivated()：被包含在<keep-alive>中的组件，会多出两个生命周期钩子函数。被激活时执行
  * onDeactivated()：比如从 A 组件，切换到 B 组件，A 组件消失时执行
  * onErrorCaptured()：当捕获一个来自子孙组件的异常时激活钩子函数
  * onRenderTracked()： 状态跟踪，跟踪页面上所有响应式变量和方法的状态，也就是我们用return返回去的值，他都会跟踪。只要页面有update的情况，他就会跟踪，然后生成一个event对象，我们通过event对象来查找程序的问题所在
  * onRenderTriggered()：状态触发,它不会跟踪每一个值，而是给你变化值的信息，并且新值和旧值都会给你明确的展示出来
  * 如果把onRenderTracked比喻成散弹枪，每个值都进行跟踪，那onRenderTriggered就是狙击枪，只精确跟踪发生变化的值，进行针对性调试。
  * 对 event 对象属性的详细介绍
    - key 那边变量发生了变化
    - newValue 更新后变量的值
    - oldValue 更新前变量的值
    - target 目前页面中的响应变量和函数

* vue2和vue3对比

Vue2--------------vue3

beforeCreate  -> setup()

created       -> setup()

beforeMount   -> onBeforeMount

mounted       -> onMounted

beforeUpdate  -> onBeforeUpdate

updated       -> onUpdated

beforeDestroy -> onBeforeUnmount

destroyed     -> onUnmounted

activated     -> onActivated

deactivated   -> onDeactivated

errorCaptured -> onErrorCaptured

* watch： 监听器(侦听器),作用是用来侦测响应式数据的变化
* 模块化
* teleport函数： 瞬间移动函数的使用
* 
  ```
    <teleport to="#modal">
    </teleport>
  ```
* suspense函数
* defineComponent是用来解决TypeScript情况下，传统的Vue.extends无法对组件给出正确的参数类型推断的。也就是说在TypeScript环境中如果参数类型推断不正常时，用defineComponent()组件来进行包装函数。
* onErrorCaptured 捕获错误，直接写在setup中即可