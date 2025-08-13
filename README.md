大佬你好！！麻烦你看看这个问题出在哪，谢谢。

## 我的操作流程

1. 测试原版md渲染器，Latex渲染正常
我创建了一篇文章，使用默认MD渲染器进行渲染，一切正常

2. 移除原版渲染器，安装新渲染器

```shell
npm un hexo-renderer-marked --save && npm i hexo-renderer-markdown-it-plus --save
```

3. 在`_config.yml`中添加配置

```yml
markdown_it_plus:
  highlight: true
  html: true
  xhtmlOut: true
  breaks: true
  langPrefix:
  linkify: true
  typographer:
  quotes: “”‘’
  pre_class: highlight
```

4. 在`_config.stellar.yml`中修改配置如下

```yml
plugins:
  - katex:
      enable: true # hexo-renderer-markdown-it-plus 默认开启 katex，此选项仅用于引入样式
      inject: |
        <link rel="stylesheet" href="https://gcore.jsdelivr.net/npm/katex@0.16/dist/katex.min.css" integrity="sha384-vKruj+a13U8yHIkAyGgK1J3ArTLzrFGBbBc0tDp4ad/EyewESeXE/Iv67Aj8gKZ0" crossorigin="anonymous">
  - mathjax:
      v3: false # 若使用 v3，需將 js 設置為 https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-mml-chtml.min.js
      enable: false # 可以在特定文章的 front-matter 中设置 mathjax: true 来开启，也可以在这里设置全局开启
      js: https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.6/MathJax.js?config=TeX-AMS-MML_HTMLorMML

```

除此之外我什么也没做了，再次清理、编译、运行，就出现了如下问题：
大佬你好，这是我复现出来的bug截图如下：
![x](https://s2.loli.net/2025/08/13/OWxDNR8megy5Fq4.png)
