# 2015-12-17 AngularJS 公开课

## 知识储备

- 在开始学习 AngularJS 之前，只需要需要具备以下基础知识：
  + HTML
  + CSS
  + JavaScript

## AngularJS 简介

### 什么是 AngularJS

- 一款非常优秀的前端高级JS框架
  + jQuery是一个框架？
  + 我个人认为jQuery是一种工具库
  + AngularJS包含我们构建Web应用程序所需要包含各种解决方案，模版，路由。。。MVC
- 由Misko Hevery 等人创建
- 2009年被Google公式收购，用于其多款产品
- 有一个全职的开发团队继续开发和维护这个库
- 有了这一类框架就可以轻松构建SPA应用程序
- 通过指令扩展了 HTML，通过表达式绑定数据到 HTML。

### 为什么使用 AngularJS

- 以前我们是这样开发应用的：

```html
<input type="text" id="value">
<input type="button" value="*2" id="btn">
<script>
  (function(window) {
    window.document.querySelector('#btn')
    .addEventListener('click',function  () {
      // 获取DOM元素
      var input = window.document.querySelector('#value');
      var value = input.value; // 取数值
      value = value - 0; // 改变类型
      value = value * 2; // 改变数值
      input.value = value; // 设置回去
    });
  })(window);
</script>
```

- 使用 AngularJS 过后则是这样的：

```html
<body ng-app ng-controller="DemoController">
  <input type="text" ng-model="value">
  <input type="button" value="*2" ng-click="do()">
  <script src="../lib/angular.min.js"></script>
  <script>
    // ng1.3.0过后不能使用这种方式实现，必须通过模块注册控制器
    function DemoController($scope) {
      $scope.value = 0;
      $scope.do = function() {
        $scope.value = $scope.value * 2;
      }
    }
  </script>
</body>
```

- 当然不仅仅是这些
- 这些只是皮毛
- 背后带来的价值才是大大地
- 带领前端进入 M V X 时代

## AngularJS 起步

### 准备

> AngularJS 是一个 JavaScript 框架，所以你可以通过以下两种方式载入到页面中：

- NPM（Node Package Manager）node 包管理工具
  + 如果需要使用NPM的方式，必须先安装Node.js
  + npm install angular
- Bower
  + bower install angular#1.4.8
- 下载 Angular.js 的包
  + https://github.com/angular/angular.js/releases
- 使用CDN上的angular.js
  + http://apps.bdimg.com/libs/angular.js/1.4.6/angular.min.js

### Hello world

- 创建一个新的HTML文件，贴入以下代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>TODOMVC - AngularJS</title>
</head>
<body>
  <div ng-app ng-init="name='zhangsan'">
    <p>在输入框中尝试输入：</p>
    <p>姓名：<input type="text" ng-model="name"></p>
    <p>{{name}}</p>
  </div>
  <script src="angular.min.js"></script>
</body>
</html>
```

- 直接启动在浏览器中查看。
- 体会AngularJS在这个过程中完成那些事情。

### 案例解析

- 当网页加载完毕，AngularJS 自动开启。
- ng-app 指令告诉 AngularJS，<div> 元素是 AngularJS 应用程序 的"所有者"。
- ng-model 指令把输入域的值绑定到应用程序变量 name。
- {{ name }}表达式把应用程序变量 name 绑定到某个段落的 innerHTML。

## TODOMVC 案例

1. 从GitHub上clone TODO 项目模板
  - git clone https://github.com/micua/todo-template.git
2. 通过NPM安装相应依赖
3. 项目模板解析
4. 创建TodoApp模块
5. 创建Main控制器
6. 创建Main存储服务
7. 完成服务方法的增删改查
8. 完成控制器逻辑 