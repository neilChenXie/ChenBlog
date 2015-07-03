title: CV
date: 2015-07-03 15:38:08
tags: [CV, Geek, Overview]
---
#CV

##TimeLine

|Time|Project|
| --- | --- |
|**Doing**| |
|2014.12-now|**Chen-Node**|
|  **Finished**|  |
|2015.2-2015.5|**Bike Safety System**|
|2014.10-2014.12|**mini TOR**|
|2014.7-2014.11|**Chen Account Service**|
|2014.2-2014.5|**Weenix**|
|2013.11-2013.12|**Health Center System**|
|2012.10-2012.12|**Wireless Voice Communication**|
|2011.7-2011.9|**Auto-Track Car**|

##Language

- [x] Node.js
- [x] Python
- [x] Java
- [x] C++
- [x] C

##Environment

| Name | Distribution | Detail |
| --- | --- |
| Linux | Ubuntu, Debian, Angstrom, Fedora, Mint | [Detail](#Linux) |
| Max | OSX | [Detail](#OSX) |
| Windows | win7 | [Detail](#Windows) |

##Project

| Category | Name | Key words| Links |
| --- | --- | --- | --- |
| **System** ||||
||**Bike Safety System**|Node.js, HTTP, BeagleBone, Java, Localization, Serial Communication,SkyTmote, ContikiOS,  Wireless|[Detail](#BSS)|
| **Website** ||||
||**Chen-Node**|Node.js, Express, BeagleBone|[Website](http://www.chen-node.com) [Github](https://github.com/neilChenXie/ChenNode)|
||**Chen Account Service**|JQueryMobile, HTML, PHP, MySQL|[Website](http://www.chenaccount.com) [Github](https://github.com/neilChenXie/CAC-account-service)|
|**Network**||||
||**mini TOR**|C, Socket, Virtual Circuit, UDP, IP, AES|[Github](http://www.github.com/neilChenXie/TOR.git)|
|**OS kernel**||||
||**Weenix**||[Detail](#Weenix)|
|Data Science||||
||MapReduce based Pearson similarity calculation||[Detail]()|

#*More*



___
###*Environment Detail*
___

<a name="Linux"></a>
##Linux (CLI)
####keyworlds:[experience](#Linux_exp), [command](#Linux_com), [tools](#Linux_tool)

   <a name="Linux_exp"></a>

###Experience & Tricks

* *configuration is normally under `/etc/`*

    * bash configuration
        >`/etc/rc.local` for every booting<br>
        >`/etc/profile` for all users<br>`~/.bash_profile` for login users
        >>* `export PATH` ubuntu/mac
        >>* `setenv PATH` for unix

* Port transfer
>  based on `iptable` in `/etc/rc.local` which runs at the **end** of booting.
>  `iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8000`
* Run in the background with CLI
> `nohup` command `&`

   <a name="Linux_com"></a>

###Command

* scp
    >`scp /path/to/local/file username@hostname:/path/to/remote/file`<br>
      `scp username1@hostname1:/path/to/file username2@hostname2:/path/to/other/file`<br>
      `scp username@hostname:/path/to/remote/file /path/to/local/file`
* tar
>uncompress:<br> `tar xvjf <file.tar.gz2>`<br>`tar xvzf <file.tar.gz>`<br>
compress:<br>`tar cvjf <file.tar.gz2>`<br>`tar cvzf <file.tar.gz>`

* chmod
>r:4 w:2 x:1<br>u/g/a + r/w/x
* tail
>`-f` to periodically read file
* xargs
* find
>* work with `rm` & `xargs`:
```
find /home/raven -name abc.txt | xargs rm -rf
```
* awk

   <a name="Linux_tool"></a>

###Tools

 * VIM
     * Settings
 >* `/etc/vim/vimrc`
 >* `~/.vim/vimrc`
     * Plugin
 >* `solarized` colorscheme
 >* `syntastic` syntax check
 >* `YouCompleteMe` autocomplete
 >* `Taglist/Ctags/Cscope` tags
     * Command:
 >* search and replace:
         * Find each occurrence of 'foo' (in all lines), and replace it with 'bar'.<br>
         `:%s/foo/bar/g`
         * Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'.<br>
         `:s/foo/bar/g`
          * Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation.<br>
          `:%s/foo/bar/gci`

 * GDB
 * Git
     * Download & Update
        > `git clone` URL<br>
        > `git remote add` newName URL<br>
        > `git fetch` newname(origin)
        > `git merge` newname(origin)/master
     * Conflict
        > Get more information `git config --global alias.conflicts "diff --name-only --diff-filter=U"`
     * Delete
        >* `git rm` Delete cache and disk
        >* `git rm --cache` Delete cache only
     * Add & Commit
        >`.gitignore` file to specify which **file** or  **folder** is not included
        >`git add . / git commit -m ` as usual
     * recover
        >`git log` list all commit log to check<br>
        >`git checkout 0d1d7fc32` go back to where you want
     * Branch
        > git checkout -b newName #create new Branch
        > git checkout master #back to master
        > git merge newName #merge to master
        > git branch -d #delete after merge, -D forced
        > git branch -v #last modification time

<a name="OSX"></a>

## OSX

###Tools

* homebrew

    *it manage all `/usr/local/` packages*
> * install package path: `/usr/local/Cellar/`
> * `brew update` update homebrew itself
> * `brew upgrade` update installed package

###Setting
* auto-completion
>* BASH:
    1. `brew install bash-completion`
    2. add to .bash_profile
```bash
            if [ -f $(brew --prefix)/etc/bash_completion ]; then
                . $(brew --prefix)/etc/bash_completion
            fi
```
> * git:
```bash
           cp ~/CLI/Template/BASH/git-completion.bash ~/.git-completion.bash
           echo 'source ~/.git-completion.bash' >> ~/.bash_profile
```

* atom
  * tricks
  >* `crtl + shift + m` markdown file preview
<a name="Windows"></a>

## Windows



___
###*Project Detail*
___

<a name="BSS"></a>
## Bike Safety System

<a name="Weenix"></a>
## Weenix