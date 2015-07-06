#Chen blog

##Prepare

###I. Node.js

> solve `npm` permission problem.<br>
> [Detail](https://docs.npmjs.com/getting-started/fixing-npm-permissions)

##Install

```bash
#install hexo
npm install hexo -g
npm install hexo-cli -g
#get main
git clone https://github.com/neilChenXie/ChenBlog.git Blog
npm install
#get next
git clone https://github.com/iissnan/hexo-theme-next themes/next
cp themes/config_backup/next_config.txt themes/next/_config.yml
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

###I. Main
>[hexo](https://github.com/hexojs/hexo/)

###II. Themes
>[next](https://github.com/iissnan/hexo-theme-next)

##Debug log
* 7/6/2015
    * add photo

    > put `photo` folder under `source` folder (it will be copied to public)<br>
    link: `/profile/photo/photoName.jpg`

* 7/3/2015
    * configure `themes/next/_config.md`

    > change `/tags` to `tags`, same with `category`,`about`...<br>
    > otherwise, they won't change based on blog **root** config
