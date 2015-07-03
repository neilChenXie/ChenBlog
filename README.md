#Chen blog

##Prepare

###Node.js

> solve `npm` permission problem.<br>
> [Detail](https://docs.npmjs.com/getting-started/fixing-npm-permissions)

##Install

```bash
git clone https://github.com/neilChenXie/ChenBlog.git Blog
npm install
hexo clean
hexo generate
```
##Server

> There are two choices.<br> The 1st choice is mainly used to check proper working.<br> The 2nd is used to integrate the **ChenBlog** with **ChenNode**

###I. Hexo server

```bash
#run under Blog directory
hexo server
```

>In browser enter `localhost:4000/profile/`.

###II. Chen-Node

```bash
#under public folder of ChneNode
ln -s [relative path to Blog/public] profile
```

>check the **symbol link** under **public folder** of ChenNode project, then start ChenNode server.

##Blog Information

###Main
>[hexo](https://github.com/hexojs/hexo/)

###Themes
>[next](https://github.com/iissnan/hexo-theme-next)

##Debug log

* 7/3/2015
    * configure themes/next/_config.md

    > change `/tags` to `tags`, same with `category`,`about`...<br>
    > otherwise, they won't change based on blog **root** config
