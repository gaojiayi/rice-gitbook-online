# 打包部署

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption><p>rice集群部署</p></figcaption></figure>

## 打包

因为Rice暂时还没有提交到公共的maven仓库，所以这边是采用手动打包的方式来引入到项目中。

```
git clone git@github.com:gaojiayi/RICE.git

cd rice-distribution

mvn -X clean package assembly:single

```

根据控制台提示，如下显示表示已成功build

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

在target目录下会生成3个压缩包

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

## 搭建控制器



## 搭建控制台

## 搭建调度器集群

## 处理器集群
