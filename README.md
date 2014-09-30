maven installation
------------------------

```
pushd /usr/local/lib
sudo wget http://mirror.cc.columbia.edu/pub/software/apache/maven/maven-3/3.2.3/binaries/apache-maven-3.2.3-bin.tar.gz
sudo tar -xvf apache-maven-3.2.3-bin.tar.gz
sudo rm apache-maven-3.2.3-bin.tar.gz
sudo ln -s apache-maven-3.2.3 apache-maven
popd

echo "export M2_HOME=/usr/local/lib/apache-maven" >> ~/.bashrc
echo "export PATH=\$PATH:\$M2_HOME/bin" >> ~/.bashrc
```

Thrift
---------------

```
sudo apt-get -y install libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev ant python-dev
```

Bigtop
------------------
```
wget -O- http://archive.apache.org/dist/bigtop/bigtop-0.7.0/repos/GPG-KEY-bigtop | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/bigtop.list http://archive.apache.org/dist/bigtop/bigtop-0.7.0/repos/quantal/bigtop.list
sudo apt-get update
sudo apt-get install bigtop-utils
sudo apt-get install hadoop-hdfs
sudo apt-get install hadoop-conf-pseudo
sudo /etc/init.d/hadoop-hdfs-namenode init
sudo service hadoop-hdfs-namenode start
sudo service hadoop-hdfs-datanode start
```

Tachyon on HDFS
-------------------------

```
mvn -DskipTests -Dhadoop.version=2.0.6-alpha package
sudo -u hdfs hadoop fs -chmod +rw /
# replace export TACHYON_UNDERFS_ADDRESS=hdfs://localhost:8020
./bin/tachyon format
./bin/tachyon-start.sh local
./bin/tachyon tfs copyFromLocal /etc/debian_version /debian_version
hadoop fs -cat /tmp/tachyon/data/*
```

