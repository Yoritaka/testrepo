# 見出しTEST h1
## 見出しTEST h2
### 見出しTEST h3




# R∞ install gide



---
## WEB Server 
### httpd install
##### yum
    
---
### Elasticsearch install
##### yumでjavaのinstall
    $ sudo yum install java-1.8.0-openjdk-devel
##### rpmパッケージのimport(署名キーのインポート)
    $ sudo rpm --import https://packages.elastic.co/GPG-KEY-elasticsearch
##### リポジトリーの追加
    $ sudo vi /etc/yum.repos.d/elasticsearch.repo
##### 編集内容
    [elasticsearch-1.7]
    name=Elasticsearch repository for 1.7.x packages
    baseurl=http://packages.elastic.co/elasticsearch/1.7/centos
    gpgcheck=nstall1
    gpgkey=http://packages.elastic.co/GPG-KEY-elasticsearch
    enabled=1
##### リポジトリーの追加(こっちでもOK)
    $ sudo sh -c  "echo -e '[elasticsearch-1.7]\nname=Elasticsearch repository for 1.7.x packages\nbaseurl=http://packages.elastic.co/elasticsearch/1.7/centos\ngpgcheck=1\ngpgkey=http://packages.elastic.co/GPG-KEY-elasticsearch\nenabled=1' > /etc/yum.repos.d/elasticsearch.repo"
##### Elasticsearchのインストール
    $ sudo yum install elasticsearch
##### ディレクトリの確認
    cd /etc/elasticsearch/


## AP Server
### tomcat8 install


##### setting
###### catalina.properties
*before style
    tomcat.util.scan.StandardJarScanFilter.jarsToScan=\
    log4j-core*.jar,log4j-taglib*.jar,log4javascript*.jar,slf4j-taglib*.jar

*after style
    tomcat.util.scan.StandardJarScanFilter.jarsToScan=log4j-core*.jar,log4j-taglib*.jar

###### server.xml
*before style
      <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />

*after style(add comment out)
    <!--
      <Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" />
    -->

*before style
    <!-- Define an AJP 1.3 Connector on port 8009 -->
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />

*after style
    <!-- Define an AJP 1.3 Connector on port 8009 -->
    <Connector port="8009" protocol="AJP/1.3" proxyPort="443" scheme="https" secure="true" />

###### tomcat8.conf
*before style
    # You can pass some parameters to java here if you wish to
    #JAVA_OPTS="-Xminf0.1 -Xmaxf0.3"
    

*after style
    # You can pass some parameters to java here if you wish to
    #JAVA_OPTS="-Xminf0.1 -Xmaxf0.3"
    JAVA_OPTS="-Xmx6g -verbose:gc -Xloggc:/var/log/tomcat8/gc.log -XX:+PrintGCDetails"

###### tomcat-users.xml
*before style
    <user username="tomcat" password="<must-be-changed>" roles="tomcat"/>
    <user username="both" password="<must-be-changed>" roles="tomcat,role1"/>
    <user username="role1" password="<must-be-changed>" roles="role1"/>

after style
    <user username="tomcat" password="tomcat" roles="tomcat"/>
    <user username="both" password="tomcat" roles="tomcat,role1"/>
    <user username="role1" password="tomcat" roles="role1"/>

###### web.xml(変更なし?)
