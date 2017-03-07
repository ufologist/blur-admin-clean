# [BlurAdmin Clean Version](https://ufologist.github.io/blur-admin-clean/)

[BlurAdmin](https://github.com/akveo/blur-admin "Angular Bootstrap Admin Panel Framework") 是一个非常好用的后台管理页面的框架, 但实际使用过程中发现有一些不太方便的地方:

* BlurAdmin 项目模版中添加了太多的第三方库依赖, 特别是第三方的 chart 库, 很多都是不会实际使用的, 这样就会造成最终打包时合并了很多没用到的第三方库, JS/CSS 文件偏大.
* BlurAdmin 项目模版中添加了太多的示例(pages 模块), 实际使用时都需要去掉, 来作为一个干净的项目模版

因此我基于 `blur-admin@1.3.1` 版本就开始删删删, BlurAdmin `干净整洁版` 就出炉了.

* 清理不太常用的依赖(bower.json)
* 去除了大多数 chart 库
* 去除了大多数 pages 模块

## 干净整洁版与原始版的对比

![blur-admin-clean](http://storage1.imgchr.com/9lUG6.png)

### 文件大小对比

| 文件(合并后)   | 干净整洁版  | 原始版     |
|-----------|--------|---------|
| vendor.js | **995 KB** | 2445 KB |
| app.js    | **78 KB**  | 291 KB  |

## 使用方法

参考 [Installation Guidelines](http://akveo.github.io/blur-admin/articles/002-installation-guidelines/)

* development mode

  `gulp serve`

* production mode

  `gulp serve:dist`

## 源码解读

```
src/                              -- [项目结构](http://akveo.github.io/blur-admin/articles/012-project-structure/)
└── app/
    └── theme/
        |── theme.run.js          -- 去掉 loadAmCharts 和延时
        └── components/
            |── baSidebar/        -- [导航菜单](http://akveo.github.io/blur-admin/articles/051-sidebar/)
            |── pageTop/          -- 顶部区域
            |── msgCenter/        -- 顶部的通知中心
            |── contentTop/       -- 内容区域的面包屑导航
            |── backTop/          -- 返回顶部
            |── baPanel/          -- 通用面板
            |── baWizard/         -- 向导
            └── progressBarRound/ -- 圆形进度条
```

## TODO

* 添加 [ocLazyLoad](https://github.com/ocombe/ocLazyLoad "Lazy load modules & components in AngularJS") 支持