title: CLI
date: 2015-07-12 08:32:42
tags: [Geek, Environment]
categories: [Environment]
---

##Linux
<a name="Linux"></a>

###Experience & Tricks

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
    >use:
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

###Command

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

  * **Recursive delete** work with `rm` & `xargs`:

    >code:
    ```bash
    find /home/raven -name abc.txt | xargs rm -rf
    ```

* awk

  * TBA

###Tools

* Screen

  * split terminal into multi windows

    >[reference](http://aperiodic.net/screen/quick_reference)

  * Tricks:

    >shortcut:
    `C-a S` split
    `C-a c` create
    `C-a :resize 10` resize



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

    >code:
    ```bash
    #Delete cache and disk
    git rm
    #Delete cache only
    git rm --cache
    ```

  * Add & Commit

    >code:
    **.gitignore** #file to specify which file or folder is not included
    ```bash
    git add . / git commit -m #as usual
    ```

  * recover

    >code:
    ```bash
    git log #list all commit log to check
    git checkout 0d1d7fc32 #go back to where you want
    ```

  * Branch

    >code:
    ```bash
    git checkout -b $newName #create new Branch
    git checkout master #back to maste
    git merge $newName #merge to master
    git branch -d #delete after merge, `-D` forced
    git branch -v #last modification time
    ```



##OSX
<a name="OSX"></a>

###Tools

* homebrew

  * it manage all `/usr/local/` packages*

    >install package path: `/usr/local/Cellar/`
    ```bash
    brew doctor #at the beginning
    brew update #update homebrew itself
    brew upgrade #update installed package
    ```

###Setting

* auto-completion

  * BASH:

    >auto-completion:
    ```bash
    brew install bash-completion
    #add to .bash_profile
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

##Editor
<a name="editor"></a>

###Vim

* [Github](https://github.com/neilChenXie/.vim_v2)

###Atom
<a name="atom"></a>
  * tricks:

    > `crtl + shift + m` markdown file preview
