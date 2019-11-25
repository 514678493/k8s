移除旧版本

sudo apt-get remove docker docker-engine docker.io containerd runc

安装

sudo apt-get install \

apt-transport-https \

ca-certificates \

curl \

gnupg-agent \

software-properties-common

curl -fsSL https:\/\/download.docker.com\/linux\/ubuntu\/gpg \| sudo apt-key add -



sudo add-apt-repository \

 "deb \[arch=amd64\] https:\/\/download.docker.com\/linux\/ubuntu \

 $\(lsb\_release -cs\) \

 stable"



sudo apt-get update



 sudo apt-get install docker-ce docker-ce-cli containerd.io

