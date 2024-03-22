## we will create a kubernates cluster with one control plain and two worker nodes.

## step 1: set hostname

```bash
    sudo hostnamectl set-hostname k8s-control
    sudo hostnamectl set-hostname k8s-worker1
    sudo hostnamectl set-hostname k8s-worker2
```

## Add hosts to all the instances
```bash
    nano /etc/hosts
```

```
    10.0.2.34 k8s-worker1
    10.0.2.99 k8s-worker2
    10.0.2.93 k8s-control
```

## Add some libraries to all the instances
```bash
    cat << EOF | sudo teee /etc/modules-load.d/containerd.conf
    overlay
    br_netfilter
    EOF
```

```bash
    sudo modprobe overlay
    sudo modprobe br_netfilter
```

```bash
    cat <<EOF | sudo tee /etc/sysctl.d/99-kubernetes-cri.conf
    net.bridge.bridge-nf-call-iptables=1
    net.ipv4.ip_forward=1
    net.bridge.bridge-nf-call-ip6tables=1
    EOF
```

```bash
    sudo apt-get install curl
    sudo apt-get install ca-certificate
    sudo apt-get install gnupg
```
install containerd
```bash
    echo \
    "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
    sudo tee /etc/apt/source.list.d/docker.list > /dev/null
```

```bash
    sudo apt-get update && sudo apt-get install -y containerd.io
```

```bash
    sudo mkdir -p /etc/containerd
```

## add config for containerd
```bash
    sudo containerd config default | sudo tee /etc/containerd/config.toml
```

```bash
    sudo swapoff -a
    sudo systemctl restart containerd
    curl -s https://packages.cloud.google.com/apt/docs/apt-key.gpg | sudo apt-key add -
    sudo  tee << EOF | sudo tee /etc/apt/sources.list.d/kuberneted.list
    deb https://apt.kubernetes.io/ kubernetes-xenial main
    EOF
```

```bash
    sudo apt-get update
    sudo apt-get install -y kubelet=1.24.0-00 kubeadm=1.24.0-00 kubectl=1.24.0-00
```

## not update on apt update
```bash
    sudo apt-mark hold kubectl kubeadm kubelet
```

## run on control plain
```bash
    sudo sysctl --system
    sudo kubeadm init --pod-network-cidr 192.168.0.0/16 --kubernetes-version 1.24.0
```

```bash
    kubectl get all
```

```bash
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
    kubectl get nodes
```

```bash
    kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.1/manifest/calico.yaml
    kubectl get nodes
```

```bash
    kubectl get all
```

```
    kubeadm token create --print-join-command
```

## run the response from above command on the worker nodes

```bash
    kubectl get nodes
```