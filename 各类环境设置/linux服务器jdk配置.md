# JDK环境配置
1. 登录远程服务器，新建目录
```
cd /usr
mkdir java
```    
2. 将下载的jdk文件上传到服务器（通过scp命令或终端建立连接sftp传送）
3. cd进入到文件路径，将jdk解压`tar -zxvf jdk-8u112-linux-x64.tar.gz`,将jdk名字按找自己的版本修改
4. 删除上传的压缩包`rm -rf jdk-8u112-linux-x64.tar.gz`
5. 配置环境变量  
    - 打开配置文件：`vi /etc/profile`
    - 再profile文件最后添加
    ```
    #set java environment
    JAVA_HOME=/usr/java/jdk1.8.0_112
    JRE_HOME=/usr/java/jdk1.8.0_112/jre
    CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
    PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
    export JAVA_HOME JRE_HOME CLASS_PATH PATH
    ```
    - 使环境变量生效`source /etc/profile`  

6. 验证JDK，输入：`java -version`
