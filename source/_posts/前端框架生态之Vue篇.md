---
title: 前端框架生态之Vue篇
date: 2020-03-03
tags:
- 前端框架
- Vue
---

***Post by 小打***

## [Vue](https://cn.vuejs.org/)
Vue 的使用方式主要有两种：
a. 在 html 里引入 vue.js，简单直接，适合初学和 Demo，也适合在其它前端框架搭建的项目里局部使用 Vue。
b. 通过 ES6 import 模块化引入，配合 Webpack 打包编译使用。这种方式更加工程化，适合大部分项目。早期的 Vue / React 项目环境配置完全要自己实现，打包工具众多：Webpack / Browserify / Rollup / Parcel。由于相关插件繁多且升级改动频繁，不少前端开发工程师快要被逼成前端配置工程师。

## [Vue CLI](https://cli.vuejs.org/zh/)（适合大部分项目）
Vue 官方指定的 Vue CLI 是一个集成了 Webpack 的基础前端框架（React 有 Create React App），环境配置方面已能满足大部分项目的需要，一定程度上解救了前端配置工程师。Vue CLI 2.x 版本把 Webpack 配置暴露在项目里，而 Vue CLI 3.x 把 Webpack 配置封装在 Vue CLI Service 内部后接受调用。一般来说，我们做技术选型应该用新不用旧，因为新技术因为着优化和维护；但 2.x 版本确实方便了我们根据项目需要对 Webpack 配置进行深度定制。

## [Vue Router](https://router.vuejs.org/zh/) / [VueX](https://vuex.vuejs.org/zh/guide/)
Vue 官方指定的路由及状态管理插件，跟 React 生态动辄好几个类似插件（Flux / Redux / MobX）比起来少了选择和决定的烦恼。需要时在 Vue CLI 生成的项目里直接引入即可使用，无需额外配置，非常方便。

## [Element UI](https://element.eleme.cn/) / [iView](http://iview.talkingdata.com/)
Vue 生态中使用人数最多的开源 UI 组件库，封装了许多常用组件，能满足大部分管理后台的需求（管理后台 UI 界面注重简洁易用）。自己开发 UI 组件库虽然可以更好地支持自定义需求，但会是很大的工作量，保持 bug 修复和文档更新更是一件困难的事。开源 UI 组件库的使用让开发者可以将更多时间花在业务逻辑而不是组件上。如果组件库提供的常用组件无法满足业务需求，则需要对相应组件做二次封装或全新开发。React 也有 Ant Design 等开源组件库。

## [Vue Element Admin](https://panjiachen.github.io/vue-element-admin-site/zh/)（管理后台类型项目推荐使用）
前台网页的界面和交互各式各样，但管理后台的界面和功能往往是类似的。这意味着前台网页开发能提炼的公共代码少，而管理后台开发能提炼的公共代码要多得多，因此管理后台模板是必然且必要的，它能提高管理后台的开发效率并且保证代码逻辑的规范和一致。Vue Admin Template 就是这样一个后台前端解决方案（React 有 React Admin），它内置了 i18n 国际化解决方案、动态路由、权限验证，提炼了典型的业务模型，提供了丰富的功能组件，在管理后台类型的项目开发中能提供有力的帮助。
