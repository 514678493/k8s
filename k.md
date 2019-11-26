### hostname

修改

hostnamectl set-hostname new-host-name

查看

hostnamectl status

设置 解析

echo "127.0.0.1 $\(hostname\)" &gt;&gt; \/etc\/hosts

关闭交换控件

swapoff -a

### 阿里源

cat &lt;&lt;EOF &gt; \/etc\/apt\/sources.list.d\/kubernetes.list

deb https:\/\/mirrors.aliyun.com\/kubernetes\/apt\/ kubernetes-xenial main

EOF

curl -s https:\/\/mirrors.aliyun.com\/kubernetes\/apt\/doc\/apt-key.gpg \| sudo apt-key add -

_apt-get update_

apt-get install -y kubelet kubeadm kubectl

\#禁止更新

apt-mark hold kubelet kubeadm kubectl

### 初始化

kuadm init   --pod-network-cidr=10.244.0.0\/16

mkdir -p $HOME\/.kube

sudo cp -i \/etc\/kubernetes\/admin.conf $HOME\/.kube\/config

sudo chown $\(id -u\):$\(id -g\) $HOME\/.kube\/config

### 加入节点

kubeadm join 192.168.129.130:6443 --token nc37kv.2fe8qi90utl8kbtf \

--discovery-token-ca-cert-hash sha256:96db2d839fa15465f619f6b76075e9cae868a6793892d4f4f971a28521ff5820

### 获取节点

kubectl get nodes -o wide

### 删除节点

kubectl delete node demo-worker-x-x

### **获得 join命令参数**

kubeadm token create --print-join-command

### 重置节点

kubeadm reset

设置开机启动

systemctl enable kubelet

查看images

kubeadm config images list

