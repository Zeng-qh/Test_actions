---
title: Vue
date: 2020-05-10
categories:
 - 前端
tags:
 - Vue
# keys:
#  - '123456' 
publish: true
---
:::tip
Vue 渐进式JavaScript 框架 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提驱动。

:::
![img](https://dss0.bdstatic.com/6Ox1bjeh1BF3odCf/it/u=3533778697,2586993014&fm=74&app=80&f=PNG&size=f121,121?sec=1880279984&t=1dbed90be2871a78074bf731b6872ed0)
<!-- more -->
## 基础
### 基本介绍
引入vue.js
 Vue 应用都是通过用 Vue 函数创建一个新的 Vue 实例开始的
 ```js
var vm = new Vue({
           el:"#app", // vue 渲染开始的地方 用来指定Vue实例托管范围
           data:{ // Vue实例中可以调用的变量
            myname:"vue"
           }
        })
 ```
### 模板语法
#### 插值
```html
<div id="app">
{{name}} 
<!-- 文本 或表达式 {{2>1 ? "2>1 为真":"2>1 为假"}} -->
 <div v-html="myhtml"></div>
 <!-- 纯HTML
 防止XSS,csrf（
(1) 前端过滤
(2) 后台转义(< > &lt; &gt;)
(3) 给cookie 加上属性 http）  -->
</div>
<script>
var vm = new Vue({
           el:"#app", // vue 渲染开始的地方 用来指定Vue实例托管范围
           data:{ // Vue实例中可以调用的变量
            name:"vue",
            myhtml:'<div v-html="myhtml"></div>'
           }
        })
</script>
```
#### 指令
是带有 v- 前缀的特殊属性
v-bind
v-if v-show
v-on:click
v-for
缩写:
v-bind:src => :src
v-on:click => @click
##### class与style
```html
 <div id="app">
        <!-- (1)绑定HTML Class -->
        <!-- -对象语法  -->
        <div :class="classobj">我是动态绑定class-对象写法</div>
        <!-- -数组语法-->
        <div :class="classarr">我是动态绑定class-数组写法</div>
        <!-- (2)绑定内联样式 -->
        <!-- -对象语法  -->
        <div :style="styleobj">我是动态绑定style-对象写法</div>
        <!-- -数组语法   -->
        <div :style="stylearr">我是动态绑定style-数组写法</div>
        <!-- 需要将 font-size =>fontSize -->

    </div>
<script>
    new Vue({
        el: "#app",
        data: {
            classobj: {
                a: true,
                b: true
                // a b, class名字
            },
            classarr: ["a", "b"],
            styleobj: {
                backgroundColor: "red"
            },
            stylearr: [{
                backgroundColor: "red"
            }, {
                color: 'blue'
            }]
        }
    })
</script>
```
##### 条件渲染
```html
<div v-if="1===1">动态创建和删除--111111111111</div>
<div v-else>动态创建和删除--2222222222</div>
<div v-show="true">v-show</div>
```
##### 列表渲染(https://codepen.io/zeng-qh/pen/VwvxMbo)
