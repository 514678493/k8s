### hostname

修改 

hostnamectl set-hostname your-new-host-name

 查看

hostnamectl status

设置 解析

echo "127.0.0.1 $\(hostname\)" &gt;&gt; \/etc\/hosts

### 阿里源

cat &lt;&lt;EOF &gt; \/etc\/apt\/sources.list.d\/kubernetes.list

deb https:\/\/mirrors.aliyun.com\/kubernetes\/apt\/ kubernetes-xenial main

EOF

_apt-get update_

_apt-get install kubeadm_

### 初始化

kuadm init

mkdir -p $HOME\/.kube

sudo cp -i \/etc\/kubernetes\/admin.conf $HOME\/.kube\/config

sudo chown $\(id -u\):$\(id -g\) $HOME\/.kube\/config

### 加入节点

kubeadm join 192.168.129.130:6443 --token nc37kv.2fe8qi90utl8kbtf \

--discovery-token-ca-cert-hash sha256:96db2d839fa15465f619f6b76075e9cae868a6793892d4f4f971a28521ff5820

