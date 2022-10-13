# 编译部署

<figure><img src=".gitbook/assets/image (4) (2).png" alt=""><figcaption><p>rice集群部署</p></figcaption></figure>

## 编译

因为Rice暂时还没有提交到公共的maven仓库，所以这边是采用手动打包的方式来引入到项目中。

```
git clone git@github.com:gaojiayi/RICE.git

mvn clean install -Dmaven.test.skip=true

cd rice-distribution

mvn -X clean package assembly:single

```

根据控制台提示，如下显示表示已成功build

<figure><img src=".gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

在target目录下会生成3个压缩包

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

## Mysql

[https://github.com/gaojiayi/RICE/tree/master/db](https://github.com/gaojiayi/RICE/tree/master/db)   将db目录下的sql脚本在mysql中执行，初始化数据库

## 搭建控制器

**以rice-bin.tar.gz为例**

<pre><code><strong>解压  tar -zxvf rice-bin.tar.gz
</strong>
cd conf
</code></pre>

编辑配置文件 rice-controller.properties，配置所有控制器的ip地址以及业务端口

```
allControllerAddressStr=127.0.0.1:8900,127.0.0.1:8901,127.0.0.1:8902

```

```
cd  ../bin

启动  ./ricecontroller
```

如果看到这样的输出信息 说明已经启动

![](<.gitbook/assets/image (1).png>)

```
关闭控制器 ./riceshutdown controller
```

接下来在其他的控制器的host上做相同的操作部署，组成控制器集群，控制器数量不少于3台。

后续关于控制器的配置 将在后续介绍。

## 搭建控制台

在控制器的主机上

* **安装nginx**
* **编译**

<pre data-line-numbers><code><strong> cd rice-manage-ui
</strong><strong> pnpm install
</strong><strong> pnpm run build</strong></code></pre>

看到这个输出说明已经成功编译

![](<.gitbook/assets/image (3).png>)

* **部署至nginx**

`1 将dist整个文件夹上传到服务Nginx的/usr/local/nginx/html 这个目录里`

`2 vi nginx.conf 进入nginx配置文件中，location里的root就是运行index.html的位置`

`3 最后重启nginx        ./nginx -s reload`

*   **打开浏览器，访问nginx配置端口**

    ****

****![](.gitbook/assets/image.png)****

## 搭建调度器集群

## 处理器集群
