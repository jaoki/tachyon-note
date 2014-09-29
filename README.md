maven installation
------------------------

pushd /usr/local/lib
sudo wget http://mirror.cc.columbia.edu/pub/software/apache/maven/maven-3/3.2.3/binaries/apache-maven-3.2.3-bin.tar.gz
sudo tar -xvf apache-maven-3.2.3-bin.tar.gz
sudo rm apache-maven-3.2.3-bin.tar.gz
sudo ln -s apache-maven-3.2.3 apache-maven
popd

echo "export M2_HOME=/usr/local/lib/apache-maven" >> ~/.bashrc
echo "export PATH=\$PATH:\$M2_HOME/bin" >> ~/.bashrc

Thrift
---------------
sudo apt-get -y install libboost-dev libboost-test-dev libboost-program-options-dev libevent-dev automake libtool flex bison pkg-config g++ libssl-dev ant python-dev


