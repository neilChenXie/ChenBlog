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

    >file:<br>
    ```bash
    #for every booting
    /etc/rc.local
    #for all users
    /etc/profile
    #for login users
    ~/.bash_profile
    ```
    use:
    ```bash
    #ubuntu/mac
    export PATH
    #unix
    setenv PATH
    ```
* Port transfer

  * based on `iptable` in `/etc/rc.local` which runs at the **end** of booting.

    >code:
    ```bash
    iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8000
    ```

* Run in the background with CLI

  * `nohup` command `&`

* start when bootup BeagleBone

  * `linux_config/chennode.sh` which should be put under `/etc/init.d/`

  * [init-script-template](https://github.com/fhd/init-script-template)

  * in case of **boot-block script**

    >code:
    ```bash
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

    >code:
    ```bash
    #upload
    scp /path/to/local/file username@hostname:/path/to/remote/file
    #transfer
    scp username1@hostname1:/path/to/file username2@hostname2:/path/to/other/file
    #download
    scp username@hostname:/path/to/remote/file /path/to/local/file
    ```

* tar

  * uncompress:

    >code:
    ```bash
    tar xvjf <file.tar.gz2>
    tar xvzf <file.tar.gz>
    ```

  * compress:

    >code:
    ```bash
    tar cvjf <file.tar.gz2>
    tar cvzf <file.tar.gz>
    ```

* chmod

  * change access

    >detail:
    r:4 w:2 x:1<br>u/g/a + r/w/x

* tail

  * check log file

    >code:
    ```bash
    #periodically
    tail -f $logfile
    ```

* xargs

  * TBA

* find

  * work with `rm` & `xargs`:

    >code:<br>
    ```bash
    find /home/raven -name abc.txt | xargs rm -rf
    ```

* awk

  * TBA

#####Tools

* Screen

  * split terminal into multi windows

    >[reference](http://aperiodic.net/screen/quick_reference)

  * Tricks:

    >shortcut:
    `C-a S` split
    `C-a c` create
    `C-a :resize 10` resize

* Vim
  * Settings
    >file:<br>
    ```bash
    vim /etc/vim/vimrc
    vim ~/.vim/vimrc
    ```

  * Plugin
    > name:
    **solarized** colorscheme
    **syntastic** syntax check
    **YouCompleteMe** autocomplete
    **Taglist/Ctags/Cscope** tags

  * Command:

    >search and replace:
    Find each occurrence of 'foo' (in all lines), and replace it with 'bar'.
    `:%s/foo/bar/g`
    Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'.
    `:s/foo/bar/g`
    Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation.
    `:%s/foo/bar/gci`

* GDB
* Git

  * Download & Update

    >code:<br>
    ```bash
    git clone $URL
    git remote add $newName $URL
    git fetch $newname #(origin)
    git merge $newname #(origin)/master
    ```

  * Conflict

    > Get more information:<br>
    ```bash
    git config --global alias.conflicts "diff --name-only --diff-filter=U"
    ```

  * Delete

    >code:<br>
    ```bash
    #Delete cache and disk
    git rm
    #Delete cache only
    git rm --cache
    ```

  * Add & Commit

    >code:<br>
    ```bash
    vim .gitignore #file to specify which file or folder is not included
    git add . / git commit -m #as usual
    ```

  * recover

    >code:<br>
    ```bash
    git log #list all commit log to check<br>
    git checkout 0d1d7fc32 #go back to where you want
    ```

  * Branch

    >code:<br>
    ```bash
    git checkout -b $newName #create new Branch
    git checkout master #back to maste
    git merge $newName #merge to master
    git branch -d #delete after merge, `-D` forced
    git branch -v #last modification time
    ```

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
