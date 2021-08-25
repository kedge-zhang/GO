＃ Golang
## 1.环境调试
### 1.1 git
```bash
#1.解决依赖
yum install asciidoc xmlto curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker  mercurial bazaar -y
#2.获取安装包
wget https://www.kernel.org/pub/software/scm/git/git-2.9.5.tar.gz --no-check-
certificate
#3.解压
tar fvx git-2.9.5.tar.gz && cd git-2.9.5
#4.编译
make configure && ./configure && make all doc && make install install-doc install-html
#5.目录位置
cd .. && mv git-2.9.5 /usr/local 
#6.环境设置
rm -rf  /usr/bin/git /usr/local/bin/git
ln -s /usr/local/git-2.9.5/git  /usr/bin/git
ln -s /usr/local/git-2.9.5/git  /usr/local/bin/git
```
## 2.go环境
```bash
vim /etc/profile
    export GOROOT=/usr/local/go
    export GOPATH=/data/Go
    export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
    export GO111MODULE=on
    export GOPROXY=https://goproxy.io,direct
source /etc/profile
```
