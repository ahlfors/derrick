# Derrick简介
Derrick可以通过类似buildpack的机制动态探测代码使用的框架、平台与类库，并动态的生成Dockerfile、docker-compose并部署到阿里云容器服务。       

# 支持的语言  
<a href="http://gitlab.alibaba-inc.com/cos/derrick/blob/master/docs/nodejs.md">Node.js</a>      
<a href="http://gitlab.alibaba-inc.com/cos/derrick/blob/master/docs/python.md">Python</a>    

# 支持命令



```
Usage:
    derrick install <platform-git-repo>
    derrick init [<platform>]
    derrick test
    derrick publish
    derrick serve
    derrick deploy


Options:
  -h --help         # Print this info and generator's options and usage
  -v --version      # Print version

```

# 使用方式   
安装derrick的<a href="http://gitlab.alibaba-inc.com/cos/derrick/blob/master/dist/derrick-0.0.1-py2.7.egg" target="_blank">egg包</a>  

```
  easy_install derrick-0.0.1-py2.7.egg
```

# 安装buildpack包   

```
  # 安装nodejs的buildpack包
  derrick install git@gitlab.alibaba-inc.com:cos/buildpack-nodejs.git
  # 安装python的buildpack包
  derrick install git@gitlab.alibaba-inc.com:cos/buildpack-python.git
```

# 测试

Node.js
```
git clone  git@gitlab.alibaba-inc.com:zhongwei.lzw/nodejs-demo.git
cd nodejs-demo
derrick init nodejs
docker build -t nodejs-test:latest
docker run -d -p 3000:3000 nodejs-test:latest
# 开启浏览器访问127.0.0.1:3000  
```

Python uwsgi
```
git clone git@gitlab.alibaba-inc.com:zhongwei.lzw/python-demo.git
cd python-demo
derrick init python
docker build -t python-test:latest
docker run -d -p 8080:80 python-test:latest
# 开启浏览器访问127.0.0.1:8080
```