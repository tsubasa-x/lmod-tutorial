# LMOD Installation tutorial
## Install Lua
```bash
wget https://sourceforge.net/projects/lmod/files/lua-5.1.4.9.tar.bz2
tar xf lua-5.1.4.9.tar.bz2
cd lua-5.1.4.9
./configure --prefix=/opt/apps/lua/X.Y.Z
sudo make; sudo make install
cd /opt/apps/lua; ln -s 5.1.4.9 lua
sudo ln -s /opt/apps/lua/lua/bin/lua /usr/local/bin/lua
sudo ln -s /opt/apps/lua/lua/bin/luac /usr/local/bin/luac
```
## Install Lmod
Might need to install `libtcl` with apt first
```bash
wget https://sourceforge.net/projects/lmod/files/Lmod-8.2.tar.bz2
tar xf Lmod-8.2.tar.bz2
cd Lmod-8.2.tar.bz2
./configure --prefix=/opt/apps
sudo make install
```

下面是官網的作法
```bash
sudo ln -s /opt/apps/lmod/lmod/init/profile        /etc/profile.d/z00_lmod.sh
sudo ln -s /opt/apps/lmod/lmod/init/cshrc          /etc/profile.d/z00_lmod.csh
```
然後重登後就裝好了
```bash
$ type module
module ()
{
  eval $($LMOD_CMD bash $*)
}

$ echo $LMOD_CMD
/opt/apps/lmod/lmod/libexec/lmod

$ echo $MODULEPATH
/opt/apps/modulefiles/Linux:/opt/apps/modulefiles/Core
```
但我不知道是不是mint的關係還是怎樣 我重登後打`type module`是出現`module not found` 然後好像也不該用csh..的樣子吧
所以我就直接
```bash
cd /opt/apps/lmod/lmod/init/
source profile
source zsh
```
## Ref
https://lmod.readthedocs.io/en/latest/030_installing.html

https://github.com/easybuilders/easybuild/issues/207
