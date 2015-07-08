title: CV
date: 2015-07-03 15:38:08
tags: [CV, Geek, Overview]
categories: [CV]
---

##TimeLine

| Time | Project | Web | Detail |
| ---- | ------- | --- | ------ |
| **Working** | | | |
|2014.12-now|**Chen-Node**| [Website](http://www.chen-node.com) | [Github](https://github.com/neilChenXie/ChenNode) |
|  **Finished** | | | |
|2015.2-2015.5|**Bike Safety System**| |[Detail](#BSS)|
|2014.10-2014.12|**mini TOR**| |[Github](http://www.github.com/neilChenXie/TOR.git) |
|2014.7-2014.11|**Chen Account Service**| [Website](http://www.chenaccount.com) |[Github](https://github.com/neilChenXie/CAC-account-service) |
|2014.2-2014.5|**Weenix**| | [Detail](#Weenix) |
|2013.11-2013.12|**Health Center System**| | |
|2012.10-2012.12|**Wireless Voice Communication**| | |
|2011.7-2011.9|**Auto-Track Car**| | | |

##Language

- [x] Node.js
- [x] Python
- [x] Java
- [x] C++
- [x] C

##Environment

| Name | Distribution | Detail |
| ---- | ------------ | ------ |
| Linux | Ubuntu, Debian, Angstrom, Fedora, Mint | [Detail](#Linux) |
| Max | OSX | [Detail](#OSX) |
| Windows | win7 | [Detail](#Windows) |

##Project

| Category | Name | Key words| Links |
| --- | --- | --- | --- |
||**Chen Account Service**|JQueryMobile, HTML, PHP, MySQL|[Website](http://www.chenaccount.com) [Github](https://github.com/neilChenXie/CAC-account-service)|
|**Network**||||
||**mini TOR**|C, Socket, Virtual Circuit, UDP, IP, AES|[Github](http://www.github.com/neilChenXie/TOR.git)|
|Data Science||||
||MapReduce based Pearson similarity calculation||[Detail]()|

##*Details*

___

###*Environment Detail*
___

<a name="Linux"></a>

####Linux (CLI)

#####Experience & Tricks

* *configuration is normally under `/etc/`*
  * bash configuration

    >`/etc/rc.local` for every booting<br>
    `/etc/profile` for all users<br>`~/.bash_profile` for login users<br>
    `export PATH` ubuntu/mac<br>
    `setenv PATH` for unix

* Port transfer
  * based on `iptable` in `/etc/rc.local` which runs at the **end** of booting.

    > `iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8000`

* Run in the background with CLI
  * `nohup` command `&`

* start when bootup BeagleBone
  * `linux_config/chennode.sh` which should be put under `/etc/init.d/`
  * [init-script-template](https://github.com/fhd/init-script-template)
  * in case of **boot-block script**

    >```bash
    #make executable
    chmod +x $filename
    #create
    update-rc.d $filename defaults
    #delete
    update-rc.d -f $filename remove
    ```

#####Command

* scp

  * auto-recognization

    >```bash
    #upload
    scp /path/to/local/file username@hostname:/path/to/remote/file
    #transfer
    scp username1@hostname1:/path/to/file username2@hostname2:/path/to/other/file
    #download
    scp username@hostname:/path/to/remote/file /path/to/local/file
    ```

* tar

  * uncompress:

    >```bash
    tar xvjf <file.tar.gz2>
    tar xvzf <file.tar.gz>
    ```

  * compress:

    >```bash
    tar cvjf <file.tar.gz2>
    tar cvzf <file.tar.gz>
    ```

* chmod

  * change access

    >r:4 w:2 x:1<br>u/g/a + r/w/x

* tail
  * check log file

    >```bash
    #periodically
    tail -f $logfile
    ```

* xargs

* find
  * work with `rm` & `xargs`:

    >```bash
    find /home/raven -name abc.txt | xargs rm -rf
    ```

* awk

#####Tools

* Screen
    * split terminal into multi windows
        >[reference](http://aperiodic.net/screen/quick_reference)

    * Tricks:
        >`C-a S` split<br>
        `C-a c` create<br>
        `C-a :resize 10` resize

* Vim
     * Settings
 > `/etc/vim/vimrc`<br>
  `~/.vim/vimrc`

     * Plugin
 > `solarized` colorscheme<br>
  `syntastic` syntax check<br>
  `YouCompleteMe` autocomplete<br>
  `Taglist/Ctags/Cscope` tags

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

        >`git clone` URL<br>
        `git remote add` newName URL<br>
        `git fetch` newname(origin)
        `git merge` newname(origin)/master

     * Conflict

        > Get more information `git config --global alias.conflicts "diff --name-only --diff-filter=U"`

     * Delete

        > `git rm` Delete cache and disk<br> `git rm --cache` Delete cache only

     * Add & Commit

        >`.gitignore` file to specify which **file** or  **folder** is not included
        `git add . / git commit -m ` as usual

     * recover

        >`git log` list all commit log to check<br>
        `git checkout 0d1d7fc32` go back to where you want

     * Branch

        >`git checkout -b` newName #create new Branch<br>
         `git checkout master` #back to master<br>
         `git merge` newName #merge to master<br>
         `git branch -d` #delete after merge, `-D` forced<br>
         `git branch -v` #last modification time

<a name="OSX"></a>

#### OSX

#####Tools

* homebrew

    * it manage all `/usr/local/` packages*
    >install package path: `/usr/local/Cellar/`<br>
    `brew doctor` at the beginning<br>
    `brew update` update homebrew itself<br>
    `brew upgrade` update installed package

#####Setting

* auto-completion
  * BASH:
    >`brew install bash-completion`<br>
    add to .bash_profile
    ```bash
    if [ -f $(brew --prefix)/etc/bash_completion ]; then
        . $(brew --prefix)/etc/bash_completion
    fi
    ```
 * Git:
    >enter the command blow:
    ```bash
    cp ~/CLI/Template/BASH/git-completion.bash ~/.git-completion.bash
    echo 'source ~/.git-completion.bash' >> ~/.bash_profile
    ```

* atom
  * tricks:<br>
    > `crtl + shift + m` markdown file preview

<a name="Windows"></a>

#### Windows

___

###*Project Detail*
___

<a name="BSS"></a>
#### Bike Safety System

* *Key words:* **Node.js, HTTP, BeagleBone, Java, Localization, Serial Communication,SkyTmote, ContikiOS,  Wireless**



<a name="Weenix"></a>
#### Weenix

* *Key words:* **TDA**
