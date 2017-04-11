## 查看当前系统Java版本
执行 `/usr/libexec/java_home -verbose`
## 安装jenv与配置
1. `brew install jenv`
2. 配置环境变量，在`~/.bash_profile`文件中添加：
```
export PATH="$HOME/.jenv/bin:$PATH"
#To enable shims and autocompletion add to your profile:
if which jenv > /dev/null; then eval "$(jenv init -)"; fi
#To use Homebrew's directories rather than ~/.jenv add to your profile:
export JENV_ROOT=/usr/local/opt/jenv
```
或者使用bash命令行的方式：
```
echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(jenv init -)"' >> ~/.bash_profile
```
3. 使配置文件生效`source ~/.bash_profile`
4. 使用jenv add加入Java版本，使用`sudo`，如不使用sudo会出现`ln: /usr/local/opt/jenv/versions/oracle64-1.7.0.51: No such file or directory`错误
```
wuyukai:~ wuyukai$ sudo jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_60.jdk/Contents/Home
Password:
oracle64-1.8.0.60 added
1.8.0.60 added
1.8 added
wuyukai:~ wuyukai$ sudo jenv add /Library/Java/JavaVirtualMachines/jdk1.7.0_80.jdk/Contents/Home
oracle64-1.7.0.80 added
1.7.0.80 added
1.7 added
```
5. 单个项目Java版本设置`sudo jenv local 1.7.0.80`,该项具体版本号根据`sudo jenv versions`设置。
6. 全局Java版本设置`sudo jenv global 1.7.0.80`
