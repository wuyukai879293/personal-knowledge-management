# 如果之前配置后过出现问题
首先，清除所有的key-pair  
```
ssh-add -D
rm -r ~/.ssh
```  
删除你在github中的public-key
# 如果是第一次配置
## 生成ssh密钥对
```
ssh-keygen -t rsa -C "xxx@xxx.com"
chmod 0700 ~/.ssh
chmod 0600 ~/.ssh/id_rsa*
```
其中一路`⏎`键使用默认的设置，不设置密码及路径。
## 配置公钥到GitHub
复制 id_rsa.pub 文件中的内容，粘贴到github的SSH Key中。
## 验证连接
在终端 `ssh -T git@github.com`
## 设置用户名和email
```
git config --global user.name "wuyukai879293"
git config --global user.email "wuyukai879293@gmail.com"
```
## 添加远程地址
`git remote add origin git@github.com:wuyukai879293/personal-knowledge-management.git`
在config文件中，origin就代表着远程仓库的地址
# 上传项目到远程仓库
上传之前先将项目pull到本地，防止远程文件修改上传失败
`git pull origin master`  
如果出现错误，使用`git pull origin <branch-name> --allow-unrelated-histories`  
最后使用push将项目上传到远程仓库`git push origin master`  
## 一些常用的 git 指令
`git status`,`git add <file name>`,`git commit -m "commit msg"`等。
## 参考
[git系列参考-git历险记](!http://www.infoq.com/cn/news/2011/03/git-adventures-index-commit?utm_source=infoq&utm_campaign=user_page&utm_medium=link)
