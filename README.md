# 見出し h1
## 見出し h2
### 見出し h3

## R∞ install gide
---
# Elasticsearch install
* 1.yumでjavaのinstall
    $ sudo yum install java-1.8.0-openjdk-devel
* 1.rpmパッケージのimport(署名キーのインポート)
    $ sudo rpm --import https://packages.elastic.co/GPG-KEY-elasticsearch
* 1.リポジトリーの追加
    $ sudo vi /etc/yum.repos.d/elasticsearch.repo
  * 編集内容
    [elasticsearch-1.7]
    name=Elasticsearch repository for 1.7.x packages
    baseurl=http://packages.elastic.co/elasticsearch/1.7/centos
    gpgcheck=nstall1
    gpgkey=http://packages.elastic.co/GPG-KEY-elasticsearch
    enabled=1
* 1.リポジトリーの追加(こっちでもOK)
    $ sudo sh -c  "echo -e '[elasticsearch-1.7]\nname=Elasticsearch repository for 1.7.x packages\nbaseurl=http://packages.elastic.co/elasticsearch/1.7/centos\ngpgcheck=1\ngpgkey=http://packages.elastic.co/GPG-KEY-elasticsearch\nenabled=1' > /etc/yum.repos.d/elasticsearch.repo"
* 1.Elasticsearchのインストール
    $ sudo yum install elasticsearch
* 1.ディレクトリの確認
    cd /etc/elasticsearch/
