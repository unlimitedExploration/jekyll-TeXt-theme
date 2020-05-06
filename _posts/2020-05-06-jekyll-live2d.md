---
layout: article
title: jekyll博客添加live2d
show_subscribe: false
license: false
footer: false
---
## 在 jekyll 静态网页上添加 live2d 看板娘
**一个笨办法：借助 Hexo**
*****
### 1. 安装 Hexo,创建项目
[Hexo官网](https://hexo.io/zh-cn/docs/)
``` 
    npm install -g hexo-cli
    hexo init blog
    cd blog
    npm install
    hexo server
```
### 2. 安装和配置 hexo-helper-live2d
[hexo-help-live2d](https://github.com/EYHN/hexo-helper-live2d)  
编辑 hexo 项目的配置文件 _config.xml :
```
# live2d
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: remu
  display:
    position: right
    width: 230
    height: 275
  mobile:
    show: true
  react:
    opacity: 0.7
```
### 3. 下载和使用 live2d 资源
详见[live2d-widget-models](https://github.com/xiazeyu/live2d-widget-models),也可以搜索下载其他 live2d 模型资源  
使用方法：
1. 在 live2d_models 下创建目录，用 model 的名字命名
2. 将下载的 live2d 模型资源复制到上一步创建的目录中
3. `hexo server` 运行项目可以看到效果

**注意：live2d_models 目录下的文件夹名对应配置文件中的 use**  

### 4. 在 jekyll 项目中使用
1. 运行 `hexo deploy` 然后在 `public/live2dw` 下可以找到编译后的文件，将 live2dw 目录复制到 jekyll 项目的目录下
2. 打开 `index.html` 文件，拉到最底部，找到如下代码并复制到想要的页面
```javascript
<script src="/live2dw/lib/L2Dwidget.min.js?094cbace49a39548bed64abff5988b05"></script><script>L2Dwidget.init({"pluginRootPath":"live2dw/","pluginJsPath":"lib/","pluginModelPath":"assets/","tagMode":false,"debug":false,"model":{"jsonPath":"/live2dw/assets/remu.model.json"},"display":{"position":"right","width":230,"height":275},"mobile":{"show":true},"react":{"opacity":0.7},"log":false});</script>
```
