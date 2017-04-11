# 如果之前配置后过出现问题
首先，清除所有的 key-pair  
```
ssh-add -D
rm -r ~/.ssh
```  
删除你在 github 中的 public-key
# 如果是第一次配置
## 生成 ssh 密钥对
```
ssh-keygen -t rsa -C "xxx@xxx.com"
chmod 0700 ~/.ssh
chmod 0600 ~/.ssh/id_rsa*
```
其中一路`⏎`键使用默认的设置，不设置密码及路径。
## 配置公钥到 GitHub
复制 id_rsa.pub 文件中的内容，粘贴到 github 的 SSH Key 中。
## 验证连接
在终端 `ssh -T git@github.com`
## 设置 username 和 email
```
git config --global user.name "wuyukai879293"
git config --global user.email "wuyukai879293@gmail.com"
```
## 添加远程地址
`git remote add origin git@github.com:wuyukai879293/personal-knowledge-management.git`
在 config 文件中，origin 就代表着远程仓库的地址
# 上传项目到远程仓库
上传之前先将项目 pull 到本地，防止远程文件修改上传失败，并且当远程仓库文件发生变更时，必须先 pull 后才能提交 push。
`git pull origin master`  
如果出现错误，使用`git pull origin <branch-name> --allow-unrelated-histories`  
最后使用 push 将项目上传到远程仓库`git push origin master`  
## 一些常用的 git 指令
`git status`,`git add <file name>`,`git commit -m "commit msg"`等。
## Atom 中 git plus 插件的配置
1. 在 Atom 中设置 git 的路径，可以通过在终端输入`which git`来得到 git 路径。
2. 使用`⌘ + ⇧ + H` 快捷键弹出 Git Plus 窗口。
3. 首次次使用 push 指令时需要先在终端运行`git push --set-upstream origin master`来为本地分支定义一个远程跟踪分支相关联，之后便可直接使用 git push，具体原理参照[Git push与pull的默认行为](https://segmentfault.com/a/1190000002783245)一文中 upstream & downstream 部分。

## 参考
[git 系列参考-git 历险记](http://www.infoq.com/cn/news/2011/03/git-adventures-index-commit?utm_source=infoq&utm_campaign=user_page&utm_medium=link)
