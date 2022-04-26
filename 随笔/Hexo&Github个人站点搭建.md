---
title: Hexo&Github个人站点搭建  

tags: [hexo,js,git]

---

通过Hexo与Github搭建静态个人站点，需要安装node.js与Git  
个人站点：https://orzyang.github.io/  

<!--more-->
### node.js安装
在cmd中输入“node -v”可以显示出版本号  

在cmd输入以下命令  
>npm config set perfix "D:\application\nodejs\node_global"  

配置node全局模块  

>npm config set cache "D:\application\nodejs\node_cache"  

配置node缓存模块  

配置环境变量  
>系统变量新建NODE_PATH  
>D:\application\nodejs\node_modules  

>将用户变量PATH中npm路径修改为  
>D:\application\nodejs\node_global  


安装一个express模块试试，会安装到node_global文件夹下
>npm install express -g  

### Hexo下载同理  
>npm install hexo -g --no-optional

安装完后留意一下环境变量  
>hexo -v

在hexo目录下运行git bash   
>hexo init blog 

在生成的blog目录下运行git bash  
>hexo g(hexo generate生成文件)  

>hexo s(hexo server部署服务)

在blog目录下运行git bash  
>npm install hexo-deployer-git --save

在根目录下的_config.yml配置  


```
deploy:  
  type: git  
  repo: https://github.com/orzyang/orzyang.github.io.git  
  branch: master
```

在blog目录下运行git bash,成功部署到github  
>hexo d  
>备注：本地预览和github不一致，试试先clean一下hexo在部署