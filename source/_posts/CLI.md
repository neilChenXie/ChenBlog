title: CLI
date: 2015-08-19 08:32:42
tags: [Geek, Environment]
categories: [Environment]
---

## Linux

<a name="Linux"></a>

### Command

#### scp

```bash
#upload
scp /path/to/local/file username@hostname:/path/to/remote/file
#transfer
scp username1@hostname1:/path/to/file username2@hostname2:/path/to/other/file
#download
scp username@hostname:/path/to/remote/file /path/to/local/file
```

#### tar & zip/unzip

```bash
#uncompress
tar xvjf <file.tar.gz2>
tar xvzf <file.tar.gz>
#compress
tar cvjf <file.tar.gz2>
tar cvzf <file.tar.gz>
```

```bash
#zip options archive inpath inpath ...
zip -r cac.zip cac
#unzip [-x xfile(s) ...] [-d exdir]
unzip cac.zip -d cac/
```

#### chmod

```
r:4 w:2 x:1<br>u/g/a + r/w/x
```

#### tail

```bash
#check log file
#periodically
tail -f $logfile
```

#### xargs

```
TBA
```

#### find

```bash
#Recursive delete work with rm & xargs
find /home/raven -name abc.txt | xargs rm -rf

#rm .DS_Store recursively
find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
```

#### awk

```
TBA
```

### Conclusion

#### configuration

```bash
#normally under `/etc/`, mostly set environment var and run applications

#bash configuration
##for every booting
/etc/rc.local
##for all users
/etc/profile
##for login users
~/.bash_profile

#set environment var
##ubuntu/mac
export PATH
##unix
setenv PATH
```

#### BeagleBone related

```bash
# run application without graphic interface, in the background when bootup

## Run in the background with CLI
nohup node index.js &

## Run when bootup

#make executable
chmod +x $filename
#create
update-rc.d $filename defaults
#delete
update-rc.d -f $filename remove
```

_notice:_

[1] don't write **boot-blocking** script

_reference:_

[1] [init-script-template](https://github.com/fhd/init-script-template)

[2] `linux_config/chennode.sh` should be put under `/etc/init.d/`

### Tricks

#### change wireless card tx power

[reference](http://www.hacking-tutorial.com/hacking-knowledge/increase-wifi-signal-strength-tx-power-on-kali-linux/#sthash.OQF8aaei.dpbs)


#### Port transfer

```bash
#based on `iptable` in `/etc/rc.local` which runs at the **end** of booting.
iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8000
```


#### Add user & change password

```bash
adduser
passwd
 ```

## OSX
<a name="OSX"></a>

### Tools

#### homebrew

```bash
#it manage all `/usr/local/` packages*
#install package path: `/usr/local/Cellar/`
brew doctor #at the beginning
brew update #update homebrew itself
brew upgrade #update installed package
```

### Setting

#### auto-completion

```bash
#bash
brew install bash-completion
#add to .bash_profile
if [ -f $(brew --prefix)/etc/bash_completion ]; then
    . $(brew --prefix)/etc/bash_completion
fi

#Git
cp ~/CLI/Template/BASH/git-completion.bash ~/.git-completion.bash
echo 'source ~/.git-completion.bash' >> ~/.bash_profile
```

###Web development tool install

[reference](http://coolestguidesontheplanet.com/get-apache-mysql-php-phpmyadmin-working-osx-10-10-yosemite/)

## Tools

### Screen

#### vertical split

```bash
#need patch
cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/sources/screen co screen
curl http://old.evanmeagher.net/files/gnu-screen-vertsplit.patch > gnu-screen-vertsplit.patch
cd screen/src
patch < ../../gnu-screen-vertsplit.patch
./configure –enable-locale –enable-telnet –enable-colors256 –enable-rxct_osc
make
sudo make install
```

#### basic operation

```bash
# create
screen -S foo
# change name in session
C-a A foo

# split
C-a S

#vertical split
C-a |

#create
C-a c

#resize
C-a :resize 10

#close split
C-a X

#detach
C-a d

#recover
screen -ls #check exist socket
screen -r $name #reattach
```

[reference](http://aperiodic.net/screen/quick_reference)

### GDB

### Git

#### Download & Update

```bash
git clone $URL
git remote add $newName $URL
git fetch $newname #(origin)
git merge $newname #(origin)/master
```

#### Conflict

```bash
#get more information
git config --global alias.conflicts "diff --name-only --diff-filter=U"

#merge tool
git mergetool origin master
```

#### Delete

```bash
#Delete cache and disk
git rm
#Delete cache only
git rm --cache
```

#### Add & Commit

```bash
#.gitignore #file to specify which file or folder is not included
#-u is used to adopt all changes to repo
git add -u .
git commit -m #as usual
```

#### recover

```bash
git log #list all commit log to check
git checkout 0d1d7fc32 #go back to where you want
```

#### Branch

```bash
git checkout -b $newName #create new Branch
git checkout master #back to maste
git merge $newName #merge to master
git branch -d #delete after merge, `-D` forced
git branch -v #last modification time
```

#### Add RSA SSH key

[reference](https://help.github.com/articles/generating-ssh-keys/)

## Editor
<a name="editor"></a>

### Vim

[Github](https://github.com/neilChenXie/.vim_v2)

### Atom

<a name="atom"></a>

#### Plugin List:

* vim-mode, vim-mode-visual-block

* term2, script

* project-manager

* git-plus
    >need set RSA SSH key to make git push work without entering username and password.

#### tricks:

* hotkeys

    >`crtl + shift + m` markdown file preview
