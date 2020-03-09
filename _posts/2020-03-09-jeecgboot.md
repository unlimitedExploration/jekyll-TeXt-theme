---
layout: article
title: jeecgboot 入门
#mathjax: true
show_subscribe: false
license: false
footer: false
---

## [官方文档](http://doc.jeecg.com/1273752)

## 配置文件
1. 前台全局配置文件，文件位置：public/index.html  
```javascript
<!-- 全局配置 -->
  <script>
    window._CONFIG = {};
    //后台服务域名
    window._CONFIG['domianURL'] = 'http://127.0.0.1:8080/jeecg-boot';
    //CAS服务器地址
    window._CONFIG['casPrefixUrl'] = 'http://cas.example.org:8443/cas';
    //图片服务器域名
    window._CONFIG['imgDomainURL'] = window._CONFIG['domianURL'] + '/sys/common/view';
    window._CONFIG['downloadUrl'] = window._CONFIG['domianURL'] + '/sys/common/download';
    //pdf文件预览地址
    window._CONFIG['pdfDomainURL'] =  window._CONFIG['domianURL'] + '/sys/common/pdf/pdfPreviewIframe';
  </script>
```  
2. 我目前用到的配置  
- 登录页面代码的位置
```
src/components/layouts/UserLayout.vue
src/views/user/Login.vue
```
- 修改首页 logo  
```
src/components/tools/Logo.vue
```
- 修改首页的顶部显示
```
src\components\page\GlobalHeader.vue
```

## online 表单开发
1. 下拉列表可以使用数据字典填充数据
2. 表单字段校验：可以使用自定义的正则表达式

## 后台开发
1. 数据库持久层使用了 [MyBatis-Plus](https://mp.baomidou.com/ "MyBatis-Plus")
```java
//QueryWrapper用于生成sql的where条件
QueryWrapper<ApiConfig> apiConfigWrapper = new QueryWrapper<>();
apiConfigWrapper.eq("merchant_id", merchantId);
ApiConfig apiConfig = apiConfigService.getOne(apiConfigWrapper);
```