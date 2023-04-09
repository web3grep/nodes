# INSTALL OKC


### update system

    apt update && apt upgrade -y

### install packages

    sudo apt install build-essential apt-transport-https lsb-release ca-certificates curl gnupg -y

### install  go

    ver="1.20.1" # задаем версию
    cd $HOME
    wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
    sudo rm -rf /usr/local/go
    sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
    rm "go$ver.linux-amd64.tar.gz"
    echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> ~/.bash_profile
    source ~/.bash_profile
    go version
### install rocksdb

    wget https://github.com/facebook/rocksdb/archive/v6.27.3.tar.gz
    tar xfz v6.27.3.tar.gz
    cd rocksdb-6.27.3/
    make shared_lib
    sudo make install-shared
